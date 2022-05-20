+++
title = "How To Add Cross Reference in Hugo Markdown Links"
description = "How to add cross reference support for Markdown links in Hugo"

date = "2022-05-20T19:24:27+08:00"                                          # manually adjust to local timezone
#lastmod = "2022-05-19T04:33:00+00:00"                                       # manually adjust to local timezone

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

One of the less commonly used feature of {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} is render hooks. In this post, we are going to use render hooks to add internal cross reference support to {{% quote type="name" lang="en" %}}Markdown{{% /quote %}}'s default way of creatings links: `[text](https://example.com#fragment "Title")`.

<!--more-->

Internal cross references in {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} is usually done by using the built-in shortcodes `{{</* ref */>}}` or `{{%/* relref */%}}` but did you know since {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} v0.62.0 [^hugo-0.62.0] the advisable method is to use render hooks [^hugo-markdown-render-hooks]?

[^hugo-0.62.0]: [Hugo v0.62.0](https://github.com/gohugoio/hugo/releases/tag/v0.62.0 "Hugo v0.62.0")
[^hugo-markdown-render-hooks]: [Hugo: Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## Features

- Use regular {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} link format to cross reference within {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}
  - `{{</* ref */>}}` and `{{%/* relref */%}}`, or any variation thereof, is a thing of the past
  - Automatically use the content's title
  - Multilingual support
  - {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} link text and title support
  - With URI fragment support

## Steps

1. Create a file called `render-link.html` in this directory `/layouts/_default/_markup/`
1. Add the code below:

    ```go-html-template
    {{- $url := (urls.Parse .Destination) -}}
    {{- $internal := site.GetPage .Destination -}}
    {{- $fragment := $url.Fragment -}}
    {{- with $fragment -}}{{ $fragment = printf "#%s" $fragment }}{{- end -}}
    {{- $destination := printf "%s%s" (or $internal.RelPermalink .Destination) $fragment -}}
    <a href="{{ $destination | safeURL }}"{{ with or .Title $internal.LinkTitle .Text }} title="{{ . }}"{{ end }}{{ if not $internal }} rel="noopener external"{{ end }}>{{ or .Text .Title $internal.LinkTitle | safeHTML }}</a>
    ```

That's it.

## How to use

The following {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links

  ```markdown {linenos=false}
  - [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](20181210-browser-wars-iii)
  - [](/20181210-browser-wars-iii)
  - [With text](20181210-browser-wars-iii)
  - [](20181210-browser-wars-iii "With title")
  - [With text, title, and fragment](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "With text, title, and fragment")
  ```

Will render in `en-ph` as:

- [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [With text](20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "With title")
- [With text, title, and fragment](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "With text, title, and fragment")

### Caveats

Currently have no support for the following formats:

```markdown {linenos=false}
- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
```

It renders without the link title, and with [link icons](hugo-link-icons-markdown-links.md), the link is incorrect.

- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)

Use the generated permalink instead, like so (the prefix `/` is important):

```markdown {linenos=false}
- [Browser Wars III Front: Browser Engine](/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)
```

Will render as:

- [Browser Wars III Front: Browser Engine](/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)

## Improve it

Feel free to improve the code above and share back to the community. Please provide your website and name so you will be properly credited.

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link="https://img.youronly.one/h/hugo-markdown-link-render.webp"
  linkrel="noopener"

  title="How To Customize Markdown Links in Hugo"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
