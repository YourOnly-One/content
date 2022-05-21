+++
title = "FacebookDown에서 배운 교훈"
description = "Facebook, Instagram, Messenger 및 WhatsApp의 가장 긴 다운타임에서 우리는 어떤 교훈을 배워야 할까요?"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = "2021-10-06T07:21:07+09:00"                                        # manually adjust to local timezone
lastmod = "2021-10-06T07:21:07+09:00"                                        # manually adjust to local timezone

#aliases = [""]
slug = "lessons-learned-facebook-down"
translationKey = "lessons-learned-facebook-down-2021279"
relCanonical = "https://im.youronly.one/techmagus/ko/lessons-learned-facebook-down-2021279/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

syndications = ["https://www.facebook.com/techmagus/posts/1911004249102503", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/515720186263883"]

channels = ["techmagus"]
categories = ["web"]                                                   # taxonomy
keywords = ["web", "federation", "decentralisation", "decentralization", "web 3.0", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["federation", "decentralization"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://img.youronly.one/p/techmagus/ddfon/decentralisation-01.webp", "https://img.youronly.one/p/techmagus/ddfon/friendica-01-frio-profile.webp", "https://img.youronly.one/p/techmagus/ddfon/hubzilla-01.webp", "https://img.youronly.one/p/techmagus/ddfon/zap-01-logo.svg", "https://img.youronly.one/p/techmagus/ddfon/misskey-01-hashtag.webp", "https://img.youronly.one/p/techmagus/ddfon/pixelfed-01-trending.webp", "https://img.youronly.one/p/techmagus/ddfon/mastodon-01-dashboard.webp", "https://img.youronly.one/p/techmagus/ddfon/peertube-01-discover.webp", "https://img.youronly.one/p/techmagus/ddfon/keybase-01-chat.webp", "https://img.youronly.one/p/techmagus/ddfon/matrix-01-element_client.webp", "https://img.youronly.one/p/techmagus/ddfon/session-01.webp"]                                                       # used by og:images, etc.; first image is cover image

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (Yuki | 雪亮)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

페이스북, 인스타그램, 메신저, 왓츠앱 역사상 가장 긴 다운타임은 많은 기업에서 비즈니스 연속성과 플랜 B와 플랜 C의 중요성에 대한 회의를 촉발했어야 했습니다. 이것은 학교와 학교에서도 기억되고 사용될 것입니다. 보안 시스템을 설정하지 않는 방법에 대한 첫 번째 사례로 연구합니다.

그러나 주요 질문은 Facebook, Instagram, Messenger 및 WhatsApp 외에 무엇이 있습니까? 그들은 시장을 궁지에 몰아넣었고 독점과도 같습니다. 그들은 *인터넷*입니다. 그들은 *소셜 웹*입니다. 오른쪽?

**아니요** 및 *아니요*.

<!--more-->

Facebook, Instagram, Messenger 및 WhatsApp이 인터넷에서 사라지는 문제가 시작된 것은 UTC 15시 40분경이었습니다.[^a] 서비스가 인터넷에 다시 연결된 것은 UTC 21시 28분이었습니다.[^a], 수십억은 아니더라도 수백만 명의 사람들이 의존하는 4개 서비스에 대해 6시간의 가동 중지 시간이 발생합니다.

Facebook과 해당 서비스의 가장 긴 다운타임에 기여한 많은 요인이 있습니다. 그 중 하나는 Facebook도 인터넷에 연결하기 위해 자체 네트워크에 의존한다는 것입니다.[^b]

{{< tweet user="sheeraf" id="1445099150316503057" >}}

하지만 당신은 어떻습니까? 고객의 로그인 방법으로 Facebook을 사용하는 온라인 서비스가 있습니까? 아니면 온라인 비즈니스가 있고 유일한 플랫폼은 Facebook과 Instagram입니까? 메신저에만 의존하고 있는 가족과의 소통은 어떻습니까? WhatsApp을 긴급 대응과 같은 중요한 서비스를 위한 통신 플랫폼으로 사용하는 사람들도 있습니다. 또 다른 주요 다운타임이 발생하면 어떻게 됩니까?

{{< tweet user="nixcraft" id="1445121124912676867" >}}

[^a]: Cloudflare: [Understanding How Facebook Disappeared from the Internet](https://blog.cloudflare.com/october-2021-facebook-outage/)
[^b]: Sheera Frenkel: [… employees unable to enter buildings this morning … because their badges weren't working to access doors](https://twitter.com/sheeraf/status/1445099150316503057)

## 배운 교훈

# FacebookDown, #InstagramDown, #MessengerDown, #WhatsAppDown에서 배워야 할 것은 페이스북뿐만 아니라 우리 모두가 배워야 합니다. 다음은 우리 모두가 고려해야 한다고 생각하는 몇 가지입니다

1. 온라인 서비스에서 계정 생성 및 로그인 방법으로 Facebook만 제공하는 경우 기존 사용자 이름과 비밀번호를 포함한 다른 로그인 방법을 추가해야 합니다.
1. 온라인 서비스에서 Facebook으로 별도의 계정을 만든 경우 고객에게 비밀번호 설정을 포함하여 다른 로그인 방법을 추가할 수 있는 옵션을 제공해야 합니다.
1. 중요/비상 대응 그룹의 일원이고 WhatsApp이 유일한 커뮤니케이션 플랫폼이라면 적어도 백업으로서 대안을 찾아야 할 때입니다. 중요한 것은 갑자기 계정 생성, 검색, 추가, 앱 및 서비스 사용법 학습을 거치지 않고 바로 사용할 수 있는 백업 서비스가 필요하다는 것입니다.
1. 온라인 비즈니스를 하고 있거나 Facebook 및 Instagram의 채널을 통해 수익을 올리는 경우, 또 다른 주요 다운타임이 발생할 경우 팬이 계속 팔로우할 수 있는 또 다른 플랫폼을 찾아야 합니다.
1. 온라인 사교 활동이 숨쉬는 공기라면 다른 플랫폼에 가입하는 것이 좋습니다.

우리가 나열할 수 있는 다른 수업이 있지만 위에 이미 나열한 내용과 함께 한두 가지가 될 것입니다. 다른 사람의 플랫폼 및/또는 서비스의 최종 사용자로서 우리는 절대 전적으로 의존해서는 안 되며 어떤 이유로든 사라질 때 대비해야 합니다.

추천 사항이 있습니까? 꼭 그리하겠습니다.

## 연합 소셜 미디어 및 소셜 네트워크 서비스

우리와 우리 가족, 친구들은 같은 소셜 미디어와 소셜 네트워크 플랫폼에 가입했습니다. 서로 다른 서비스를 사용하고 있다면 서로 소통할 방법이 없기 때문입니다. 그러나 이것이 구식 모델이고 이미 다른 플랫폼과 서비스에서 서로 사교하는 것이 가능하다는 것을 알고 계셨습니까? 예, 이것을 "페더레이션"이라고 하며 이러한 연합된 플랫폼과 서비스를 집합적으로 "페디버스"라고 합니다.

이것이 새롭다고 생각한다면 놀라움! 페더레이션은 2008년부터 존재했으며 통신 또는 메신저의 경우 1999년부터 존재했습니다("XMPP" 또는 이전에는 "Jabber"라고 함). 그런 의미에서 개인적으로 추천하는 몇 가지 서비스를 소개합니다.

### Friendica

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/friendica-01-frio-profile.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/friendica-01-frio-profile.webp"
  linkrel="noopener"

  title="Frio Theme"
  caption="User Profile"
  alt="Frio Theme User Profile"

  attribalign=""

  licensecode="allrightsreserved"
  licenseurl=""
  licensename=""

  attribto="Friendica"
  attriburl="https://friendi.ca"
  attribrel="noopener external nofollow"
>}}

**Friendica**(이전 *Friendika*, 프로젝트 이름 *Mistpark*)는 분산 및 연합 소셜 네트워크입니다. 페디버스를 시작한 최초의 소프트웨어 중 하나입니다.

#### 기능 및 이점

- "상태 업데이트" 게시
- 사진, 앨범
- 해시태그
- 은둔
- 군사 암호화
- 달력
- 다른 사람과 커뮤니티에 다른 "프로필" 표시
- 다른 프로필 및 해시태그 팔로우
- 다양한 테마 및 애드온
- Diaspora, Mastodon, Pleroma, Hubzilla, WordPress, Nextcloud, Pixelfed, PeerTube, Twitter 등의 사람들과 연결할 수 있습니다.

스핀을 주고 싶다면 [여기](https://friendi.ca/#try)에서 사용 가능한 서버 중 하나를 선택하세요. 어떤 서버를 선택하든 상관없이 fediverse의 모든 사람과 연결할 수 있습니다.

### Hubzilla

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/hubzilla-01.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/hubzilla-01.webp"
  linkrel="noopener"

  title="Hubzilla"
  caption=""
  alt="Hubzilla"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Hubzilla**는 같은 개발자 [Mike Macgirvin](https://macgirvin.com/channel/mike)에 의해 시작되었다는 점에서 *Friendica*와 유사합니다. Macgirvin은 비전의 사람이며 선택의 자유, 분권화, 연합 및 검열 반대의 강력한 옹호자이자 지지자입니다. *Hubzilla*를 통해 그는 다른 페디버스 플랫폼(*Zap* 제외)이 오늘날까지 가지고 있지 않은 고유한 기능인 **유목민 신원 및 복제**를 개발했습니다.

#### 유목민의 정체성과 복제란 무엇인가

유목민의 정체성은 온라인 정체성의 진정한 소유권을 의미합니다. Hubzilla를 사용하면 서버에 계정이 없으며 그리드를 통해 가져올 수 있는 ID를 소유하게 됩니다. 네트워크 장애 또는 검열에 대한 복원력을 위해 여러 허브에 걸쳐 채널을 복제하거나 한 허브에서 다른 허브로 채널을 완전히 이동하여 데이터와 연결을 가져올 수 있습니다.[^c]

example.com에 채널을 만든 다음 example.net에서 복제할 수 있습니다. 두 개의 서로 다른 서버에 있기 때문에 두 개의 별도 계정인 것처럼 보이지만 실제로는 동일합니다. 유목민 정체성의 기본 기술을 이해하는 모든 플랫폼은 둘 다 단일 채널로 취급합니다. example.net을 통해 로그인하면 동일한 통신, 연결을 수신하고 답장을 보내거나 새 게시물/업데이트를 생성할 수 있습니다. example.com을 통해 로그인했습니다.

기능과 관련하여 Hubzilla는 Friendica와 거의 동일한 세트를 공유하지만 결코 코드가 동일하지는 않습니다. 근데 이 부분? 이것은 개발자와 서버 운영자에게 좋습니다. 게다가 유목민의 아이덴티티는 다른 모든 플랫폼이 구현해야 하는 훌륭한 기능임에는 틀림없겠죠?

[여기](https://hubzilla.org/pubsites)에 있는 사용 가능한 서버 중 하나에서 Hubzilla 채널(또는 원하는 경우 계정)에 가입할 수 있습니다.

[^c]: Hubzilla: [Nomadic identity and cloning](https://hubzilla.org//page/hubzilla/hubzilla-project)

### Zap

{{< image
  type="image"

  height="50%"
  width="50%"

  src="https://img.youronly.one/p/techmagus/ddfon/zap-01-logo.svg"
  link="https://img.youronly.one/p/techmagus/ddfon/zap-01-logo.svg"
  linkrel="noopener"

  title="Zap"
  caption="logo"
  alt="Zap logo"

  attribalign=""

  licensecode="allrightsreserved"
  licenseurl=""
  licensename=""

  attribto="Zap"
  attriburl="https://zotlabs.com/zap/"
  attribrel="noopener external nofollow"
>}}

**Zap**은 몇 가지 추가 기능과 오늘날 Fediverse에서 사용할 수 있는 최고의 개인 정보 보호 및 남용 방지 기능을 통해 Facebook 사용자에게 친숙하고 편안한 경험을 제공합니다.[^d]

[^d]: Zap: [Zap Fediverse Server, an ethical alternative](https://zotlabs.com/zap/)

#### 기능 및 이점

- 그룹: 공개, 비공개 및 중재. 거의 모든 fediverse 플랫폼에서 작동합니다.
- 이벤트: 일정 및 출석; 자동 시간대 조정; 친구를 위한 생일 알림
- 권한: 각 기능에 대한 세분화된 권한 제어
- 클라우드 스토리지: 소셜 네트워킹 액세스/권한이 있는 내장 네트워크 파일 스토리지.
- 편집기: 마크다운, html 및 bbcode 지원
- 목록: *서클* 또는 *측면*이라고도 함
- 친구 확대/축소: 연결과의 "근접성" 정도를 설정한 다음 친구 확대/축소를 사용하여 대시보드 스트림을 필터링하여 친한 친구 또는 모든 사람만 표시하도록 합니다.
- 유목민 프로토콜: (위의 *Hubzilla* 아래 "유목민 정체성" 참조)

온라인 소셜 웹 ID를 생성할 준비가 되었다면 [여기](https://z.macgirvin.com/sites?project=zap)에서 아무 서버나 선택하세요.

### Misskey

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/misskey-01-hashtag.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/misskey-01-hashtag.webp"
  linkrel="noopener"

  title="Misskey"
  caption="Stream"
  alt="Misskey Stream"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Misskey**는 분산형 마이크로블로깅 플랫폼입니다. Fediverse 내에 존재하며 다른 소셜 미디어 플랫폼과 상호 연결됩니다.[^e] 일본 개발자인 [しゅいろ (syuilo)](https://misskey.io/@syuilo)에 의해 시작되어 합류했습니다. 다른 기여자에 의해. Misskey는 페디버스와 관련하여 일본에서 선택하는 플랫폼입니다.

[^e]: Misskey: [Let's start Misskey](https://join.misskey.page)

#### 기능 및 이점

- 게시 또는 상태 업데이트
- 반응
- 다양한 UI 옵션
- 미스키 드라이브
- 채팅
- 포토 갤러리
- 여러 떼
- 페이지
- 개인 메시지
- 기울기
- 채널
- 안테나
- 미스키 게임

당신에게 딱 맞는 Misskey 커뮤니티는 [여기](https://join.misskey.page/instances)에서 찾을 수 있습니다.

### Pixelfed

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/pixelfed-01-trending.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/pixelfed-01-trending.webp"
  linkrel="noopener"

  title="Pixelfed"
  caption="Trending view"
  alt="Pixelfed Trending view"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Pixelfed**는 fediverse의 일부로 연결된 개인 정보 보호 중심의 사진 공유 플랫폼입니다. 오늘날 Pixelfed의 사용자 인터페이스는 Instagram 팬에게 매우 익숙해야 합니다. 즉, Pixelfed를 사진 공유 플랫폼으로 사용하는 것은 어렵지 않습니다.[^f]

[^f]: Pixelfed: [A free and ethical photo sharing platform](https://pixelfed.org)

#### 기능 및 이점

- ad-free: 타임라인 또는 그 어디에도 광고 없음
- chronological: 타임라인이 적절하게 정렬됨, 알고리즘 없음
- 발견: 새로운 콘텐츠 및 제작자 탐색
- 필터: 사진에 선택적 필터 추가
- 사진 앨범: 한 번에 하나의 게시물로 사진 공유
- 개인 정보 보호: 타사 분석 또는 추적이 포함되지 않음
- 이중 인증: 계정 보안
- 콘텐츠 경고: 사진 및/또는 댓글이 민감한 경우 자동 감지하여 자동으로 흐리게 처리하거나 숨깁니다.
- 댓글 비활성화: 게시물당 댓글을 끄는 기능
- 라이센스 선언: 사진 라이센스 정보 포함
- 추종자 및 추종자 수 숨기기
- 계정 뮤트
- 개인 계정
- 비공개 게시물
- 비공개 게시물: 공개 게시물이지만 글로벌 공개 타임라인/스트림에는 나열되지 않습니다.

[Pixelfed 인스턴스](https://fedidb.org/software/pixelfed)에 가입하여 오늘부터 사진을 fediverse에 업로드할 수 있습니다.

### Mastodon

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/mastodon-01-dashboard.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/mastodon-01-dashboard.webp"
  linkrel="noopener"

  title="Mastodon"
  caption="Dashboard"
  alt="Mastodon Dashboard"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Mastodon**은 원활한 소셜 미디어 경험을 제공하는 다양한 조직과 개인이 운영하는 수천 개의 커뮤니티 네트워크입니다.[^g] Friendica, Hubzilla, Zap, Misskey, Pixelfed, PeerTube, Write.as 및 분산형 소셜 네트워킹 프로토콜인 소셜 웹 표준인 ActivityPub에 연결된 모든 것.

[^g]: Mastodon: [Social networking, back in your hands](https://joinmastodon.org)

#### 기능 및 이점

- 효과적인 남용 방지 도구
- 중재자
- 500자 이상
- 이모티콘 및 사용자 정의 이모티콘
- 스포일러 태그
- 내용 경고
- 상태 업데이트

정기적으로 Twitter를 사용하고 흐름이 마음에 든다면 Mastodon이 적합한 플랫폼입니다. 지금 [마스토돈에 가입](https://joinmastodon.org/communities)하고 페디버스의 모든 사람들과 연결하세요.

### PeerTube

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/peertube-01-discover.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/peertube-01-discover.webp"
  linkrel="noopener"

  title="PeerTube"
  caption="Discover view"
  alt="PeerTube Discover view"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

*Framasoft*에서 개발한 **PeerTube**는 비디오 플랫폼에 대한 무료 분산형 대안으로, 페디버스 전역에서 60,000명의 사용자가 게시하고 1,500만 회[^h] 이상 조회된 400,000개 이상의 비디오를 제공합니다.

PeerTube는 전 세계의 비디오를 중앙 집중화하는 거대한 플랫폼이 되기 위한 것이 아닙니다. 오히려 상호 연결된 소규모 비디오 호스팅 업체의 네트워크입니다. 사용자는 여전히 다른 서버에서 호스팅되는 비디오를 볼 수 있으며 자신이 업로드한 비디오는 다른 PeerTube 서버에서 볼 수 있습니다.

PeerTube는 fediverse의 일부이기 때문에 fediverse의 모든 사용자는 자신의 플랫폼에서 직접 PeerTube가 호스팅하는 비디오에 댓글을 남길 수 있습니다.

[^h]: PeerTube: [A decentralized and free/libre alternative to video broadcasting services](https://joinpeertube.org)

#### 기능 및 이점

- 다른 플랫폼에서 비디오 가져오기
- 라이센스 정보
- 해시태그
- 채널
- 광고 없는
- 추적기 무료
- 필요할 때마다 P2P(Peer-to-Peer) 프로토콜을 사용하여 바이러스성 비디오를 방송할 수 있습니다.
- 역사
- 구독
- 재생 목록

비디오를 업로드하고 수많은 열성적인 시민들이 볼 준비가 되셨습니까? 이 [페이지](https://joinpeertube.org/instances#instances-list)에서 귀하의 요구에 가장 적합한 서버를 찾으십시오.

## 통신 플랫폼

### Keybase

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/keybase-01-chat.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/keybase-01-chat.webp"
  linkrel="noopener"

  title="Keybase"
  caption="Chat view"
  alt="Keybase Chat view"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Keybase**는 메시징, 파일 공유, 파일 호스팅, 웹 호스팅, 파일 암호화 및 텍스트 암호화를 위한 가장 안전한 플랫폼 및 서비스입니다. 게다가 Keybase는 온라인 계정과 PGP 키를 확인하는 가장 쉬운 방법입니다.[^k]

팀당 100GB의 스토리지를 제공하는 Keybase Teams와 개인 계정에서 파일과 웹사이트를 호스팅하도록 선택하면 250GB의 클라우드 스토리지가 무료로 제공됩니다. git 사용법을 안다면 이 블로그처럼 Keybase git을 사용하여 호스팅용 소스 파일로 사용할 수 있습니다.

[^k]: Keybase: [End-to-end encryption for things that matter](https://keybase.io)

#### 기능 및 이점

- 온라인 신원 확인
- 종단간 암호화 채팅: 직접 채팅, 비공개 그룹 및 공개 채팅방
- 개인 및 팀 모두를 위한 파일
- 각각 별도의 종단 간 암호화 채팅 채널이 있는 팀 및 하위 팀
- 사이트 또는 Keybase 호스팅
- Keybase git: 개인 및 팀 모두용 웹사이트를 호스팅하는 데에도 사용할 수 있습니다.
- 지갑: 스텔라 루멘(XLM)을 저장하기 위해
- 파일과 텍스트를 수동으로 암호화, 암호 해독, 서명 및 확인합니다. 다음은 예입니다.

  - 텍스트 암호화(Keybase를 사용하여 암호 해독)

    > BEGIN KEYBASE SALTPACK ENCRYPTED MESSAGE. kiPgBwdlv6bV9N8 dSkCcFVY51Q7KCw fMbJcaTPSiZstY4 LgWXhgtnlkbS2sf 7PIZgXSaqi0BxiB ZSn5xSPvXc3PUAo s9OKZFOsVgnC9XD oQHcUxbAK8euOKI thP5nCqtCla172G X7uNyVhXJngekIc GMXIMSAM2h2B3Nb N7b9lP2cjQKWulw yqL68ZqqxE1lzNC kBlby47HPRKjMCM zgaoj1TqIp1uZHL eFaFODkHLAX7qCC SNi6T3mvgcSKStL hF8jeqe55dzw5UY JH4K0eWTycxvKEI 7CGGRPKz9PgoWdC CNb62OqgfrMlR4h wS0jXCH4PP6Nf7J romvq81QCjPsIfN 90v63EHZ5ThWZF0 pnJmD7Fhpsc8zIG YDhFr0lSvlOZRSo kCqhxsTL92LRBKQ IWeokZfaGd1AMXv fA0vy4JK2QPezrt vKJgA1yjnwedeQZ LswMNNqg8K6peok O32mmvW9KaHo9YK SXwbM7cDNuwt5Qi RE0cBISJFZMCDOO ldEVPTKlgDwZN4M BTvxgBdrXFHrZ2y BRVUBvvtTGZVWHE b9ykiVbh1RnM2a7 j2IxheFV8mheRFr LfEAKCIgKhwEC9f P2CeFknseSSQpyu 2rxDKR0LmkoxQgG q1VEZuB7Oo0boWR WSGvbenuwSd5efz qjhIGxzOkGOcWq2 dMxBbizQiWam2oP HwACYMLAQRzY97l bcCL685QAsWNiXn f93kcDweScZZhqw dGmXeQCjbMfYcgn 5C4we1mi5jWHLNH oqAgpBhAUI8Uovm r4vAXjvzBwPx8Cv WV. END KEYBASE SALTPACK ENCRYPTED MESSAGE.

  - 텍스트 서명(Keybase에서 서명을 확인하여 이 메시지를 작성했음을 확인)

    > 아미레이에게
    >
    > 나는 그저 한 소년일 뿐이고, 한 소녀 앞에 서서 그녀에게 그를 사랑해 달라고 부탁합니다.
    >
    > 당신의 은밀한 추종자로부터,
    >
    > I'M YourOnly.One

    > BEGIN KEYBASE SALTPACK SIGNED MESSAGE. kXR7VktZdyH7rvq v5weRa0zkP4VNyC 8WftM9nW4fgPe6n Zl3jKJsRhCjvlTD OXqz3yNPCECfoMX cnUDVmucUAg4cvX OX4zeGMjUYkTLiy dNkVnRzDBDVxG2u mO3jOunXUM2XMAn DmL43DloFf1Qf4Z luDL9CnuCsYIPR8 yk4QDxSmdhqcJrh j375yin0QIoWmg2 o7qIKBGzNO76WWb KjIzyaGFMcdwNee BAQse3vqHNs4KVW t7ilkOLlPk7Ez6e N3UtebnA7h4sMBm baupTDkWdm2uGyl nzviRp0C6chszgx jhqiHLAkRp1vqZS SXgNMXUK0b2Lg7x lac0bXJOWK23bvb P50HA8XpS2ApKmE tUcMMIoesBAklIf dVAkCfo6oFAba4b ubhodatClJTJ1Ia WIkZ07O0B4wGIN4 cbSIZJKSGA1I8gk yYR1KKSxBf9GlsZ Eof. END KEYBASE SALTPACK SIGNED MESSAGE.

#### Keybase 시작하기

- [Keybase 계정을 만드는 방법](https://im.youronly.one/techmagus/create-keybase-2020160/)

- [Keybase를 통해 계정을 확인해야 하는 이유](https://im.youronly.one/techmagus/verify-account-keybase-2020161/)

### Matrix

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/matrix-01-element_client.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/matrix-01-element_client.webp"
  linkrel="noopener"

  title="Matrix"
  caption="Element Web Client"
  alt="Matrix Element Web Client"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Matrix**는 안전하고 분산된 실시간 커뮤니케이션 플랫폼입니다. Matrix의 대화는 참여하는 모든 서버에 복제되며 단일 제어 지점이나 오류가 없습니다. 또한 의도한 수신자만 메시지를 해독할 수 있도록 하는 최첨단 종단 간 암호화를 제공하는 동시에 예기치 않은 장치가 대화에 추가되면 경고를 표시합니다.[^i]

Matrix에는 언급된 것보다 훨씬 더 많은 기능이 있지만 이러한 훌륭한 기능은 개발자와 서버 호스트에만 해당됩니다. 회사에서 커뮤니케이션 플랫폼을 찾고 있고 *Matrix*에 대해 더 알고 싶다면 [공식 웹사이트](https://matrix.org)를 방문하세요.

[^i]: Matrix: [An open network for secure, decentralized communication](https://matrix.org)

#### 기능 및 이점

- Android에서 사용 가능한 앱
- iOS에서 사용 가능한 앱
- 웹 클라이언트
- Windows, Linux 및 Mac용 데스크톱 클라이언트
- 명령줄 클라이언트
- 종단 간 암호화
- 다른 네트워크에 대한 브리지

[오늘](https://matrix.org/docs/projects/try-matrix-now/) Matrix를 사용해 보세요!

### Session

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/session-01.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/session-01.webp"
  linkrel="noopener"

  title="Session"
  caption="Linux Client"
  alt="Session Linux Client"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Session**은 민감한 메타데이터를 최소화하는 종단 간 암호화 메신저로, 모든 형태의 감시로부터 완전한 개인 정보 보호와 자유를 원하는 사람들을 위해 설계 및 구축되었습니다.[^j]

[^j]: Session: [Send Messages, Not Metadata](https://getsession.org)

#### 기능 및 이점

- 전화번호 및 이메일 주소 없음: 세션 계정은 완전히 익명입니다.
- 데이터 유출 없음: 세션에서 데이터를 수집하지 않으므로 누출될 사항이 없습니다.
- 발자국 없음: 세션의 양파 라우팅 네트워크를 통해 메시지를 보내고 흔적을 남기지 않습니다.
- 검열 저항: 중앙 실패 지점이 없으면 세션을 종료하기가 더 어렵습니다.
- 오픈 소스: 세션의 코드에는 숨길 것이 없습니다. 누구나 보고, 감사하고, 기여할 수 있습니다.
- 그룹 채팅: 비공개 및 공개 그룹
- 음성 메시지
- 첨부 파일: 암호화되지 않은 서비스에 해당 문서를 업로드하지 마십시오. 개인 정보를 중요하게 생각하는 네트워크를 통해 모든 파일, 이미지 및 첨부 파일을 보내십시오.

[Session](https://getsession.org/download)을 데스크탑이나 휴대폰에서 다운로드하여 사용하세요.

## 마지막 단어

위의 플랫폼 및 서비스 목록이 백업 계획 수립을 시작하기에 충분하기를 바랍니다. 많은 사람들이 Facebook, Instagram, Messenger 및 WhatsApp 계정을 마이그레이션하고 삭제해야 한다고 말하지만 여기 **YourOnly.One**에서 백업 플랫폼과 서비스가 있어야 한다고 제안합니다. Facebook, Instagram, Twitter 및 WhatsApp을 계속 사용할 수 있지만 오늘 우리가 했던 #FacebookDown, #InstagramDown, #MessengerDown 및 #WhatsAppDown 이후에 준비된 대안 또는 보조 플랫폼 및 서비스가 없는 것은 나중에 후회하게 될 결정입니다. *if* 하지만 **때**, 다시 발생합니다.

마지막으로 가장 중요한 것은 데이터, 플랫폼 및 서비스의 탈중앙화, 배포 및 연합을 완전히 수용할 때입니다. 오늘 일어난 일은 이것이 인터넷과 우리가 의존하는 서비스가 계속 존재하고 작동할 수 있도록 하는 유일한 논리적 단계임을 입증했습니다.

즐기고 샬롬!

---

{{< image
  type="imagecoverattrib"

  link="https://img.youronly.one/p/techmagus/ddfon/decentralisation-01.gif"
  linkrel="noopener"

  title="Decentralisation"
  caption=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

---

고시 : Google 번역
