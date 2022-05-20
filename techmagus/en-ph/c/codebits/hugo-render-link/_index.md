+++
title = "Hugo: Customize Your Markdown Links"
description = "How to add cross reference support, link icons, and more in Hugo Markdown links."

date = "2022-05-15T11:23:48+08:00"                           # manually adjust to local timezone
#lastmod = "2022-04-07T17:53:01+08:00"                        # manually adjust to local timezone

aliases = ["/codebits/how-to-customize-markdown-links-hugo-2022135"]
#url = ""                            # to override .Permalink
#slug = ""
translationKey = "section-hugo-markdown-links"
#relCanonical = "https://im.youronly.one/{BLOG-NAME}/{LANG}/{POST-TITLE}-{DATE}/"
#disqus_url = ""                     # not used in sites by Yelosan Publishing
#disquq_identifier = ""              # set if date of this content is different from main translation

#redirecto = ""                      # Yelosan Publishing: used in _index.md
#metarobots = "noindex"              # Yelosan Publishing: used in _index.md

syndications = ["https://twitter.com/YourOnlyONEofcl/status/1525681466302246912", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/657387235430510", "https://diasp.org/posts/f23d3ae0b62f013a6afb28a1592b385a", "https://mastodon.social/web/@youronlyone/108303915231124593"]

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

#audio = [""]                        # used for og:audio, etc.
images = ["https://img.youronly.one/h/hugo-markdown-link-render.webp"]                 # used for og:images, etc.; first image is cover image
#videos = ["https://www.youtube.com/watch?v="]                       # used for og:video, etc.

#type = ""                           # article, sitepage, review

#draft = true

#license = ""                        # only set if the post license is not the same as the site license

# For /yuki/ choose one and remove everything else
[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (Yuki | 雪亮)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

Are you looking for ways to customize how {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links are rendered in {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}? Maybe you want to add link icons? Or, how about add support for internal cross reference without using (the old method) `{{</* ref */>}}`?

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}} has a feature called {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} render hooks which {{% quote type="work" lang="en" %}}allow custom templates to override markdown rendering functionality{{% /quote %}} [^hugo-markdown-render-hooks]. It currently supports four, commonly requested, {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} rendering areas:

- codeblock
- heading
- image
- link

Here are various ways to customize how {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links in {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} can be rendered.

[^hugo-markdown-render-hooks]: Hugo: [Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")
