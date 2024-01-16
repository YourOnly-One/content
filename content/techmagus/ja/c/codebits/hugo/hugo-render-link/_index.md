+++
title = "Hugo：Markdown リンクをカスタマイズする"
description = "Hugo Markdownリンクに相互参照サポート、リンクアイコンなどを追加する方法。"

#lastmod = {{ .Date }}                 # last update; manually adjust to local timezone
#publishdate = {{ .Date }}             # first publication; manually adjust to local timezone
#date = {{ .Date }}                    # first created; manually adjust to local timezone
#expirydate = 2022-04-07T17:53:01+08:00              # expiry; manually adjust to local timezone

aliases = ["/ja/codebits/how-to-customize-markdown-links-hugo-2022135", "/ja/c/codebits/hugo-render-link"]                                        # "/post"
#url = ""                                              # "path/post"; override .Permalink
#slug = ""
translationKey = "section-hugo-markdown-links"
#relCanonical = "https://im.youronly.one/{BLOG-NAME}/{LANG}/{POST-TITLE}-{DATE}/"
#disqus_url = ""                                       # not used in sites by Yelosan Publishing
#disquq_identifier = ""                                # set if date of this content is different from main translation

#redirectto = ""                                       # Yelosan Publishing: used in _index.md
#metarobots = "noindex"                                # Yelosan Publishing: used in _index.md

syndications = ["https://mastodon.social/@youronlyone/108303916946754498", "https://diasp.org/posts/21145789", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/pfbid036F7UJdHLFXMvcXkuA1ox3iUDUougC3w7WJjCcB8198AtFrwHqAA52fBzgHMj22Upl", "https://twitter.com/YourOnlyONEofcl/status/1525681470022508544"]

#channels = [""]
#categories = [""]
#keywords = [""]
#series = [""]
#tags = [""]

comments = false
#weight = ""

#featured = true
#math = true
toc = true

#audio = [""]
images = ["images/h/hugo-markdown-link-render.webp"]                 # used for og:images, etc.; first image is cover image
#videos = ["https://www.youtube.com/watch?v="]

#type = ""                                             # article, sitepage, review

#draft = true

#license = ""                                          # only set if the post license is not the same as the site license

#### AUTHOR: TECHMAGUS ####
[[authors]]
  person = "yuki"
  #id = ""
  name = "謝雪矢（ゆきや）"
  #name = "techmagus 🚀 / テク魔法使い 🚀 / 테크마법사 🚀"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}での{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンクのレンダリング方法をカスタマイズする方法をお探しですか？ リンクアイコンを追加したいですか？ または、（古い方法） `{{</* ref */>}}`を使用せずに内部相互参照のサポートを追加するのはどうですか？

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}には、{{% quote type="work" lang="en" %}}allow custom templates to override markdown rendering functionality{{% /quote %}} (翻訳：カスタムテンプレートがマークダウンレンダリング機能をオーバーライドできるようにする) [^hugo-markdown-render-hooks] {{% quote type="name" lang="en" %}}Markdown{{% /quote %}}レンダリングフックと呼ばれる機能があります。 現在、一般的に要求される4つの{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}レンダリング領域をサポートしています。

- codeblock
- heading
- image
- link

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンクのレンダリング方法をカスタマイズするさまざまな方法があります。

[^hugo-markdown-render-hooks]: Hugo: [Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")
