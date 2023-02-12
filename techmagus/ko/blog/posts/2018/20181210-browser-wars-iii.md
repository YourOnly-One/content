+++
title = "브라우저 전쟁 III: Blink 대 Gecko Quantum"
description = "Browser Wars 3는 Chromium과 Firefox에 관한 것이 아닙니다. 세 번째 브라우저 전쟁은 Blink와 Gecko Quantum 간의 전쟁에 관한 것입니다."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = 2018-12-10T07:54:23+09:00                                        # manually adjust to local timezone
lastmod = 2018-12-10T07:54:23+09:00                                        # manually adjust to local timezone

#aliases = [""]
slug = "browser-wars-3-blink-gecko"
translationKey = "browser-wars-3-blink-gecko-2018344"
relCanonical = "https://im.youronly.one/techmagus/ko/browser-wars-3-blink-gecko-2018344/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["literature"]                                                   # taxonomy
keywords = ["browsers", "browser wars", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["browserwars"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

featured = true
#math = true
toc = true

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://1.bp.blogspot.com/-irPJoRWat9Y/XuNle8K_vGI/AAAAAAAAiuY/oG6Bx5jed14nCOoDhfu0-cp7m1EqDWH6wCLcBGAsYHQ/s1600/Firefox-Chromium.jpg"]                                                       # used by og:images, etc.; first image is cover image

[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (雪亮 | 스노 | Yuki)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

**Microsoft**가 *EdgeHTML* 브라우저 엔진과 *Microsoft Edge* 브라우저 프론트엔드를 포기한다는 최근 발표는 **Browser Wars 2.0**의 끝을 의미합니다. 그들의 다음 주력 브라우저가 Chromium 기반이고 따라서 Blink 브라우저 엔진에 의해 구동될 것이라는 그들의 계시는 브라우저 엔진을 통해 인터넷을 제어하기 위한 전쟁인 **Browser Wars III**의 시작을 알립니다.

<!--more-->

**Browser Wars III**를 이해하려면 이 새로운 전쟁에는 ***Browser Frontend***와 ***Browser Engine***이라는 두 가지 전선이 있음을 알아야 합니다. 이 두 가지 전선을 구별할 수 있습니다.

## 브라우저 워즈 III 프론트: 브라우저 프론트엔드

브라우저 프론트엔드는 단순히 사용자가 보는 브라우저입니다. 이 경우 *Chromium* 및 **Mozilla**의 *Firefox [Quantum]*이 있습니다. Chromium 브라우저(프론트엔드 및 엔진)가 있기 전에 가장 많이 분기된 브라우저는 Firefox였습니다. 가장 인기 있는 Firefox 기반 프로젝트 중 일부는 *[Pale Moon](https://www.palemoon.org)*(*Gecko* 엔진을 *Goanna*로 분기하기도 함), *[Waterfox](https://www.waterfoxproject.org)*, **Comodo** *IceDragon*, *[Tor Browser](https://www.torproject.org/projects/torbrowser.html.en)* 및 원본 *Flock* 브라우저 .

Chromium이 현장에 도착했을 때 천천히 전환자를 얻었습니다. Flock은 Firefox 기반 브라우저에서 Chromium 기반 브라우저로 마이그레이션하여 충성도 높은 사용자를 확보했습니다(훨씬 나중에 Flock 개발이 종료됨). *Opera Browser*의 배후에 있는 회사인 **Opera Software**는 브라우저 프론트엔드와 *Presto* 브라우저 엔진의 개발을 중단했습니다. 거기에서 그들은 새로운 Chromium 기반 Opera를 만들었습니다! 마이크로소프트가 그들이 할 것이라고 발표한 것과 정확히 일치합니다.

그것으로 충분하지 않다면 Opera 브라우저의 팬들은 *[Otter Browser](https://otter-browser.org)* 및 *[Vivaldi](https://vivaldi.com)*라는 자체 브라우저도 만들었습니다. 새로운 Chromium 기반 Opera 브라우저보다 훨씬 낫습니다).

다른 Chromium 기반 브라우저는 다음과 같습니다. ***[Yandex Browser](https://browser.yandex.com)***; **코모도** *드래곤*; *용감한*; *에픽 브라우저*; 그리고 *Torch*, 몇 가지만 언급하자면. 아무도 더 이상 Firefox를 선택하지 않습니다!

이것은 우리를 …

## Browser Wars III Front: 브라우저 엔진 {#browser-wars-iii-front-browser-engine}

브라우저 전쟁 III의 브라우저 엔진 부분은 지난 두 번의 브라우저 전쟁에서 가장 중요하고 대부분 무시되었습니다. 오늘날 기사는 Chromium과 Blink를 교환하고 있습니다. 그러나 Chromium은 브라우저 프론트엔드이고 Blink는 브라우저 엔진입니다.

### 교환 불가

프론트엔드와 엔진은 호환되지 않습니다. 개발자가 할 수 있는 ...

- … 기존 브라우저 프론트엔드를 사용하지만 다른 브라우저 엔진을 사용합니다.
- … 기존 브라우저 프론트엔드를 사용하지만 기본 브라우저 엔진 위에 추가 브라우저 엔진 추가
- … 브라우저 엔진을 사용하지만 브라우저 프론트엔드는 사용하지 않습니다(일반적으로 브라우징 기능이 내장된 소프트웨어에서 볼 수 있음)
- … 브라우저 엔진을 사용하지만 처음부터 브라우저 프론트엔드 개발

Firefox의 브라우저 엔진인 Gecko는 위에서 언급한 사용 사례를 가진 많은 제품을 보았습니다. Blink의 사용은 주로 Chromium에 집중되어 있습니다. 결국, 이미 Chromium이 있는데 왜 처음부터 브라우저 프론트엔드를 구축해야 할까요? 데스크톱과 모바일 플랫폼 모두에서 소프트웨어나 앱의 일부인 것처럼 Chromium을 직접 사용할 수 있는데 왜 내장 브라우징 기능을 추가해야 할까요? (기본 브라우저가 Firefox로 설정되어 있어도 브라우징 경험이 *Chrome* 자체에 잠겨 있는 소프트웨어를 발견했습니다. Chrome은 **Google**의 Chromium 기반 브라우저입니다.)

그러나 Chromium과 Blink가 상호 교환 가능하다는 것을 의미하지는 않습니다. 특히 ...

### 중요한 것은 브라우저 엔진입니다

프론트엔드 개발자는 소프트웨어와 웹사이트를 디자인할 때 다른 브라우저에 대해 테스트합니다. 현실은 이러한 브라우저를 구동하는 엔진에 대해 테스트하고 있다는 것입니다. 제품 또는 웹사이트가 Blink, Gecko 및 *WebKit*(*Safari* 및 모든 **Apple** 제품) 기반 브라우저에서 테스트된 경우 일반적으로 개발자는 다른 브라우저에서도 동일하게 해석할 수 있습니다. 동일한 엔진에 의해 구동됩니다(반복하지만 *일반적으로*, 엔진과 해당 버전이 동일하더라도 결과를 변경할 수 있는 다른 요인이 관련되어 있음). Chromium, Chrome, Opera, Vivaldi, Brave 및 Yandex를 설치할 필요가 없으며 모두 Chromium을 통해 Blink에서 구동됩니다.

모두가 Chromium을 기본 브라우저 프론트엔드(개발자) 또는 일일 브라우저(최종 사용자)로 선택하면서 "*이 웹사이트가 가장 잘 작동하는*" 및 "*Google과 같은 Blink 기반 브라우저를 다운로드하세요. Chrome, Opera, Vivaldi, Yandex 및 Brave를 사용하여 이 웹사이트*로 계속 이동합니다. 또한 웹사이트를 운영하고 자금이 최대한 빨리 흐르도록 하는 데에만 관심이 있는 개발자와 회사는 Blink가 오늘날 시장에서 가장 큰 점유율을 차지하고 있기 때문에 테스트만 할 것입니다.

그것은 인터넷에 불균형을 초래합니다. Blink의 개발자이기도 한 Chromium 개발자는 이제 인터넷이 표시되는 방식에 대해 더 많은 권한을 갖게 되었습니다. 그들이 그것을 남용하지 않기를 바랍니다. 그러나 숫자나 특정 요소 또는 속성이 작동하는 방식을 기반으로 **W3C 컨소시엄**(웹 표준을 설정하는 그룹) 내에서 결정이 있었고, 앞으로도 항상 있을 것입니다. 또는 새로운 웹 기능이 Chromium의 버전이나 Mozilla의 해석을 따라야 하는지 여부.

## 결론

크롬은 표면일 뿐입니다. 브라우저 엔진은 여기에서 진짜 위험입니다. Chromium은 단순히 Blink의 주력 브라우저입니다. 대부분은 브라우저를 처음부터 시작하는 것을 원하지 않기 때문에 분명히 Chromium을 사용하기로 결정하고 원하는 모양으로 조정하고 고유한 기능을 추가했습니다. 그러나 아무도 브라우저 프론트엔드를 처음부터 구축하고 Blink를 브라우저 엔진으로 사용하는 것을 막지 못합니다. Chromium은 개수가 적고 Blink는 개수가 많습니다.

"*이 사이트는 다음에서 가장 잘 작동합니다*" 및 "*이 웹사이트는 완벽하게 테스트되었습니다*"는 모두 브라우저 엔진에 관한 것이기 때문에 어떤 브라우저 프론트엔드가 가장 인기 있는지는 중요하지 않습니다. Blink, Gecko, WebKit, Goanna 및 *KHTML*에 관한 것입니다.

Firefox Quantum을 사용하세요. 하지만 어떤 이유로든 Firefox가 마음에 들지 않는다면 Gecko Quantum 엔진으로 구동되는 브라우저를 사용하세요. Chromium 기반 브라우저가 유일한 대안은 아니며 Firefox 기반 브라우저도 있습니다. 프론트엔드 개발자라면 Gecko Quantum 기반 브라우저에서도 웹사이트 프로젝트를 테스트하십시오. 특정 브라우저 엔진이 시장에서 큰 격차와 지배력을 갖게 함으로써 인터넷을 위험에 빠뜨리지 맙시다.

내 개인적인 경험에 따르면 Gecko는 **항상** W3C 권장 사양을 구현하는 데 있어 항상 앞서 있었습니다. Chromium에는 항상 무시되거나 "버그가 아님" 및/또는 "의도한 대로 작동"으로 반복적으로 닫힌 버그가 있습니다. 예를 들어 일부 [아시아] 스크립트에 영향을 미치지만 다음에서 완벽하게 작동하는 글꼴 대체 메커니즘에서 Gecko 기반 브라우저!

마지막 생각 하나. 3개의 브라우저 엔진(Trident, Gecko 및 Blink)이 있는 2개의 아시아 브라우저가 있습니다. IE 기반 *[Avant Browser](http://www.avantbrowser.com)* 중국 개발자 및 IE 기반 *[Lunascape](https://www.lunascape.tv)* 일본 개발자. 예, 다중 엔진 브라우저(Firefox의 경우 확장)가 있습니다.

이 브라우저 전쟁 III는 분명히 브라우저 엔진인 Blink와 Gecko에 관한 것입니다. Chromium과 Firefox인 브라우저 프론트엔드는 부차적인 것입니다. 평범한 Joe와 Jane은 이러한 "이름"에만 익숙하기 때문에 더 많이 언급됩니다.

---

{{< image
  type="imagecoverattrib"

  link="https://1.bp.blogspot.com/-irPJoRWat9Y/XuNle8K_vGI/AAAAAAAAiuY/oG6Bx5jed14nCOoDhfu0-cp7m1EqDWH6wCLcBGAsYHQ/s1600/Firefox-Chromium.jpg"
  linkrel="noopener external"

  title="Browser Wars III: Firefox-Chromium"
  caption=""

  licensecode="cc0"
  licenseurl="https://creativecommons.org/publicdomain/zero/1.0/"
  licensename="CC0"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"

  cc0country="Philippines"
  cc0countrycode="PH"
  cc0countryurl="https://en.wikipedia.org/wiki/Philippines"
>}}

---

고시 : Google 번역
