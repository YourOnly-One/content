+++
title = "Browser Wars III：Blink vs Gecko Quantum"
description = "Browser Wars 3は、ChromiumとFirefoxに関するものではありません。 3番目のブラウザ戦争はBlinkとGeckoQuantumの間の戦争についてです。"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = "2018-12-10T07:54:23+09:00"                                        # manually adjust to local timezone
lastmod = "2018-12-10T07:54:23+09:00"                                        # manually adjust to local timezone

#aliases = [""]
slug = "browser-wars-3-blink-gecko"
translationKey = "browser-wars-3-blink-gecko-2018344"
relCanonical = "https://im.youronly.one/techmagus/ja/browser-wars-3-blink-gecko-2018344/"                                                   # the actual URL of the post; also used for disqus ID and url
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

**Microsoft**による最近の発表は*EdgeHTML*ブラウザエンジンと*Microsoft Edge*ブラウザフロントエンドをあきらめ、**Browser Wars 2.0**の終わりを示しています。 次の主力ブラウザがChromiumベースであり、Blinkブラウザエンジンを搭載するという彼らの啓示は、ブラウザエンジンを介してインターネットを制御する戦争の始まりを示しています。

<!--more-->

**Browser Wars III**を理解するには、この新しい戦争には***Browser Frontend***と***Browser Engine***の2つのフロントがあることを理解する必要があります。 これら2つの面を区別させてください。

## ブラウザ戦争IIIフロント：ブラウザフロントエンド

ブラウザフロントエンドは、単にユーザーに表示されるブラウザです。 この場合、*Chromium*と**Mozilla**の*Firefox [Quantum]*があります。 Chromiumブラウザ（フロントエンドとエンジン）が登場する前は、最もフォークされたブラウザはFirefoxでした。 最も人気のあるFirefoxベースのプロジェクトには、*[Pale Moon](https://www.palemoon.org)*(*Gecko*エンジンを*Goanna*にフォークしたもの）、*[Waterfox](https://www.waterfoxproject.org)*、**Comodo** *IceDragon*、*[Tor Browser](https://www.torproject.org/projects/torbrowser.html.en)*、および元の*Flock*ブラウザー 。

Chromiumが現場に到着すると、ゆっくりと改宗者を獲得しました。 Flockは、FirefoxベースのブラウザーからChromiumベースのブラウザーに移行し、忠実なユーザーを連れてきました（ただし、Flockの開発は終了しました）。 *Opera Browser*の背後にある会社である**Opera Software**は、ブラウザフロントエンドとその*Presto*ブラウザエンジンの開発を終了しました。 そこから、彼らは新しいChromiumベースのOperaを作成しました！ まさにマイクロソフトが発表したことは、彼らもやることになるでしょう。

それだけでは不十分な場合、OperaBrowserのファンは *[Otter Browser](https://otter-browser.org)* および *[Vivaldi](https://vivaldi.com)*（ これはたまたま新しいChromiumベースのOperaBrowserよりもはるかに優れています）。

その他のChromiumベースのブラウザは次のとおりです。***[Yandexブラウザ](https://browser.yandex.com)***; **コモド** *ドラゴン*; *勇敢*; *エピックブラウザ*; と*トーチ*、いくつか言及します。 誰もFirefoxを選択しなくなりました！

これは私たちを…にもたらします

## ブラウザ戦争IIIフロント：ブラウザエンジン {#browser-wars-iii-front-browser-engine}

Browser Wars IIIのブラウザエンジン部分は最も重要であり、過去2回のBrowserWarsではほとんど無視されていました。 今日、記事はChromiumとBlinkを交換しています。 ただし、Chromiumはブラウザのフロントエンドであり、Blinkはブラウザエンジンです。

### 互換性がありません

フロントエンドとエンジンは互換性がありません。 開発者は…

- …既存のブラウザフロントエンドを使用しますが、別のブラウザエンジンを使用します
- …既存のブラウザフロントエンドを使用しますが、デフォルトに加えてブラウザエンジンを追加します
- …ブラウザエンジンを使用しますが、ブラウザフロントエンドは使用しません（通常、ブラウジング機能が組み込まれたソフトウェアで見られます）
- …ブラウザエンジンを使用しますが、ブラウザのフロントエンドを最初から開発します

Firefoxの背後にあるブラウザエンジンであるGeckoは、上記のユースケースを持つ多くの製品を見てきました。 Blinkの使用は主にChromiumに集中しています。 結局のところ、Chromiumがすでに存在するのに、なぜブラウザーのフロントエンドを最初から構築するのでしょうか。 デスクトップとモバイルの両方のプラットフォームでソフトウェアまたはアプリの一部であるかのようにChromiumを直接使用できるのに、なぜ組み込みのブラウジング機能を追加するのですか？ （デフォルトのブラウザがFirefoxに設定されていても、ブラウジングエクスペリエンスが*Chrome*自体にロックされているソフトウェアに出くわしました。Chromeは**Google**によるChromiumベースのブラウザです。）

それでも、特に…の場合、ChromiumとBlinkが交換可能であることを意味するわけではありません。

### 重要なのはブラウザエンジンです

フロントエンド開発者がソフトウェアとWebサイトを設計するとき、彼らはさまざまなブラウザーに対してそれをテストします。 現実には、彼らはこれらのブラウザに電力を供給するエンジンに対してそれをテストしています。 製品またはWebサイトが、Blink、Gecko、および*WebKit*（*Safari*およびすべての**Apple**製品）を搭載したブラウザーでテストされている限り、開発者は通常、他のブラウザーでも同じように解釈できます。 同じエンジンを搭載しています（繰り返しになりますが、*一般的に*、エンジンとそのバージョンが同じであっても、結果を変更する可能性のある他の要因が関係しています）。 Chromium、Chrome、Opera、Vivaldi、Brave、Yandexをインストールする必要はありません。これらはすべて、Chromiumを介してBlinkを利用しています。

基盤となるブラウザフロントエンド（開発者）または日常のブラウザ（エンドユーザー）としてChromiumを選択しているすべての人が、《*このウェブサイトは最適に動作します*》および《*GoogleのようなBlink搭載ブラウザをダウンロードしてください》の時代に再び向かっています。 Chrome、Opera、Vivaldi、Yandex、Braveは、このWebサイトに引き続きアクセスします*」。 さらに、ウェブサイトを稼働させ、できるだけ早くお金を流すことだけを考えている開発者や企業は、市場で最大のシェアを獲得している今、Blinkに対してのみテストを行います…今日。

それはインターネットに不均衡をもたらします。 Blinkの開発者でもあるChromium開発者は、インターネットの表示方法についてより強力になりました。 うまくいけば、彼らがそれを悪用するわけではありませんが、**W3Cコンソーシアム**（Web標準を設定するグループ）内で、数字や特定の要素や属性がどのように機能するかに基づいて決定があり、常にあります。 または、新しいWeb機能がChromiumのバージョンまたはMozillaの解釈に従う必要があるかどうか。

## 結論

クロムは表面にすぎません。 ここではブラウザエンジンが本当の危険です。 Chromiumは、Blinkの主力ブラウザにすぎません。 ほとんどの人はブラウザを最初から起動したくないので、明らかにChromiumを使用することに決め、希望の外観に調整して独自の機能を追加しました。 しかし、誰もがブラウザフロントエンドを最初から構築し、ブラウザエンジンとしてBlinkを使用することを阻止しているわけではありません。Chromiumの数は少なく、Blinkの数は多くなっています。

《 *このサイトは*で最適に動作します*》と《*このウェブサイトは完全にテストされました* 》はすべてブラウザエンジンに関するものであるため、どのブラウザフロントエンドが最も人気があるかは関係ありません。 これは、Blink、Gecko、WebKit、Goanna、および KHTML に関するものです。

はい、Firefox Quantumを使用しますが、何らかの理由でFirefoxが気に入らない場合は、GeckoQuantumエンジンを搭載したブラウザを使用してください。 Chromiumベースのブラウザだけが代替手段ではなく、Firefoxベースのブラウザもあります。 フロントエンド開発者の場合は、GeckoQuantumを搭載したブラウザーでもWebサイトプロジェクトをテストしてください。 ある特定のブラウザエンジンに市場で大きなギャップと優位性を持たせることで、インターネットを危険にさらさないようにしましょう。

私の個人的な経験から、Geckoは、W3C推奨仕様の実装に関して、**常に**常に先を行ってきました。 Chromiumには、常に無視されるか、《バグではない》および/または《意図したとおりに機能する》として繰り返し閉じられるバグもあります。たとえば、一部の[アジア]スクリプトに影響を与えているが、 Geckoを搭載したブラウザ！

最後に1つ考えます。 3つのブラウザエンジン（Trident、Gecko、Blink）を備えた2つのアジアのブラウザがあります。中国の開発者によるIEベースの *[Avant Browser](http://www.avantbrowser.com)* とIEベースの *[Lunascape](https://www.lunascape.tv)* 日本の開発者による。 はい、マルチエンジンブラウザ（およびFirefoxの場合は拡張機能）があります。

このBrowserWars IIIは、明らかにブラウザエンジンのBlinkとGeckoに関するものであり、ChromiumとFirefoxであるブラウザフロントエンドはセカンダリにすぎません。平均的なJoeとJaneはこれらの《名前》にしか精通していないため、さらに言及されています。

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
  attribrel="noopener external"

  cc0country="Philippines"
  cc0countrycode="PH"
  cc0countryurl="https://en.wikipedia.org/wiki/Philippines"
>}}

---

注意：Google翻訳
