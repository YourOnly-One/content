+++
title = "Browser Wars III: Blink vs Gecko Quantum"
description = "Browser Wars 3 is not about Chromium and Firefox. The third Browser Wars is about the war between Blink and Gecko Quantum."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

date = "2018-12-10T06:54:23+08:00"                                        # manually adjust to local timezone
lastmod = "2018-12-10T06:54:23+08:00"                                        # manually adjust to local timezone

aliases = ["/2018/12/browser-wars-3-blink-gecko-quantum.html"]
slug = "browser-wars-3-blink-gecko"
translationKey = "browser-wars-3-blink-gecko-2018344"
relCanonical = "https://im.youronly.one/techmagus/browser-wars-3-blink-gecko-2018344/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["literature"]                                                   # taxonomy
keywords = ["browsers", "browser wars", "blink", "gecko", "chromium", "google", "chrome", "mozilla", "firefox", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
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
  name = "ᜌᜓᜃᜒ (Yuki | 雪亮)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

The recent announcement by **Microsoft** giving up on their *EdgeHTML* browser engine as well as their *Microsoft Edge* browser frontend marks the end of the **Browser Wars 2.0**. Their revelation that their next flagship browser will be Chromium-based and thus powered by the Blink browser engine, signals the beginning of **Browser Wars III** a war to control the Internet through browser engines.

<!--more-->

To understand **Browser Wars III** we need to realise that there are two fronts in this new war: the ***Browser Frontend*** and the ***Browser Engine***. Allow me to differentiate these two fronts.

## Browser Wars III Front: Browser Frontend

A browser frontend is simply the browser that users see. In this case, we have *Chromium* and **Mozilla**'s *Firefox [Quantum]*. Before there was a Chromium browser (the frontend and the engine), the most forked browser was Firefox. Some of the most popular Firefox-based projects are *[Pale Moon](https://www.palemoon.org)* (also forked the *Gecko* engine into *Goanna*), *[Waterfox](https://www.waterfoxproject.org)*, **Comodo** *IceDragon*, *[Tor Browser](https://www.torproject.org/projects/torbrowser.html.en)*, and the original *Flock* browser.

When Chromium arrived in the scene, it slowly gained converts. Flock migrated from being a Firefox-based browser to a Chromium-based browser bringing with them their loyal users (much later though, Flock development has ended). **Opera Software**, the company behind the *Opera Browser*, ended development of their browser frontend and its *Presto* browser engine. From there, they created a new Chromium-based Opera! Exactly what Microsoft has announced they will be doing too.

If that was not enough, fans of the Opera Browser also created their own browser called *[Otter Browser](https://otter-browser.org)* and *[Vivaldi](https://vivaldi.com)* (which happens to be far better than the new Chromium-based Opera Browser).

Other Chromium-based browsers are: ***[Yandex Browser](https://browser.yandex.com)***; **Comodo** *Dragon*; *Brave*; *Epic Browser*; and *Torch*, to mention a few. No one is choosing Firefox any longer!

This brings us to the …

## Browser Wars III Front: Browser Engine

The browser engine part of the Browser Wars III is the most important and largely ignored in the past two Browser Wars. Today, articles are interchanging Chromium and Blink. However, Chromium is a browser frontend while Blink is a browser engine.

### Not interchangeable

The frontend and engine are not interchangeable. A developer can …

- … use an existing browser frontend but use a different browser engine
- … use an existing browser frontend but add additional browser engines on top of the default
- … use a browser engine but without the browser frontend (usually seen in software with a built-in browsing feature)
- … use a browser engine but develop a browser frontend from scratch

Gecko, the browser engine behind Firefox, had seen a lot of products with the use-cases mentioned above. Blink's use mainly concentrated on Chromium; after all, why build a browser frontend from scratch when there is already Chromium? Why add a built-in browsing feature when one can use Chromium directly as if it's part of the software or app in both the desktop and mobile platforms? (I came across software where its browsing experience was locked into *Chrome* itself even if your default browser was set to Firefox. Chrome is a Chromium-based browser by **Google**.)

Yet, it does not mean Chromium and Blink are interchangeable, especially when …

### It's the browser engine that counts

When frontend developers design software and websites, they test it against different browsers. The reality is they are testing it against the engine powering these browsers. As long as a product or website has been tested in any browsers powered by Blink, Gecko, and *WebKit* (*Safari* and all **Apple** products), a developer can generally interpret it as the same in any other browsers powered by the same engine (to reiterate, *generally*, there are other factors involved that may change the result even if the engine and its version is the same). There is no need to install Chromium, Chrome, Opera, Vivaldi, Brave, and Yandex, these are all powered by Blink through Chromium.

With everyone choosing Chromium as their underlying browser frontend (developers) or daily browser (end-users) we are heading once again to the days of "*this website works best with*" and "*please download a Blink-powered browser like Google Chrome, Opera, Vivaldi, Yandex, and Brave to continue to this website*". In addition, developers and companies who only cares to get a website running and money flowing as fast as possible, will only do tests against Blink now that it has the largest share of the market… today.

It puts an imbalance in the Internet. The Chromium developers, who are also the developers behind Blink, now have more power over how the Internet should be displayed. Not that they will abuse it, hopefully, but there were, are, and will always be decisions within the **W3C Consortium** (the group that sets Web Standards) based on numbers or how a particular element or attribute should work; or if a new web feature should follow Chromium's version or Mozilla's interpretation.

## Conclusion

Chromium is just the surface. The browser engine is the real danger here. Chromium is simply the flagship browser of Blink. Since most do not want to start a browser from scratch, they obviously decided to use Chromium and tweaked it to their desired look and added their own features. But no one is stopping anyone from building a browser frontend from scratch and use Blink as their browser engine, Chromium have less count while Blink has a higher count.

It does not matter which browser frontend is the most popular because "*this site works best on*" and "*this website was tested fully on*" is all about the browser engine. It is about Blink, Gecko, WebKit, Goanna, and *KHTML*.

Use Firefox Quantum, yes, but if you do not like Firefox for whatever reason, then use a browser powered by the Gecko Quantum engine. A Chromium-based browser is not the only alternative, there are Firefox-based browsers too. If you are a frontend developer, test your website projects on Gecko Quantum powered browsers too. Let us not put the Internet in danger by letting one particular browser engine have a major gap and dominance in the market.

From my personal experience, Gecko has always been way ahead when it comes to implementing the W3C recommended specifications, **always**. There are also bugs in Chromium that are always ignored or were repeatedly closed as "not a bug" and/or "working as intended", for example, in its font fallback mechanism which is affecting some [Asian] scripts but is working perfectly in Gecko-powered browsers!

One final thought. There are two Asian browsers with three browser engines (Trident, Gecko, and Blink): IE-based *[Avant Browser](http://www.avantbrowser.com)* by a Chinese developer and IE-based *[Lunascape](https://www.lunascape.tv)* by a Japanese developer. Yes, there are multi-engine browsers (and extensions in the case of Firefox).

This Browser Wars III clearly is about the browser engines Blink and Gecko, the browser frontends that is Chromium and Firefox are only secondary, we just see them mentioned more because the average Joe and Jane are only familiar with those "names".

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
