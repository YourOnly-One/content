+++
title = "Hugo markdownリンクに相互参照を追加する方法"
description = "Hugoでmarkdownリンクの相互参照サポートを追加する方法"

publishdate = 2022-05-20T20:24:27+09:00                                          # manually adjust to local timezone
lastmod = 2022-06-17T15:07:00+09:00                                       # manually adjust to local timezone

aliases = ["/ja/codebits/how-to-add-cross-reference-hugo-markdown-links-2022140", "/ja/codebits/hugo-render-link/how-to-add-cross-reference-hugo-markdown-links-2022140"]
slug = "how-to-add-cross-reference-hugo-markdown-links"
translationKey = "how-to-add-cross-reference-hugo-markdown-links-2022140"
relCanonical = "https://im.youronly.one/techmagus/ja/codebits/hugo/hugo-render-link/how-to-add-cross-reference-hugo-markdown-links-2022140/"
#disqus_url = ""                                                    # no use case in sites by Yelosan Publishing (YourOnly.One)
#disqus_identifier = ""                                             # set if slug date of this content is different from main translation (en-PH)

syndications = ["https://mastodon.social/@youronlyone/108375677574797367", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/pfbid02ZfsK99Hp9oNthMJdSgEMyGS3EiVKH8tqrHf5yKCAPdsPakvzvByUAJRyttNzyz4dl", "https://twitter.com/YourOnlyONEofcl/status/1530277663293595649"]

channels = ["techmagus"]
categories = ["howto"]
keywords = ["Hugo", "How To", "Markdown Links", "Cross Reference", "YourOnlyOne", "YourOnly.One", "techmagus"]
#series = [""]
tags = ["hugo"]

comments = true
#weight = ""

#featured = true
#math = true
toc = true

#audio = [""]                                                          # used for og:audio, etc.
images = ["images/h/hugo-markdown-link-render.webp"]                 # used for og:images, etc.; first image is cover image
#videos = ["https://www.youtube.com/watch?v="]                         # used for og:video, etc.

type = "article"                                                             # article, sitepage, review

#draft = false

#license = ""                                                         # only set if the post license is not the same as the site license

# For /yuki/ choose one and remove everything else
[[authors]]
  person = "yuki"
  #id = ""
  name = "謝雪矢（ゆきや）"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}であまり使用されない機能の1つは、レンダリングフックです。 この投稿では、レンダリングフックを使用して、リンクを作成する{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}のデフォルトの方法である `[文章](https://example.com#fragment "題名")`に内部相互参照サポートを追加します。

<!--more-->

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}の内部相互参照は通常、組み込みのショートコード `{{</* ref */>}}`または`{{%/* relref */%}}`を使用して行われますが、{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}バージョン0.62.0以降ご存知でしたか [^hugo-0.62.0] 推奨される方法は、レンダリングフックを使用することですか [^hugo-markdown-render-hooks]？

[^hugo-0.62.0]: [Hugo v0.62.0](https://github.com/gohugoio/hugo/releases/tag/v0.62.0 "Hugo v0.62.0")
[^hugo-markdown-render-hooks]: [Hugo: Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## 特徴

- {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}内で相互参照するには、通常の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンク形式を使用します
  - `{{</* ref */>}}`と`{{%/* relref */%}}`、またはそれらのバリエーションは過去のものです
  - コンテンツのタイトルを自動的に使用する
  - 多言語サポート
  - {{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンクのテキストとタイトルのサポート
  - URIフラグメントのサポートあり

## 新着情報

- 2022年6月17日：
  - 修正：`[text](./path/to/content/)`と`[text.ext](./path/to/file.ext)`の構文

- 2022年5月27日：
  - `[文章](./path/to/content/)`
  - `[text.ext](./path/to/file.ext)`
  - [使い方](#how-to-use)セクションを再編成

## 手順

1. このディレクトリに`render-link.html`というファイルを作成します`/layouts/_default/_markup/`
1. 以下のコードを追加します。

    ```go-html-template
    {{- $baseurl := urls.Parse site.BaseURL -}}
    {{- $url := urls.Parse .Destination -}}
    {{- $getpage := site.GetPage .Destination -}}
    {{- $internal := lt (len $url.Host) 1 -}} {{/* NOTE: internal links will always have an empty $url.Host */}}

    {{- $fragment := $url.Fragment -}}
    {{- with $fragment -}}{{ $fragment = printf "#%s" $fragment }}{{- end -}}

    {{- $destination := "" -}}
    {{- if $internal -}}
      {{- if (strings.HasPrefix $url.Path "./") -}}
        {{/* NOTE: for links starting with ./ */}}
        {{- $urltrimmed := strings.TrimPrefix "./" $url -}}
        {{- $destination = printf "%s://%s/%s%s" $baseurl.Scheme $baseurl.Host $urltrimmed $fragment -}}
      {{- else -}}
        {{/* NOTE: for internal links */}}
        {{- $destination = printf "%s%s" $getpage.RelPermalink $fragment -}}
      {{- end -}}
    {{- else -}}
      {{- $destination = .Destination -}}
    {{- end -}}

    <a href="{{ $destination | safeURL }}"{{ with or .Title $getpage.LinkTitle .Text }} title="{{ . }}"{{ end }}{{ if not $internal }} rel="noopener external"{{ end }}>{{ or .Text .Title $getpage.LinkTitle | safeHTML }}</a>
    ```

それでおしまい。

## 使い方 {#how-to-use}

### 伝統的

```markdown
- [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- [直接](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/ "題名")
- [#fragmentで直接](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/#fragment "題名")
- [＃フラグメントのみ](#fragment)
```

- [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- [直接](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/ "題名")
- [#fragmentで直接](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/#fragment "題名")
- [＃フラグメントのみ](#fragment)

### 新しい

#### 特別な

`[text](./path/to/content/)`形式は、現在の{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}の一部ではなく、同じ（サブ）ドメインの下で、Webサイトの別の部分へのリンクを作成する場合に役立ちます。 事業。 [](hugo-link-icons-markdown-links.md)もインストールされている場合、この形式では外部リンクアイコンは生成されません。

`[text.ext](./path/to/file.ext)`は、現在の{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}プロジェクトの内部または外部の同じ（サブ）ドメインでホストされているダウンロードリンクに役立ちます。

```markdown
- [贈り物を送る](./p/gift/)
- [link-icons.7z](./techmagus/dls/link-icons.7z)
```

- [贈り物を送る](./p/gift/)
- [link-icons.7z](./techmagus/dls/link-icons.7z)

#### ファイル拡張子なし

```markdown
- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "題名")
- [](/20181210-browser-wars-iii "題名")
- [文章](20181210-browser-wars-iii)
- [文章](/20181210-browser-wars-iii)
- [文章](20181210-browser-wars-iii "題名")
- [文章](/20181210-browser-wars-iii "題名")
```

- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "題名")
- [](/20181210-browser-wars-iii "題名")
- [文章](20181210-browser-wars-iii)
- [文章](/20181210-browser-wars-iii)
- [文章](20181210-browser-wars-iii "題名")
- [文章](/20181210-browser-wars-iii "題名")

#### ファイル拡張子付き

```markdown
- [](20181210-browser-wars-iii.md#fragment)
- [](/20181210-browser-wars-iii.md#fragment)
- [](20181210-browser-wars-iii.md#fragment "題名")
- [](/20181210-browser-wars-iii.md#fragment "題名")
- [Text＃fragment](20181210-browser-wars-iii.md#fragment)
- [Text＃fragment](/20181210-browser-wars-iii.md#fragment)
- [Text＃fragment](20181210-browser-wars-iii.md#fragment "題名")
- [Text＃fragment](/20181210-browser-wars-iii.md#fragment "題名")
```

- [](20181210-browser-wars-iii.md#fragment)
- [](/20181210-browser-wars-iii.md#fragment)
- [](20181210-browser-wars-iii.md#fragment "題名")
- [](/20181210-browser-wars-iii.md#fragment "題名")
- [Text＃fragment](20181210-browser-wars-iii.md#fragment)
- [Text＃fragment](/20181210-browser-wars-iii.md#fragment)
- [Text＃fragment](20181210-browser-wars-iii.md#fragment "題名")
- [Text＃fragment](/20181210-browser-wars-iii.md#fragment "題名")

### サポートされていません

ファイル拡張子がなく、 `＃fragment`を使用した内部リンクでは、間違ったリンクが生成されます。

```markdown
- [](20181210-browser-wars-iii#fragment)
- [](/20181210-browser-wars-iii#fragment)
- [](20181210-browser-wars-iii#fragment "題名")
- [](/20181210-browser-wars-iii#fragment "題名")
- [Text＃fragment](20181210-browser-wars-iii#fragment)
- [Text＃fragment](/20181210-browser-wars-iii#fragment)
- [Text＃fragment](20181210-browser-wars-iii#fragment "題名")
- [Text＃fragment](/20181210-browser-wars-iii#fragment "題名")
```

次の形式にも注意してください。

```markdown
- [link-icons.7z](/dls/link-icons.7z)
- [link-icons.7z](../../dls/link-icons.7z)
```

上記の代わりに、 `[文章](./path/to/file.ext)`を次のように使用します。`[link-icons.7z](./techmagus/dls/link-icons.7z)`は次のようにレンダリングされます。 [link-icons.7z](./techmagus/dls/link-icons.7z)

## それを改善

上記のコードを自由に改善して、コミュニティに共有してください。 あなたが適切にクレジットされるようにあなたのウェブサイトと名前を提供してください。

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link=""
  linkrel="noopener"

  title="HugoでMarkdownリンクをカスタマイズする方法"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
