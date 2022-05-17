+++
title = "HugoでMarkdownリンクをカスタマイズする方法"
description = "Hugo Markdownリンクに相互参照サポートとリンクアイコンを追加する方法"

date = "2022-05-15T12:23:48+09:00"                                          # manually adjust to local timezone
#lastmod = "2022-04-07T17:53:01+00:00"                                       # manually adjust to local timezone

#aliases = [""]
slug = "how-to-customize-markdown-links-hugo"
translationKey = "how-to-customize-markdown-links-hugo-2022135"
relCanonical = "https://im.youronly.one/techmagus/ja/codebits/how-to-customize-markdown-links-hugo-2022135/"
#disqus_url = ""                                                    # no use case in sites by Yelosan Publishing (YourOnly.One)
#disqus_identifier = ""                                             # set if slug date of this content is different from main translation (en-PH)

syndications = ["https://twitter.com/YourOnlyONEofcl/status/1525681470022508544", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/657387235430510", "https://diasp.org/posts/f23d3ae0b62f013a6afb28a1592b385a", "https://mastodon.social/web/@youronlyone/108303916946754498"]

channels = ["techmagus"]
categories = ["howto"]
keywords = ["Hugo", "How To", "Markdown Links", "Link Icons", "Cross Reference", "YourOnlyOne", "YourOnly.One", "techmagus"]
#series = [""]
tags = ["hugo"]

comments = true
#weight = ""

#featured = true
#math = true
toc = true

#audio = [""]                                                          # used for og:audio, etc.
images = ["https://img.youronly.one/h/hugo-markdown-link-render.webp"]                 # used for og:images, etc.; first image is cover image
#videos = ["https://www.youtube.com/watch?v="]                         # used for og:video, etc.

type = "article"                                                             # article, sitepage, review

draft = false

#license = ""                                                         # only set if the post license is not the same as the site license

# For /yuki/ choose one and remove everything else
[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (Yuki | 雪亮)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}で{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}リンクをレンダリングする方法をカスタマイズする方法をお探しですか？ リンクアイコンを追加したいですか？ または、（古い方法） `{{</* ref */>}}`を使用せずに内部相互参照のサポートを追加するのはどうですか？

<!--more-->

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}には、「カスタムテンプレートが<bdi lang="en">Markdown</bdi>レンダリング機能をオーバーライドできるようにする」 [^hugo-markdown-render-hooks] {{% quote type="name" lang="en" %}}Markdown{{% /quote %}}レンダリングフックと呼ばれる機能があります。 現在、一般的に要求される4つの{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}レンダリング領域をサポートしています。

- <bdi lang="en">codeblock</bdi>
- <bdi lang="en">heading</bdi>
- <bdi lang="en">image</bdi>
- <bdi lang="en">link</bdi>

この投稿では、{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンクのレンダリング方法を変更します。

[^hugo-markdown-render-hooks]: Hugo: [Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## 特徴

- 通常の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンク形式を使用して、{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}内で相互参照します
  - `{{</* ref */>}}`と`{{％/* relref */％}}`、またはそれらのバリエーションは過去のものです
  - コンテンツのタイトルを自動的に使用する
  - 多言語サポート
  - {{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンクのテキストとタイトルのサポート
  - URIフラグメントのサポートあり
- {{% quote type="name" lang="en" %}}JavaScript{{% /quote %}}を使用せずにリンクアイコンを追加する
  - 内部の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンクのサポート付き

## 相互参照を追加

1. このディレクトリに`render-link.html`というファイルを作成します`/layouts/_default/_markup/`
1. 以下のコードを追加します。

    ```go-html-template
    {{- $url := (urls.Parse .Destination) -}}
    {{- $internal := site.GetPage .Destination -}}
    {{- $fragment := $url.Fragment -}}
    {{- with $fragment -}}{{ $fragment = printf "#%s" $fragment }}{{- end -}}
    {{- $destination := printf "%s%s" (or $internal.RelPermalink .Destination) $fragment -}}
    <a href="{{ $destination | safeURL }}"{{ with or .Title $internal.LinkTitle .Text }} title="{{ . }}"{{ end }}{{ if not $internal }} rel="noopener external"{{ end }}>{{ or .Text .Title $internal.LinkTitle | safeHTML }}</a>
    ```

それでおしまい。

### 使い方

次の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンク

  ```markdown {linenos=false}
  - [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](20181210-browser-wars-iii)
  - [](/20181210-browser-wars-iii)
  - [テキスト付き](20181210-browser-wars-iii)
  - [](20181210-browser-wars-iii "タイトル付き")
  - [テキスト、タイトル、フラグメント付き](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "テキスト、タイトル、フラグメント付き")
  ```

`ja`で次のようにレンダリングされます：

- [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [テキスト付き](20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "タイトル付き")
- [テキスト、タイトル、フラグメント付き](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "テキスト、タイトル、フラグメント付き")

#### 警告

現在、次の形式はサポートされていません。

```markdown {linenos=false}
- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
```

間違ったリンクで次のようにレンダリングされます。

- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)

代わりに、生成されたパーマリンクを次のように使用します（プレフィックス `/`が重要です）：

```markdown {linenos=false}
- [ブラウザ戦争IIIフロント：ブラウザエンジン](/ja/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)
```

次のようにレンダリングされます：

- [ブラウザ戦争IIIフロント：ブラウザエンジン](/ja/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)

#### それを改善

上記のコードを自由に改善して、コミュニティに共有してください。 あなたが適切にクレジットされるようにあなたのウェブサイトと名前を提供してください。

## リンクアイコンを追加する

リンクアイコンを追加するには、以下の手順に従います。

1. ファイル`render-link.html`（前のセクションで作成）を開きます
1. コード全体を次のように置き換えます。

    ```go-html-template
    {{- $url := (urls.Parse .Destination) -}}
    {{- $internal := site.GetPage .Destination -}}

    {{- $fragment := $url.Fragment -}}
    {{- with $fragment -}}{{ $fragment = printf "#%s" $fragment }}{{- end -}}
    {{- $destination := printf "%s%s" (or $internal.RelPermalink .Destination) $fragment -}}

    {{- $chat := or (strings.HasPrefix .Destination "irc://") (strings.HasPrefix .Destination "ircs://") (strings.HasPrefix .Destination "irc6://") (strings.HasPrefix .Destination "jabber://") (strings.HasPrefix .Destination "xmpp://") (strings.HasPrefix .Destination "discord://") (strings.HasPrefix .Destination "skype://") -}}
    {{- $ftp := or (strings.HasPrefix .Destination "ftp://") (strings.HasPrefix .Destination "aftp://") -}}
    {{- $mail := strings.HasPrefix .Destination "mailto://" -}}
    {{- $magnet := strings.HasPrefix .Destination "magnet://" -}}
    {{- $remote := or (strings.HasPrefix .Destination "telnet://") (strings.HasPrefix .Destination "ssh://") (strings.HasPrefix .Destination "sftp://") (strings.HasPrefix .Destination "git://") (strings.HasPrefix .Destination "svn://") (strings.HasPrefix .Destination "bzr://") -}}
    {{- $tel := strings.HasPrefix .Destination "tel://" -}}

    {{- $books := or (strings.HasSuffix .Destination ".epub") (strings.HasSuffix .Destination ".mobi") -}}
    {{- $docs := or (strings.HasSuffix .Destination ".pdf") (strings.HasSuffix .Destination ".txt") (strings.HasPrefix .Destination "doi://") -}}
    {{- $compressed := or (strings.HasSuffix .Destination ".zip") (strings.HasSuffix .Destination ".7z") (strings.HasSuffix .Destination ".7zip") (strings.HasSuffix .Destination ".rar") (strings.HasSuffix .Destination ".tar") (strings.HasSuffix .Destination ".gz") (strings.HasSuffix .Destination ".gzip") -}}

    {{- $icon := "" -}}
    {{- if $chat -}}{{ $icon = "chat" }}
      {{- else if $ftp -}}{{ $icon = "ftp" }}
      {{- else if $mail -}}{{ $icon = "mail" }}
      {{- else if $magnet -}}{{ $icon = "magnet" }}
      {{- else if $remote -}}{{ $icon = "remote" }}
      {{- else if $tel -}}{{ $icon = "tel" }}
      {{- else if $books -}}{{ $icon = "books" }}
      {{- else if $docs -}}{{ $icon = "docs" }}
      {{- else if $compressed -}}{{ $icon = "compressed" }}
      {{- else if not $internal -}}{{ $icon = "external" }}
    {{- end -}}

    <a href="{{ $destination | safeURL }}"{{ with or .Title $internal.LinkTitle .Text }} title="{{ . }}"{{ end }}{{ with $icon }} class="icon_{{ . }}"{{ end }}{{ if not $internal }} rel="noopener external"{{ end }}>{{ or .Text .Title $internal.LinkTitle | safeHTML }}</a>
    ```

1. スタイルシートファイルに次を追加します。

    ```css
    /********************
    ** BGN: Link icons **
    ********************/
      [class^="icon_"]::after {
        display: inline-block;
        text-decoration: none;
        white-space: pre-wrap;
      }
      .icon_external::after   { content: "\20\1F517"      /* 🔗 */ }
      .icon_chat::after       { content: "\20\1F4AC"      /* 💬 */ }
      .icon_ftp::after        { content: "\20\23EC"       /* ⏬ */ }
      .icon_mail::after       { content: "\20\1F4E7"      /* 📧 */ }
      .icon_magnet::after     { content: "\20\1F9F2"      /* 🧲 */ }
      .icon_remote::after     { content: "\20\1F4BB"      /* 💻 */ }
      .icon_tel::after        { content: "\20\260E\FE0F"  /* ☎️ */ }
      .icon_books::after      { content: "\20\1F4D6"      /* 📖 */ }
      .icon_docs::after       { content: "\20\1F4C4"      /* 📄 */ }
      .icon_compressed::after { content: "\20\1F5DC\FE0F" /* 🗜️ */ }
    /********************
    ** END: Link icons **
    ********************/
    ```

### 使い方

次の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンク

  ```markdown {linenos=false}
  - [example.com#fragment](https://example.com/#fragment)
  - [irc](irc://example.com) | [ircs](ircs://example.com) | [irc6](irc6://example.com) | [jabber](jabber://example.com) | [xmpp](xmpp://example.com) | [discord](discord://example.com) | [skype](skype://example.com)
  - [ftp](ftp://example.com) | [aftp](aftp://example.com)
  - [mail](mailto://example.com)
  - [magnet](magnet://example.com)
  - [telnet](telnet://example.com) | [ssh](ssh://example.com) | [sftp](sftp://example.com) | [git](git://example.com) | [svn](svn://example.com) | [bzr](bzr://example.com)
  - [tel](tel://example.com)
  - [pdf](https://example.com/file.pdf) | [txt](https://example.com/file.txt) | [doi](doi://example.com)
  - [epub](https://example.com/file.epub) | [mobi](https://example.com/file.mobi)
  - [zip](https://example.com/file.zip) | [7z](https://example.com/file.7z) | [7zip](https://example.com/file.7zip) | [rar](https://example.com/file.rar) | [tar](https://example.com/file.tar) | [gz](https://example.com/file.gz) | [tar.gz](https://example.com/file.tar.gz) | [gzip](https://example.com/file.gzip) | [tar.gzip](https://example.com/file.tar.gzip)
  ```

次のようにレンダリングされます：

- [example.com#fragment](https://example.com/#fragment)
- [irc](irc://example.com) | [ircs](ircs://example.com) | [irc6](irc6://example.com) | [jabber](jabber://example.com) | [xmpp](xmpp://example.com) | [discord](discord://example.com) | [skype](skype://example.com)
- [ftp](ftp://example.com) | [aftp](aftp://example.com)
- [mail](mailto://example.com)
- [magnet](magnet://example.com)
- [telnet](telnet://example.com) | [ssh](ssh://example.com) | [sftp](sftp://example.com) | [git](git://example.com) | [svn](svn://example.com) | [bzr](bzr://example.com)
- [tel](tel://example.com)
- [pdf](https://example.com/file.pdf) | [txt](https://example.com/file.txt) | [doi](doi://example.com)
- [epub](https://example.com/file.epub) | [mobi](https://example.com/file.mobi)
- [zip](https://example.com/file.zip) | [7z](https://example.com/file.7z) | [7zip](https://example.com/file.7zip) | [rar](https://example.com/file.rar) | [tar](https://example.com/file.tar) | [gz](https://example.com/file.gz) | [tar.gz](https://example.com/file.tar.gz) | [gzip](https://example.com/file.gzip) | [tar.gzip](https://example.com/file.tar.gzip)

URI（Uniform Resource Identifier）スキームの公式リストは、IANAの公式Webサイトにあります。 [^uri-schemes-iana] ただし、すべての一般的なURIスキームが登録および/または送信されたわけではありません。たとえば、 `discord：//`や `bzr：//`（2022-05-13日付のIANAドキュメントの時点）。 とにかく、これらの人気のある未登録のURIスキームは上記のコードに含まれていました。

[^uri-schemes-iana]: IANA: [URI Schemes](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml)

お役に立てば幸いです。

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link="https://img.youronly.one/h/hugo-markdown-link-render.webp"
  linkrel="noopener"

  title="HugoでMarkdownリンクをカスタマイズする方法"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

---

注意：Google翻訳
