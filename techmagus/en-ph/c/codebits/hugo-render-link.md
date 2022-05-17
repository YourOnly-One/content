+++
title = "How To Customize Markdown Links in Hugo"
description = "How to add cross reference support and link icons in Hugo Markdown links"

date = "2022-05-15T11:23:48+08:00"                                          # manually adjust to local timezone
#lastmod = "2022-04-07T17:53:01+00:00"                                       # manually adjust to local timezone

#aliases = [""]
slug = "how-to-customize-markdown-links-hugo"
translationKey = "how-to-customize-markdown-links-hugo-2022135"
relCanonical = "https://im.youronly.one/techmagus/codebits/how-to-customize-markdown-links-hugo-2022135/"
#disqus_url = ""                                                    # no use case in sites by Yelosan Publishing (YourOnly.One)
#disqus_identifier = ""                                             # set if slug date of this content is different from main translation (en-PH)

syndications = ["https://twitter.com/YourOnlyONEofcl/status/1525681466302246912", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/657387235430510", "https://diasp.org/posts/f23d3ae0b62f013a6afb28a1592b385a", "https://mastodon.social/web/@youronlyone/108303915231124593"]

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

Are you looking for ways to customize how {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links are rendered in {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}? Maybe you want to add link icons? Or, how about add support for internal cross reference without using (the old method) `{{</* ref */>}}`?

<!--more-->

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}} has a feature called {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} render hooks which {{% quote type="work" lang="en" %}}allow custom templates to override markdown rendering functionality{{% /quote %}} [^hugo-markdown-render-hooks]. It currently supports four, commonly requested, {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} rendering areas:

- codeblock
- heading
- image
- link

In this post, we are going to change how {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links in {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} are rendered.

[^hugo-markdown-render-hooks]: Hugo: [Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## Features

- Use regular {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} link format to cross reference within {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}
  - `{{</* ref */>}}` and `{{%/* relref */%}}`, or any variation thereof, is a thing of the past
  - Automatically use the content's title
  - Multilingual support
  - {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} link text and title support
  - With URI fragment support
- Add link icons without using {{% quote type="name" lang="en" %}}JavaScript{{% /quote %}}
  - With internal {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links support

## Add cross reference

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

### How to use

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

#### Caveats

Currently have no support for the following formats:

```markdown {linenos=false}
- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
```

It will render like this with the wrong link:

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

#### Improve it

Feel free to improve the code above and share back to the community. Please provide your website and name so you will be properly credited.

## Add link icons

To add link icons, follow the steps below:

1. Open the file `render-link.html` (created in the previous section)
1. Replace the entire code with:

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

1. In your stylesheet file add:

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

### How to use

The following {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links

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

Will render as:

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

An official list of Uniform Resource Identifier (URI) Schemes can be found at the IANA official website. [^uri-schemes-iana] However, not all popular URI Schemes were registered and/or submitted, for example, `discord://` and `bzr://` (as of IANA document dated 2022-05-13). Regardless, these popular unregistered URI Schemes were included in the above code.

[^uri-schemes-iana]: IANA: [URI Schemes](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml)

I hope you find it useful!

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
