+++
title = "How To Add Cross Reference in Hugo Markdown Links"
description = "How to add cross reference support for Markdown links in Hugo"

publishdate = "2022-05-20T19:24:27+08:00"                                          # manually adjust to local timezone
lastmod = "2022-06-17T14:07:00+08:00"                                       # manually adjust to local timezone

aliases = ["/codebits/how-to-add-cross-reference-hugo-markdown-links-2022140", "/codebits/hugo-render-link/how-to-add-cross-reference-hugo-markdown-links-2022140"]
slug = "how-to-add-cross-reference-hugo-markdown-links"
translationKey = "how-to-add-cross-reference-hugo-markdown-links-2022140"
relCanonical = "https://im.youronly.one/techmagus/codebits/hugo/hugo-render-link/how-to-add-cross-reference-hugo-markdown-links-2022140/"
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

One of the less commonly used feature of {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} is render hooks. In this post, we are going to use render hooks to add internal cross reference support to {{% quote type="name" lang="en" %}}Markdown{{% /quote %}}'s default way of creating links: `[text](https://example.com#fragment "Title")`.

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

## What's new

- 2022-06-17:
  - fix: `[text](./path/to/content/)` and `[text.ext](./path/to/file.ext)` formats

- 2022-05-27:
  - `[text](./path/to/content/)`
  - `[text.ext](./path/to/file.ext)`
  - reorganized the [How To Use](#how-to-use) section

## Steps

1. Create a file called `render-link.html` in this directory `/layouts/_default/_markup/`
1. Add the code below:

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

That's it.

## How to use

### Traditional

```markdown
- [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- [direct](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/ "Title")
- [direct with #fragment](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/#fragment "Title")
- [#fragment only](#fragment)
```

- [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- [direct](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/ "Title")
- [direct with #fragment](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/#fragment "Title")
- [#fragment only](#fragment)

### New

#### Special

The `[text](./path/to/content/)` format is useful when you want to create a link to another part of your website, under the same (sub)-domain but not part of the current {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} project. This format will not generate an external link icon if the [](hugo-link-icons-markdown-links.md) is also installed.

The `[text.ext](./path/to/file.ext)` is useful for download links hosted under the same (sub)-domain, within or external relative to the current {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} project.

```markdown
- [send a gift](./p/gift/)
- [link-icons.7z](./techmagus/dls/link-icons.7z)
```

- [send a gift](./p/gift/)
- [link-icons.7z](./techmagus/dls/link-icons.7z)

#### Without a file extension

```markdown
- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "Title")
- [](/20181210-browser-wars-iii "Title")
- [Text](20181210-browser-wars-iii)
- [Text](/20181210-browser-wars-iii)
- [Text](20181210-browser-wars-iii "Title")
- [Text](/20181210-browser-wars-iii "Title")
```

- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "Title")
- [](/20181210-browser-wars-iii "Title")
- [Text](20181210-browser-wars-iii)
- [Text](/20181210-browser-wars-iii)
- [Text](20181210-browser-wars-iii "Title")
- [Text](/20181210-browser-wars-iii "Title")

#### With file extension

```markdown
- [](20181210-browser-wars-iii.md#fragment)
- [](/20181210-browser-wars-iii.md#fragment)
- [](20181210-browser-wars-iii.md#fragment "Title")
- [](/20181210-browser-wars-iii.md#fragment "Title")
- [Text#fragment](20181210-browser-wars-iii.md#fragment)
- [Text#fragment](/20181210-browser-wars-iii.md#fragment)
- [Text#fragment](20181210-browser-wars-iii.md#fragment "Title")
- [Text#fragment](/20181210-browser-wars-iii.md#fragment "Title")
```

- [](20181210-browser-wars-iii.md#fragment)
- [](/20181210-browser-wars-iii.md#fragment)
- [](20181210-browser-wars-iii.md#fragment "Title")
- [](/20181210-browser-wars-iii.md#fragment "Title")
- [Text#fragment](20181210-browser-wars-iii.md#fragment)
- [Text#fragment](/20181210-browser-wars-iii.md#fragment)
- [Text#fragment](20181210-browser-wars-iii.md#fragment "Title")
- [Text#fragment](/20181210-browser-wars-iii.md#fragment "Title")

### Not supported

Internal linking without a file extension and with a `#fragment` produces a wrong link.

```markdown
- [](20181210-browser-wars-iii#fragment)
- [](/20181210-browser-wars-iii#fragment)
- [](20181210-browser-wars-iii#fragment "Title")
- [](/20181210-browser-wars-iii#fragment "Title")
- [Text#fragment](20181210-browser-wars-iii#fragment)
- [Text#fragment](/20181210-browser-wars-iii#fragment)
- [Text#fragment](20181210-browser-wars-iii#fragment "Title")
- [Text#fragment](/20181210-browser-wars-iii#fragment "Title")
```

Also take note of the following formats.

```markdown
- [link-icons.7z](/dls/link-icons.7z)
- [link-icons.7z](../../dls/link-icons.7z)
```

Instead of the above, use `[text](./path/to/file.ext)` like so `[link-icons.7z](./techmagus/dls/link-icons.7z)` will render as: [link-icons.7z](./techmagus/dls/link-icons.7z)

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
