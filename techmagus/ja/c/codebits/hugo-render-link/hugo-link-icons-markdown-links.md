+++
title = "Hugo Markdownリンクにリンクアイコンを追加する方法"
description = "HugoでMarkdownリンクのリンクアイコンを追加する方法"

publishdate = "2022-05-20T20:24:27+09:00"                                          # manually adjust to local timezone
lastmod = "2022-05-27T20:28:28+08:00"                                       # manually adjust to local timezone

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

リンクアイコンは素晴らしいです。 リンクが何であるかを読者に知らせます。 外部ですか？ それともビデオ？ リンクをクリックすると、ダウンロードが開始されますか、それともデフォルトのメールプログラムが開きますか？ リンクアイコンは、開発者またはコンテンツ作成者がリンクまたはリンクの欠如を簡単に見つけるのにも役立ちます。

<!--more-->

リンクアイコンは、10年前に{{% quote type="title" lang="en" %}}Wikipedia{{% /quote %}}で始まり、普及しました [^wikipedia-link-icons]。 誰もが自分のウェブサイトやブログにリンクアイコンを追加するためのCMSプラグインを探していました。 当時の方法は、小さな`.png`画像ファイルをアイコンとして使用することでした。 でも今日は？ {{% quote type="name" lang="en" %}}Unicode{{% /quote %}}絵文字を使用し、適切な絵文字が利用できない場合にのみ`.svg`を使用します。

この投稿では、{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンクを介して{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}にリンクアイコンのサポートを追加します。 レンダリングフックの力のおかげで、ショートコードは必要ありません。通常の `[text](https://example.com "Title")`リンクだけです [^hugo-markdown-render-hooks]。

[^wikipedia-link-icons]: [w:Help:External link icons](https://en.wikipedia.org/wiki/Help:External_link_icons "w:Help:External link icons")
[^hugo-markdown-render-hooks]: [Hugo: Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## 特徴

- {{% quote type="name" lang="en" %}}JavaScript{{% /quote %}}を使用せずにリンクアイコンを追加する
  - 内部{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンクのサポート付き
- [](hugo-cross-reference-markdown-links.md)の機能

## 新着情報

これらは、2022年5月27日現在の新機能です。

- 同じ（サブ）ドメインに外部アイコンがなくなりました。
- オーディオ、ビデオ、フォント、ディスクイメージ、ドキュメント、プレゼンテーション、スプレッドシートなど、より多くの外部リンクのサポート！

## 手順

リンクアイコンを追加するには、以下の手順に従います。

1. このディレクトリに`render-link.html`というファイルを作成します`/layouts/_default/_markup/`
1. このコードをコピーして貼り付けます。

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
      {{- $chat := or (strings.HasPrefix .Destination "irc://") (strings.HasPrefix .Destination "ircs://") (strings.HasPrefix .Destination "irc6://") (strings.HasPrefix .Destination "xmpp://") (strings.HasPrefix .Destination "jabber://") (strings.HasPrefix .Destination "discord://") (strings.HasPrefix .Destination "skype://") -}}
      {{- $ftp := or (strings.HasPrefix .Destination "ftp://") (strings.HasPrefix .Destination "aftp://") -}}
      {{- $magnet := strings.HasPrefix .Destination "magnet://" -}}
      {{- $mail := strings.HasPrefix .Destination "mailto:" -}}
      {{- $remote := or (strings.HasPrefix .Destination "telnet://") (strings.HasPrefix .Destination "ssh://") (strings.HasPrefix .Destination "sftp://") (strings.HasPrefix .Destination "git://") (strings.HasPrefix .Destination "svn://") (strings.HasPrefix .Destination "bzr://") -}}
      {{- $tel := strings.HasPrefix .Destination "tel:" -}}

    {{/* READING */}}
      {{- $books := or (strings.HasPrefix .Destination "doi://") (strings.HasSuffix .Destination ".epub") (strings.HasSuffix .Destination ".mobi") (strings.HasSuffix .Destination ".pdf") -}}
      {{- $document := or (strings.HasSuffix .Destination ".odt") (strings.HasSuffix .Destination ".sdw") (strings.HasSuffix .Destination ".sxw") (strings.HasSuffix .Destination ".uof") (strings.HasSuffix .Destination ".uot") (strings.HasSuffix .Destination ".doc") (strings.HasSuffix .Destination ".docx") -}}
      {{- $text := or (strings.HasSuffix .Destination ".txt") (strings.HasSuffix .Destination ".csv") -}}
      {{- $presentation := or (strings.HasSuffix .Destination ".odp") (strings.HasSuffix .Destination ".fodp") (strings.HasSuffix .Destination ".sdd") (strings.HasSuffix .Destination ".sdp") (strings.HasSuffix .Destination ".sxi") (strings.HasSuffix .Destination ".uop") (strings.HasSuffix .Destination ".ppt") (strings.HasSuffix .Destination ".pptx") -}}
      {{- $spreadsheet := or (strings.HasSuffix .Destination ".ods") (strings.HasSuffix .Destination ".fods") (strings.HasSuffix .Destination ".sdc") (strings.HasSuffix .Destination ".sxc") (strings.HasSuffix .Destination ".uos") (strings.HasSuffix .Destination ".xls") (strings.HasSuffix .Destination ".xlsx") -}}

    {{/* MEDIA */}}
      {{- $audio := or (strings.HasSuffix .Destination ".flac") (strings.HasSuffix .Destination ".aac") (strings.HasSuffix .Destination ".mka") (strings.HasSuffix .Destination ".ogg") (strings.HasSuffix .Destination ".oga") (strings.HasSuffix .Destination ".opus") (strings.HasSuffix .Destination ".mp3") (strings.HasSuffix .Destination ".mpa") (strings.HasSuffix .Destination ".mid") (strings.HasSuffix .Destination ".midi") (strings.HasSuffix .Destination ".wav") (strings.HasSuffix .Destination ".wave") (strings.HasSuffix .Destination ".wma") -}}
      {{- $video := or (strings.HasSuffix .Destination ".av1") (strings.HasSuffix .Destination ".webm") (strings.HasSuffix .Destination ".xvid") (strings.HasSuffix .Destination ".mkv") (strings.HasSuffix .Destination ".mk3d") (strings.HasSuffix .Destination ".ogm") (strings.HasSuffix .Destination ".ogv") (strings.HasSuffix .Destination ".divx") (strings.HasSuffix .Destination ".avi") (strings.HasSuffix .Destination ".mp4") (strings.HasSuffix .Destination ".mpeg4") (strings.HasSuffix .Destination ".mpv") (strings.HasSuffix .Destination ".mpeg") (strings.HasSuffix .Destination ".mpg") -}}
      {{- $subtitle := or (strings.HasSuffix .Destination ".vtt") (strings.HasSuffix .Destination ".ttml") (strings.HasSuffix .Destination ".dfxp") (strings.HasSuffix .Destination ".srt") (strings.HasSuffix .Destination ".sub") (strings.HasSuffix .Destination ".sbv") (strings.HasSuffix .Destination ".scc") (strings.HasSuffix .Destination ".mks") -}}

    {{/* EXECUTABLES */}}
      {{- $executable := or (strings.HasSuffix .Destination ".deb") (strings.HasSuffix .Destination ".apk") (strings.HasSuffix .Destination ".exe") (strings.HasSuffix .Destination ".com") (strings.HasSuffix .Destination ".msi") -}}
      {{- $scripts := or (strings.HasSuffix .Destination ".bat") (strings.HasSuffix .Destination ".sh") -}}

    {{/* OTHERS */}}
      {{- $fonts := or (strings.HasSuffix .Destination ".woff") (strings.HasSuffix .Destination ".woff2") (strings.HasSuffix .Destination ".otf") (strings.HasSuffix .Destination ".ttf") (strings.HasSuffix .Destination ".ttc") -}}
      {{- $compressed := or (strings.HasSuffix .Destination ".7z") (strings.HasSuffix .Destination ".7zip") (strings.HasSuffix .Destination ".tar") (strings.HasSuffix .Destination ".gz") (strings.HasSuffix .Destination ".gzip") (strings.HasSuffix .Destination ".bz2") (strings.HasSuffix .Destination ".bzip2") (strings.HasSuffix .Destination ".zip") (strings.HasSuffix .Destination ".rar") -}}
      {{- $diskimage := or (strings.HasSuffix .Destination ".img") (strings.HasSuffix .Destination ".iso") (strings.HasSuffix .Destination ".dmg")  (strings.HasSuffix .Destination ".mds") (strings.HasSuffix .Destination ".mdf") (strings.HasSuffix .Destination ".mdx") -}}
      {{- $imagediting := or (strings.HasSuffix .Destination ".xcf") (strings.HasSuffix .Destination ".psd") -}}

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

1. スタイルシートファイルに次を追加します。

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
      .icon_ftp::after          { content: "\23EC";                                     /* ⏬ */ }
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

1. `.svg`アイコンをダウンロードします：[link-icons.7z](./techmagus/dls/link-icons.7z)

    - ソース（すべてパブリックドメイン）：
      - プレゼンテーション：[warszawianka](https://openclipart.org/artist/warszawianka)による[tango x office presentation](https://openclipart.org/detail/36505/tango-x-office-presentation)
      - スプレッドシート：[warszawianka](https://openclipart.org/artist/warszawianka)による[tango x office spreadsheet](https://openclipart.org/detail/36517/tango-x-office-spreadsheet)
      - 字幕：[sixsixfive](https://openclipart.org/artist/sixsixfive)の[mimetype subtitle](https://openclipart.org/detail/212110/mimetype-subtitle)
      - 実行可能ファイル：[sixsixfive](https://openclipart.org/artist/sixsixfive)による[mimetype binary](https://openclipart.org/detail/212161/mimetype-binary)
      - スクリプト：[warszawianka](https://openclipart.org/artist/warszawianka)による[tango text x script](https://openclipart.org/detail/36175/tango-text-x-script)
      - フォント：[warszawianka](https://openclipart.org/artist/warszawianka)による[tango preferences desktop font](https://openclipart.org/detail/35257/tango-preferences-desktop-font)
      - 画像編集：[GDJ](https://openclipart.org/artist/GDJ)による[Artists Brush And Paint](https://openclipart.org/detail/231061/artists-brush-and-paint)

      リストされたソースからホットリンクすることが可能です。 ただし、それらが設定されているかどうかについての情報はありません。
      {.note}

1. `/static/fonts/`フォルダーにある`.svg`ファイルを抽出します。

## 使い方

次の{{% quote type="name" lang="en" %}}Markdown{{% /quote %}}リンク

  ```markdown {linenos=false}
  - 外部リンク
    - [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
  - チャット
    - [irc://](irc://example.com "irc://") | [ircs://](ircs://example.com "ircs://") | [irc6://](irc6://example.com "irc6://") | [xmpp://](xmpp://example.com "xmpp://") | [jabber://](jabber://example.com "jabber://") | [discord://](discord://example.com "discord://") | [skype://](skype://example.com "skype://")
  - FTP
    - [ftp://](ftp://example.com "ftp://") | [aftp://](aftp://example.com "aftp://")
  - Magnet
    - [magnet://](magnet://example.com "magnet://")
  - Mail
    - [mailto:](mailto:noreply@example.com "mailto:")
  - リモート
    - [telnet://](telnet://example.com "telnet://") | [ssh://](ssh://example.com "ssh://") | [sftp://](sftp://example.com "sftp://") | [git://](git://example.com "git://") | [svn://](svn://example.com "svn://") | [bzr://](bzr://example.com "bzr://")
  - Tel
    - [tel:](tel:123-456-7890 "tel:")
  - 本
    - [doi://](doi://example.com "doi://") | [.epub](https://example.com/file.epub ".epub") | [.mobi](https://example.com/file.mobi ".mobi") | [.pdf](https://example.com/file.pdf ".pdf")
  - 書類
    - [.odt](https://example.com/file.odt ".odt") | [.sdw](https://example.com/file.sdw ".sdw") | [.sxw](https://example.com/file.sxw ".sxw") | [.uof](https://example.com/file.uof ".uof") | [.uot](https://example.com/file.uot ".uot") | [.doc](https://example.com/file.doc ".doc") | [.docx](https://example.com/file.docx ".docx")
  - 文章
    - [.txt](https://example.com/file.txt ".txt") | [.csv](https://example.com/file.csv ".csv")
  - プレゼンテーション
    - [.odp](https://example.com/file.odp ".odp") | [.fodp](https://example.com/file.fodp ".fodp") | [.sdd](https://example.com/file.sdd ".sdd") | [.sdp](https://example.com/file.sdp ".sdp") | [.sxi](https://example.com/file.sxi ".sxi") | [.uop](https://example.com/file.uop ".uop") | [.ppt](https://example.com/file.ppt ".ppt") | [.pptx](https://example.com/file.pptx ".pptx")
  - スプレッドシート
    - [.ods](https://example.com/file.ods ".ods") | [.fods](https://example.com/file.fods ".fods") | [.sdc](https://example.com/file.sdc ".sdc") | [.sxc](https://example.com/file.sxc ".sxc") | [.uos](https://example.com/file.uos ".uos") | [.xls](https://example.com/file.xls ".xls") | [.xlsx](https://example.com/file.xlsx ".xlsx")
  - オーディオ
    - [.flac](https://example.com/file.flac ".flac") | [.aac](https://example.com/file.aac ".aac") | [.mka](https://example.com/file.mka ".mka") | [.ogg](https://example.com/file.ogg ".ogg") | [.oga](https://example.com/file.oga ".oga") | [.opus](https://example.com/file.opus ".opus") | [.mp3](https://example.com/file.mp3 ".mp3") | [.mpa](https://example.com/file.mpa ".mpa") | [.mid](https://example.com/file.mid ".mid") | [.midi](https://example.com/file.midi ".midi") | [.wav](https://example.com/file.wav ".wav") | [.wave](https://example.com/file.wave ".wave") | [.wma](https://example.com/file.wma ".wma")
  - ビデオ
    - [.av1](https://example.com/file.av1 ".av1") | [.webm](https://example.com/file.webm ".webm") | [.xvid](https://example.com/file.xvid ".xvid") | [.mkv](https://example.com/file.mkv ".mkv") | [.mk3d](https://example.com/file.mk3d ".mk3d") | [.ogm](https://example.com/file.ogm ".ogm") | [.ogv](https://example.com/file.ogv ".ogv") | [.divx](https://example.com/file.divx ".divx") | [.avi](https://example.com/file.avi ".avi") | [.mp4](https://example.com/file.mp4 ".mp4") | [.mpeg4](https://example.com/file.mpeg4 ".mpeg4") | [.mpv](https://example.com/file.mpv ".mpv") | [.mpeg](https://example.com/file.mpeg ".mpeg") | [.mpg](https://example.com/file.mpg ".mpg")
  - 字幕
    - [.vtt](https://example.com/file.vtt ".vtt") | [.ttml](https://example.com/file.ttml ".ttml") | [.dfxp](https://example.com/file.dfxp ".dfxp") | [.srt](https://example.com/file.srt ".srt") | [.sub](https://example.com/file.sub ".sub") | [.sbv](https://example.com/file.sbv ".sbv") | [.scc](https://example.com/file.scc ".scc") | [.mks](https://example.com/file.mks ".mks")
  - 実行可能ファイル
    - [.deb](https://example.com/file.deb ".deb") | [.apk](https://example.com/file.apk ".apk") | [.exe](https://example.com/file.exe ".exe") | [.com](https://example.com/file.com ".com") | [.msi](https://example.com/file.msi ".msi")
  - スクリプト
    - [.bat](https://example.com/file.bat ".bat") | [.sh](https://example.com/file.sh ".sh")
  - フォント
    - [.woff](https://example.com/file.woff ".woff") | [.woff2](https://example.com/file.woff2 ".woff2") | [.otf](https://example.com/file.otf ".otf") | [.ttf](https://example.com/file.ttf ".ttf") | [.ttc](https://example.com/file.ttc ".ttc")
  - 圧縮されたファイル
    - [.7z](https://example.com/file.7z ".7z") | [.7zip](https://example.com/file.7zip ".7zip") | [.tar](https://example.com/file.tar ".tar") | [.gz](https://example.com/file.gz ".gz") | [.gzip](https://example.com/file.gzip ".gzip") | [.bz2](https://example.com/file.bz2 ".bz2") | [.bzip2](https://example.com/file.bzip2 ".bzip2") | [.zip](https://example.com/file.zip ".zip") | [.rar](https://example.com/file.rar ".rar")
  - ディスクイメージ
    - [.img](https://example.com/file.img ".img") | [.iso](https://example.com/file.iso ".iso") | [.dmg](https://example.com/file.dmg ".dmg") | [.mds](https://example.com/file.mds ".mds") | [.mdf](https://example.com/file.mdf ".mdf") | [.mdx](https://example.com/file.mdx ".mdx")
  - 画像編集
    - [.xcf](https://example.com/file.xcf ".xcf") | [.psd](https://example.com/file.psd ".psd")
  ```

次のようにレンダリングされます：

- 外部リンク
  - [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- チャット
  - [irc://](irc://example.com "irc://") | [ircs://](ircs://example.com "ircs://") | [irc6://](irc6://example.com "irc6://") | [xmpp://](xmpp://example.com "xmpp://") | [jabber://](jabber://example.com "jabber://") | [discord://](discord://example.com "discord://") | [skype://](skype://example.com "skype://")
- FTP
  - [ftp://](ftp://example.com "ftp://") | [aftp://](aftp://example.com "aftp://")
- Magnet
  - [magnet://](magnet://example.com "magnet://")
- Mail
  - [mailto:](mailto:noreply@example.com "mailto:")
- リモート
  - [telnet://](telnet://example.com "telnet://") | [ssh://](ssh://example.com "ssh://") | [sftp://](sftp://example.com "sftp://") | [git://](git://example.com "git://") | [svn://](svn://example.com "svn://") | [bzr://](bzr://example.com "bzr://")
- Tel
  - [tel:](tel:123-456-7890 "tel:")
- 本
  - [doi://](doi://example.com "doi://") | [.epub](https://example.com/file.epub ".epub") | [.mobi](https://example.com/file.mobi ".mobi") | [.pdf](https://example.com/file.pdf ".pdf")
- 書類
  - [.odt](https://example.com/file.odt ".odt") | [.sdw](https://example.com/file.sdw ".sdw") | [.sxw](https://example.com/file.sxw ".sxw") | [.uof](https://example.com/file.uof ".uof") | [.uot](https://example.com/file.uot ".uot") | [.doc](https://example.com/file.doc ".doc") | [.docx](https://example.com/file.docx ".docx")
- 文章
  - [.txt](https://example.com/file.txt ".txt") | [.csv](https://example.com/file.csv ".csv")
- プレゼンテーション
  - [.odp](https://example.com/file.odp ".odp") | [.fodp](https://example.com/file.fodp ".fodp") | [.sdd](https://example.com/file.sdd ".sdd") | [.sdp](https://example.com/file.sdp ".sdp") | [.sxi](https://example.com/file.sxi ".sxi") | [.uop](https://example.com/file.uop ".uop") | [.ppt](https://example.com/file.ppt ".ppt") | [.pptx](https://example.com/file.pptx ".pptx")
- スプレッドシート
  - [.ods](https://example.com/file.ods ".ods") | [.fods](https://example.com/file.fods ".fods") | [.sdc](https://example.com/file.sdc ".sdc") | [.sxc](https://example.com/file.sxc ".sxc") | [.uos](https://example.com/file.uos ".uos") | [.xls](https://example.com/file.xls ".xls") | [.xlsx](https://example.com/file.xlsx ".xlsx")
- オーディオ
  - [.flac](https://example.com/file.flac ".flac") | [.aac](https://example.com/file.aac ".aac") | [.mka](https://example.com/file.mka ".mka") | [.ogg](https://example.com/file.ogg ".ogg") | [.oga](https://example.com/file.oga ".oga") | [.opus](https://example.com/file.opus ".opus") | [.mp3](https://example.com/file.mp3 ".mp3") | [.mpa](https://example.com/file.mpa ".mpa") | [.mid](https://example.com/file.mid ".mid") | [.midi](https://example.com/file.midi ".midi") | [.wav](https://example.com/file.wav ".wav") | [.wave](https://example.com/file.wave ".wave") | [.wma](https://example.com/file.wma ".wma")
- ビデオ
  - [.av1](https://example.com/file.av1 ".av1") | [.webm](https://example.com/file.webm ".webm") | [.xvid](https://example.com/file.xvid ".xvid") | [.mkv](https://example.com/file.mkv ".mkv") | [.mk3d](https://example.com/file.mk3d ".mk3d") | [.ogm](https://example.com/file.ogm ".ogm") | [.ogv](https://example.com/file.ogv ".ogv") | [.divx](https://example.com/file.divx ".divx") | [.avi](https://example.com/file.avi ".avi") | [.mp4](https://example.com/file.mp4 ".mp4") | [.mpeg4](https://example.com/file.mpeg4 ".mpeg4") | [.mpv](https://example.com/file.mpv ".mpv") | [.mpeg](https://example.com/file.mpeg ".mpeg") | [.mpg](https://example.com/file.mpg ".mpg")
- 字幕
  - [.vtt](https://example.com/file.vtt ".vtt") | [.ttml](https://example.com/file.ttml ".ttml") | [.dfxp](https://example.com/file.dfxp ".dfxp") | [.srt](https://example.com/file.srt ".srt") | [.sub](https://example.com/file.sub ".sub") | [.sbv](https://example.com/file.sbv ".sbv") | [.scc](https://example.com/file.scc ".scc") | [.mks](https://example.com/file.mks ".mks")
- 実行可能ファイル
  - [.deb](https://example.com/file.deb ".deb") | [.apk](https://example.com/file.apk ".apk") | [.exe](https://example.com/file.exe ".exe") | [.com](https://example.com/file.com ".com") | [.msi](https://example.com/file.msi ".msi")
- スクリプト
  - [.bat](https://example.com/file.bat ".bat") | [.sh](https://example.com/file.sh ".sh")
- フォント
  - [.woff](https://example.com/file.woff ".woff") | [.woff2](https://example.com/file.woff2 ".woff2") | [.otf](https://example.com/file.otf ".otf") | [.ttf](https://example.com/file.ttf ".ttf") | [.ttc](https://example.com/file.ttc ".ttc")
- 圧縮されたファイル
  - [.7z](https://example.com/file.7z ".7z") | [.7zip](https://example.com/file.7zip ".7zip") | [.tar](https://example.com/file.tar ".tar") | [.gz](https://example.com/file.gz ".gz") | [.gzip](https://example.com/file.gzip ".gzip") | [.bz2](https://example.com/file.bz2 ".bz2") | [.bzip2](https://example.com/file.bzip2 ".bzip2") | [.zip](https://example.com/file.zip ".zip") | [.rar](https://example.com/file.rar ".rar")
- ディスクイメージ
  - [.img](https://example.com/file.img ".img") | [.iso](https://example.com/file.iso ".iso") | [.dmg](https://example.com/file.dmg ".dmg") | [.mds](https://example.com/file.mds ".mds") | [.mdf](https://example.com/file.mdf ".mdf") | [.mdx](https://example.com/file.mdx ".mdx")
- 画像編集
  - [.xcf](https://example.com/file.xcf ".xcf") | [.psd](https://example.com/file.psd ".psd")

URI（Uniform Resource Identifier）スキームの公式リストは、IANAの公式Webサイトにあります。 [^uri-schemes-iana] ただし、すべての一般的なURIスキームが登録および/または送信されたわけではありません。たとえば、 `discord：//`や `bzr：//`（2022-05-13日付のIANAドキュメントの時点）。 とにかく、これらの人気のある未登録のURIスキームは上記のコードに含まれていました。

[^uri-schemes-iana]: IANA: [URI Schemes](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml)

お役に立てば幸いです。

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
