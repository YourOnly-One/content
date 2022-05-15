+++
title = "Hugo에서 Markdown 링크를 사용자 지정하는 방법"
description = "Hugo Markdown 링크에 상호 참조 지원 및 링크 아이콘을 추가하는 방법"

date = "2022-05-15T12:23:48+09:00"                                          # manually adjust to local timezone
#lastmod = "2022-04-07T17:53:01+00:00"                                       # manually adjust to local timezone

#aliases = [""]
slug = "how-to-customize-markdown-links-hugo"
translationKey = "how-to-customize-markdown-links-hugo-2022135"
relCanonical = "https://im.youronly.one/techmagus/ko/codebits/how-to-customize-markdown-links-hugo-2022135/"
#disqus_url = ""                                                    # no use case in sites by Yelosan Publishing (YourOnly.One)
#disqus_identifier = ""                                             # set if slug date of this content is different from main translation (en-PH)

syndications = ["https://twitter.com/YourOnlyONEofcl/status/1525681473948471296", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/657387235430510", "https://diasp.org/posts/f23d3ae0b62f013a6afb28a1592b385a", "https://mastodon.social/web/@youronlyone/108303918152249905"]

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

{{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크가 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}에서 렌더링되는 방식을 사용자 정의하는 방법을 찾고 계십니까? 링크 아이콘을 추가하고 싶습니까? 또는 (이전 방법) `{{</* ref */>}}`를 사용하지 않고 내부 상호 참조에 대한 지원을 추가하는 것은 어떻습니까?

<!--more-->

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}에는 {{% quote type="work" lang="en" %}}맞춤 템플릿이 <bdi lang="en">Markdown</bdi> 렌더링 기능을 재정의할 수 있도록{{% /quote %}}하는 [^hugo-markdown-render-hooks] {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 렌더 후크라는 기능이 있습니다. 현재 일반적으로 요청되는 4개의 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 렌더링 영역을 지원합니다.

- <bdi lang="en">codeblock</bdi>
- <bdi lang="en">heading</bdi>
- <bdi lang="en">image</bdi>
- <bdi lang="en">link</bdi>

이 게시물에서는 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}의 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크가 렌더링되는 방식을 변경할 것입니다.

[^hugo-markdown-render-hooks]: Hugo: [Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## 특징

- 일반 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크 형식을 사용하여 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} 내에서 상호 참조
  - `{{</* ref */>}}` 및 `{{%/* relref */%}}` 또는 그 변형은 과거의 것입니다.
  - 콘텐츠 제목 자동 사용
  - 다국어 지원
  - {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크 텍스트 및 제목 지원
  - URI 조각 지원
- {{% quote type="name" lang="en" %}}JavaScript{{% /quote %}}를 사용하지 않고 링크 아이콘 추가
  - 내부 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크 지원

## 상호 참조 추가

1. 이 디렉토리 `/layouts/_default/_markup/`에 `render-link.html`이라는 파일을 만듭니다.
1. 아래 코드를 추가하세요.

    ```go-html-template
    {{- $url := (urls.Parse .Destination) -}}
    {{- $internal := site.GetPage .Destination -}}
    {{- $fragment := $url.Fragment -}}
    {{- with $fragment -}}{{ $fragment = printf "#%s" $fragment }}{{- end -}}
    {{- $destination := printf "%s%s" (or $internal.RelPermalink .Destination) $fragment -}}
    <a href="{{ $destination | safeURL }}"{{ with or .Title $internal.LinkTitle .Test }} title="{{ . }}"{{ end }}{{ if not $internal }} rel="noopener external"{{ end }}>{{ or .Text .Title $internal.LinkTitle | safeHTML }}</a>
    ```

그게 다야

### 사용하는 방법

다음 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크

  ```markdown {linenos=false}
  - [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](20181210-browser-wars-iii)
  - [](/20181210-browser-wars-iii)
  - [텍스트 포함](20181210-browser-wars-iii)
  - [](20181210-browser-wars-iii "제목으로")
  - [텍스트, 제목 및 조각 포함](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "텍스트, 제목 및 조각 포함")
  ```

`ko`에서 다음과 같이 렌더링됩니다.

- [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [텍스트 포함](20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "제목으로")
- [텍스트, 제목 및 조각 포함](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "텍스트, 제목 및 조각 포함")

#### 주의 사항

현재 다음 형식을 지원하지 않습니다.

```markdown {linenos=false}
- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
```

잘못된 링크로 다음과 같이 렌더링됩니다.

- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)

다음과 같이 생성된 영구 링크를 대신 사용하세요(접두사 `/`가 중요).

```markdown {linenos=false}
- [Browser Wars III Front: 브라우저 엔진](/ko/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)
```

다음과 같이 렌더링됩니다.

- [Browser Wars III Front: 브라우저 엔진](/ko/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)

#### 개선

위의 코드를 자유롭게 개선하고 커뮤니티에 다시 공유하십시오. 귀하의 웹사이트와 이름을 제공하여 적절하게 크레딧을 받으십시오.

## 링크 아이콘 추가

링크 아이콘을 추가하려면 다음 단계를 따르세요.

1. `render-link.html` 파일을 엽니다(이전 섹션에서 생성).
1. 전체 코드를 다음으로 교체합니다.

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

1. 스타일시트 파일에 다음을 추가합니다.

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

### 사용하는 방법

다음 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크

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

다음과 같이 렌더링됩니다.

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

URI(Uniform Resource Identifier) 체계의 공식 목록은 IANA 공식 웹사이트에서 확인할 수 있습니다. [^uri-schemes-iana] 그러나 `discord://` 및 `bzr://`(2022-05-13 일자 IANA 문서 기준)과 같이 널리 사용되는 모든 URI 체계가 등록 및/또는 제출된 것은 아닙니다. 그럼에도 불구하고 이러한 인기 있는 등록되지 않은 URI 스키마가 위의 코드에 포함되었습니다.

[^uri-schemes-iana]: IANA: [URI Schemes](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml)

유용하게 사용하시길 바랍니다!

---

<!-- markdownlint-disable -->
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
<!-- markdownlint-enable -->

---

고시 : Google 번역
