+++
title = "Bidirectional Test Case"
description = "The bidirectional test case."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

date = "2015-07-29T09:09:57+08:00"                                        # manually adjust to local timezone
lastmod = "2017-02-25T17:53:01+08:00"                                     # manually adjust to local timezone

aliases = ["/p/bidirectional-test-case.html"]
slug = "bidirectional-test-case"
translationKey = "bidirectional-test-case-2015210"
relCanonical = "https://im.youronly.one/techmagus/testcases/bidirectional-test-case-2015210/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["web"]                                                   # taxonomy
keywords = ["web", "html", "bidirectional", "multilang", "multi-language", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["html"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://4.bp.blogspot.com/-h6sAKgKjLWA/XrBAaaYaHtI/AAAAAAAAhe8/Rv-FK3as0hICWlYSC2U2JwizFb0q0IKYACLcBGAsYHQ/s1600/ball-63527_1280.jpg"]                                                       # used by og:images, etc.; first image is cover image

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

# For /yuki/ choose one and remove everything else
[[authors]]
    person = "yuki"
    #id = ""
    name = "ᜌᜓᜃᜒ (Yuki | 雪亮)"
    url = "https://im.youronly.one/techmagus/"
    avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
    #rel = "noopener external nofollow"
+++

## BDI (Bidirectional Isolation)

1. The title of the book is: <bdi dir="rtl" lang="hbo-Hebr">𐤌𐤍𐤉𐤀 𐤋 <bdi class="reset-1_25em" dir="ltr" lang="en">C++</bdi></bdi>
    - Firefox 40.0 beta (2015-07-29)
    - Chrome 58.0.3018.3 dev (2017-02-25) - fixed
1. The title of the book is: <bdi dir="rtl" lang="he">מבוא ל- <bdi class="reset-1_25em" dir="ltr" lang="en">C++</bdi></bdi>
    - Firefox 40.0 beta (2015-07-29)
    - Chrome 58.0.3018.3 dev (2017-02-25)
1. My name in Hebrew is <bdi dir="rtl" lang="hbo-Hebr">𐤉𐤅𐤇𐤍𐤍!</bdi>
    - Firefox 40.0 beta (2015-07-29)
    - Chrome 58.0.3018.3 dev (2017-02-25) - fixed
1. My name in Hebrew is <bdi dir="rtl" lang="he">יוחנן!</bdi>
    - Firefox 40.0 beta (2015-07-29)
    - Chrome 58.0.3018.3 dev (2017-02-25)

## BDO (Bidirectional Override)

1. The title of the book is: <bdo dir="rtl" lang="hbo-Hebr">𐤌𐤍𐤉𐤀 𐤋 <bdo class="reset-1_25em" dir="ltr" lang="en">C++</bdo></bdo>
    - Firefox 40.0 beta (2015-07-29)
    - Chrome 58.0.3018.3 dev (2017-02-25)
1. The title of the book is: <bdo dir="rtl" lang="he">מבוא ל- <bdo class="reset-1_25em" dir="ltr" lang="en">C++</bdo></bdo>
    - Firefox 40.0 beta (2015-07-29)
    - Chrome 58.0.3018.3 dev (2017-02-25)
1. My name in Hebrew is <bdo dir="rtl" lang="hbo-Hebr">𐤉𐤅𐤇𐤍𐤍!</bdo>
    - Firefox 40.0 beta (2015-07-29)
    - Chrome 58.0.3018.3 dev (2017-02-25)
1. My name in Hebrew is <bdo dir="rtl" lang="he">יוחנן!</bdo>
    - Firefox 40.0 beta (2015-07-29)
    - Chrome 58.0.3018.3 dev (2017-02-25)

---

{{< image
  type="imagecoverattrib"

  link="https://pixabay.com/en/ball-http-www-crash-administrator-63527/"
  linkrel="noopener external nofollow"

  title="Ball, Crash, Administrator"
  caption=""

  licensecode="pixabay"
  licenseurl="https://pixabay.com/service/license/"
  licensename="Pixabay License"

  attribto="geralt"
  attriburl="https://pixabay.com/en/users/geralt-9301/"
  attribrel="noopener external nofollow"
>}}
