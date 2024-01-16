+++
title = "Hugo: Markdown 링크 사용자 지정"
description = "Hugo Markdown 링크에 상호 참조 지원, 링크 아이콘 등을 추가하는 방법."

#lastmod = {{ .Date }}                 # last update; manually adjust to local timezone
#publishdate = {{ .Date }}             # first publication; manually adjust to local timezone
#date = {{ .Date }}                    # first created; manually adjust to local timezone
#expirydate = 2022-04-07T17:53:01+08:00              # expiry; manually adjust to local timezone

aliases = ["/ko/codebits/how-to-customize-markdown-links-hugo-2022135", "/ko/c/codebits/hugo-render-link"]                                        # "/post"
#url = ""                                              # "path/post"; override .Permalink
#slug = ""
translationKey = "section-hugo-markdown-links"
#relCanonical = "https://im.youronly.one/{BLOG-NAME}/{LANG}/{POST-TITLE}-{DATE}/"
#disqus_url = ""                                       # not used in sites by Yelosan Publishing
#disquq_identifier = ""                                # set if date of this content is different from main translation

#redirectto = ""                                       # Yelosan Publishing: used in _index.md
#metarobots = "noindex"                                # Yelosan Publishing: used in _index.md

syndications = ["https://mastodon.social/@youronlyone/108303918152249905", "https://diasp.org/posts/21145789", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/pfbid036F7UJdHLFXMvcXkuA1ox3iUDUougC3w7WJjCcB8198AtFrwHqAA52fBzgHMj22Upl", "https://twitter.com/YourOnlyONEofcl/status/1525681473948471296"]

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
  name = "사요한"
  #name = "techmagus 🚀 / テク魔法使い 🚀 / 테크마법사 🚀"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}에서 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크가 렌더링되는 방식을 사용자 정의하는 방법을 찾고 계십니까? 링크 아이콘을 추가하고 싶습니까? 또는 (이전 방법) `{{</* ref */>}}`를 사용하지 않고 내부 상호 참조에 대한 지원을 추가하는 것은 어떻습니까?

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}에는 {{% quote type="work" lang="en" %}}allow custom templates to override markdown rendering functionality{{% /quote %}} (번역: 맞춤 템플릿이 마크다운 렌더링 기능을 재정의할 수 있도록)하는 [^hugo-markdown-render-hooks] {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 렌더 후크라는 기능이 있습니다. 현재 일반적으로 요청되는 4개의 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 렌더링 영역을 지원합니다.

- codeblock
- heading
- image
- link

다음은 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}의 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크를 렌더링하는 방법을 사용자 지정하는 다양한 방법입니다.

[^hugo-markdown-render-hooks]: Hugo: [Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")
