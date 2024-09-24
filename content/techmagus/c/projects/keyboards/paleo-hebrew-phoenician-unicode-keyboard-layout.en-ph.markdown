+++
title = "Paleo-Hebrew / Phoenician Unicode Keyboard Layout"
description = "The official page of the Paleo-Hebrew / Phoenician Unicode Keyboard Layout."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = 2015-07-19T21:48:00+08:00                                        # manually adjust to local timezone
lastmod = 2016-09-11T10:04:05+08:00                                     # manually adjust to local timezone

aliases = ["/projects/keyboards/paleo-hebrew-phoenician-unicode-keyboard-2015200", "/p/paleo-hebrew-phoenician-keyboard-layout.html", "/projects/keyboard/paleo-hebrew-phoenician-unicode-keyboard-2015200"]
slug = "paleo-hebrew-phoenician-unicode-keyboard"
translationKey = "paleo-hebrew-phoenician-unicode-keyboard"
relCanonical = "https://im.youronly.one/techmagus/projects/keyboards/paleo-hebrew-phoenician-unicode-keyboard/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
disqus_identifier = "paleo-hebrew-phoenician-unicode-keyboard-2015200"                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["unicode"]                                                   # taxonomy
keywords = ["unicode", "paleo-hebrew", "hebrew", "modern hebrew", "phoenician", "keyboard", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
#tags = [""]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Noto_Sans_Phoenician_font.png", "https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Ancient_Hebrew_6000-1700BCE_font.png", "https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Paleo-Hebrew_Gezer_1000-901BCE_font.png"]                                                       # used by og:images, etc.; first image is cover image

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

# For /yuki/ choose one and remove everything else
[[authors]]
  person = "yuki"
  #id = ""
  name = "Yohan Yukiya Sese-Cuneta"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

The **Phoenician Unicode Keyboard Layout** or **PHNX-UKL** is the first Unicode-compliant keyboard layout for the Phoenician Unicode block. Its main feature is the incorporation of the characters commonly used in various ancient Western Asian writing scripts.

<!--more-->

- Ammonite
- Early Aramaic
- Old Hebrew dialects
- Palæo-Hebrew (1000 B.C.E.)
- Siloam Hebrew
- Hebrew seals
- Moabite
- Phoenician
- Archaic Phoenician
- Late Phoenician cursive
- Phoenician papyri
- Punic

In addition to the above, the Phoenician Unicode block is also compatible with a much earlier script than Palæo-Hebrew/Phoenician which is *Ancient Hebrew (a.k.a. Proto-Canaanite; Early Hebrew; Proto-Sinaitic)*, a pictograph script which was in used from 6000 B.C.E. to 1700 B.C.E. As the Ancient Hebrew script is still being deciphered and might have more glyphs, the Unicode Consortium in the future may assign a separate block for this.

There are also some exceptions. While the Samaritan script is similar and one of the closely related and surviving writing system to the Palæo-Hebrew/Phoenician family, the Unicode consortium assigned a separate block ([U+0800…U+083F](https://www.unicode.org/charts/PDF/U0800.pdf)) for the Samaritan script. As such, do not use the Phoenician Unicode block when creating a font for or typing in Samaritan.

Lastly, why "Phoenician" and not "Palœo-Hebrew"? Simply because the former was the name chosen by the Unicode Consortium to refer to this Unicode block. As this keyboard project is a Unicode-compliant layout, using the name assigned by the Unicode is part of it. If in the future they change the block name to the latter, then this project will implement the same.

## Project info

- Based on: [Unicode 8.0](https://blog.unicode.org/2015/06/announcing-unicode-standard-version-80.html) (2015-06-17)
- Unicode block: [U+10900…U+1091F](https://www.unicode.org/charts/PDF/U10900.pdf)
- Unicode name: Phoenician
- Latest version: 1.0.0
- First release: 2015-07-19
- Official website: [https://im.youronly.one/techmagus/projects/keyboard/paleo-hebrew-phoenician-unicode-keyboard-2015200/](https://im.youronly.one/techmagus/projects/keyboard/paleo-hebrew-phoenician-unicode-keyboard-2015200/)
- Git: [https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician](https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician)
- Project contact: [techmagus](https://im.youronly.one/p/contact-us/)

*A project of [Yelosan Publishing](https://yelosan.youronly.one).*

## Fonts

To see the glyphs that you are typing, you will need a Unicode-compliant or mixed-Unicode set of fonts. For more information and download links, visit our [wiki here](https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/wiki/Fonts).

## License

- Content License: Creative Commons-Attribution 4.0 International (CC BY-SA 4.0 International License)
- Code Copyright and License:
  - Copyright © 2015, 2016, 2018 JC John Sese Cuneta.
  - Copyleft 🄯 2015, 2016, 2018 JC John Sese Cuneta. [The MIT License](https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/src/branch/main/LICENSE)

## Keyboard Layout Images

### Neo-Paleo Layout Images

There were some keys which were left unassigned, what I did was assign a value. These are:

- Y = yod; so we have Y and I for yod/iod
- U = uau; so we have U and V for uau/vav
- F = pe; so we have F and P for pe
- K = kaf; so we have K and C for kaf/caf

If you would like to master the pure Neo-Paleo Layout, just remember not to use the keys Y; U; F; and K. These were only added in the keyboard layout to help in transitioning to the Neo-Paleo Layout (and eliminate the chance of getting a "missing key" bug report).

I also added 3 Unicode code points for inline directional use. These are:

- U+2067 (Shift+R): Right-to-Left isolate (invisible marker)
- U+2066 (Shift+L): Left-to-Right isolate (invisible marker)
- U+2069 (Shift+.): terminate RTL/LTR isolate markers

Examples:

- The title of the book is: <bdi dir="rtl" lang="hbo-Hebr">𐤌𐤍𐤉𐤀 𐤋 <bdi class="reset-1_25em" dir="ltr" lang="en">C++</bdi></bdi> ("An Introduction to C++")
- My name in Hebrew is <bdi dir="rtl" lang="hbo-Hebr">𐤉𐤅𐤇𐤍𐤍!</bdi> (Yahuhanan)

Without these invisible markers, in the first example, the "C++" will become "++C"; in the second example, the exclamation point "!" will be on the right side not left. Also, you would have to cheat by first typing "C++" or the exclamation point "!" before typing Hebrew just to achieve the correct format (which is not advisable as far as semantics, relationships, and typing-flow are concerned). See [https://www.w3.org/International/articles/inline-bidi-markup/](https://www.w3.org/International/articles/inline-bidi-markup/).

{{< image
  height=""
  width=""
  class=""
  style=""

  isrepresentativeofpage=false

  src="https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Ancient_Hebrew_6000-1700BCE_font.png"
  link="https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Ancient_Hebrew_6000-1700BCE_font.png"
  linkrel="noopener external"

  title="Neo-Paleo Layout"
  caption="Ancient Hebrew 6000-1700 BCE font"
  alt="Neo-Paleo Layout in Ancient Hebrew 6000-1700 BCE font"

  datepublished="2015-07-19"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons-Attribution-ShareAlike (CC-BY-SA) 4.0 International License"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

{{< image
  height=""
  width=""
  class=""
  style=""

  isrepresentativeofpage=false

  src="https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Noto_Sans_Phoenician_font.png"
  link="https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Noto_Sans_Phoenician_font.png"
  linkrel="noopener external"

  title="Neo-Paleo Layout"
  caption="Noto Sans Phoenician font"
  alt="Neo-Paleo Layout in Noto Sans Phoenician font"

  datepublished="2015-07-19"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons-Attribution-ShareAlike (CC-BY-SA) 4.0 International License"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

{{< image
  height=""
  width=""
  class=""
  style=""

  isrepresentativeofpage=false

  src="https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Paleo-Hebrew_Gezer_1000-901BCE_font.png"
  link="https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Paleo-Hebrew_Gezer_1000-901BCE_font.png"
  linkrel="noopener external"

  title="Neo-Paleo Layout"
  caption="Paleo-Hebrew Gezer 1000-901 BCE font"
  alt="Neo-Paleo Layout in Paleo-Hebrew Gezer 1000-901 BCE font"

  datepublished="2015-07-19"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="Creative Commons-Attribution-ShareAlike (CC-BY-SA) 4.0 International License"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

## Attributions

### To <bdi class="font-Hebr-ancient" dir="rtl" lang="hbo-Hebr">𐤉𐤄𐤅𐤄</bdi> (Yahuwah) and his son <bdi dir="rtl" lang="hbo-Hebr">𐤉𐤄𐤅𐤔𐤏</bdi> (Yahushua)

Thank you for the strength and support. You deserve all the glory, honour, praise, and worship, now and forevermore. AHMEIN! <bdi dir="rtl" lang="hbo-Hebr">𐤄𐤋𐤋𐤅𐤉𐤄</bdi> (HalleluYAH)

### Neo-Paleo Keyboard Layout

This site, [Neo-Paleo Layout](https://loveandtruth.net/neopaleo.html), was shown to me by brother [Ted Walther](https://www.facebook.com/tederific), I am very grateful, blessings to you from <bdi class="font-Hebr-ancient" dir="rtl" lang="hbo-Hebr">𐤉𐤄𐤅𐤄</bdi> (Yahuwah) and his son <bdi dir="rtl" lang="hbo-Hebr">𐤉𐤄𐤅𐤔𐤏</bdi> (Yahushua).

### To all the followers of Aluahim

This Unicode-compliant keyboard layout is for you. I hope it will help in spreading the Besorah of Yahushua and in learning the original Hebrew language.

### Blank Keyboard Layout

The keyboard layout shown in the images were:

- Based on: [KB United States-NoAltGr.svg](https://commons.wikimedia.org/wiki/File:KB_United_States-NoAltGr.svg)
- By: DaemonDice
- Source: [Blank BRSB Keyboard Layout.svg](https://commons.wikimedia.org/wiki/File%3ABlank_BRSB_Keyboard_Layout.svg)

## Download and install

- [Download the Keyboard installer tagged "PHNX-UKL"](https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/releases)
- [Get Unicode fonts here](https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/wiki/Fonts)

---

{{< image
  type="imagecoverattrib"

  link="https://codeberg.org/yelosan/unicode-keyboard-layout-phoenician/raw/branch/main/images/PHNX-Neo_in_Noto_Sans_Phoenician_font.png"
  linkrel="noopener"

  title="Paleo Hebrew Unicode Keyboard"
  caption=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
