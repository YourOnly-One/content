+++
title = "FacebookDownから学んだ教訓"
description = "Facebook、Instagram、Messenger、WhatsAppの最長のダウンタイムからどのような教訓を学ぶ必要がありますか？"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = "2021-10-06T07:21:07+09:00"                                        # manually adjust to local timezone
lastmod = "2021-10-06T07:21:07+09:00"                                        # manually adjust to local timezone

#aliases = [""]
slug = "lessons-learned-facebook-down"
translationKey = "lessons-learned-facebook-down-2021279"
relCanonical = "https://im.youronly.one/techmagus/ja/lessons-learned-facebook-down-2021279/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

syndications = ["https://www.facebook.com/techmagus/posts/1911004249102503", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/515720186263883"]

channels = ["techmagus"]
categories = ["web"]                                                   # taxonomy
keywords = ["web", "web 3.0", "federation", "decentralisation", "decentralization", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["federation", "decentralization"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["images/d/decentralisation-01.webp", "images/f/friendica-01-frio-profile.webp", "images/h/hubzilla-01.webp", "images/z/zap-01-logo.svg", "images/m/misskey-01-hashtag.webp", "images/p/pixelfed-01-trending.webp", "images/m/mastodon-01-dashboard.webp", "images/p/peertube-01-discover.webp", "images/k/keybase-01-chat.webp", "images/m/matrix-01-element-client.webp", "images/s/session-01.webp"]                                                       # used by og:images, etc.; first image is cover image

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

Facebook、Instagram、Messenger、WhatsAppの歴史の中で最も長いダウンタイムは、ビジネスの継続性と、プランBとプランCを持つことの重要性について、多くの企業で会議を引き起こしたはずです。これは、学校や セキュリティシステムをセットアップしない方法に関する一番の例として研究します。

それでも主な質問は、Facebook、Instagram、Messenger、WhatsApp以外に何がありますか？ 彼らは市場を追い詰め、独占と同じくらい良いです。 それらは*インターネット*です。 それらは*ソーシャルウェブ*です。 右？

**NO**および*no*。

<!--more-->

Facebook、Instagram、Messenger、WhatsAppがインターネットから姿を消す原因となったトラブルが始まったのは15:40 UTC頃でした。[^a]彼らのサービスがインターネットに再接続されたのは、21：28UTCまででした[^a]、4つのサービスで6時間のダウンタイムが発生し、数十億とまではいかなくても数百万の人々が依存しています。

Facebookとそのサービスの最長のダウンタイムに貢献した多くの要因があります。そのようなものの1つは、Facebookがインターネットに接続するために独自のネットワークに依存していることです。[^b]

{{< tweet user="sheeraf" id="1445099150316503057" >}}

しかし、あなたはどうですか？ 顧客のログイン方法としてFacebookに依存するオンラインサービスはありますか？ または、おそらくあなたはオンラインビジネスを持っていて、あなたの唯一のプラットフォームはFacebookとInstagramですか？ 家族とのコミュニケーションはどうですか、メッセンジャーだけに頼っていますか？ 緊急時の対応など、重要なサービスの通信プラットフォームとしてWhatsAppを使用している人もいますが、別の大きなダウンタイムが発生した場合はどうなりますか？

{{< tweet user="nixcraft" id="1445121124912676867" >}}

[^a]: Cloudflare: [Understanding How Facebook Disappeared from the Internet](https://blog.cloudflare.com/october-2021-facebook-outage/)
[^b]: Sheera Frenkel: [… employees unable to enter buildings this morning … because their badges weren't working to access doors](https://twitter.com/sheeraf/status/1445099150316503057)

## 学んだ教訓

＃FacebookDown、＃InstagramDown、＃MessengerDown、および#WhatsAppDownから学ぶ必要があるのはFacebookだけではなく、私たち全員がこれから学ぶ必要があります。 ここに私たち全員が考慮すべきだと思ういくつかがあります。

1. オンラインサービスがアカウントの作成とログイン方法としてFacebookのみを提供している場合は、従来のユーザー名とパスワードを含む別のログイン方法を追加するときが来ました。
1. オンラインサービスでFacebookで作成されたアカウントを分離する場合は、パスワードの設定など、別のログイン方法を追加するオプションを顧客に提供するときが来ました。
1. あなたがクリティカル/緊急対応グループの一員であり、WhatsAppが唯一のコミュニケーションプラットフォームである場合は、少なくともバックアップとして、代替手段を探す時が来ました。 重要なのは、アカウントの作成、検索、追加、アプリとサービスの使用方法の学習を突然行うのではなく、すぐに利用できるバックアップサービスの必要性です。
1. あなたがオンラインビジネスをしている場合、またはFacebookやInstagramのチャンネルを通じて稼いでいる場合は、別の大きなダウンタイムが発生した場合にファンがあなたをフォローし続けることができる別のプラットフォームを見つける時が来ました。
1. オンラインでの付き合いがあなたの息吹である場合は、何かが起こらないように他のプラットフォームに参加することをお勧めします。

私たちがリストできる他のレッスンがありますが、おそらく私たちがすでに上にリストしたものと1つか2つに分類されるでしょう。 他の誰かのプラットフォームやサービスのエンドユーザーとして、私たちはそれだけに頼るべきではありません。何らかの理由でそれが消えたときに備えておく必要があります。

おすすめはありますか？ 確かにそうです。

## 連合ソーシャルメディアとソーシャルネットワークサービス

私たち、そして私たちの家族や友人は、同じソーシャルメディアとソーシャルネットワークプラットフォームにサインアップしました。なぜなら、私たちが異なるサービスを利用している場合、互いに通信する方法がないからです。 しかし、これは時代遅れのモデルであり、さまざまなプラットフォームやサービスを利用しながら、お互いに交流することがすでに可能であることをご存知ですか？ はい、これは《フェデレーション》と呼ばれ、これらのフェデレーションプラットフォームとサービスはまとめて《フェディバース》と呼ばれます。

これが新しいと思うなら、驚きます！ フェデレーションは2008年から存在し、通信またはメッセンジャーの場合は1999年から存在します（《XMPP》または以前は《Jabber》と呼ばれていました）。 そうは言っても、ここに私が個人的にお勧めするサービスのいくつかがあります。

### Friendica

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/f/friendica-01-frio-profile.webp"
  link="images/f/friendica-01-frio-profile.webp"
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

**Friendica**（以前は*Friendika*と呼ばれ、プロジェクト名は*Mistpark*）は、分散型のフェデレーションソーシャルネットワークです。 これは、Fediverseを開始した最初のソフトウェアの1つでした。

#### 機能と利点

- 《ステータスの更新》を投稿する
- 写真、アルバム
- ハッシュタグ
- プライバシー
- 軍事暗号化
- カレンダー
- さまざまな人々やコミュニティにさまざまな《プロファイル》を表示する
- 他のプロファイルとハッシュタグをフォローする
- さまざまなテーマとアドオン
- Diaspora、Mastodon、Pleroma、Hubzilla、WordPress、Nextcloud、Pixelfed、PeerTube、Twitterなどのユーザーと接続できます。

試してみたい場合は、[ここ](https://friendi.ca/#try)で利用可能なサーバーの1つを選択してください。 どのサーバーを選択するかは関係ありません。連邦内のすべての人と接続できます。

### Hubzilla

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/h/hubzilla-01.webp"
  link="images/h/hubzilla-01.webp"
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

**Hubzilla**は、同じ開発者[Mike Macgirvin](https://macgirvin.com/channel/mike)によって開始されたという点で*Friendica*に似ています。 Macgirvinはビジョンのある人であり、選択の自由、地方分権化、連合、および反検閲の強力な支持者および支持者です。 彼は*Hubzilla*を使用して、他の連邦プラットフォーム（*Zap*以外）が今日まで持っていない独自の機能を開発しました。**遊牧民のアイデンティティとクローン作成**です。

#### 遊牧民のアイデンティティとクローニングとは

遊牧民のアイデンティティは、オンラインアイデンティティの真の所有権を意味します。 Hubzillaを使用すると、サーバーにアカウントがなく、グリッド全体で持ち運べるIDを所有します。 ネットワーク障害や検閲に対する回復力のために複数のハブにまたがってチャネルのクローンを作成するか、データと接続を取得して、チャネルを1つのハブから別のハブに完全に移動することができます。[^c]

example.comにチャネルを作成し、example.netにクローンを作成できます。 これらは2つの異なるサーバー上にあるため、これらは2つの別個のアカウントであるように見えますが、実際には1つで同じです。 遊牧民のアイデンティティの基盤となるテクノロジーを理解しているプラットフォームは、両方を単一のチャネルとして扱います。example.net経由でログインすると、同じ通信と接続を受信し、返信を送信したり、新しい投稿/更新を作成したりすることができます。 example.comからログインしました。

機能に関しては、HubzillaはFriendicaとほぼ同じセットを共有していますが、コードが同じというわけではありません。 しかし、この部分は？ これは、開発者やサーバーオペレーターにとっては良いことです。ユーザーとしては、手元にあるので安心してください。 その上、遊牧民のアイデンティティは確かに他のすべてのプラットフォームが実装する必要がある素晴らしい機能ですよね？

[ここ](https://hubzilla.org/pubsites)にある利用可能なサーバーのいずれかでHubzillaチャネル（または必要に応じてアカウント）にサインアップできます。

[^c]: Hubzilla: [Nomadic identity and cloning](https://hubzilla.org//page/hubzilla/hubzilla-project)

### Zap

{{< image
  type="image"

  height="48%"
  width="48%"

  src="images/z/z/zap-01-logo.svg"
  link="images/z/z/zap-01-logo.svg"
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

**Zap**は、Facebookユーザーにとってなじみのある快適なエクスペリエンスを提供し、いくつかの追加機能と、今日のFediverseで利用可能な最高のプライバシーおよび乱用防止機能のいくつかを備えています。[^d]

[^d]: Zap: [Zap Fediverse Server, an ethical alternative](https://zotlabs.com/zap/)

#### 機能と利点

- グループ：パブリック、プライベート、およびモデレート。 これは、ほぼすべてのFedverseプラットフォームで機能します。
- イベント：カレンダーと出席; 自動タイムゾーン調整。 友達の誕生日の通知
- 権限：各機能に対するきめ細かい権限制御
- クラウドストレージ：ソーシャルネットワーキングアクセス/権限を備えた組み込みのネットワークファイルストレージ。
- エディター：マークダウン、html、bbcodeをサポート
- リスト：*サークル*または*アスペクト*と呼ばれることもあります
- フレンドズーム：接続の《近さ》の度合いを設定してから、フレンドズームを使用してダッシュボードストリームをフィルタリングし、親しい友人または全員のみを表示します。
- 遊牧民のプロトコル:(上記の*Hubzilla*の下の《遊牧民のアイデンティティ》を参照）

ジャンプしてオンラインソーシャルWebIDを作成する準備ができている場合は、[ここ](https://z.macgirvin.com/sites?project=zap)で任意のサーバーを選択してください。

### Misskey

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/m/misskey-01-hashtag.webp"
  link="images/m/misskey-01-hashtag.webp"
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

**Misskey**は分散型のマイクロブログプラットフォームです。 Fediverse内に存在し、他のソーシャルメディアプラットフォームと相互にリンクしています。[^e]日本の開発者である[しゅいろ（syuilo）](https://misskey.io/@syuilo)によって開始され、参加しました。 他の寄稿者による。 Misskeyは、連邦政府に関して日本で選択されているプラットフォームです。

[^e]: Misskey: [Let's start Misskey](https://join.misskey.page)

#### 機能と利点

- 投稿またはステータスの更新
- 反応
- さまざまなUIオプション
- ミスキードライブ
- チャット
- フォトギャラリー
- グループ
- ページ
- プライベートメッセージ
- リスト
- チャネル
- アンテナ
- ミスキーゲーム

あなたにぴったりのMisskeyコミュニティを見つけることができます[ここ](https://join.misskey.page/instances)。

### Pixelfed

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/p/pixelfed-01-trending.webp"
  link="images/p/pixelfed-01-trending.webp"
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

**Pixelfed**は、フェデレーションの一部である、プライバシーに重点を置いたフェデレーションの写真共有プラットフォームです。 今日のPixelfedのユーザーインターフェイスは、Instagramのファンに非常に精通している必要があります。つまり、Pixelfedを写真共有プラットフォームとして使用するのは簡単です。[^f]

[^f]: Pixelfed: [A free and ethical photo sharing platform](https://pixelfed.org)

#### 機能と利点

- 広告なし：タイムラインやどこにも広告はありません
- 時系列：タイムラインは適切に順序付けられており、アルゴリズムはありません
- 発見：新しいコンテンツとクリエイターを探す
- フィルタ：写真にオプションのフィルタを追加します
- フォトアルバム：一度に1つの投稿で写真を共有します
- プライバシー重視：サードパーティの分析や追跡は含まれていません
- 二要素認証：アカウントを保護する
- コンテンツの警告：写真やコメントが機密である可能性がある場合は自動検出され、自動的にぼかし/非表示になります
- コメントを無効にする：投稿ごとにコメントをオフにする機能
- ライセンス宣言：写真のライセンス情報を含める
- フォロワーとフォローカウントを非表示
- アカウントをミュートする
- プライベートアカウント
- プライベート投稿
- 限定公開の投稿：公開投稿ですが、グローバル公開タイムライン/ストリームには掲載されていません

[Pixelfedインスタンス](https://fedidb.org/software/pixelfed)に参加すると、今日から写真のフェディバースへのアップロードを開始できます。

### Mastodon

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/m/mastodon-01-dashboard.webp"
  link="images/m/mastodon-01-dashboard.webp"
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

**Mastodon**は、さまざまな組織や個人が運営する何千ものコミュニティのネットワークであり、シームレスなソーシャルメディアエクスペリエンスを提供します。[^g] Friendica、Hubzilla、Zap、Misskey、Pixelfed、PeerTubeなどの他のプラットフォームにも接続できます。 Write.as、およびソーシャルWeb標準であるActivityPub、分散型ソーシャルネットワーキングプロトコルに接続されているもの。

[^g]: Mastodon: [Social networking, back in your hands](https://joinmastodon.org)

#### 機能と利点

- 効果的な虐待防止ツール
- モデレーター
- 500文字以上
- 絵文字とカスタム絵文字
- ネタバレタグ
- コンテンツの警告
- ステータスの更新

Twitterを定期的に使用していて、そのフローが気に入っている場合は、Mastodonが最適なプラットフォームです。 [マストドンに参加](https://joinmastodon.org/communities)今日、連邦内のすべての人とつながりましょう。

### PeerTube

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/p/peertube-01-discover.webp"
  link="images/p/peertube-01-discover.webp"
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

*Framasoft*によって開発された**PeerTube**は、ビデオプラットフォームに代わる無料の分散型の代替手段であり、60,000人のユーザーが公開した40万本以上の動画を提供し、連邦全土から1,500万回以上視聴されています[^h]。

PeerTubeは、世界中のビデオを一元化する巨大なプラットフォームになることを意図したものではありません。 むしろ、それは相互接続された小さなビデオホスティング業者のネットワークです。 ユーザーは引き続き別のサーバーからホストされているビデオを視聴でき、自分でアップロードしたビデオは他のPeerTubeサーバーで見ることができます。

また、PeerTubeはフェディバースの一部であるため、フェディバースの誰もが自分のプラットフォームから直接PeerTubeがホストするビデオにコメントを残すことができます。

[^h]: PeerTube: [A decentralized and free/libre alternative to video broadcasting services](https://joinpeertube.org)

#### 機能と利点

- 他のプラットフォームからビデオをインポートする
- ライセンス情報
- ハッシュタグ
- チャネル
- 広告なし
- トラッカー無料
- 必要に応じて、ピアツーピア（P2P）プロトコルを使用してバイラルビデオをブロードキャストできます。
- 歴史
- サブスクリプション
- プレイリスト

あなたのビデオをアップロードして、無数の連邦市民に見られる準備はできていますか？ この[ページ](https://joinpeertube.org/instances#instances-list)で、ニーズに合った最適なサーバーを見つけてください。

## 通信プラットフォーム

### Keybase

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/k/keybase-01-chat.webp"
  link="images/k/keybase-01-chat.webp"
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

**Keybase**は、メッセージング、ファイル共有、ファイルホスティング、Webホスティング、ファイル暗号化、およびテキスト暗号化のための最も安全なプラットフォームおよびサービスです。 さらに、Keybaseは、オンラインアカウントとPGP鍵を確認する最も簡単な方法です。[^k]

チームごとに100GBのストレージを提供するKeybaseTeams。個人アカウントでファイルとWebサイトをホストすることを選択した場合、250GBのクラウドストレージを無料で利用できます。 gitの使用方法を知っている場合は、Keybase gitを使用して、このブログのように、ホスティングのソースファイルとして使用できます。

[^k]: Keybase: [End-to-end encryption for things that matter](https://keybase.io)

#### 機能と利点

- オンラインID検証
- エンドツーエンドの暗号化されたチャット：直接チャット、プライベートグループ、およびパブリックチャットルーム
- 個人用とチーム用の両方のファイル
- チームとサブチーム、それぞれが個別のエンドツーエンドの暗号化されたチャットチャネルを持っている
- サイトまたはキーベースホスティング
- Keybase git：個人用とチーム用。 あなたのウェブサイトをホストするために使用することもできます
- ウォレット：Stellar Lumens（XLM）を保管する
- ファイルとテキストを手動で暗号化、復号化、署名、および検証します。 次に例を示します。

  - テキスト暗号化（Keybaseを使用してこれを復号化します）

    > BEGIN KEYBASE SALTPACK ENCRYPTED MESSAGE. kiPgBwdlv6bV9N8 dSkCcFVY51RjYpI Yshtm8m8tsVuUbB OEJigEAr8jAHoBd 9WxEx4VzL44c8XR STsItCeQJqL215b 9XBDiMO6eT31J3h OhZDvSgMUN8FKy8 efbS6RyNWMAJ8G4 2o0mkh5z9hlJoW5 34X9TtZhFUpWwTd Iv3rsbS0IrxyCAJ hv9gEK69Vi1uuNP edgKdpxJyAStK9H tTuRrYEkgwZ74fB lQrzS17alDfXy36 4svbpvjNUVtR7Jt cRafaXbi3VWT1eY Loqpf9I2M4UfHFC 8jgkOJzqcPijs9w W9CJj4iJFKmHAp7 wJu6Kty2MIhbC0P MFagNkP32I233gT RUqb7R8lS57yhxb HrpUMABjpMwYcZA BXiEfCcA0H8Smxo xaC9p4NupSj2Thg OOfQUHT3mha8SjV WvHFB8TqZ1coqWP fHmt9IFfDlBVvxV CpMashM0MyodKzm Nd870prmcIJ2eYL ktekaOK0GP9uOTG Q0MYhoDwBbfcFLE 8sstqRcqm1vTRVg gTj8irjfEHwcY27 aTrNW6dRwIaypn8 irntZcJVZn9yn5c MlS0R4RabT4tSZh v2v9u7UOkPQBjsq ENaFlrNOCawEz6P atucVhR8oVfW5zd cd4MoEbME4Kg3Hj dLP82aqHeEW3AD6 MV3sDPVIHhouSVm dURfQCH4c39n7bq 5dTwb4tnkGhNsXA ZS0WbVLqwqQoiin dViQD1itO8C6yt0 q2fHYW8pj8F5HPJ vWtDQzokeh367hC HkE8x9NL91gG6oX 8pivGkxMY8K0hQe IJwII2ZlQ7dTKwu x. END KEYBASE SALTPACK ENCRYPTED MESSAGE.

  - テキスト署名（Keybaseで署名を確認してこのメッセージを書いたことを確認してください）

    > アミレイに、
    >
    > 私はただの男の子で、女の子の前に立って、彼女に彼を愛するように頼んでいます。
    >
    > あなたの秘密の崇拝者から、
    >
    > I'M YourOnly.One

    > BEGIN KEYBASE SALTPACK SIGNED MESSAGE. kXR7VktZdyH7rvq v5weRa0zkP4VNyC 8WftM9nW4fgPe6n Zl3jKJsRhCjvlTD OXqz3yNPCDbjnts ixxYFUcZO91b9wZ MRb58qv7PPi118B Y4iejcS2a4z0q5w 2EpVxKd7L9BsmEg qwEId1Xb8O5lO4c c2g50ZUkP3alV2n 3YZQC1EQx3jhcEk 8O8G8eceJexvYtI iQoYO48RliDzUqc UTD0xUndXx5Dwl6 bDReedDnKw0Fac6 a6hSpYcx2tkv54K zi7UkcDpJu770pb uO7Zz09tMwyg9px GEtXkU3UtMv77qJ nrwpCqBZ1x7PEYt QX8na3I4iAXbvNL LiL2r6n5I8auJeZ 4H6I5XQ6IG6erYg 97ycpItKF5BjBWz TYwfVylpPKkhaFu VusaIi87ZAVD6mo akeIVNXeRUYih1K yReT4PaQW1Ard6v 8elxT8LxOn. END KEYBASE SALTPACK SIGNED MESSAGE.

#### Keybaseを使い始める

- [キーベースアカウントを作成する方法](https://im.youronly.one/techmagus/create-keybase-2020160/)

- [キーベースを介してアカウントを確認する必要がある理由](https://im.youronly.one/techmagus/verify-account-keybase-2020161/)

### Matrix

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/m/matrix-01-element-client.webp"
  link="images/m/matrix-01-element-client.webp"
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

**Matrix**は、安全な分散型のリアルタイム通信プラットフォームです。 Matrixでの会話は、参加しているすべてのサーバーに複製され、単一の制御ポイントや障害はありません。 また、最新のエンドツーエンド暗号化を提供し、意図した受信者のみがメッセージを復号化できるようにすると同時に、予期しないデバイスが会話に追加された場合に警告を発します。[^i]

Matrixには、言及されたものよりもはるかに多くのものがありますが、これらの優れた機能は、開発者とサーバーホストにのみ関係します。 あなたの会社がコミュニケーションプラットフォームを探していて、*Matrix*についてもっと知りたい場合は、彼らの[公式ウェブサイト](https://matrix.org)にアクセスしてください。

[^i]: Matrix: [An open network for secure, decentralized communication](https://matrix.org)

#### 機能と利点

- Androidで利用可能なアプリ
- iOSで利用可能なアプリ
- Webクライアント
- Windows、Linux、およびMac用のデスクトップクライアント
- コマンドラインクライアント
- エンドツーエンド暗号化
- 他のネットワークへのブリッジ

Matrix [今日](https://matrix.org/docs/projects/try-matrix-now/)をお試しください！

### Session

{{< image
  type="image"

  height="80%"
  width="80%"

  src="images/s/session-01.webp"
  link="images/s/session-01.webp"
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

**セッション**は、機密性の高いメタデータを最小限に抑えるエンドツーエンドの暗号化されたメッセンジャーであり、絶対的なプライバシーとあらゆる形態の監視からの解放を望む人々のために設計および構築されています。[^j]

[^j]: Session: [Send Messages, Not Metadata](https://getsession.org)

#### 機能と利点

- 電話番号とメールアドレスはありません：セッションアカウントは完全に匿名です。
- データ侵害なし：セッションはデータを収集しないため、リークするものはありません。
- フットプリントなし：セッションのオニオンルーティングネットワークを介してメッセージを送信し、痕跡を残しません。
- 検閲に強い：障害の中心点がないため、セッションをシャットダウンするのが難しくなります。
- オープンソース：Sessionのコードには隠すものは何もありません。 誰でも表示、監査、および貢献できます。
- グループチャット：プライベートグループとオープングループ
- ボイスメッセージ
- 添付ファイル：暗号化されていないサービスにこれらのドキュメントをアップロードしないでください。 プライバシーを真剣に受け止めているネットワークを介して、すべてのファイル、画像、添付ファイルを送信します。

デスクトップまたは携帯電話で[セッションをダウンロードして使用](https://getsession.org/download)。

## 最後の言葉

上記のプラットフォームとサービスのリストが、バックアップ計画の作成を開始するのに十分すぎることを願っています。 Facebook、Instagram、Messenger、WhatsAppのアカウントを移行し、おそらく削除する必要があると多くの人が言うでしょうが、ここ**YourOnly.One**では、バックアッププラットフォームとサービスが必要であることを提案しているだけです。 Facebook、Instagram、Twitter、WhatsAppを引き続き使用できますが、今日の＃FacebookDown、＃InstagramDown、＃MessengerDown、＃WhatsAppDownの後に、代替またはセカンダリのプラットフォームとサービスが用意されていない場合は、後悔することになります。 *if*しかし**when**の場合、それは再び起こります。

最後になりましたが、最も重要なのは、データ、プラットフォーム、およびサービスの分散化、配布、およびフェデレーションを完全に受け入れるときです。 今日起こったことは、これがインターネットと私たちが依存するサービスが存在し、機能し続けることを保証するための唯一の論理的なステップであることを証明しました。

シャロームをお楽しみください！

---

{{< image
  type="imagecoverattrib"

  link="images/d/decentralisation-01.gif"
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

注意：Google翻訳
