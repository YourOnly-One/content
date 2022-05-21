+++
title = "LANG 속성"
description = "LANG 속성은 웹사이트를 디자인할 때 강력한 코드 조각입니다. LANG 속성을 올바르게 사용하는 방법을 보여드리겠습니다."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = "2009-06-21T01:20:37+09:00"                                        # manually adjust to local timezone
lastmod = "2009-06-21T01:20:37+09:00"                                        # manually adjust to local timezone

#aliases = [""]
slug = "lang-attribute"
translationKey = "lang-attribute-2009172"
relCanonical = "https://im.youronly.one/techmagus/ko/kb/webdev/lang-attribute-2009172/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["howto"]                                                   # taxonomy
keywords = ["lang", "language", "multilang", "multi-language", "techmagus", "how to", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["html"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://3.bp.blogspot.com/-OjERfiifRYA/Xqp2WZ_WrEI/AAAAAAAAhbo/TExJwOEWDcMF2UU48Fbn4Pz-vZe7pgiLQCLcBGAsYHQ/s1600/lave%2Bt%2527es%2Bmains-1800x.jpg"]                                                       # used by og:images, etc.; first image is cover image

[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (Yuki | 雪亮)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

이전 게시물에서 "Baybayin - 잊혀진 필리핀 이전 히스패닉 작문"에 대해 이야기했습니다. [Unicode Standard](https://unicode.org) 버전 5.0에서 "Philippine Scripts" 그룹 아래 Buhid, Hanunoo, Tagbanwa와 함께 추가되었습니다. 그러나 다른 언어와 스크립트로 작성된 콘텐츠를 어떻게 적절하게 작성하거나 표시해야 할까요?

이 게시물에서는 콘텐츠의 언어를 올바르게 선언하는 방법에 대해 설명합니다. 이렇게 하면 번역 소프트웨어와 도우미 응용 프로그램, 그리고 종종 당연하게 여겨지는 이 HTML 속성에 의존하는 기타 기술에 친숙해질 수 있습니다. 우리의 이미지에서 볼 수 있듯이 모든 사람이 사용 된 스크립트를 볼 수 있지만 디지털 세계에는 사용 중인 글꼴이 없는 사람들이 있습니다. 당신과 내가 사용하는 것과 같은 브라우저를 사용하지 않는 사람들도 있습니다. 그것은 텍스트 전용 브라우저, 음성 브라우저 또는 점자 브라우저일 수 있습니다.

그런 다음 우리가 사용하는 언어와 스크립트로 콘텐츠에 적절하고 올바르게 태그를 지정하는 것이 적절합니다. LANG 속성을 많이 사용할 준비를 하십시오.

<!--more-->

웹 사이트를 만들 때 웹 사이트에서 사용되는 언어를 올바르게 선언하는 것이 중요합니다. 예를 들어 내 사이트에 다음을 사용합니다.

```html
<html lang="en-PH">
```

특히 ASCII 범위를 벗어난 문자를 사용하려는 경우 문자 집합을 선언하는 것도 중요합니다. 다음과 같이 보입니다.

```html
    <meta charset="UTF-8" />
```

모든 것을 합치면 기본 HTML이 되어야 합니다.

```html
<!DOCTYPE html>
<html lang="en-PH">
    <head>
        <meta charset="UTF-8" />
        <meta description="My Website" />
        <meta keywords="Philippines, Baybayin" />
        <title>My Baybayin Website</title>
    </head>
    <body>
        <p>Mabuhay!</p>
    </body>
</html>
```

이제 파헤쳐보자...

## *lang* 속성

HTML lang 속성은 선언된 요소 내에 포함된 콘텐츠의 언어를 정의합니다. 코드는 *subtag* 라고 하며 필리핀 독자의 경우 걱정해야 할 하위 태그 유형은 language-Script-REGION의 세 가지뿐입니다. 전체 형식: language-extended_language-Script-REGION-variant-extension-privateuse.

아래 표를 참조하십시오.
<style>
  #langcode {
    margin: 0 auto;
  }
  #langcode th {
    border: 1px outset;
    padding: 4px;
    text-align: center;
  }
  #langcode td {
    border: 1px inset;
    padding: 3px;
  }
</style>
<table id="langcode" border="2" summary="Language code example" style="min-width: 80%; width: 80%;">
  <thead style="text-align: center;">
    <tr>
      <th style="min-width: 15%; width: 15%;">암호</th>
      <th>언어</th>
      <th>하위 태그 배치</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>en</td>
      <td>(일반) 영어</td>
      <td>language</td>
    </tr>
    <tr>
      <td>en-PH</td>
      <td>필리핀 영어</td>
      <td>language+REGION</td>
    </tr>
    <tr>
      <td>fil-Tglg</td>
      <td>Baybayin의 필리핀</td>
      <td>language+Script</td>
    </tr>
    <tr>
      <td>bik-cts-Tglg</td>
      <td>Baybayin 스크립트의 Pandan(북부 카탄두아네스) 방언의 Bikolano</td>
      <td>language+extended_language+Script</td>
    </tr>
    <tr>
      <td>phi-Tglg-tsg</td>
      <td>Baybayin 스크립트로 작성된 Tausug 필리핀 언어</td>
      <td>language+Script+variant</td>
    </tr>
  </tbody>
</table>
<p></p>

특정 언어에 대한 하위 태그를 찾으려면 이전에 다른 웹사이트와 많은 공식 코드 목록을 확인해야 했습니다. 시간이 많이 걸리는 작업(일반적으로 한 번만 수행하면 됨), 맞습니까? 이제 최신 공식 하위 태그를 [IANA 언어 하위 태그 레지스트리](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry)에서 찾을 수 있습니다. 이제 모든 유효한 하위 태그의 범용 소스입니다.

최신 목록(이 글을 쓰는 현재)에 따르면 필리핀과 관련된 하위 태그는 다음과 같습니다.

### 언어

- Tagalog
  - Type: language
  - Subtag: tl
  - Description: Tagalog
  - Added: 2005-10-16
  - Suppress-Script: Latn

- Bikol
  - Type: language
  - Subtag: bik
  - Description: Bikol
  - Added: 2005-10-16
- Cebuano
  - Type: language
  - Subtag: ceb
  - Description: Cebuano
  - Added: 2005-10-16
- Filipino/Pilipino
  - Type: language
  - Subtag: fil
  - Description: Filipino
  - Description: Pilipino
  - Added: 2005-10-16
- Hiligaynon
  - Type: language
  - Subtag: hil
  - Description: Hiligaynon
  - Added: 2005-10-16
- Iloko
  - Type: language
  - Subtag: ilo
  - Description: Iloko
  - Added: 2005-10-16
- Pangasinan
  - Type: language
  - Subtag: pag
  - Description: Pangasinan
  - Added: 2005-10-16
- Pampanga/Kapampangan
  - Type: language
  - Subtag: pam
  - Description: Pampanga
  - Description: Kapampangan
  - Added: 2005-10-16
- Philippine languages
  - Type: language
  - Subtag: phi
  - Description: Philippine languages
  - Added: 2005-10-16
- Waray
  - Type: language
  - Subtag: war
  - Description: Waray
  - Added: 2005-10-16

### 지역

- Philippines
  - Type: region
  - Subtag: PH
  - Description: Philippines
  - Added: 2005-10-16

### 스크립트 작성

- Buhid
  - Type: script
  - Subtag: Buhd
  - Description: Buhid
  - Added: 2005-10-16

- Hanunoo (Hanunóo)
  - Type: script
  - Subtag: Hano
  - Description: Hanunoo (Hanunóo)
  - Added: 2005-10-16
- Tagbanwa
  - Type: script
  - Subtag: Tagb
  - Description: Tagbanwa
  - Added: 2005-10-16
- Tagalog
  - Type: script
  - Subtag: Tglg
  - Description: Tagalog
  - Description: Baybayin
  - Description: Alibata
  - Added: 2005-10-16

이제 필요한 하위 태그가 있으므로 모든 필리핀 언어 및 스크립트에 대해 올바른 `lang` 값을 코딩할 수 있습니다. 다음 예를 참조하십시오.

- 필리핀에서 성장하고 영어를 배웠다면 필리핀 전용 영어 단어를 사용하고 있을 뿐만 아니라 필리핀 영어로만 가르치는 엄격한 언어 규칙을 따르고 있을 가능성이 큽니다. 웹사이트의 올바른 `lang` 값입니다. `lang="en-PH"`
- 타갈로그어가 아닌 필리핀어로 작성하는 경우 다음을 사용하십시오. `lang="fil"`
- 필리핀어가 아닌 타갈로그어로 작성하는 경우 다음을 사용하십시오. `lang="tl"`
- Bikolano의 경우 다음을 사용하십시오. `lang="bik"`
- 세부아노에서는 `lang="ceb"`를 사용합니다.
- Hiligaynon, 다음을 사용하십시오: `lang="hil"`
- Iloko에서는 `lang="ilo"`를 사용합니다.
- Pangasinense에서: `lang="pag"`
- 카팜팡안: `lang="pam"`
- Waray: `lang="war"`
- 해당 [ISO-639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php) 코드가 없는 필리핀 언어의 경우 일반 하위 태그인 `lang="을 사용해야 합니다. 파이"`

그런 다음 Baybayin 스크립트로 무언가를 작성하려면 스크립트 하위 태그 "Tglg"로 올바르게 묶어야 합니다. 형식은 다음과 같습니다.

- Baybayin 스크립트를 사용하여 필리핀어 및 타갈로그어로 작성하는 경우 다음을 사용하십시오. `lang="fil-Tglg"`
- Bikolano에서 Baybayin 스크립트: `lang="bik-Tglg"`
- Baybayin 스크립트를 사용하는 세부아노: `lang="ceb-Tglg"`
- ISO-639-2 하위 태그가 없는 다른 모든 필리핀 언어는 `lang="phi-Tglg"`를 사용해야 합니다.

<del datetime="2021-09-24T18:32:17+08:00">`lang="tl-Tglg"` 하위 태그 코드가 없는 이유는 무엇인가요? *Suppress-Script: Latn* 으로 인해 IANA 언어 하위 태그 레지스트리에서 이전에 표시된 대로. 내가 그것을 올바르게 이해했다면 공식 표준에 따라 타갈로그 언어는 항상 라틴 문자로 작성되어야 함을 의미합니다. 그런 다음 lang="tl-Tglg"가 잘못되었고 응용 프로그램에 이를 무시하거나 "Tglg" 스크립트 하위 태그를 삭제할 수 있는 옵션이 있다고 가정합니다. 이 경우 "fil-Tglg"를 사용하십시오.</del>

## ISO-639-3 언어

[dialects and macrolanguages](https://web.archive.org/web/20130218160105///www.sil.org:80/iso639-3/macrolanguages.asp)를 타겟팅하려는 경우 배워야 하는 또 다른 하위 태그가 있습니다. ). ISO 표준 [ISO-639-3](https://web.archive.org/web/20130217113439///www.sil.org:80/iso639-3/codes.asp?)에서 목록을 찾을 수 있습니다. . Bikolano를 예로 들어 보겠습니다. 사용할 형식은 language-extended_language-Script입니다.

- Central Bikolano로 작성하는 경우 `lang="bik-bcl"`을 사용하십시오.
- Albay Bikolano / Buhi-Daraga로 작성하는 경우: `lang="bik-bhk"`
- Iriga Bikolano에서 Baybayin 스크립트를 사용하는 경우: `lang="bik-bto-Tglg"`
- Baybayin 스크립트를 사용하는 Pandan(Northern Catanduanes)의 경우: `lang="bik-cts-Tglg"`

언어-***extended_language***-스크립트는 이 문서에서 아직 구현되지 않았습니다. lang 속성의 기본은 *extended_languages*를 포함하도록 업데이트되면 항상 [IANA 언어 하위 태그 레지스트리](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry)입니다. * 그런 다음 필요한 곳에서 사용할 수 있습니다.

### *phi* 언어 하위 태그

다음은 언어에 ISO-639-3 코드가 있고 ISO-639-2에서 언어 코드 "phi" 아래 또는 일부인 경우 *phi* 하위 태그가 사용됩니다. 이 하위 태그 코드는 **집단 언어**로 간주됩니다. 좋은 예는 다음과 같습니다.

- Kinaray-a 언어: `lang="phi-krj"`
- Maguindanao 언어: `lang="phi-mdh"`
- Baybayin 스크립트로 작성된 마라나오 언어: `lang="phi-Tglg-mrw"`
- Baybayin 스크립트로 작성된 Tausug 언어: `lang="phi-Tglg-tsg"`

내가 사용한 형식이 *language-extended_language-Script*가 아니라 *language-Script-variant*라는 것을 눈치채셨을 것입니다. 내 추론은 간단합니다. *phi* 언어 코드는 실제로 언어가 아닙니다. 이 ISO 버전에서는 **찾을 수 없는** 다른 모든 필리핀 언어에 대해 ISO-639-2에서 "집합적인" 언어 항목이라고 합니다. 언어 표준. *bik* 언어 코드와 비교하면 ISO-639-2 및 ISO-639-3 모두에서 "매크로 언어"로 명확하게 표시되었습니다.

또한, [월드 와이드 웹 컨소시엄](https://www.w3.org/International/articles/language-tags/) 또는 W3C에 따르면 매크로 언어의 **방언**은 **즉시 작성되어야 합니다**. 언어 하위 태그 뒤에. 즉, ISO-639-2 코드가 매크로 언어로 간주되는 경우 `lang="bik-cts-Tglg"`와 같은 *extended_language* 하위 태그 위치를 사용해야 합니다. 매크로 언어로 정의되지 않은 경우 `lang="phi-Tglg-tsg"`의 경우와 같이 *variant* 하위 태그 위치를 사용해야 합니다.

## 예, 예 및 더 많은 예…

웹사이트가 주로 Iriga에 관한 것이고 자신의 언어로 작성하는 경우 웹사이트의 헤더 파일을 적절하게 조정해야 합니다.

```html
<!DOCTYPE html>
<html lang="bik-bto">
    <head>
        <meta charset="UTF-8" />
        <meta description="Ang Website Ko Sa Iriga Bikolano" />
        <meta keywords="Philippines, Baybayin, Iriga, Bikolano" />
        <title>Ang Website Ko Sa Iriga Bikolano</title>
    </head>
    <body>
        <p>Mabuhay!</p>
    </body>
</html>
```

Baybayin에서 "해피 아버지의 날"을 쓰고 싶다면 다음과 같이 하세요.

```html
  <bdi lang="fil-Tglg">ᜋᜎᜒᜄᜌᜅ᜔ ᜀᜍᜏ᜔ ᜈᜅ᜔ ᜋᜅ ᜀᜋ</bdi>
```

단순한? 멋있는! 언어 태그를 작성할 때 가능한 한 간단하고 짧게 유지하는 것을 기억하십시오. `lang="bik-bcl"`과 같이 매우 구체적일 필요가 없다면 그렇게 하지 마십시오! `lang="bik"`를 사용하기만 하면 됩니다. 이것은 특히 블로그에 해당됩니다. 따라서 블로그가 필리핀 언어(!타갈로그어가 아닙니다!)로 되어 있으면 다음을 사용합니다.

```html
<html lang="fil">
```

필요할 때나 사이트가 특정 청중 및/또는 지역을 주로 수용할 때만 구체적으로 작성하십시오. 또한, 다른 언어와 스크립트를 사용하려는 경우(아마도) 위의 Baybayin 예제에서 본 것처럼 항상 span 또는 div 요소로 묶습니다.

쉬운? 그렇습니다. 익숙해지려면 시간이 걸리고 처음에는 혼란스럽습니다. 그러나 당신은 결국 그것에 걸림돌이 될 것입니다. 지금 웹사이트를 업데이트하고 올바른 언어와 스크립트로 콘텐츠를 표시하는 연습을 시작하세요.

---

{{< image
  type="imagecoverattrib"

  link="https://www.flickr.com/photos/29233640@N07/24754999650"
  linkrel="noopener external nofollow"

  title="lave t'es mains"
  caption=""

  licensecode="ccby2"
  licenseurl="https://creativecommons.org/licenses/by/2.0/"
  licensename="CC-BY 2.0"

  attribto="Robert Couse-Baker"
  attriburl="https://www.flickr.com/photos/29233640@N07/"
  attribrel="noopener external nofollow"
>}}

---

고시 : Google 번역
