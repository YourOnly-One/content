+++
title = "Blogroll이 돌아왔습니다"
description = "링크 목록과 블로그 롤을 다시 가져옵니다!"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = 2021-12-19T15:14:41+09:00                                        # manually adjust to local timezone
lastmod = 2021-12-19T15:14:41+09:00                                        # manually adjust to local timezone

#aliases = [""]
slug = "linklists-are-back"
translationKey = "linklists-are-back-2021353"
relCanonical = "https://im.youronly.one/techmagus/ko/linklists-are-back-2021353/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

syndications = ["https://twitter.com/YourOnlyONEofcl/status/1472455861368868865", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/564152718087296"]

channels = ["techmagus"]
categories = ["web"]                                                   # taxonomy
keywords = ["bookmarks", "linklists", "blogroll", "listicle"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["design"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#audio = [""]                                                        # used by og:audio, etc.
images = ["images/l/linklist-01.png"]                                                       # used by og:images, etc.; first image is cover image
#videos = [""]                                                       # used by og:video, etc.

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

# For /yuki/ choose one and remove everything else
[[authors]]
  person = "yuki"
  #id = ""
  name = "Yuki (유키 雪矢)"
  url = "https://im.youronly.one/yuki/"
  avatar = "https://rsc.youronly.one/img/y/Yuki_flag-square-300x.webp"
  #rel = "noopener external nofollow"
+++

월드 와이드 웹의 초기(90년대 중후반)에서 2010년 또는 2012년까지 링크 목록 또는 블로그 롤은 대중적일 뿐만 아니라 웹 디자인의 표준 부분이었습니다. 어느 좋은 아침에 그것은 사라지고 더 이상 관련이 없습니다. 하지만 정말 죽은 것일까?

<!--more-->

{{% quotebox boxstyle="qbs_generic" qmarkstyle="qbm_doublequotationmark" boxcolour="qbc_blue-midnight" attribalign="txt_right" srctitle="The Small Website Discoverability Crisis" srclink="https://memex.marginalia.nu/log/19-website-discoverability-crisis.gmi" srcrel="noopener external nofollow" attribto="Marginalia" attriblink="https://memex.marginalia.nu" attribrel="noopener external nofollow" %}}
A proposal, dear reader: Create a list of bookmarks linking to websites you find interesting, and publish it for the world to see. You decide what constitutes "interesting".
{{% /quotebox %}}

## 링크 목록 또는 블로그 롤이란 무엇입니까?

*linklist* 또는 *blogroll*은 웹사이트 소유자 또는 블로거가 수집하여 사이트의 사이드바 또는 전용 페이지에 표시하는 추천 링크 모음입니다. 가족 및 친구의 블로그 링크 또는 흥미로운 웹 사이트에 대한 링크가 될 수 있습니다.

웹사이트 구축 및 블로깅의 초기에는 블로그 네트워크를 만들고 소셜화하는 것이 중요했습니다. 나중에 초점이 되었지만 검색 엔진 최적화(SEO) 때문이 아니라 방문자가 서로를 찾을 수 있도록 돕기 위한 것이었습니다. 어느 날 모든 사람들이 블로그롤을 만들고 있었는데 다음 날 모든 것이 사라졌습니다.

웹사이트는 더 이상 "사회적으로 연결"되지 않았습니다. 웹사이트 간의 모든 연결은 비즈니스 또는 마케팅으로 전환되었습니다. 다른 웹사이트로 연결되는 링크는 주로 기사에서 인용되었기 때문이지 독자가 발견할 가치가 있다고 판단했기 때문이 아닙니다.

그때였다. 오늘, 우리는 그것을 다시 가져옵니다!

## 하지만 왜?

내 블로그를 *WordPress*에서 *Hugo*로 마이그레이션하기 시작한 이후로 linklist 또는 blogroll은 항상 내 ToDo 목록에 있었습니다. 인용할 기사를 찾는 대신 지속적으로 언급할 가치가 있는 추천 웹사이트와 블로거를 추천하는 방법입니다. 또한 단일 기사에 링크하는 것과 비교하여 웹 사이트 자체 및 작성자에 대한 권장 사항입니다.

하지만, 나는 계속 그것을 뒤로 밀었다. 추천하고 싶은 웹사이트와 블로거가 너무 많아서 목록을 선별하고 유지하는 작업을 생각하는 것만으로도 이미 피곤합니다. 지금까지 소규모로 이것을 하는 아주 좋은 방법과 이유를 찾았습니다.

{{% quotebox boxstyle="qbs_generic" qmarkstyle="qbm_doublequotationmark" boxcolour="qbc_green" attribalign="txt_right" srctitle="The Small Website Discoverability Crisis" srclink="https://memex.marginalia.nu/log/19-website-discoverability-crisis.gmi" srcrel="noopener external nofollow" attribto="Marginalia" attriblink="https://memex.marginalia.nu" attribrel="noopener external nofollow" %}}
A proposal, dear reader: Create a list of bookmarks linking to websites you find interesting, and publish it for the world to see. You decide what constitutes "interesting".

The model is as recursive as it is simple. There is nothing preventing a list of bookmarks from linking to another list of bookmarks.

…

Looking through a sample of personal websites, very few of them has links to other personal websites. A hyperlink isn't a marriage proposal. It is enough to find some redeeming quality in a website to link to it. It costs nothing, and helps bring traffic to pages that you yourself think deserve it.

If we actually want these small websites to flourish as a healthy community, we need to promote each other much more than we do. It is advertisement, yes, but in earnest. I like it when other people link to my stuff. What sort of hypocrite would I then be if I only ever linked to my own websites?
{{% /quotebox %}}

<span class="unicode_emoji">👉🏽</span> 그리고 여기 [YourOnly.One 블로그롤](https://im.youronly.one/p/linklist/)이 있습니다! <span class="unicode_emoji">👈🏽</span>

(만약 우리가 서로를 알고 있고 당신의 블로그가 목록에 없다면 당신이 이미 검색 순위에 있기 때문일 가능성이 큽니다. 나는 나중에 가족과 친구를 위한 별도의 목록을 만들 수 있고 당신이 나를 다시 추천해주기를 바랍니다.)

## 자주하는 질문

질문: 패널티가 있습니까?

: 아니요. 링크 목록이나 블로그 롤에 웹 사이트를 추가하면 웹 사이트를 보증하거나 다른 방식으로 추천하는 것입니다. `rel=nofollow`는 유료 링크, 댓글 및 포럼의 링크, 예, 타사 테마 바닥글 크레딧(해당 링크를 업데이트해야 함)과 같이 보증할 수 없는 링크에만 사용됩니다.

: *테크 마구스*에 대한 링크를 추가하려면:

  ```html
  <a href="https://im.youronly.one/techmagus/ko/" rel="noopener external">테크 마구스</a>
  ```

: 내 블로그 롤에 연결하려면:

  ```html
  <a href="https://im.youronly.one/p/linklist/" rel="noopener external">YourOnly.One 블로그롤</a>
  ```

: 간단합니다!

질문: `rel=nofollow`가 무엇인지는 알지만 `noopener`와 `external`은 무엇입니까?

: [Mozilla 개발자 네트워크](https://developer.mozilla.org)에서 답변해 드리겠습니다.

: `rel=noopener`:

  : 해당 속성을 사용하여 링크를 클릭하면, 브라우저 컨텍스트 권한 없이 열립니다. 이 말은 곧, 새 창에서 [Window.opener](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener) 속성이 null 값을 반환하는것과 같습니다.

  : 해당 속성은 특히나 신뢰할 수 없는 링크를 열 때 유용합니다. [Window.opener](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener) 속성을 통한 컨트롤을 막아주고, (더욱 자세한 사항은 링크를 참조하세요. [About rel=noopener](https://mathiasbynens.github.io/rel-noopener/)) Referer HTTP 헤더를 사용합니다.

  : noopener 속성을 사용한다면, target 속성의 값으로 *_top*, *_self*, *_parent* 속성을 제외한 다른 속성은, 새 브라우저 창을 열 것인가에 대하여 *_blank* 속성으로써 적용됨을 주의하세요.[^a]

: `rel=external`:

  : 하이퍼링크가 현재 사이트 바깥의 리소스를 가리킴을 나타냅니다. 즉, 이 링크를 따라가면 사이트를 떠나게 됩니다.[^a]

[^a]: MDN Web Docs: [Link types](https://developer.mozilla.org/ko/docs/Web/HTML/Link_types)

## 당신의 공유

나만의 선별된 책갈피 목록이나 블로그롤을 만드셨습니까? 아래 댓글에 링크를 공유해 주시면 [YourOnly.One 블로그롤](https://im.youronly.one/p/linklist/)에도 추가하겠습니다. 신뢰할 수 있는 링크를 공유하고 링크 목록을 서로 연결하는 것입니다.

샬롬!

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link=""
  linkrel="noopener"

  title="Linklist"
  caption=""
  alt="Linklist"
  inlanguage="en"

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

---

고시 : Google 번역
