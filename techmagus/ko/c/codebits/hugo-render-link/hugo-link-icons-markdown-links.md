+++
title = "Hugo Markdown 링크에 링크 아이콘을 추가하는 방법"
description = "Hugo에서 Markdown 링크에 대한 링크 아이콘을 추가하는 방법"

publishdate = "2022-05-20T20:24:30+09:00"                                          # manually adjust to local timezone
lastmod = "2022-06-17T09:00:00+09:00"                                       # manually adjust to local timezone

#aliases = [""]
slug = "how-to-add-link-icons-hugo-markdown-links"
translationKey = "how-to-add-link-icons-hugo-markdown-links-2022140"
relCanonical = "https://im.youronly.one/techmagus/codebits/how-to-add-link-icons-hugo-markdown-links-2022140/"
#disqus_url = ""                                                    # no use case in sites by Yelosan Publishing (YourOnly.One)
#disqus_identifier = ""                                             # set if slug date of this content is different from main translation (en-PH)

#syndications = [""]

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

링크 아이콘은 훌륭합니다. 링크가 무엇인지 독자에게 알립니다. 외부인가? 아니면 아마도 비디오? 링크를 클릭하면 다운로드가 시작됩니까? 아니면 기본 메일 프로그램이 열립니까? 링크 아이콘은 또한 개발자 또는 콘텐츠 작성자가 링크 또는 링크가 없는 것을 쉽게 찾도록 도와줍니다.

<!--more-->

링크 아이콘은 10년 전에 {{% quote type="title" lang="en" %}}Wikipedia{{% /quote %}}로 시작되어 대중화되었습니다 [^wikipedia-link-icons]. 모두가 자신의 웹사이트와 블로그에 링크 아이콘을 추가할 CMS 플러그인을 찾고 있었습니다. 당시 방식은 작은 '.png' 이미지 파일을 아이콘으로 사용하는 것이었다. 근데 오늘? {{% quote type="name" lang="en" %}}Unicode{{% /quote %}} 이모티콘을 사용하고 적절한 이모티콘을 사용할 수 없는 경우에만 `.svg`를 사용합니다.

이 포스트에서는 MARKDOWN 링크를 통해 HUGO에서 지원하는 링크 아이콘을 추가합니다. 렌더 후크의 기능 덕분에 단축 코드가 필요하지 않고 일반 일반 `[text](https://example.com "Title")` 링크만 있으면 됩니다 [^hugo-markdown-render-hooks].

[^wikipedia-link-icons]: [w:Help:External link icons](https://en.wikipedia.org/wiki/Help:External_link_icons "w:Help:External link icons")
[^hugo-markdown-render-hooks]: [Hugo: Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## 특징

- {{% quote type="name" lang="en" %}}JavaScript{{% /quote %}}를 사용하지 않고 링크 아이콘 추가
  - 내부 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크 지원
- [](hugo-cross-reference-markdown-links.md)의 기능

## 새로운 소식

- 2022년 6월 17일:
  - ftp 아이콘이 <span class="emoji">&#x2194;&#xFE0F;</span>로 변경되었습니다.
  - `sftp://` 프로토콜이 ftp 범주로 이동됨
  - 리팩토링: 적절한 경우 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}의 `findRE`로 전환

- 2022년 5월 27일:
  - 동일한(하위) 도메인에는 더 이상 외부 아이콘이 없습니다.
  - 오디오, 비디오, 글꼴, 디스크 이미지, 문서, 프레젠테이션, 스프레드시트 등과 같은 더 많은 외부 링크 지원!

## 단계

링크 아이콘을 추가하려면 다음 단계를 따르세요.

1. 이 디렉토리 `/layouts/_default/_markup/`에 `render-link.html`이라는 파일을 만듭니다.
1. 이 코드를 복사하여 붙여넣습니다.

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
        {{- $destination = printf "%s%s%s" $baseurl.Host $url $fragment | replaceRE "\\.(.*)" "$1" -}}
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

1. 스타일시트 파일에 다음을 추가합니다.

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

1. `.svg` 아이콘 다운로드: [link-icons.7z](/dls/link-icons.7z)

    - 출처(모두 공개 도메인):
      - 프레젠테이션: [warszawianka](https://openclipart.org/artist/warszawianka)의 [tango x office presentation](https://openclipart.org/detail/36505/tango-x-office-presentation)
      - 스프레드시트: [warszawianka](https://openclipart.org/artist/warszawianka)의 [tango x office spreadsheet](https://openclipart.org/detail/36517/tango-x-office-spreadsheet)
      - 자막: [sixsixfive](https://openclipart.org/artist/sixsixfive)의 [mimetype subtitle](https://openclipart.org/detail/212110/mimetype-subtitle)
      - 실행 파일: [sixsixfive](https://openclipart.org/artist/sixsixfive)의 [mimetype binary](https://openclipart.org/detail/212161/mimetype-binary)
      - 대본: [warszawianka](https://openclipart.org/artist/warszawianka)의 [tango text x script](https://openclipart.org/detail/36175/tango-text-x-script)
      - 글꼴: [warszawianka](https://openclipart.org/artist/warszawianka)의 [tango preferences desktop font](https://openclipart.org/detail/35257/tango-preferences-desktop-font)
      - 이미지 편집: [GDJ](https://openclipart.org/artist/GDJ)의 [Artists Brush And Paint](https://openclipart.org/detail/231061/artists-brush-and-paint)

      나열된 소스에서 핫링크할 수 있습니다. 그러나 설정한 경우 정보가 없습니다.
      {.note}

1. `/static/fonts/` 폴더에서 `.svg` 파일의 압축을 풉니다.

## 사용하는 방법

다음 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크

  ```markdown {linenos=false}
  - 외부 링크
    - [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
  - 채팅
    - [irc://](irc://example.com "irc://") | [ircs://](ircs://example.com "ircs://") | [irc6://](irc6://example.com "irc6://") | [xmpp://](xmpp://example.com "xmpp://") | [jabber://](jabber://example.com "jabber://") | [discord://](discord://example.com "discord://") | [skype://](skype://example.com "skype://")
  - FTP
    - [sftp://](sftp://example.com "sftp://") | [ftp://](ftp://example.com "ftp://") | [aftp://](aftp://example.com "aftp://")
  - Magnet
    - [magnet://](magnet://example.com "magnet://")
  - Mail
    - [mailto:](mailto:noreply@example.com "mailto:")
  - 원격
    - [telnet://](telnet://example.com "telnet://") | [ssh://](ssh://example.com "ssh://") | [git://](git://example.com "git://") | [svn://](svn://example.com "svn://") | [bzr://](bzr://example.com "bzr://")
  - Tel
    - [tel:](tel:123-456-7890 "tel:")
  - 서적
    - [doi://](doi://example.com "doi://") | [.epub](https://example.com/file.epub ".epub") | [.mobi](https://example.com/file.mobi ".mobi") | [.pdf](https://example.com/file.pdf ".pdf")
  - 문서
    - [.odt](https://example.com/file.odt ".odt") | [.sdw](https://example.com/file.sdw ".sdw") | [.sxw](https://example.com/file.sxw ".sxw") | [.uof](https://example.com/file.uof ".uof") | [.uot](https://example.com/file.uot ".uot") | [.doc](https://example.com/file.doc ".doc") | [.docx](https://example.com/file.docx ".docx")
  - 텍스트
    - [.txt](https://example.com/file.txt ".txt") | [.csv](https://example.com/file.csv ".csv")
  - 프레젠테이션
    - [.odp](https://example.com/file.odp ".odp") | [.fodp](https://example.com/file.fodp ".fodp") | [.sdd](https://example.com/file.sdd ".sdd") | [.sdp](https://example.com/file.sdp ".sdp") | [.sxi](https://example.com/file.sxi ".sxi") | [.uop](https://example.com/file.uop ".uop") | [.ppt](https://example.com/file.ppt ".ppt") | [.pptx](https://example.com/file.pptx ".pptx")
  - 스프레드시트
    - [.ods](https://example.com/file.ods ".ods") | [.fods](https://example.com/file.fods ".fods") | [.sdc](https://example.com/file.sdc ".sdc") | [.sxc](https://example.com/file.sxc ".sxc") | [.uos](https://example.com/file.uos ".uos") | [.xls](https://example.com/file.xls ".xls") | [.xlsx](https://example.com/file.xlsx ".xlsx")
  - 오디오
    - [.flac](https://example.com/file.flac ".flac") | [.aac](https://example.com/file.aac ".aac") | [.mka](https://example.com/file.mka ".mka") | [.ogg](https://example.com/file.ogg ".ogg") | [.oga](https://example.com/file.oga ".oga") | [.opus](https://example.com/file.opus ".opus") | [.mp3](https://example.com/file.mp3 ".mp3") | [.mpa](https://example.com/file.mpa ".mpa") | [.mid](https://example.com/file.mid ".mid") | [.midi](https://example.com/file.midi ".midi") | [.wav](https://example.com/file.wav ".wav") | [.wave](https://example.com/file.wave ".wave") | [.wma](https://example.com/file.wma ".wma")
  - 동영상
    - [.av1](https://example.com/file.av1 ".av1") | [.webm](https://example.com/file.webm ".webm") | [.xvid](https://example.com/file.xvid ".xvid") | [.mkv](https://example.com/file.mkv ".mkv") | [.mk3d](https://example.com/file.mk3d ".mk3d") | [.ogm](https://example.com/file.ogm ".ogm") | [.ogv](https://example.com/file.ogv ".ogv") | [.divx](https://example.com/file.divx ".divx") | [.avi](https://example.com/file.avi ".avi") | [.mp4](https://example.com/file.mp4 ".mp4") | [.mpeg4](https://example.com/file.mpeg4 ".mpeg4") | [.mpv](https://example.com/file.mpv ".mpv") | [.mpeg](https://example.com/file.mpeg ".mpeg") | [.mpg](https://example.com/file.mpg ".mpg")
  - 부제
    - [.vtt](https://example.com/file.vtt ".vtt") | [.ttml](https://example.com/file.ttml ".ttml") | [.dfxp](https://example.com/file.dfxp ".dfxp") | [.srt](https://example.com/file.srt ".srt") | [.sub](https://example.com/file.sub ".sub") | [.sbv](https://example.com/file.sbv ".sbv") | [.scc](https://example.com/file.scc ".scc") | [.mks](https://example.com/file.mks ".mks")
  - 실행 파일
    - [.deb](https://example.com/file.deb ".deb") | [.apk](https://example.com/file.apk ".apk") | [.exe](https://example.com/file.exe ".exe") | [.com](https://example.com/file.com ".com") | [.msi](https://example.com/file.msi ".msi")
  - 스크립트
    - [.bat](https://example.com/file.bat ".bat") | [.sh](https://example.com/file.sh ".sh")
  - 글꼴
    - [.woff](https://example.com/file.woff ".woff") | [.woff2](https://example.com/file.woff2 ".woff2") | [.otf](https://example.com/file.otf ".otf") | [.ttf](https://example.com/file.ttf ".ttf") | [.ttc](https://example.com/file.ttc ".ttc")
  - 압축 파일
    - [.7z](https://example.com/file.7z ".7z") | [.7zip](https://example.com/file.7zip ".7zip") | [.tar](https://example.com/file.tar ".tar") | [.gz](https://example.com/file.gz ".gz") | [.gzip](https://example.com/file.gzip ".gzip") | [.bz2](https://example.com/file.bz2 ".bz2") | [.bzip2](https://example.com/file.bzip2 ".bzip2") | [.zip](https://example.com/file.zip ".zip") | [.rar](https://example.com/file.rar ".rar")
  - 디스크 이미지
    - [.img](https://example.com/file.img ".img") | [.iso](https://example.com/file.iso ".iso") | [.dmg](https://example.com/file.dmg ".dmg") | [.mds](https://example.com/file.mds ".mds") | [.mdf](https://example.com/file.mdf ".mdf") | [.mdx](https://example.com/file.mdx ".mdx")
  - 이미지 편집
    - [.xcf](https://example.com/file.xcf ".xcf") | [.psd](https://example.com/file.psd ".psd")
  ```

다음과 같이 렌더링됩니다.

- 외부 링크
  - [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- 채팅
  - [irc://](irc://example.com "irc://") | [ircs://](ircs://example.com "ircs://") | [irc6://](irc6://example.com "irc6://") | [xmpp://](xmpp://example.com "xmpp://") | [jabber://](jabber://example.com "jabber://") | [discord://](discord://example.com "discord://") | [skype://](skype://example.com "skype://")
- FTP
  - [sftp://](sftp://example.com "sftp://") | [ftp://](ftp://example.com "ftp://") | [aftp://](aftp://example.com "aftp://")
- Magnet
  - [magnet://](magnet://example.com "magnet://")
- Mail
  - [mailto:](mailto:noreply@example.com "mailto:")
- 원격
  - [telnet://](telnet://example.com "telnet://") | [ssh://](ssh://example.com "ssh://") | [git://](git://example.com "git://") | [svn://](svn://example.com "svn://") | [bzr://](bzr://example.com "bzr://")
- Tel
  - [tel:](tel:123-456-7890 "tel:")
- 서적
  - [doi://](doi://example.com "doi://") | [.epub](https://example.com/file.epub ".epub") | [.mobi](https://example.com/file.mobi ".mobi") | [.pdf](https://example.com/file.pdf ".pdf")
- 문서
  - [.odt](https://example.com/file.odt ".odt") | [.sdw](https://example.com/file.sdw ".sdw") | [.sxw](https://example.com/file.sxw ".sxw") | [.uof](https://example.com/file.uof ".uof") | [.uot](https://example.com/file.uot ".uot") | [.doc](https://example.com/file.doc ".doc") | [.docx](https://example.com/file.docx ".docx")
- 텍스트
  - [.txt](https://example.com/file.txt ".txt") | [.csv](https://example.com/file.csv ".csv")
- 프레젠테이션
  - [.odp](https://example.com/file.odp ".odp") | [.fodp](https://example.com/file.fodp ".fodp") | [.sdd](https://example.com/file.sdd ".sdd") | [.sdp](https://example.com/file.sdp ".sdp") | [.sxi](https://example.com/file.sxi ".sxi") | [.uop](https://example.com/file.uop ".uop") | [.ppt](https://example.com/file.ppt ".ppt") | [.pptx](https://example.com/file.pptx ".pptx")
- 스프레드시트
  - [.ods](https://example.com/file.ods ".ods") | [.fods](https://example.com/file.fods ".fods") | [.sdc](https://example.com/file.sdc ".sdc") | [.sxc](https://example.com/file.sxc ".sxc") | [.uos](https://example.com/file.uos ".uos") | [.xls](https://example.com/file.xls ".xls") | [.xlsx](https://example.com/file.xlsx ".xlsx")
- 오디오
  - [.flac](https://example.com/file.flac ".flac") | [.aac](https://example.com/file.aac ".aac") | [.mka](https://example.com/file.mka ".mka") | [.ogg](https://example.com/file.ogg ".ogg") | [.oga](https://example.com/file.oga ".oga") | [.opus](https://example.com/file.opus ".opus") | [.mp3](https://example.com/file.mp3 ".mp3") | [.mpa](https://example.com/file.mpa ".mpa") | [.mid](https://example.com/file.mid ".mid") | [.midi](https://example.com/file.midi ".midi") | [.wav](https://example.com/file.wav ".wav") | [.wave](https://example.com/file.wave ".wave") | [.wma](https://example.com/file.wma ".wma")
- 동영상
  - [.av1](https://example.com/file.av1 ".av1") | [.webm](https://example.com/file.webm ".webm") | [.xvid](https://example.com/file.xvid ".xvid") | [.mkv](https://example.com/file.mkv ".mkv") | [.mk3d](https://example.com/file.mk3d ".mk3d") | [.ogm](https://example.com/file.ogm ".ogm") | [.ogv](https://example.com/file.ogv ".ogv") | [.divx](https://example.com/file.divx ".divx") | [.avi](https://example.com/file.avi ".avi") | [.mp4](https://example.com/file.mp4 ".mp4") | [.mpeg4](https://example.com/file.mpeg4 ".mpeg4") | [.mpv](https://example.com/file.mpv ".mpv") | [.mpeg](https://example.com/file.mpeg ".mpeg") | [.mpg](https://example.com/file.mpg ".mpg")
- 부제
  - [.vtt](https://example.com/file.vtt ".vtt") | [.ttml](https://example.com/file.ttml ".ttml") | [.dfxp](https://example.com/file.dfxp ".dfxp") | [.srt](https://example.com/file.srt ".srt") | [.sub](https://example.com/file.sub ".sub") | [.sbv](https://example.com/file.sbv ".sbv") | [.scc](https://example.com/file.scc ".scc") | [.mks](https://example.com/file.mks ".mks")
- 실행 파일
  - [.deb](https://example.com/file.deb ".deb") | [.apk](https://example.com/file.apk ".apk") | [.exe](https://example.com/file.exe ".exe") | [.com](https://example.com/file.com ".com") | [.msi](https://example.com/file.msi ".msi")
- 스크립트
  - [.bat](https://example.com/file.bat ".bat") | [.sh](https://example.com/file.sh ".sh")
- 글꼴
  - [.woff](https://example.com/file.woff ".woff") | [.woff2](https://example.com/file.woff2 ".woff2") | [.otf](https://example.com/file.otf ".otf") | [.ttf](https://example.com/file.ttf ".ttf") | [.ttc](https://example.com/file.ttc ".ttc")
- 압축 파일
  - [.7z](https://example.com/file.7z ".7z") | [.7zip](https://example.com/file.7zip ".7zip") | [.tar](https://example.com/file.tar ".tar") | [.gz](https://example.com/file.gz ".gz") | [.gzip](https://example.com/file.gzip ".gzip") | [.bz2](https://example.com/file.bz2 ".bz2") | [.bzip2](https://example.com/file.bzip2 ".bzip2") | [.zip](https://example.com/file.zip ".zip") | [.rar](https://example.com/file.rar ".rar")
- 디스크 이미지
  - [.img](https://example.com/file.img ".img") | [.iso](https://example.com/file.iso ".iso") | [.dmg](https://example.com/file.dmg ".dmg") | [.mds](https://example.com/file.mds ".mds") | [.mdf](https://example.com/file.mdf ".mdf") | [.mdx](https://example.com/file.mdx ".mdx")
- 이미지 편집
  - [.xcf](https://example.com/file.xcf ".xcf") | [.psd](https://example.com/file.psd ".psd")

URI(Uniform Resource Identifier) 체계의 공식 목록은 IANA 공식 웹사이트에서 확인할 수 있습니다. [^uri-schemes-iana] 그러나 `discord://` 및 `bzr://` (2022-05-13 일자 IANA 문서 기준)과 같이 널리 사용되는 모든 URI 체계가 등록 및/또는 제출된 것은 아닙니다. 그럼에도 불구하고 이러한 인기 있는 등록되지 않은 URI 스키마가 위의 코드에 포함되었습니다.

[^uri-schemes-iana]: IANA: [URI Schemes](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml)

유용하게 사용하시길 바랍니다!

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link="https://img.youronly.one/h/hugo-markdown-link-render.webp"
  linkrel="noopener"

  title="Hugo에서 Markdown 링크를 사용자 지정하는 방법"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
