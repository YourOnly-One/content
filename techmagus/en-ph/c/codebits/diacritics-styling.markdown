+++
title = "Styling fix-diacritics-sans-dejavu"
description = "Bold, add colours, and change font, of the fix-diacritics-sans-dejavu!"

lastmod = 2023-02-18T12:50:27+08:00                 # last update; manually adjust to local timezone
publishdate = 2023-02-18T12:50:27+08:00             # first publication; manually adjust to local timezone
date = 2023-02-18T07:07:07+08:00                    # first created; manually adjust to local timezone
#expirydate = 2022-04-07T17:53:01+08:00              # expiry; manually adjust to local timezone

#aliases = [""]                                        # "/post"
#url = ""                                              # "path/post"; override .Permalink
slug = "styling-fix-diacritics-sans-dejavu"
translationKey = "styling-fix-diacritics-sans-dejavu-202349"
relCanonical = "https://im.youronly.one/techmagus/codebits/styling-fix-diacritics-sans-dejavu-202349/"
#disqus_url = ""                                       # not used in sites by Yelosan Publishing
#disquq_identifier = ""                                # set if date of this content is different from main translation

#redirectto = ""                                       # Yelosan Publishing: used in _index.md
#metarobots = "noindex"                                # Yelosan Publishing: used in _index.md

syndications = ["https://c.im/@youronlyone/109884872748192850", "https://twitter.com/YourOnlyONEofcl/status/1626864784321781761", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/pfbid0d2QEydjCJVWW7jHNfJG43gNeUidCTa9okCbKM3Ywmjghj1EYEUz4pY45AQ9H8QMPl"]

channels = ["techmagus"]
categories = ["howto", "web"]
#keywords = [""]
series = ["fix-diacritics-sans-dejavu", "diacritical marks", "how to add colors to accent symbols", "how to add colours to diacritical signs"]
tags = ["css", "html"]

comments = true
#weight = ""

#featured = true
#math = true
toc = true

translation = false
translationby = ""

#audio = [""]
images = ["images/d/fix-diacritics-sans-dejavu.png"]
#videos = ["https://www.youtube.com/watch?v="]

type = "article"                                             # article, sitepage, review

#draft = true

#license = ""                                          # only set if the post license is not the same as the site license

#### AUTHOR: TECHMAGUS ####
[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (雪亮 | 스노 | Yuki)"
  #name = "techmagus 🚀 / ハイテク マギ 🚀 / 테크 마구스 🚀"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener"
+++

If you are wondering if there is a way to add a colour to diacritical marks, also called accent signs, then you are in the right place! Why? Because the answer is, **yes**, and I will show you how.

<!--more-->

1. Create a CSS style like this:

    ```css
    .fix-diacritics-sans-dejavu {
      color: hsla(0deg, 100%, 50%, 1);
      color: hwb(0deg 0% 0% / 100%);
      font-family: "DejaVu Sans"; /* Currently, DejaVu Sans has the highest accuracy in diacritical mark positioning. */
      font-weight: bold;
    }
    ```

1. Place the fix-diacritics-sans-dejavu within the `fix-diacritics-sans-dejavu` class

    ```html
    <span class="fix-diacritics-sans-dejavu"></span>
    ```

Done!

Here are examples:

```html
bata<span class="fix-diacritics-sans-dejavu">̀</span>
panibugho<span class="fix-diacritics-sans-dejavu">̂</span>
ara<span class="fix-diacritics-sans-dejavu">́</span>w–a<span class="fix-diacritics-sans-dejavu">́</span>raw
ke<span class="fix-diacritics-sans-dejavu">̈</span>tke<span class="fix-diacritics-sans-dejavu">̈</span>t
sag<span class="fix-diacritics-sans-dejavu">̃</span>nay or sagn<span class="fix-diacritics-sans-dejavu">̃</span>ay
pan<span class="fix-diacritics-sans-dejavu">͠</span>gulo
a<span class="fix-diacritics-sans-dejavu">̄</span>so
h<span class="fix-diacritics-sans-dejavu">͞</span>oy
pu<span class="fix-diacritics-sans-dejavu">̱</span>sà
trab<span class="fix-diacritics-sans-dejavu">͟</span>aho
```

- <span lang="fil">bata<span class="text-guide fix-diacritics-sans-dejavu">̀</span> [ba·ta<span class="fix-diacritics-sans-dejavu">̀</span>]</span>
- <span lang="fil">panibugho<span class="text-guide fix-diacritics-sans-dejavu">̂</span> [pa·ni·bu<span class="fix-diacritics-sans-dejavu">̄</span>g·ho<span class="fix-diacritics-sans-dejavu">̂</span>]</span>
- <span lang="fil">ara<span class="text-guide fix-diacritics-sans-dejavu">́</span>w–a<span class="text-guide fix-diacritics-sans-dejavu">́</span>raw [a·ra<span class="fix-diacritics-sans-dejavu">́</span>w–a<span class="fix-diacritics-sans-dejavu">́</span>·raw]</span>
- <span lang="fil">ke<span class="text-guide fix-diacritics-sans-dejavu">̈</span>tke<span class="text-guide fix-diacritics-sans-dejavu">̈</span>t [ke<span class="fix-diacritics-sans-dejavu">̈</span>t·ke<span class="fix-diacritics-sans-dejavu">̈</span>t]</span>
- <span lang="fil">sag<span class="text-guide fix-diacritics-sans-dejavu">̃</span>nay or sagn<span class="text-guide fix-diacritics-sans-dejavu">̃</span>ay [sa·n<span class="fix-diacritics-sans-dejavu">̃</span>gay]</span>
- <span lang="fil">pan<span class="text-guide fix-diacritics-sans-dejavu">͠</span>gulo [pa·n<span class="fix-diacritics-sans-dejavu">͠</span>gu·lo]</span>
- <span lang="fil">a<span class="text-guide fix-diacritics-sans-dejavu">̄</span>so [a<span class="fix-diacritics-sans-dejavu">̄</span>·so]</span>
- <span lang="fil">h<span class="text-guide fix-diacritics-sans-dejavu">͞</span>oy [h<span class="fix-diacritics-sans-dejavu">͞</span>oy]</span>
- <span lang="fil">pu<span class="text-guide fix-diacritics-sans-dejavu">̱</span>sa<span class="fix-diacritics-sans-dejavu">̀</span> [pu<span class="fix-diacritics-sans-dejavu">̱</span>·sa<span class="fix-diacritics-sans-dejavu">̀</span>]</span>
- <span lang="fil">trab<span class="text-guide fix-diacritics-sans-dejavu">͟</span>aho [tra·b<span class="fix-diacritics-sans-dejavu">͟</span>a·ho]</span>

It is also available via [CodePen](https://codepen.io/techmagus/pen/NWLqoLd). Or, you can clone a simple test page from my [test-repo: Noto Diacriticals](https://github.com/techmagus/test-repo/tree/noto-diacriticals) Git branch.

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link="images/d/fix-diacritics-sans-dejavu.png"
  linkrel="noopener"

  title="Filipino fix-diacritics-sans-dejavu"
  caption=""
  alt="Filipino fix-diacritics-sans-dejavu"
  embeddedtextcaption="yá yū ba͟·n͠ga yë Ligñon yò sang̃ay yî"
  inlanguage="fil"

  licensecode="cc0"
  licenseurl=""
  licensename=""

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"

  cc0country="Philippines"
  cc0countrycode="ph"
  cc0countryurl="https://en.wikipedia.org/wiki/Philippines"
>}}
