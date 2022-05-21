+++
title = "Hugo Markdownリンクに相互参照を追加する方法"
description = "HugoでMarkdownリンクの相互参照サポートを追加する方法"

publishdate = "2022-05-20T20:24:27+09:00"                                          # manually adjust to local timezone
lastmod = "2022-05-20T20:24:27+09:00"                                       # manually adjust to local timezone

#aliases = [""]
slug = "how-to-add-cross-reference-hugo-markdown-links"
translationKey = "how-to-add-cross-reference-hugo-markdown-links-2022140"
relCanonical = "https://im.youronly.one/techmagus/codebits/how-to-add-cross-reference-hugo-markdown-links-2022140/"
#disqus_url = ""                                                    # no use case in sites by Yelosan Publishing (YourOnly.One)
#disqus_identifier = ""                                             # set if slug date of this content is different from main translation (en-PH)

#syndications = [""]

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
images = ["https://img.youronly.one/h/hugo-markdown-link-render.webp"]                 # used for og:images, etc.; first image is cover image
#videos = ["https://www.youtube.com/watch?v="]                         # used for og:video, etc.

type = "article"                                                             # article, sitepage, review

#draft = false

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

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}であまり使用されない機能の1つは、レンダリングフックです。 この投稿では、レンダリングフックを使用して、リンクを作成する{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}のデフォルトの方法である `[text](https://example.com#fragment "Title")`に内部相互参照サポートを追加します。

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

## 手順

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

## 使い方

次の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンク

  ```markdown {linenos=false}
  - [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](20181210-browser-wars-iii)
  - [](/20181210-browser-wars-iii)
  - [With text](20181210-browser-wars-iii)
  - [](20181210-browser-wars-iii "With title")
  - [With text, title, and fragment](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "With text, title, and fragment")
  ```

`ja`で次のようにレンダリングされます：

- [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [With text](20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "With title")
- [With text, title, and fragment](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "With text, title, and fragment")

### 警告

現在、次の形式はサポートされていません。

```markdown {linenos=false}
- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
```

リンクタイトルなしでレンダリングされ、[リンクアイコン](hugo-link-icons-markdown-links.md)を使用すると、リンクが正しくありません。

- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)

代わりに、生成されたパーマリンクを次のように使用します（プレフィックス `/`が重要です）：

```markdown {linenos=false}
- [Browser Wars III：Blink vs Gecko Quantum](/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)
```

次のようにレンダリングされます：

- [Browser Wars III：Blink vs Gecko Quantum](/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)

## それを改善

上記のコードを自由に改善して、コミュニティに共有してください。 あなたが適切にクレジットされるようにあなたのウェブサイトと名前を提供してください。

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
