+++
title = "LANG属性"
description = "LANG属性は、Webサイトを設計する際の強力なコードです。 LANG属性を正しく使用する方法を紹介します。"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = 2009-06-21T01:20:37+09:00                                        # manually adjust to local timezone
lastmod = 2009-06-21T01:20:37+09:00                                        # manually adjust to local timezone

aliases = ["/ja/kb/webdev/lang-attribute-2009172"]
slug = "lang-attribute"
translationKey = "lang-attribute"
relCanonical = "https://im.youronly.one/techmagus/ja/kb/webdev/lang-attribute/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
disqus_identifier = "lang-attribute-2009172"                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["howto"]                                                   # taxonomy
keywords = ["lang", "language", "multilang", "multi-language", "how to", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
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
  name = "謝雪矢（ゆきや）"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"

+++

前回の投稿で、《バイバイン-フィリピン人の忘れられたヒスパニック以前の執筆》について話しました。 [Unicode Standard](https://unicode.org)のバージョン5.0で、ブヒッド文字、ハヌノオ文字、タグバヌワ文字とともに《フィリピン文字》グループに追加されました。 しかし、別の言語やスクリプトで書かれたコンテンツを適切に記述またはマークするにはどうすればよいでしょうか。

この投稿では、コンテンツの言語を正しく宣言する方法について説明します。これにより、翻訳ソフトウェアやヘルパーアプリケーション、およびこの頻繁に認められるHTML属性に依存するその他のテクノロジに慣れることができます。 私たちの画像に示されているように、誰もが使用されている書記を見ることができますが、デジタルの世界では、使用しているフォントを持っていない人がいます。 あなたと私が使用しているのと同じブラウザを使用していない人もいます。テキストのみのブラウザ、音声ブラウザ、点字ブラウザの可能性があります。

その場合、使用している言語とスクリプトでコンテンツに適切かつ正しくタグを付けることが適切です。 LANG属性をたくさん使用する準備をしてください。

<!--more-->

ウェブサイトを作成するときは、ウェブサイトで使用されている言語を適切に宣言することが重要です。 たとえば、私は自分のサイトに次のものを使用しています。

```html
<html lang="en-PH">
```

ASCIIの範囲を超える文字を使用する場合は特に、文字セットを宣言することも重要です。 これはどのように見えるかです：

```html
    <meta charset="UTF-8" />
```

すべてをまとめると、基本的なHTMLは次のようになります。

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

では、掘り下げてみましょう…

## *lang*属性

HTML lang属性は、宣言された要素内に含まれるコンテンツの言語を定義します。 コードは*subtag*と呼ばれ、私のフィリピン人の読者にとって、心配すべきサブタグの種類は、language-Script-REGIONの3つだけです。 完全な形式：language-extended_language-Script-REGION-variant-extension-privateuse。

以下の表を参照してください。
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
      <th style="min-width: 15%; width: 15%;">コード</th>
      <th>言語</th>
      <th>サブタグの配置</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>en</td>
      <td>（ジェネリック）英語</td>
      <td>language</td>
    </tr>
    <tr>
      <td>en-PH</td>
      <td>フィリピン英語</td>
      <td>language+REGION</td>
    </tr>
    <tr>
      <td>fil-Tglg</td>
      <td>バイバインのフィリピン人</td>
      <td>language+Script</td>
    </tr>
    <tr>
      <td>bik-cts-Tglg</td>
      <td>バイバインスクリプトのパンダン（北カタンドゥアネス）方言のビコラノ</td>
      <td>language+extended_language+Script</td>
    </tr>
    <tr>
      <td>phi-Tglg-tsg</td>
      <td>バイバイン文字で書かれたタウスグ語フィリピン語</td>
      <td>language+Script+variant</td>
    </tr>
  </tbody>
</table>
<p></p>

特定の言語のサブタグを見つけたい場合は、以前はさまざまなWebサイトと多数の公式コードリストを確認する必要がありました。 時間のかかる作業です（通常は一度だけ行う必要がありますが）。 さて、最新の公式サブタグは、[IANA言語サブタグレジストリ](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry)にあります。 これは、すべての有効なサブタグのユニバーサルソースになりました。

最新のリスト（この記事の執筆時点）によると、フィリピンに関連するサブタグは次のとおりです（何か見落とした場合は、以下にコメントを残してください）。

### 言語

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

### 領域

- Philippines
  - Type: region
  - Subtag: PH
  - Description: Philippines
  - Added: 2005-10-16

### スクリプトを書く

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

必要なサブタグができたので、フィリピンの言語とスクリプトの正しい `lang`値のコーディングを開始できます。 次の例を参照してください。

- あなたがフィリピンで成長して英語を学んだ場合、おそらくフィリピン専用の英語の単語を使用しているだけでなく、フィリピン英語でのみ教えられている厳格な言語規則に従っています。 これはあなたのウェブサイトの正しい `lang`値です：` lang= "en-PH" `
- タガログ語ではなくフィリピン語で書いている場合は、次のように使用します： `lang="fil"`
- フィリピン語ではなくタガログ語で書いている場合は、次を使用します： `lang="tl"`
- ビコラノの場合は、次を使用します： `lang="bik"`
- セブアノ語では、次を使用します： `lang="ceb"`
- ヒリガイノン語、これを使用してください： `lang="hil"`
- イロカノ語では、これを使用します： `lang="ilo"`
- パンガシナン語： `lang="pag"`
- パンパンガ語： `lang="pam"`
- ワライ語： `lang="war"`
- 対応する[ISO-639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php)コードがないフィリピンの言語の場合、一般的なサブタグ `lang="を使用する必要があります。 ファイ "`

次に、Baybayinスクリプトで何かを書きたい場合は、スクリプトサブタグ《Tglg》で正しく囲む必要があります。 形式は次のとおりです。言語-スクリプト、次のようになります。

- バイバインスクリプトを使用してフィリピン語とタガログ語で書く場合は、次を使用します： `lang="fil-Tglg"`
- ビコラノ語だがバイバイン語のスクリプト： `lang="bik-Tglg"`
- バイバインスクリプトを使用したセブアノ語： `lang="ceb-Tglg"`
- ISO-639-2サブタグのない他のすべてのフィリピン語は、次を使用する必要があります： `lang="phi-Tglg"`

<del datetime="2021-09-24T18:32:17+08:00">`lang="tl-Tglg"`サブタグコードがないのはなぜですか？ *Suppress-Script：Latn*のため、前に示したようにIANA言語サブタグレジストリにあります。 私がそれを正しく理解していれば、それは公式の基準によるタガログ語が常にラテン文字で書かれるべきであることを意味します。 その場合、lang="tl-Tglg"が間違っており、アプリケーションにはそれを無視するか、《Tglg》スクリプトサブタグを削除するオプションがあると思います。 この場合、《fil-Tglg》を使用するだけです。</del>

## ISO-639-3言語

[方言とマクロランゲージ](https://web.archive.org/web/20130218160105///www.sil.org:80/iso639-3/macrolanguages.asp)をターゲットにする場合に学習する必要のある別のサブタグがあります。 ISO規格[ISO-639-3](https://web.archive.org/web/20130217113439///www.sil.org:80/iso639-3/codes.asp？)からリストを見つけることができます。 。 例としてビコラノを使用してみましょう。 使用する形式は、language-extended_language-Scriptです。

- 中央ビコラノ語で書いている場合は、次を使用します： `lang="bik-bcl"`
- アルバイビコール語/ブヒダラガ語で書く場合： `lang="bik-bhk"`
- バイバインスクリプトを使用してイリガビコラノにいる場合： `lang="bik-bto-Tglg"`
- バイバインスクリプトを使用してパンダン（北カタンドゥアネス）にいる場合： `lang="bik-cts-Tglg"`

言語-***extended_language***-スクリプトは、この記事の時点ではまだ実装されていません。 lang属性の基礎は、*extended_language*を含むように更新されると、常に[IANA言語サブタグレジストリ](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry)になります。 その後、必要に応じて使用を開始できます。

### *phi*言語サブタグ

次に、言語にISO-639-3コードがあり、ISO-639-2の言語コード《phi》の下またはその一部である場合は、*phi*サブタグが使用されます。 このサブタグコードは**集合言語**と見なされます。 良い例は次のとおりです。

- キナライア語-言語： `lang="phi-krj"`
- マギンダナオ語： `lang="phi-mdh"`
- バイバインスクリプトで書かれたマラナオ語： `lang="phi-Tglg-mrw"`
- バイバインスクリプトで書かれたタウスグ語： `lang="phi-Tglg-tsg"`

お気づきかもしれませんが、私が使用した形式は*language-Script-variant*であり、*language-extended_language-Script*ではありませんでした。 私の推論は単純です-*phi*言語コードは実際には言語ではなく、このバージョンのISOでは**見つからない**他のすべてのフィリピン言語のISO-639-2では《集合》言語エントリと正確に呼ばれます 言語標準。 これを*bik*言語コードと比較すると、ISO-639-2とISO-639-3の両方で《マクロ言語》として明確にマークされています。

さらに、[World Wide Web Consortium](https://www.w3.org/International/articles/language-tags/)またはW3Cによると、マクロ言語の**ダイアレクト**が検討されます/すぐに作成する必要があります**言語サブタグの後**。 つまり、ISO-639-2コードがマクロ言語と見なされる場合は、 `lang="bik-cts-Tglg"`のような*extended_language*サブタグの位置を使用する必要があります。 マクロランゲージとして定義されていない場合は、 `lang="phi-Tglg-tsg"`の場合と同様に、*バリアント*サブタグの位置を使用する必要があります。

## 例、例、その他の例…

あなたのウェブサイトが主にイリガに関するものであり、あなたがあなた自身の言語で書いているなら、あなたはそれに応じてあなたのウェブサイトのヘッダーファイルを調整するべきです：

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

バイバインで《ハッピー父の日》を書きたい場合は、次のようにします。

```html
  <bdi lang="fil-Tglg">ᜋᜎᜒᜄᜌᜅ᜔ ᜀᜍᜏ᜔ ᜈᜅ᜔ ᜋᜅ ᜀᜋ</bdi>
```

単純？ いいね！ 言語タグを作成するときは、できるだけシンプルで短くすることを忘れないでください。 `lang="bik-bcl"`のように具体的にする必要がない場合は、そうしないでください。 単に `lang="bik"`を使用してください。 これは特にブログに当てはまります。 したがって、ブログがフィリピン語（タガログ語ではない！）である場合は、次を使用します。

```html
<html lang="fil">
```

必要な場合、またはサイトが主にその特定のオーディエンスや地域に対応している場合にのみ具体的にしてください。 さらに、他の言語やスクリプトを使用する場合は（おそらく使用するでしょう）、上記のBaybayinの例で示したように、常にspanまたはdiv要素で囲みます。

簡単？ はい、そうです。 慣れるまでには時間がかかりますが、最初は混乱します。 しかし、最終的にはコツをつかむでしょう。 続けて今すぐWebサイトを更新し、正しい言語とスクリプトでコンテンツをマークする練習を始めてください。

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

注意：Google翻訳
