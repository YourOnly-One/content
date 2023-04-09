+++
title = "Linklists Are Back"
description = "We are bringing back linklists and blogrolls!"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = 2021-12-19T14:14:41+08:00                                        # manually adjust to local timezone
lastmod = 2021-12-19T14:14:41+08:00                                        # manually adjust to local timezone

#aliases = [""]
slug = "linklists-are-back"
translationKey = "linklists-are-back-2021353"
relCanonical = "https://im.youronly.one/techmagus/linklists-are-back-2021353/"                                                   # the actual URL of the post; also used for disqus ID and url
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

In the early days of the World Wide Web (mid to late 90s) all the way to 2010 or 2012, linklists or blogrolls were not only popular but a standard part of webdesign. One fine morning it disappeared and no longer relevant. But is it really dead?

<!--more-->

{{% quotebox boxstyle="qbs_generic" qmarkstyle="qbm_doublequotationmark" boxcolour="qbc_blue-midnight" attribalign="txt_right" srctitle="The Small Website Discoverability Crisis" srclink="https://memex.marginalia.nu/log/19-website-discoverability-crisis.gmi" srcrel="noopener external nofollow" attribto="Marginalia" attriblink="https://memex.marginalia.nu" attribrel="noopener external nofollow" %}}
A proposal, dear reader: Create a list of bookmarks linking to websites you find interesting, and publish it for the world to see. You decide what constitutes "interesting".
{{% /quotebox %}}

## What is a linklist or blogroll?

A *linklist* or *blogroll* is a collection of recommend links a website owner or blogger collected and displays on the site's sidebar or in a dedicated page. It could be blog links of family and friends, or links to interesting websites.

Back in the early days of website building and blogging, socialising and creating a network of blogs was important. It was not because of search engine optimizations (SEO)—although later it became the focus—rather it was to help each other get discovered by visitors. One day everybody were creating their blogrolls, the next day it was all gone.

Websites were no longer "socially connected". Any connection between websites turned into a business or a marketing. A link to another website was primarily because it was cited in an article and not because one found it worthy to be discovered by their own readers.

That was then. Today, we are bringing it back!

## But why?

Since I started migrating my blogs from *WordPress* to *Hugo*, a linklist or blogroll has always been in my ToDo list. It is a way for me to recommended websites and bloggers I find worthy of constant mention instead of finding an article to cite. It is also a recommendation for the website itself and the author as compared to linking to a single article.

However, I kept on pushing it back. There are too many websites and bloggers I want to recommend, just thinking about the work in curating and maintaining the list is tiring already. Until now, I found a very good way and reason to do this in a small scale.

{{% quotebox boxstyle="qbs_generic" qmarkstyle="qbm_doublequotationmark" boxcolour="qbc_green" attribalign="txt_right" srctitle="The Small Website Discoverability Crisis" srclink="https://memex.marginalia.nu/log/19-website-discoverability-crisis.gmi" srcrel="noopener external nofollow" attribto="Marginalia" attriblink="https://memex.marginalia.nu" attribrel="noopener external nofollow" %}}
A proposal, dear reader: Create a list of bookmarks linking to websites you find interesting, and publish it for the world to see. You decide what constitutes "interesting".

The model is as recursive as it is simple. There is nothing preventing a list of bookmarks from linking to another list of bookmarks.

…

Looking through a sample of personal websites, very few of them has links to other personal websites. A hyperlink isn't a marriage proposal. It is enough to find some redeeming quality in a website to link to it. It costs nothing, and helps bring traffic to pages that you yourself think deserve it.

If we actually want these small websites to flourish as a healthy community, we need to promote each other much more than we do. It is advertisement, yes, but in earnest. I like it when other people link to my stuff. What sort of hypocrite would I then be if I only ever linked to my own websites?
{{% /quotebox %}}

<span class="unicode_emoji">👉🏽</span> And here is the [YourOnly.One Linklist](https://im.youronly.one/p/linklist/)! <span class="unicode_emoji">👈🏽</span>

(If we know each other and your blog is not listed, more likely than not it was because you are ranking in searches already. I might create a separate list for family and friends in the future and I'm hoping you will recommend me back.)

## FAQ

Q: Is there a penalty?

: No. By adding a website in your linklist or blogroll you are endorsing it, or to put it another way, you are recommending it. `rel=nofollow` is used only for links which you can not endorse such as but is not limited to: paid links, links in comments and forums, and yes, third-party theme footer credits (be sure to update those links).

: To add a link to *techmagus*:

  ```html
  <a href="https://im.youronly.one/techmagus/" rel="noopener external">techmagus</a>
  ```

: If you want to link to my linklist:

  ```html
  <a href="https://im.youronly.one/p/linklist/" rel="noopener external">YourOnly.One Linklist</a>
  ```

: It's that simple!

Q: I know what `rel=nofollow` is but what are `noopener` and `external`?

: I'll let the [Mozilla Developer Network](https://developer.mozilla.org) answer that.

: `rel=noopener`:

  : Instructs the browser to open the link without granting the new browsing context access to the document that opened it — by not setting the [Window.opener](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener) property on the opened window (it returns null).

  : This is especially useful when opening untrusted links, in order to ensure they cannot tamper with the originating document via the [Window.opener](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener) property (see [About rel=noopener](https://mathiasbynens.github.io/rel-noopener/) for more details), while still providing the Referer HTTP header (unless noreferrer is used as well).

  : Note that when noopener is used, nonempty target names other than *_top*, *_self*, and *_parent* are all treated like *_blank* in terms of deciding whether to open a new window/tab.[^a]

: `rel=external`:

  : Indicates that the hyperlink leads to a resource outside the site of the current page; that is, following the link will make the user leave the site.[^a]

[^a]: MDN Web Docs: [Link types](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types)

## Share yours

Have you created your own curated bookmark list or blogroll? Share your link in the comments below and I will also add you in [YourOnly.One Linklist](https://im.youronly.one/p/linklist/). It is all about sharing trusted links and interlinking our linklists.

Shalom!

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
