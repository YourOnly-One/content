+++
title = "Blogrollが帰ってきた"
description = "リンクリストとブログロールを復活させます！"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = 2021-12-19T15:14:41+09:00                                        # manually adjust to local timezone
lastmod = 2021-12-19T15:14:41+09:00                                        # manually adjust to local timezone

#aliases = [""]
slug = "linklists-are-back"
translationKey = "linklists-are-back-2021353"
relCanonical = "https://im.youronly.one/techmagus/ja/linklists-are-back-2021353/"                                                   # the actual URL of the post; also used for disqus ID and url
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
  name = "ᜌᜓᜃᜒ (雪亮 | 스노 | Yuki)"
  url = "https://im.youronly.one/yuki/"
  avatar = "https://rsc.youronly.one/img/y/Yuki_flag-square-300x.webp"
  #rel = "noopener external nofollow"
+++

ワールドワイドウェブの初期（90年代半ばから後半）から2010年または2012年にかけて、リンクリストまたはブログロールは人気があっただけでなく、ウェブデザインの標準的な部分でした。 ある晴れた朝、それは消えて、もはや関係がなくなりました。 しかし、それは本当に死んでいますか？

<!--more-->

{{% quotebox boxstyle="qbs_generic" qmarkstyle="qbm_doublequotationmark" boxcolour="qbc_midnightblue" attribalign="txt_right" srctitle="The Small Website Discoverability Crisis" srclink="https://memex.marginalia.nu/log/19-website-discoverability-crisis.gmi" srcrel="noopener external nofollow" attribto="Marginalia" attriblink="https://memex.marginalia.nu" attribrel="noopener external nofollow" %}}
A proposal, dear reader: Create a list of bookmarks linking to websites you find interesting, and publish it for the world to see. You decide what constitutes "interesting".
{{% /quotebox %}}

## リンクリストまたはブログロールとは何ですか？

*リンクリスト*または*ブログロール*は、ウェブサイトの所有者またはブロガーが収集した推奨リンクのコレクションであり、サイトのサイドバーまたは専用ページに表示されます。 家族や友人のブログリンク、または興味深いWebサイトへのリンクである可能性があります。

ウェブサイトの構築とブログの初期の頃には、ブログのネットワークをソーシャル化して作成することが重要でした。 それは、検索エンジン最適化（SEO）のせいではなく、後で焦点になりましたが、訪問者がお互いを見つけられるようにするためでした。 ある日、誰もがブログロールを作成していましたが、翌日はすべてなくなりました。

ウェブサイトはもはや《社会的に接続》されていませんでした。 ウェブサイト間の接続は、ビジネスまたはマーケティングに変わりました。 別のウェブサイトへのリンクは、主に記事で引用されたためであり、自分の読者が発見する価値があると判断したためではありません。

その時でした。 今日、私たちはそれを持ち帰ります！

## しかし、なぜ？

ブログを*WordPress*から*Hugo*に移行し始めて以来、リンクリストまたはブログロールは常にToDoリストに含まれています。 それは私が引用する記事を見つける代わりに私が絶えず言及する価値があると思う推薦されたウェブサイトとブロガーに私のための方法です。 また、単一の記事にリンクする場合と比較して、Webサイト自体と作成者への推奨事項でもあります。

しかし、私はそれを押し戻し続けました。 私がお勧めしたいウェブサイトやブロガーが多すぎます。リストのキュレーションと維持の作業について考えるだけでも、すでに疲れています。 今まで、私はこれを小規模で行うための非常に良い方法と理由を見つけました。

{{% quotebox boxstyle="qbs_generic" qmarkstyle="qbm_doublequotationmark" boxcolour="qbc_green" attribalign="txt_right" srctitle="The Small Website Discoverability Crisis" srclink="https://memex.marginalia.nu/log/19-website-discoverability-crisis.gmi" srcrel="noopener external nofollow" attribto="Marginalia" attriblink="https://memex.marginalia.nu" attribrel="noopener external nofollow" %}}
A proposal, dear reader: Create a list of bookmarks linking to websites you find interesting, and publish it for the world to see. You decide what constitutes "interesting".

The model is as recursive as it is simple. There is nothing preventing a list of bookmarks from linking to another list of bookmarks.

…

Looking through a sample of personal websites, very few of them has links to other personal websites. A hyperlink isn't a marriage proposal. It is enough to find some redeeming quality in a website to link to it. It costs nothing, and helps bring traffic to pages that you yourself think deserve it.

If we actually want these small websites to flourish as a healthy community, we need to promote each other much more than we do. It is advertisement, yes, but in earnest. I like it when other people link to my stuff. What sort of hypocrite would I then be if I only ever linked to my own websites?
{{% /quotebox %}}

<span class="unicode_emoji">👉🏽</span> そして、これが[YourOnly.Oneリンクリスト](https://im.youronly.one/p/linklist/)です！ <span class="unicode_emoji">👈🏽</span>

（私たちがお互いを知っていて、あなたのブログがリストされていない場合は、あなたがすでに検索でランク付けされているためである可能性が高いです。将来、家族や友人のために別のリストを作成する可能性があります。 。）

## よくある質問

質問：ペナルティはありますか？

: いいえ。リンクリストまたはブログロールにWebサイトを追加することで、それを承認します。言い換えると、推奨します。 `rel=nofollow`は、有料リンク、コメントやフォーラムのリンク、サードパーティのテーマフッタークレジットなど、承認できないリンクにのみ使用されます（これらのリンクは必ず更新してください）。

: *ハイテク マギ*へのリンクを追加するには：

  ```html
  <a href="https://im.youronly.one/techmagus/ja/" rel="noopener external">ハイテク マギ</a>
  ```

: 私のブログロールにリンクしたい場合：

  ```html
  <a href="https://im.youronly.one/p/linklist/" rel="noopener external">YourOnly.One ブログロール</a>
  ```

: とても簡単です！

質問： `rel=nofollow`とは何か知っていますが、`noopener`と `external`とは何ですか？

: [Mozilla Developer Network](https://developer.mozilla.org)に答えさせます。

: `rel=noopener`:

  : リンクを新しい閲覧コンテキストで開き、リンク元の文書へアクセスできないようにすることをブラウザーに指示します。つまり、新たに開いたウィンドウで [Window.opener](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener) プロパティを設定しません（null を返します）。

  : これは信頼できないリンクを開く際、 [Window.opener](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener) プロパティでリンク元の文書を変更できないようにするために特に役に立つリンク種別です（詳しくは [About rel=noopener](https://mathiasbynens.github.io/rel-noopener/) を参照してください）。ただし、 Referer HTTP ヘッダーは（noreferrer を使用しない限り）提供します。

  : **注**: noopener を使用した場合、ターゲット名に *_top*, *_self*, *_parent* 以外の空でない名前を使用すると、新しいウィンドウやタブを開くかどうかの判断において、すべて *_blank* と同様に扱われます。[^a]

: `rel=external`:

  : ページが存在するサイトの外部にあるリソースへのハイパーリンクであることを示します。つまり、現在のサイトから離れるリンクです。[^a]

[^a]: MDN Web Docs: [リンク種別](https://developer.mozilla.org/ja/docs/Web/HTML/Link_types)

## あなたのものを共有してください

独自の厳選されたブックマークリストまたはブログロールを作成しましたか？ 以下のコメントであなたのリンクを共有してください。[YourOnly.One ブログロール](https://im.youronly.one/p/linklist/)にもあなたを追加します。 信頼できるリンクを共有し、リンクリストを相互リンクすることがすべてです。

シャローム！

---

{{< image
  type="imagecoverattrib"

  isrepresentativeofpage=true

  link="images/l/linklist-01.png"
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

注意：Google翻訳
