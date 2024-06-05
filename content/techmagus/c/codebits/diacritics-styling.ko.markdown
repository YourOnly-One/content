+++
title = "스타일 구분 기호"
description = "분음 부호의 굵게, 색상 추가 및 글꼴 변경!"

lastmod = 2023-02-18T13:50:27+09:00                 # last update; manually adjust to local timezone
publishdate = 2023-02-18T13:50:27+09:00             # first publication; manually adjust to local timezone
date = 2023-02-18T08:07:07+09:00                    # first created; manually adjust to local timezone
#expirydate = 2022-04-07T17:53:01+08:00              # expiry; manually adjust to local timezone

aliases = ["/ko/codebits/styling-diacritics-202349"]                                        # "/post"
#url = ""                                              # "path/post"; override .Permalink
slug = "styling-diacritics"
translationKey = "styling-diacritics"
relCanonical = "https://im.youronly.one/techmagus/ko/codebits/styling-diacritics/"
#disqus_url = ""                                       # not used in sites by Yelosan Publishing
disquq_identifier = "styling-diacritics-202349"                                # set if date of this content is different from main translation

#redirectto = ""                                       # Yelosan Publishing: used in _index.md
#metarobots = "noindex"                                # Yelosan Publishing: used in _index.md

syndication = ["https://c.im/@youronlyone/109884874152798444", "https://twitter.com/YourOnlyONEofcl/status/1626864787660369921", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/pfbid0d2QEydjCJVWW7jHNfJG43gNeUidCTa9okCbKM3Ywmjghj1EYEUz4pY45AQ9H8QMPl"]

channels = ["techmagus"]
categories = ["howto", "web"]
keywords = ["diacritics", "diacritical marks", "how to add colors to accent symbols", "how to add colours to diacritical signs"]
#series = [""]
tags = ["css", "html"]

comments = true
#weight = ""

#featured = true
#math = true
toc = true

translation = false
translationby = ""

#audio = [""]
images = ["images/d/diacritics.png"]
#videos = ["https://www.youtube.com/watch?v="]

type = "article"                                             # article, sitepage, review

#draft = true

#license = ""                                          # only set if the post license is not the same as the site license

#### AUTHOR: TECHMAGUS ####
[[authors]]
  person = "yuki"
  #id = ""
  name = "사요한"
  #name = "techmagus / テク魔法使い / 테크마법사"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

억양 기호라고도 불리는 발음 구별기에 색을 추가하는 방법이 있는지 궁금하다면, 여러분은 올바른 위치에 있습니다! 왜요? 정답은 '예'이기 때문입니다. 그리고 제가 그 방법을 보여드리겠습니다.

<!--more-->

1. 다음과 같은 CSS 스타일을 만듭니다:

    ```css
    .diacritics {
      color: hsla(0deg, 100%, 50%, 1);
      color: hwb(0deg 0% 0% / 100%);
      font-family: "DejaVu Sans"; /* 현재 DejaVu Sans는 분음 부호 위치에서 가장 높은 정확도를 가지고 있다. */
      font-weight: bold;
    }
    ```

1. 분음 부호를 `diacritics` 클래스 내에 배치합니다

    ```html
    <span class="diacritics"></span>
    ```

알았어요!

다음은 예입니다:

```html
bata<span class="diacritics">̀</span>
panibugho<span class="diacritics">̂</span>
ara<span class="diacritics">́</span>w–a<span class="diacritics">́</span>raw
ke<span class="diacritics">̈</span>tke<span class="diacritics">̈</span>t
sag<span class="diacritics">̃</span>nay or sagn<span class="diacritics">̃</span>ay
pan<span class="diacritics">͠</span>gulo
a<span class="diacritics">̄</span>so
h<span class="diacritics">͞</span>oy
pu<span class="diacritics">̱</span>sà
trab<span class="diacritics">͟</span>aho
```

- <span lang="fil">bata<span class="text-guide diacritics-sans-dejavu">̀</span> [ba·ta<span class="diacritics-sans-dejavu">̀</span>]</span>
- <span lang="fil">panibugho<span class="text-guide diacritics-sans-dejavu">̂</span> [pa·ni·bu<span class="diacritics-sans-dejavu">̄</span>g·ho<span class="diacritics-sans-dejavu">̂</span>]</span>
- <span lang="fil">ara<span class="text-guide diacritics-sans-dejavu">́</span>w–a<span class="text-guide diacritics-sans-dejavu">́</span>raw [a·ra<span class="diacritics-sans-dejavu">́</span>w–a<span class="diacritics-sans-dejavu">́</span>·raw]</span>
- <span lang="fil">ke<span class="text-guide diacritics-sans-dejavu">̈</span>tke<span class="text-guide diacritics-sans-dejavu">̈</span>t [ke<span class="diacritics-sans-dejavu">̈</span>t·ke<span class="diacritics-sans-dejavu">̈</span>t]</span>
- <span lang="fil">sag<span class="text-guide diacritics-sans-dejavu">̃</span>nay or sagn<span class="text-guide diacritics-sans-dejavu">̃</span>ay [sa·n<span class="diacritics-sans-dejavu">̃</span>gay]</span>
- <span lang="fil">pan<span class="text-guide diacritics-sans-dejavu">͠</span>gulo [pa·n<span class="diacritics-sans-dejavu">͠</span>gu·lo]</span>
- <span lang="fil">a<span class="text-guide diacritics-sans-dejavu">̄</span>so [a<span class="diacritics-sans-dejavu">̄</span>·so]</span>
- <span lang="fil">h<span class="text-guide diacritics-sans-dejavu">͞</span>oy [h<span class="diacritics-sans-dejavu">͞</span>oy]</span>
- <span lang="fil">pu<span class="text-guide diacritics-sans-dejavu">̱</span>sa<span class="diacritics-sans-dejavu">̀</span> [pu<span class="diacritics-sans-dejavu">̱</span>·sa<span class="diacritics-sans-dejavu">̀</span>]</span>
- <span lang="fil">trab<span class="text-guide diacritics-sans-dejavu">͟</span>aho [tra·b<span class="diacritics-sans-dejavu">͟</span>a·ho]</span>

[CodePen](https://codepen.io/techmagus/pen/NWLqoLd)를 통해서도 이용할 수 있습니다. 또는 [test-repo: Noto Diacriticals](https://github.com/techmagus/test-repo/tree/noto-diacriticals) Git 지점에서 간단한 테스트 페이지를 복제할 수 있습니다.

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link=""
  linkrel="noopener"

  title="필리핀어 발음 구별 기호"
  caption=""
  alt="필리핀어 발음 구별 기호"
  embeddedtextcaption="yá yū ba͟·n͠ga yë Ligñon yò sang̃ay yî"
  inlanguage="fil"

  licensecode="cc0"
  licenseurl=""
  licensename=""

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"

  cc0country="필리핀"
  cc0countrycode="ph"
  cc0countryurl="https://en.wikipedia.org/wiki/Philippines"
>}}

---

주의사항 : 네이버 파파고 신경번역
