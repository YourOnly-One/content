+++
title = "How-To implement cross-browser @font-face support"
description = "Do you want to make your site's font to show up the same across browsers and platforms? Use @font-face! Let me show you how."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

# DATE checked and correct

publishdate = 2010-01-22T14:55:48+08:00                                        # manually adjust to local timezone
lastmod = 2010-01-22T14:55:48+08:00                                        # manually adjust to local timezone

aliases = ["/2010/01/how-to-implement-cross-browser-font.html"]
slug = "css-font-face-support"
translationKey = "css-font-face-support-201022"
relCanonical = "https://im.youronly.one/techmagus/kb/webdev/css-font-face-support-201022/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["howto"]                                                   # taxonomy
keywords = ["how to", "css", "font-face", "webfonts", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["css"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://3.bp.blogspot.com/-tmNYWbX20wY/XqLEfgbdjtI/AAAAAAAAhXA/JI64YoxA9Ok2jchMsBEpq1VY8RQ2mj63QCPcBGAYYCw/s1600/Web-01.jpg"]                                                       # used by og:images, etc.; first image is cover image

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (雪亮 | 스노 | Yuki)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

*Firefox* 3.6 "Final" was released today and one of the major addition is the support for the *Web Open Font Format* or "WOFF". The result of a collaboration between the font designers [Erik van Blokland](https://www.letterror.com) and [Tal Leming](https://talleming.com) with help from Mozilla's Jonathan Kew.

<!--more-->

What is it for? How can you use it? By using the CSS2 **@font-face** (yes CSS2 not CSS3). This new format is promising because of the large number of support from the font creators and font foundries. <del>Hopefully this will be the first font format that Microsoft® will accept for Internet Explorer browser other than their existing *Embedded OpenType* or "EOT".</del>

<del>If IE9 supports WOFF, then this format will be the first cross-browser @font-face/webfont format. There is no question when it comes to Chromium/Chrome, Opera, and Safari, the problem with cross-browser technology is always with MSIE.</del>

**Update**: Microsoft added WOFF support in Internet Explorer 9 Platform Preview 3.

So how can you start using WOFF? Just follow these simple steps:

1. Search for your font of choice
1. Check the license of your font if it is allowed to be used in a website (sometimes called website embedding). I strongly suggest to contact the font creator/foundry and clarify the matter to them.
    - @font-face fonts or *webfont*s use "open"/"share"/"freedom" type licenses, examples are:
      - [OpenFont License](https://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&amp;item_id=OFL&amp;_sc=1)
      - [Creative Commons](https://creativecommons.org)
      - [GNU/GPL](https://www.gnu.org/licenses/gpl-3.0.html)
      - [Apache License](https://opensource.org/licenses/apache2.0.php)
    - If you can not find any, check out [Fonts available for @font-face embedding](https://web.archive.org/web/20141128120836/https://webfonts.info/resources/fonts-available-for-@fontface-embedding).
1. Go to FontSquirrel's [@font-face generator](https://www.fontsquirrel.com/tools/webfont-generator). The tool is self-explanatory.
1. Then click the "Download Your Kit" button and open the zip file.
1. You should have the following files (assuming you uploaded one font only)
    - Your original font (ttf/otf)
    - 1 eot file
    - 1 svg file
    - 1 woff file
    - stylesheet css files
1. Edit the stylesheet for your own use (the URL location of the font, etc.)

## Sample @font-face stylesheet

```css
@font-face {
  font-family: 'BaybayinLopezRegular';
  src: url('baylopez-webfont.eot');
  src: url('baylopez-webfont.woff') format('woff'),
       url('baylopez-webfont.ttf') format('truetype'),
       url('baylopez-webfont.svgz#webfontsBCU3ofZ') format('svg'),
       url('baylopez-webfont.svg#webfontsBCU3ofZ') format('svg');
  unicode-range: U+1700-171F, U+1720-173F, U+1740-175F, U+1760-177F;
}
```

And here's what happens when a browser reads your font stylesheet:

1. font-family name declared as: BaybayinLopezRegular
1. If MSIE: downloads baylopez-webfont.eot
1. If not, then it reads the WOFF file if the browser supports it
1. If not, then it reads the TTF file if the browser supports it
1. If not, then the browser reads the SVG file if it supports it
1. If all else fails, then it does nothing. Depending on your setup, it will either display boxes or it will search your other font declarations
1. The browser will also read the unicode-range if it supports it, and only download those specific Unicode points and ignore the rest. Making the size of transmitted to your visitors smaller.

<!--
## The @font-face Smiley variation
```css
src: local('☺')
```

The above technique prevents your visitor's browser in using any locally installed fonts. By doing this, you can be sure that your own font is the actual file the browser is rendering. This usually becomes a problem when there are [1] fonts with the same name; or [2] there are updates to the font that more likely is not installed on your visitor's machine. You can read more about it <a class="popper animate" href="https://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/#smiley" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin" data-popper="Bulletproof @font-face: Smiley variation">here</a>.
-->

## @font-face CSS Rule Browser Compatibility Chart

The table below presents which font format is supported by the four major browsers - Chromium/Chrome, Firefox, Internet Explorer, Opera, and Safari. As you will see, no font format is supported across all five browsers except for WOFF… in the near future.

Microsoft's EOT is out of the race, even though many font creators and foundries support it, the other four browsers are likely never going to support it. Then OTF, SVG, and TTF are out too because Internet Explorer is surely never going to implement it, and font creators/foundries do not like these formats for @font-face use.

That is where WOFF comes in. Commercial font creators and font foundries wants control (or restriction if you want it that way) to the fonts that can be used for the CSS @font-face rule.

Of course there are other advantages to WOFF like compression. WOFF is compressed, which site administrators will like because it eats less bandwidth. You can go check the fonts that came with your FontSquirrel generated font kit, WOFF is the smallest of them.

For now as with all new technologies, we have to wait until all major browsers adds support for WOFF. But that should not stop you from using it today. Just like with CSS3 and some HTML5, you can use it right now. It will save you time later if you do the update now than whenever you feel like to, which you will probably forget.

<table style="text-align: center; margin: 0 auto; margin-top: 30px; margin-bottom: 30px; width: 88%;" border="1">
  <thead>
    <tr>
      <th style="text-align: center;"> </th>
      <th style="text-align: center;">Chrome<br />(WebKit)</th>
      <th style="text-align: center;">Firefox<br />(Gecko)</th>
      <th style="text-align: center;">IE<br />(Trident)</th>
      <th style="text-align: center;">Opera<br />(Presto)</th>
      <th style="text-align: center;">Safari<br />(WebKit)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th style="text-align: center;">EOT</th>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v4.0</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
    </tr>
    <tr>
      <th style="text-align: center;">OTF</th>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v3.5</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v10.0</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v3.1</td>
    </tr>
    <tr>
      <th style="text-align: center;">SVG</th>
      <td style="background: #90ff90; color: #000; text-align: center;">v0.3</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v10.0</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v3.1</td>
    </tr>
    <tr>
      <th style="text-align: center;">TTF</th>
      <td style="background: #90ff90; color: #000; text-align: center;">v2.0</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v3.5</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v10.0</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v3.1</td>
    </tr>
    <tr>
      <th style="text-align: center;">WOFF</th>
      <td style="background: #90ff90; color: #000; text-align: center;">v5.0</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v3.6</td>
      <td style="background: #90ff90; color: #000; text-align: center;">v9.0</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
      <td style="background: #ff9090; color: #000; text-align: center;">No</td>
    </tr>
  </tbody>
</table>

## Let's Test Your Browser

If you see the Baybayin writing script below, then your browser supports one of the font formats - EOT, OTF, SVG, TTF, or WOFF. If not, then you should upgrade your browser because my font stylesheet captures all browsers. (At least from my testing, on two computers without any Baybayin fonts - it displays correctly on all the major browsers.)

### Example #1

- Filipino-Baybayin: <bdi lang="fil-Tglg">ᜀᜅ᜔ ᜊᜓᜃᜓ ᜀᜌ᜔ ᜉᜍ ᜐ ᜆᜂ ᜇᜑᜒᜎ᜔ ᜏᜎ ᜈᜅ᜔ ᜉᜓᜏᜒᜇᜒᜅ᜔ ᜋᜁᜈᜓᜋ᜔ ᜈ ᜄᜆᜐ᜔᜶</bdi>

- Filipino-Latin: <bdi lang="fil">Ang buko ay para sa tao dahil wala nang puwedeng mainom na gatas.</bdi>
- English: The coconut is for people because there is not enough milk to drink.

### Example #2

- Filipino-Baybayin: <bdi lang="fil-Tglg">ᜉᜓᜏᜒᜇᜒ ᜃᜅ᜔ ᜌᜓᜋᜋᜈ᜔ ᜇᜑᜒᜎ᜔ ᜐ ᜊᜄᜓᜅ᜔ ᜍᜓᜎᜒᜆ᜶</bdi>

- Filipino-Latin: <bdi lang="fil">Puwede kang yumaman dahil sa bagong roleta.</bdi>
- English: You can be rich because of the new wheel.

<!--
What are these? These are called *pangrams*. A pangram is a sentence using every letter of the alphabet at least once. The most common pangram (in English) is: *The quick brown fox jumps over the lazy dog.* Which is written in:
* Filipino-Baybayin: <bdi lang="fil-Tglg">ᜀᜅ᜔ ᜋᜊᜒᜎᜒᜐ᜔ ᜈ ᜃᜌᜓᜋᜅ᜔ᜑᜒᜅ᜔ ᜐᜓᜍᜓ ᜀᜌ᜔ ᜆᜒᜈᜎᜓᜈᜈ᜔ ᜀᜅ᜔ ᜆᜆᜋᜇ᜔ᜆᜋᜇ᜔ ᜈ ᜀᜐᜓ᜶</bdi>
* Filipino-Latin: <bdi lang="fil">Ang mabilis na kayumangging soro ay tinalunan ang tatamad-tamad na aso.</bdi>
-->

Enjoy!

---

Sources:

- [Web Open Font Format for Firefox 3.6](https://hacks.mozilla.org/2009/10/woff/)
- [Web typography](https://en.wikipedia.org/wiki/Web_typography)
- [Mozilla Supports Web Open Font Format](https://blog.mozilla.org/blog/2009/10/20/mozilla-supports-web-open-font-format/) (includes a list of font creators and font foundries supporting WOFF)
<!--
* <a class="popper animate" href="https://en.wikipedia.org/wiki/Pangram" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin" data-popper="Wikipedia: Pangram">Wikipedia: Pangram</a>
* <a class="popper animate" href="https://web.archive.org/web/20141012231620/https://en.wikipedia.org/wiki/List_of_pangrams" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin" data-popper="Wikipedia: List of pangrams">Wikipedia: List of pangrams</a>
-->

---

{{< image
  type="imagecoverattrib"

  link="https://www.flickr.com/photos/manoftaste-de/14069118533"
  linkrel="noopener external nofollow"

  title="Web"
  caption=""

  licensecode="ccbysa2"
  licenseurl="ttps://creativecommons.org/licenses/by-sa/2.0/"
  licensename="CC BY-SA 2.0"

  attribto="www.manoftaste.de"
  attriburl="https://www.flickr.com/photos/manoftaste-de/"
  attribrel="noopener external nofollow"
>}}
