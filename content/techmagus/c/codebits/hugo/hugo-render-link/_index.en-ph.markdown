+++
title = "Hugo: Customize Your Markdown Links"
description = "How to add cross reference support, link icons, and more in Hugo Markdown links."

#lastmod = {{ .Date }}                 # last update; manually adjust to local timezone
#publishdate = {{ .Date }}             # first publication; manually adjust to local timezone
#date = {{ .Date }}                    # first created; manually adjust to local timezone
#expirydate = 2022-04-07T17:53:01+08:00              # expiry; manually adjust to local timezone

aliases = ["/codebits/how-to-customize-markdown-links-hugo-2022135", "/c/codebits/hugo-render-link"]                                        # "/post"
#url = ""                                              # "path/post"; override .Permalink
#slug = ""
translationKey = "section-hugo-markdown-links"
#relCanonical = "https://im.youronly.one/{BLOG-NAME}/{LANG}/{POST-TITLE}-{DATE}/"
#disqus_url = ""                                       # not used in sites by Yelosan Publishing
#disqus_identifier = ""                                # set if date of this content is different from main translation

#redirectto = ""                                       # Yelosan Publishing: used in _index.md
#metarobots = "noindex"                                # Yelosan Publishing: used in _index.md

syndication = ["https://mastodon.social/@youronlyone/108303915231124593", "https://diasp.org/posts/21145789", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/pfbid036F7UJdHLFXMvcXkuA1ox3iUDUougC3w7WJjCcB8198AtFrwHqAA52fBzgHMj22Upl", "https://twitter.com/YourOnlyONEofcl/status/1525681466302246912"]

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
images = ["images/h/hugo-markdown-link-render.webp"]
#videos = ["https://www.youtube.com/watch?v="]

#type = ""                                             # article, sitepage, review

#draft = true

#license = ""                                          # only set if the post license is not the same as the site license

#### AUTHOR: TECHMAGUS ####
[[authors]]
  person = "yuki"
  #id = ""
  name = "Yohan Yuki Xie"
  #name = "techmagus / テク魔法使い / 테크마법사"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

Are you looking for ways to customize how {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links are rendered in {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}? Maybe you want to add link icons? Or, how about add support for internal cross reference without using (the old method) `{{</* ref */>}}`?

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}} has a feature called {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} render hooks which {{% quote type="work" lang="en" %}}allow custom templates to override markdown rendering functionality{{% /quote %}} [^hugo-markdown-render-hooks]. It currently supports four, commonly requested, {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} rendering areas:

- codeblock
- heading
- image
- link

Here are various ways to customize how {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links in {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} can be rendered.

[^hugo-markdown-render-hooks]: Hugo: [Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")
