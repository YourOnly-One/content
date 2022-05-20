+++
title = "Hugo Markdown 링크에 상호 참조를 추가하는 방법"
description = "Hugo에서 Markdown 링크에 대한 상호 참조 지원을 추가하는 방법"

date = "2022-05-20T20:24:27+09:00"                                          # manually adjust to local timezone
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

{{% quote type="name" lang="en" %}}Hugo{{% /quote %}}의 덜 일반적으로 사용되는 기능 중 하나는 렌더 후크입니다. 이 게시물에서는 렌더 후크를 사용하여 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}}의 기본 링크 생성 방식인 `[text](https://example.com#fragment "Title")`에 내부 상호 참조 지원을 추가할 것입니다.

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

## 단계

1. 이 디렉토리 `/layouts/_default/_markup/`에 `render-link.html`이라는 파일을 만듭니다.
1. 아래 코드를 추가하세요.

    ```go-html-template
    {{- $url := (urls.Parse .Destination) -}}
    {{- $internal := site.GetPage .Destination -}}
    {{- $fragment := $url.Fragment -}}
    {{- with $fragment -}}{{ $fragment = printf "#%s" $fragment }}{{- end -}}
    {{- $destination := printf "%s%s" (or $internal.RelPermalink .Destination) $fragment -}}
    <a href="{{ $destination | safeURL }}"{{ with or .Title $internal.LinkTitle .Text }} title="{{ . }}"{{ end }}{{ if not $internal }} rel="noopener external"{{ end }}>{{ or .Text .Title $internal.LinkTitle | safeHTML }}</a>
    ```

그게 다야

## 사용하는 방법

다음 {{% quote type="name" lang="en" %}}Markdown{{% /quote %}} 링크

  ```markdown {linenos=false}
  - [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
  - [](20181210-browser-wars-iii)
  - [](/20181210-browser-wars-iii)
  - [With text](20181210-browser-wars-iii)
  - [](20181210-browser-wars-iii "With title")
  - [With text, title, and fragment](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "With text, title, and fragment")
  ```

`ko`에서 다음과 같이 렌더링됩니다.

- [](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine)
- [](20181210-browser-wars-iii)
- [](/20181210-browser-wars-iii)
- [With text](20181210-browser-wars-iii)
- [](20181210-browser-wars-iii "With title")
- [With text, title, and fragment](20181210-browser-wars-iii.md#browser-wars-iii-front-browser-engine "With text, title, and fragment")

### 주의 사항

현재 다음 형식을 지원하지 않습니다.

```markdown {linenos=false}
- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
```

링크 제목 없이 렌더링되고 [링크 아이콘](hugo-link-icons-markdown-links.md)이 있는 경우 링크가 올바르지 않습니다.

- [](20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](ja/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)
- [](/ko/20181210-browser-wars-iii#browser-wars-iii-front-browser-engine)

다음과 같이 생성된 영구 링크를 대신 사용하세요(접두사 `/`가 중요).

```markdown {linenos=false}
- [브라우저 전쟁 III: Blink 대 Gecko Quantum](/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)
```

다음과 같이 렌더링됩니다.

- [브라우저 전쟁 III: Blink 대 Gecko Quantum](/browser-wars-3-blink-gecko-2018344#browser-wars-iii-front-browser-engine)

## 개선

위의 코드를 자유롭게 개선하고 커뮤니티에 다시 공유하십시오. 귀하의 웹사이트와 이름을 제공하여 적절하게 크레딧을 받으십시오.

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
