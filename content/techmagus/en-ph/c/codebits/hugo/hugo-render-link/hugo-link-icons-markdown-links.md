+++
title = "How-To add link icons in Hugo markdown links"
description = "How to add link icons for Markdown links in Hugo"

publishdate = 2022-05-20T19:24:30+08:00                                          # manually adjust to local timezone
lastmod = 2022-06-17T14:07:01+08:00                                       # manually adjust to local timezone

aliases = ["/codebits/how-to-add-link-icons-hugo-markdown-links-2022140", "/codebits/hugo-render-link/how-to-add-link-icons-hugo-markdown-links-2022140"]
slug = "how-to-add-link-icons-hugo-markdown-links"
translationKey = "how-to-add-link-icons-hugo-markdown-links-2022140"
relCanonical = "https://im.youronly.one/techmagus/codebits/hugo/hugo-render-link/how-to-add-link-icons-hugo-markdown-links-2022140/"
#disqus_url = ""                                                    # no use case in sites by Yelosan Publishing (YourOnly.One)
#disqus_identifier = ""                                             # set if slug date of this content is different from main translation (en-PH)

syndications = ["https://mastodon.social/@youronlyone/108390777306425065", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/pfbid02m3H8WrP1eW6MqiEPGBhbJGGzdcrXAzBEx2tsbNUA8mmebsyTgktKNhM9sKQDrjibl", "https://twitter.com/YourOnlyONEofcl/status/1531244042117341184"]

channels = ["techmagus"]
categories = ["howto"]
keywords = ["Hugo", "How To", "Markdown Links", "Link Icons", "YourOnlyOne", "YourOnly.One", "techmagus"]
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
  name = "Yuki (유키 雪矢)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

Link icons are great. It signals to the reader what a link is. It is external? Or perhaps a video? If the link is clicked, will it start a download or will it open the default mail program? Link icons also helps a developer or content creator to easily find links, or the lack thereof.

<!--more-->

Link icons started with and was popularised by {{% quote type="title" lang="en" %}}Wikipedia{{% /quote %}} a decade ago [^wikipedia-link-icons]. Everyone were looking for CMS plugins to add link icons to their websites and blogs. The method back then was to use a small `.png` image file as the icon. But today? We are going to use {{% quote type="name" lang="en" %}}Unicode{{% /quote %}} emojis and only use `.svg` if an appropriate emoji is not available.

In this post, we will add link icons support in {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} through {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links. No shortcode needed, just plain regular `[text](https://example.com "Title")` links, thanks to the power of render hooks [^hugo-markdown-render-hooks].

[^wikipedia-link-icons]: [w:Help:External link icons](https://en.wikipedia.org/wiki/Help:External_link_icons "w:Help:External link icons")
[^hugo-markdown-render-hooks]: [Hugo: Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## Features

- Add link icons without using {{% quote type="name" lang="en" %}}JavaScript{{% /quote %}}
  - With internal {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links support
- Features from [](hugo-cross-reference-markdown-links.md)

## What's new

- 2022-06-17:
  - ftp icon changed to: <span class="emoji">&#x2194;&#xFE0F;</span>
  - `sftp://` protocol moved to ftp category
  - ref: switched to {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}'s `findRE` where appropriate
  - fix: `[text](./path/to/content/)` and `[text.ext](./path/to/file.ext)` formats

- 2022-05-27:
  - Same (sub)-domain no longer have external icon.
  - More external link support like audio, video, fonts, disk images, documents, presentations, spreadsheets, and more!

## Steps

To add link icons, follow the steps below:

1. Create a file called `render-link.html` in this directory `/layouts/_default/_markup/`
1. Copy and paste this code:

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

    {{/* PROTOCOLS */}}
      {{- $chat := findRE "^(?:discord|irc[s6]?|jabber|skype|xmpp)://" .Destination -}}
      {{- $ftp := findRE "^(?:[as]?ftp)://" .Destination -}}
      {{- $magnet := strings.HasPrefix .Destination "magnet://" -}}
      {{- $mail := strings.HasPrefix .Destination "mailto:" -}}
      {{- $remote := findRE "^(?:bzr|git|s(?:sh|vn)|telnet)://" .Destination -}}
      {{- $tel := strings.HasPrefix .Destination "tel:" -}}

    {{/* READING */}}
      {{- $books := or (strings.HasPrefix .Destination "doi://") (findRE "\\.(?:epub|mobi|pdf)$" .Destination) -}}
      {{- $document := findRE "\\.(?:docx?|odt|s(?:dw|xw)|sxw|uo[ft])$" .Destination -}}
      {{- $text := findRE "\\.(?:csv|txt)$" .Destination -}}
      {{- $presentation := findRE "\\.(?:f?odp|pptx?|s(?:d[dp]|xi)|uop)$" .Destination -}}
      {{- $spreadsheet := findRE "\\.(?:f?ods|s(?:d[cx]|xc)|uos|xlsx?)$" .Destination -}}

    {{/* MEDIA */}}
      {{- $audio := findRE "\\.(?:(?:fl|a)ac|mka|og[ag]|opus|mp[3a]|midi?|wave?|wma)$" .Destination -}}
      {{- $video := findRE "\\.(?:av[1i]|divx|mk(?:3d|v)|mp(?:(?:e?g)?4?|v)|og[mv]|xvid|webm)$" .Destination -}}
      {{- $subtitle := findRE "\\.(?:dfxp|mks|s(?:bv|cc|rt|ub)|ttml|vtt)$" .Destination -}}

    {{/* EXECUTABLES */}}
      {{- $executable := findRE "\\.(?:apk|com|deb|exe|msi)$" .Destination -}}
      {{- $scripts := findRE "\\.(?:bat|sh)$" .Destination -}}

    {{/* OTHERS */}}
      {{- $fonts := findRE "\\.(?:otf|tt[fc]|woff2?)$" .Destination -}}
      {{- $compressed := findRE "\\.(?:[7g]?z(?:ip)?|bz(?:ip)?2?|[rt]ar)$" .Destination -}}
      {{- $diskimage := findRE "\\.(?:[di]mg|iso|md[sfx])$" .Destination -}}
      {{- $imagediting := findRE "\\.(?:psd|xcf)$" .Destination -}}

    {{- $icon := "" -}}
    {{- if $chat -}}{{ $icon = "chat" }}
      {{- else if $ftp -}}{{ $icon = "ftp" }}
      {{- else if $magnet -}}{{ $icon = "magnet" }}
      {{- else if $mail -}}{{ $icon = "mail" }}
      {{- else if $remote -}}{{ $icon = "remote" }}
      {{- else if $tel -}}{{ $icon = "tel" }}

      {{- else if $books -}}{{ $icon = "books" }}
      {{- else if $document -}}{{ $icon = "document" }}
      {{- else if $text -}}{{ $icon = "text" }}
      {{- else if $presentation -}}{{ $icon = "presentation" }}
      {{- else if $spreadsheet -}}{{ $icon = "spreadsheet" }}

      {{- else if $audio -}}{{ $icon = "audio" }}
      {{- else if $video -}}{{ $icon = "video" }}
      {{- else if $subtitle -}}{{ $icon = "subtitle" }}

      {{- else if $executable -}}{{ $icon = "executable" }}
      {{- else if $scripts -}}{{ $icon = "scripts" }}

      {{- else if $fonts -}}{{ $icon = "fonts" }}
      {{- else if $compressed -}}{{ $icon = "compressed" }}
      {{- else if $diskimage -}}{{ $icon = "diskimage" }}
      {{- else if $imagediting -}}{{ $icon = "imagediting" }}

      {{- else if and (not $internal) (ne $url.Host $baseurl.Host) -}}{{ $icon = "external" }}
    {{- end -}}
    <a href="{{ $destination | safeURL }}"{{ with or .Title $getpage.LinkTitle .Text }} title="{{ . }}"{{ end }}{{ with $icon }} class="icon_{{ . }}"{{ end }}{{ if not $internal }} rel="noopener external"{{ end }}>{{ or .Text .Title $getpage.LinkTitle | safeHTML }}</a>
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
        margin-left: 0.25em;
        width: 1em;
      }
      .icon_external::after     { content: "\1F517";                                    /* 🔗 */ }

      .icon_chat::after         { content: "\1F4AC";                                    /* 💬 */ }
      .icon_ftp::after          { content: "\2194\FE0F";                                /* ↔️ */ }
      .icon_magnet::after       { content: "\1F9F2";                                    /* 🧲 */ }
      .icon_mail::after         { content: "\1F4E7";                                    /* 📧 */ }
      .icon_remote::after       { content: "\1F4BB";                                    /* 💻 */ }
      .icon_tel::after          { content: "\260E\FE0F";                                /* ☎️ */ }

      .icon_books::after        { content: "\1F4D6";                                    /* 📖 */ }
      .icon_document::after     { content: "\1F4C4";                                    /* 📄 */ }
      .icon_text::after         { content: "\1F4DD";                                    /* 📝 */ }
      .icon_presentation::after { content: url("../fonts/link-icons-presentation.svg"); /* https://openclipart.org/detail/36505/tango-x-office-presentation */ }
      .icon_spreadsheet::after  { content: url("../fonts/link-icons-spreadsheet.svg");  /* https://openclipart.org/detail/36517/tango-x-office-spreadsheet */ }

      .icon_audio::after        { content: "\1F3B5";                                    /* 🎵 */ }
      .icon_video::after        { content: "\1F4FD\FE0F";                               /* 📽️ */ }
      .icon_subtitle::after     { content: url("../fonts/link-icons-subtitle.svg");     /* https://openclipart.org/detail/212110/mimetype-subtitle */ }

      .icon_executable::after   { content: url("../fonts/link-icons-executable.svg");   /* https://openclipart.org/detail/212161/mimetype-binary */ }
      .icon_scripts::after      { content: url("../fonts/link-icons-scripts.svg");      /* https://openclipart.org/detail/36175/tango-text-x-script */ }

      .icon_fonts::after        { content: url("../fonts/link-icons-fonts.svg");        /* https://openclipart.org/detail/35257/tango-preferences-desktop-font */ }
      .icon_compressed::after   { content: "\1F5DC\FE0F";                               /* 🗜️ */ }
      .icon_diskimage::after    { content: "\1F4BD";                                    /* 💽 */ }
      .icon_imagediting::after  { content: url("../fonts/link-icons-imageediting.svg"); /* https://openclipart.org/detail/231061/artists-brush-and-paint */ }
    /********************
    ** END: Link icons **
    ********************/
    ```

1. Download `.svg` icons: [link-icons.7z](./techmagus/dls/link-icons.7z)

    - Sources (all in the Public Domain):
      - Presentation: [tango x office presentation](https://openclipart.org/detail/36505/tango-x-office-presentation) by [warszawianka](https://openclipart.org/artist/warszawianka)
      - Spreadsheet: [tango x office spreadsheet](https://openclipart.org/detail/36517/tango-x-office-spreadsheet) by [warszawianka](https://openclipart.org/artist/warszawianka)
      - Subtitle: [mimetype subtitle](https://openclipart.org/detail/212110/mimetype-subtitle) by [sixsixfive](https://openclipart.org/artist/sixsixfive)
      - Executable: [mimetype binary](https://openclipart.org/detail/212161/mimetype-binary) by [sixsixfive](https://openclipart.org/artist/sixsixfive)
      - Scripts: [tango text x script](https://openclipart.org/detail/36175/tango-text-x-script) by [warszawianka](https://openclipart.org/artist/warszawianka)
      - Fonts: [tango preferences desktop font](https://openclipart.org/detail/35257/tango-preferences-desktop-font) by [warszawianka](https://openclipart.org/artist/warszawianka)
      - Image editing: [Artists Brush And Paint](https://openclipart.org/detail/231061/artists-brush-and-paint) by [GDJ](https://openclipart.org/artist/GDJ)

      It is possible to hotlink from the listed sources. However, there is no information if they were setup for it.
      {.note}

1. Extract the `.svg` files in `/static/fonts/` folder.

## How to use

The following {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} links

  ```markdown {linenos=false}
  - External links
    - [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
  - Chat
    - [irc://](irc://example.com "irc://") | [ircs://](ircs://example.com "ircs://") | [irc6://](irc6://example.com "irc6://") | [xmpp://](xmpp://example.com "xmpp://") | [jabber://](jabber://example.com "jabber://") | [discord://](discord://example.com "discord://") | [skype://](skype://example.com "skype://")
  - FTP
    - [sftp://](sftp://example.com "sftp://") | [ftp://](ftp://example.com "ftp://") | [aftp://](aftp://example.com "aftp://")
  - Magnet
    - [magnet://](magnet://example.com "magnet://")
  - Mail
    - [mailto:](mailto:noreply@example.com "mailto:")
  - Remote
    - [telnet://](telnet://example.com "telnet://") | [ssh://](ssh://example.com "ssh://") | [git://](git://example.com "git://") | [svn://](svn://example.com "svn://") | [bzr://](bzr://example.com "bzr://")
  - Tel
    - [tel:](tel:123-456-7890 "tel:")
  - Books
    - [doi://](doi://example.com "doi://") | [.epub](https://example.com/file.epub ".epub") | [.mobi](https://example.com/file.mobi ".mobi") | [.pdf](https://example.com/file.pdf ".pdf")
  - Document
    - [.odt](https://example.com/file.odt ".odt") | [.sdw](https://example.com/file.sdw ".sdw") | [.sxw](https://example.com/file.sxw ".sxw") | [.uof](https://example.com/file.uof ".uof") | [.uot](https://example.com/file.uot ".uot") | [.doc](https://example.com/file.doc ".doc") | [.docx](https://example.com/file.docx ".docx")
  - Text
    - [.txt](https://example.com/file.txt ".txt") | [.csv](https://example.com/file.csv ".csv")
  - Presentation
    - [.odp](https://example.com/file.odp ".odp") | [.fodp](https://example.com/file.fodp ".fodp") | [.sdd](https://example.com/file.sdd ".sdd") | [.sdp](https://example.com/file.sdp ".sdp") | [.sxi](https://example.com/file.sxi ".sxi") | [.uop](https://example.com/file.uop ".uop") | [.ppt](https://example.com/file.ppt ".ppt") | [.pptx](https://example.com/file.pptx ".pptx")
  - Spreadsheet
    - [.ods](https://example.com/file.ods ".ods") | [.fods](https://example.com/file.fods ".fods") | [.sdc](https://example.com/file.sdc ".sdc") | [.sxc](https://example.com/file.sxc ".sxc") | [.uos](https://example.com/file.uos ".uos") | [.xls](https://example.com/file.xls ".xls") | [.xlsx](https://example.com/file.xlsx ".xlsx")
  - Audio
    - [.flac](https://example.com/file.flac ".flac") | [.aac](https://example.com/file.aac ".aac") | [.mka](https://example.com/file.mka ".mka") | [.ogg](https://example.com/file.ogg ".ogg") | [.oga](https://example.com/file.oga ".oga") | [.opus](https://example.com/file.opus ".opus") | [.mp3](https://example.com/file.mp3 ".mp3") | [.mpa](https://example.com/file.mpa ".mpa") | [.mid](https://example.com/file.mid ".mid") | [.midi](https://example.com/file.midi ".midi") | [.wav](https://example.com/file.wav ".wav") | [.wave](https://example.com/file.wave ".wave") | [.wma](https://example.com/file.wma ".wma")
  - Video
    - [.av1](https://example.com/file.av1 ".av1") | [.webm](https://example.com/file.webm ".webm") | [.xvid](https://example.com/file.xvid ".xvid") | [.mkv](https://example.com/file.mkv ".mkv") | [.mk3d](https://example.com/file.mk3d ".mk3d") | [.ogm](https://example.com/file.ogm ".ogm") | [.ogv](https://example.com/file.ogv ".ogv") | [.divx](https://example.com/file.divx ".divx") | [.avi](https://example.com/file.avi ".avi") | [.mp4](https://example.com/file.mp4 ".mp4") | [.mpeg4](https://example.com/file.mpeg4 ".mpeg4") | [.mpv](https://example.com/file.mpv ".mpv") | [.mpeg](https://example.com/file.mpeg ".mpeg") | [.mpg](https://example.com/file.mpg ".mpg")
  - Subtitle
    - [.vtt](https://example.com/file.vtt ".vtt") | [.ttml](https://example.com/file.ttml ".ttml") | [.dfxp](https://example.com/file.dfxp ".dfxp") | [.srt](https://example.com/file.srt ".srt") | [.sub](https://example.com/file.sub ".sub") | [.sbv](https://example.com/file.sbv ".sbv") | [.scc](https://example.com/file.scc ".scc") | [.mks](https://example.com/file.mks ".mks")
  - Executables
    - [.deb](https://example.com/file.deb ".deb") | [.apk](https://example.com/file.apk ".apk") | [.exe](https://example.com/file.exe ".exe") | [.com](https://example.com/file.com ".com") | [.msi](https://example.com/file.msi ".msi")
  - Scripts
    - [.bat](https://example.com/file.bat ".bat") | [.sh](https://example.com/file.sh ".sh")
  - Fonts
    - [.woff](https://example.com/file.woff ".woff") | [.woff2](https://example.com/file.woff2 ".woff2") | [.otf](https://example.com/file.otf ".otf") | [.ttf](https://example.com/file.ttf ".ttf") | [.ttc](https://example.com/file.ttc ".ttc")
  - Compressed files
    - [.7z](https://example.com/file.7z ".7z") | [.7zip](https://example.com/file.7zip ".7zip") | [.tar](https://example.com/file.tar ".tar") | [.gz](https://example.com/file.gz ".gz") | [.gzip](https://example.com/file.gzip ".gzip") | [.bz2](https://example.com/file.bz2 ".bz2") | [.bzip2](https://example.com/file.bzip2 ".bzip2") | [.zip](https://example.com/file.zip ".zip") | [.rar](https://example.com/file.rar ".rar")
  - Disk images
    - [.img](https://example.com/file.img ".img") | [.iso](https://example.com/file.iso ".iso") | [.dmg](https://example.com/file.dmg ".dmg") | [.mds](https://example.com/file.mds ".mds") | [.mdf](https://example.com/file.mdf ".mdf") | [.mdx](https://example.com/file.mdx ".mdx")
  - Image editing
    - [.xcf](https://example.com/file.xcf ".xcf") | [.psd](https://example.com/file.psd ".psd")
  ```

Will render as:

- External links
  - [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- Chat
  - [irc://](irc://example.com "irc://") | [ircs://](ircs://example.com "ircs://") | [irc6://](irc6://example.com "irc6://") | [xmpp://](xmpp://example.com "xmpp://") | [jabber://](jabber://example.com "jabber://") | [discord://](discord://example.com "discord://") | [skype://](skype://example.com "skype://")
- FTP
  - [sftp://](sftp://example.com "sftp://") | [ftp://](ftp://example.com "ftp://") | [aftp://](aftp://example.com "aftp://")
- Magnet
  - [magnet://](magnet://example.com "magnet://")
- Mail
  - [mailto:](mailto:noreply@example.com "mailto:")
- Remote
  - [telnet://](telnet://example.com "telnet://") | [ssh://](ssh://example.com "ssh://") | [git://](git://example.com "git://") | [svn://](svn://example.com "svn://") | [bzr://](bzr://example.com "bzr://")
- Tel
  - [tel:](tel:123-456-7890 "tel:")
- Books
  - [doi://](doi://example.com "doi://") | [.epub](https://example.com/file.epub ".epub") | [.mobi](https://example.com/file.mobi ".mobi") | [.pdf](https://example.com/file.pdf ".pdf")
- Document
  - [.odt](https://example.com/file.odt ".odt") | [.sdw](https://example.com/file.sdw ".sdw") | [.sxw](https://example.com/file.sxw ".sxw") | [.uof](https://example.com/file.uof ".uof") | [.uot](https://example.com/file.uot ".uot") | [.doc](https://example.com/file.doc ".doc") | [.docx](https://example.com/file.docx ".docx")
- Text
  - [.txt](https://example.com/file.txt ".txt") | [.csv](https://example.com/file.csv ".csv")
- Presentation
  - [.odp](https://example.com/file.odp ".odp") | [.fodp](https://example.com/file.fodp ".fodp") | [.sdd](https://example.com/file.sdd ".sdd") | [.sdp](https://example.com/file.sdp ".sdp") | [.sxi](https://example.com/file.sxi ".sxi") | [.uop](https://example.com/file.uop ".uop") | [.ppt](https://example.com/file.ppt ".ppt") | [.pptx](https://example.com/file.pptx ".pptx")
- Spreadsheet
  - [.ods](https://example.com/file.ods ".ods") | [.fods](https://example.com/file.fods ".fods") | [.sdc](https://example.com/file.sdc ".sdc") | [.sxc](https://example.com/file.sxc ".sxc") | [.uos](https://example.com/file.uos ".uos") | [.xls](https://example.com/file.xls ".xls") | [.xlsx](https://example.com/file.xlsx ".xlsx")
- Audio
  - [.flac](https://example.com/file.flac ".flac") | [.aac](https://example.com/file.aac ".aac") | [.mka](https://example.com/file.mka ".mka") | [.ogg](https://example.com/file.ogg ".ogg") | [.oga](https://example.com/file.oga ".oga") | [.opus](https://example.com/file.opus ".opus") | [.mp3](https://example.com/file.mp3 ".mp3") | [.mpa](https://example.com/file.mpa ".mpa") | [.mid](https://example.com/file.mid ".mid") | [.midi](https://example.com/file.midi ".midi") | [.wav](https://example.com/file.wav ".wav") | [.wave](https://example.com/file.wave ".wave") | [.wma](https://example.com/file.wma ".wma")
- Video
  - [.av1](https://example.com/file.av1 ".av1") | [.webm](https://example.com/file.webm ".webm") | [.xvid](https://example.com/file.xvid ".xvid") | [.mkv](https://example.com/file.mkv ".mkv") | [.mk3d](https://example.com/file.mk3d ".mk3d") | [.ogm](https://example.com/file.ogm ".ogm") | [.ogv](https://example.com/file.ogv ".ogv") | [.divx](https://example.com/file.divx ".divx") | [.avi](https://example.com/file.avi ".avi") | [.mp4](https://example.com/file.mp4 ".mp4") | [.mpeg4](https://example.com/file.mpeg4 ".mpeg4") | [.mpv](https://example.com/file.mpv ".mpv") | [.mpeg](https://example.com/file.mpeg ".mpeg") | [.mpg](https://example.com/file.mpg ".mpg")
- Subtitle
  - [.vtt](https://example.com/file.vtt ".vtt") | [.ttml](https://example.com/file.ttml ".ttml") | [.dfxp](https://example.com/file.dfxp ".dfxp") | [.srt](https://example.com/file.srt ".srt") | [.sub](https://example.com/file.sub ".sub") | [.sbv](https://example.com/file.sbv ".sbv") | [.scc](https://example.com/file.scc ".scc") | [.mks](https://example.com/file.mks ".mks")
- Executables
  - [.deb](https://example.com/file.deb ".deb") | [.apk](https://example.com/file.apk ".apk") | [.exe](https://example.com/file.exe ".exe") | [.com](https://example.com/file.com ".com") | [.msi](https://example.com/file.msi ".msi")
- Scripts
  - [.bat](https://example.com/file.bat ".bat") | [.sh](https://example.com/file.sh ".sh")
- Fonts
  - [.woff](https://example.com/file.woff ".woff") | [.woff2](https://example.com/file.woff2 ".woff2") | [.otf](https://example.com/file.otf ".otf") | [.ttf](https://example.com/file.ttf ".ttf") | [.ttc](https://example.com/file.ttc ".ttc")
- Compressed files
  - [.7z](https://example.com/file.7z ".7z") | [.7zip](https://example.com/file.7zip ".7zip") | [.tar](https://example.com/file.tar ".tar") | [.gz](https://example.com/file.gz ".gz") | [.gzip](https://example.com/file.gzip ".gzip") | [.bz2](https://example.com/file.bz2 ".bz2") | [.bzip2](https://example.com/file.bzip2 ".bzip2") | [.zip](https://example.com/file.zip ".zip") | [.rar](https://example.com/file.rar ".rar")
- Disk images
  - [.img](https://example.com/file.img ".img") | [.iso](https://example.com/file.iso ".iso") | [.dmg](https://example.com/file.dmg ".dmg") | [.mds](https://example.com/file.mds ".mds") | [.mdf](https://example.com/file.mdf ".mdf") | [.mdx](https://example.com/file.mdx ".mdx")
- Image editing
  - [.xcf](https://example.com/file.xcf ".xcf") | [.psd](https://example.com/file.psd ".psd")

An official list of Uniform Resource Identifier (URI) Schemes can be found at the IANA official website. [^uri-schemes-iana] However, not all popular URI Schemes were registered and/or submitted, for example, `discord://` and `bzr://` (as of IANA document dated 2022-05-13). Regardless, these popular unregistered URI Schemes were included in the above code.

[^uri-schemes-iana]: IANA: [URI Schemes](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml)

I hope you find it useful!

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link=""
  linkrel="noopener"

  title="How To Customize Markdown Links in Hugo"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
