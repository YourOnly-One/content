+++
title = "Hugo Markdown 링크에 상호 참조를 추가하는 방법"
description = "Hugo에서 Markdown 링크에 대한 상호 참조 지원을 추가하는 방법"

publishdate = 2022-05-20T20:24:27+09:00                                          # manually adjust to local timezone
lastmod = 2022-06-17T15:07:00+09:00                                       # manually adjust to local timezone

aliases = ["/ko/codebits/how-to-add-cross-reference-hugo-markdown-links-2022140", "/ko/codebits/hugo-render-link/how-to-add-cross-reference-hugo-markdown-links-2022140"]
slug = "how-to-add-cross-reference-hugo-markdown-links"
translationKey = "how-to-add-cross-reference-hugo-markdown-links-2022140"
relCanonical = "https://im.youronly.one/techmagus/ko/codebits/hugo/hugo-render-link/how-to-add-cross-reference-hugo-markdown-links-2022140/"
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
images = ["images/h/hugo-markdown-link-render.webp"]                 # used for og:images, etc.; first image is cover image
#videos = ["https://www.youtube.com/watch?v="]                         # used for og:video, etc.

type = "article"                                                             # article, sitepage, review

#draft = false

#license = ""                                                         # only set if the post license is not the same as the site license

# For /yuki/ choose one and remove everything else
[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (雪亮 | 스노 | Yuki)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}의 덜 일반적으로 사용되는 기능 중 하나는 렌더 후크입니다. 이 게시물에서는 렌더 후크를 사용하여 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}}의 기본 링크 생성 방식인 `[텍스트](https://example.com#fragment "제목")`에 내부 상호 참조 지원을 추가할 것입니다.

<!--more-->

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}의 내부 상호 참조는 일반적으로 내장 단축 코드 `{{</* ref */>}}` 또는 `{{%/* relref */%}}`를 사용하여 수행되지만 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} 버전 0.62.0부터 [^hugo-0.62.0] 알고 계셨습니까? 권장되는 방법은 렌더 후크를 사용하는 것입니까 [^hugo-markdown-render-hooks]?

[^hugo-0.62.0]: [Hugo v0.62.0](https://github.com/gohugoio/hugo/releases/tag/v0.62.0 "Hugo v0.62.0")
[^hugo-markdown-render-hooks]: [Hugo: Markdown Render Hooks](https://gohugo.io/templates/render-hooks/ "Hugo: Markdown Render Hooks")

## 특징

- 일반 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크 형식을 사용하여 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} 내에서 상호 참조
  - `{{</* ref */>}}` 및 `{{%/* relref */%}}` 또는 그 변형은 과거의 것입니다.
  - 콘텐츠 제목 자동 사용
  - 다국어 지원
  - {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크 텍스트 및 제목 지원
  - URI 조각 지원

## 새로운 소식

- 2022년 6월 17일:
  - 수정: `[text](./path/to/content/)` 및 `[text.ext](./path/to/file.ext)` 구문

- 2022년 5월 27일:
  - `[텍스트](./path/to/content/)`
  - `[text.ext](./path/to/file.ext)`
  - [사용하는 방법](#how-to-use) 섹션을 재구성했습니다.

## 단계

1. 이 디렉토리 `/layouts/_default/_markup/`에 `render-link.html`이라는 파일을 만듭니다.
1. 아래 코드를 추가하세요.

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

그게 다야

## 사용하는 방법 {#how-to-use}

### 전통적인

```markdown
- [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- [직접](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/ "제목")
- [#fragment로 직접](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/#fragment "제목")
- [#조각만](#fragment)
```

- [https://example.com/#fragment](https://example.com/#fragment "https://example.com/#fragment")
- [직접](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/ "제목")
- [#fragment로 직접](https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/#fragment "제목")
- [#조각만](#fragment)

### 새로운

#### 특별한

`[text](./path/to/content/)` 형식은 현재 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}}의 일부가 아닌 동일한 (하위) 도메인 아래 웹사이트의 다른 부분에 대한 링크를 생성하려는 경우에 유용합니다. 프로젝트. 이 형식은 [](hugo-link-icons-markdown-links.md)도 설치된 경우 외부 링크 아이콘을 생성하지 않습니다.

`[text.ext](./path/to/file.ext)`는 현재 {{% quote type="name" lang="en" %}}Hugo{{% /quote %}} 프로젝트 내부 또는 외부에서 동일한 (하위) 도메인에서 호스팅되는 다운로드 링크에 유용합니다.

```markdown
- [선물을 보내다](./p/gift/)
- [link-icons.7z](./techmagus/dls/link-icons.7z)
```

- [선물을 보내다](./p/gift/)
- [link-icons.7z](./techmagus/dls/link-icons.7z)

#### 파일 확장자 없이

```markdown
- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "제목")
- [](/20181210-browser-wars-iii "제목")
- [텍스트](20181210-browser-wars-iii)
- [텍스트](/20181210-browser-wars-iii)
- [텍스트](20181210-browser-wars-iii "제목")
- [텍스트](/20181210-browser-wars-iii "제목")
```

- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "제목")
- [](/20181210-browser-wars-iii "제목")
- [텍스트](20181210-browser-wars-iii)
- [텍스트](/20181210-browser-wars-iii)
- [텍스트](20181210-browser-wars-iii "제목")
- [텍스트](/20181210-browser-wars-iii "제목")

#### 파일 확장자로

```markdown
- [](20181210-browser-wars-iii.md#fragment)
- [](/20181210-browser-wars-iii.md#fragment)
- [](20181210-browser-wars-iii.md#fragment "제목")
- [](/20181210-browser-wars-iii.md#fragment "제목")
- [텍스트#조각](20181210-browser-wars-iii.md#fragment)
- [텍스트#조각](/20181210-browser-wars-iii.md#fragment)
- [텍스트#조각](20181210-browser-wars-iii.md#fragment "제목")
- [텍스트#조각](/20181210-browser-wars-iii.md#fragment "제목")
```

- [](20181210-browser-wars-iii.md#fragment)
- [](/20181210-browser-wars-iii.md#fragment)
- [](20181210-browser-wars-iii.md#fragment "제목")
- [](/20181210-browser-wars-iii.md#fragment "제목")
- [텍스트#조각](20181210-browser-wars-iii.md#fragment)
- [텍스트#조각](/20181210-browser-wars-iii.md#fragment)
- [텍스트#조각](20181210-browser-wars-iii.md#fragment "제목")
- [텍스트#조각](/20181210-browser-wars-iii.md#fragment "제목")

### 지원되지 않음

파일 확장자가 없고 `#fragment`가 있는 내부 링크는 잘못된 링크를 생성합니다.

```markdown
- [](20181210-browser-wars-iii#fragment)
- [](/20181210-browser-wars-iii#fragment)
- [](20181210-browser-wars-iii#fragment "제목")
- [](/20181210-browser-wars-iii#fragment "제목")
- [텍스트#조각](20181210-browser-wars-iii#fragment)
- [텍스트#조각](/20181210-browser-wars-iii#fragment)
- [텍스트#조각](20181210-browser-wars-iii#fragment "제목")
- [텍스트#조각](/20181210-browser-wars-iii#fragment "제목")
```

또한 다음 형식에 유의하십시오.

```markdown
- [link-icons.7z](/dls/link-icons.7z)
- [link-icons.7z](../../dls/link-icons.7z)
```

위 대신 `[텍스트](./path/to/file.ext)`를 사용하면 `[link-icons.7z](./techmagus/dls/link-icons.7z)`가 다음과 같이 렌더링됩니다. [link-icons.7z](./techmagus/dls/link-icons.7z)

## 개선

위의 코드를 자유롭게 개선하고 커뮤니티에 다시 공유하십시오. 귀하의 웹사이트와 이름을 제공하여 적절하게 크레딧을 받으십시오.

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link=""
  linkrel="noopener"

  title="Hugo에서 Markdown 링크를 사용자 지정하는 방법"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons Attribution-ShareAlike 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
