+++
title = "Philippines Unicode Keyboard Layout for Linux Is Now Available!"
description = "Filipino Linux users around the world can now download and use the first release of the Philippines Unicode Keyboard Layout."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

date = "2010-10-23T19:40:10+08:00"                                        # manually adjust to local timezone
lastmod = "2010-10-23T19:40:10+08:00"                                        # manually adjust to local timezone

aliases = ["/p/philippines-unicode-keyboard-linux.html"]
slug = "philippines-baybayin-unicode-linux"
translationKey = "philippines-baybayin-unicode-linux-2010296"
relCanonical = "https://im.youronly.one/techmagus/projects/keyboard/philippines-baybayin-unicode-linux-2010296/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["unicode", "linux"]                                                   # taxonomy
keywords = ["unicode", "linux", "philippines", "unicode", "keyboard", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
#tags = [""]                                                         # taxonomy

comments = true
#weight = "20"                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://3.bp.blogspot.com/-IPzJrxh1_vg/TncoS7FQ61I/AAAAAAAAAVQ/65UR2jN6Aes/s1600/Philippines-Dvorak%252520Simplified%252520%252528Latin%252529.png", "https://2.bp.blogspot.com/-s6u_KKylKpg/TMJT_n8RdXI/AAAAAAAAAHw/ErsBqZlFJeg/s1600/Philippines%252520National%252520Keyboard%252520Layout.png"]                                                       # used by og:images, etc.; first image is cover image

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

Today, 23<sup>rd</sup> of October 2010, Filipino Linux users around the world can now download and use the first release of the **Philippines Unicode Keyboard Layout**, officially launched during the Philippines Ubuntu 10.10 Maverick Meerkat Release Party.

What is this all about? Simple: being able to type the characters that Filipinos use, especially the ₱eso sign and <bdi lang="fil-Tglg">ᜊᜌ᜔ᜊᜌᜒᜈ᜔</bdi> (Baybayin) glyphs that has been available for use since Unicode 3.2 (March 2002). Other characters are: Ññ, ©, ®, ™, ¢, ¥, ¶, Pahilís (acute diacritic), Paiwà (grave diacritic), Pakupyâ (circumflex diacritic), Ng̃ (the shortened form of nan͠g), and many more.

How about Windows users? <del>You will have to wait more or less 2 weeks, it will be usable for Windows 7, Vista, and XP; both 64-bit and 32-bit installations.</del> It is now available for [download]({{% ref "philippines-unicode-keyboard-layout-windows.md" %}} "Philippines Unicode Keyboard Layout for Windows").

Without further ado, here are the steps to get you started with using our very own Unicode Keyboard Layout.

<!--more-->

- Download the PH-UKL-Linux file (available in 7-zip and zip format) <a href="https://bitbucket.org/paninap/ph-ukl/downloads" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">here</a>
- Extract the content of the archive file you just downloaded
- Install the font included so your system can display Baybayin (Alibata) glyphs
- Then copy the file "ph" to the correct folder by typing in the terminal (be sure to adjust ~/Downloads/ to where the file is on your end)

  ```shell
  sudo cp ~/Downloads/ph /usr/share/X11/xkb/symbols
  ```

- Open these two files by typing:

  ```shell
  gksu gedit /usr/share/X11/xkb/rules/evdev.lst
  ```

  ```shell
  gksu gedit /usr/share/X11/xkb/rules/base.lst
  ```

- Search for:

  ```
  ! layout
  ```

- After it add:

  ```
  ph              Philippines
  ```

- Search for:

  ```
  ! variant
  ```

- After it add:

  ```
  qwerty-bay            ph: QWERTY (Baybayin)
  capewell-dvorak       ph: Capewell-Dvorak (Latin)
  capewell-dvorak-bay   ph: Capewell-Dvorak (Baybayin)
  capewell-qwerf2k6     ph: Capewell-QWERF 2006 (Latin)
  capewell-qwerf2k6-bay ph: Capewell-QWERF 2006 (Baybayin)
  colemak               ph: Colemak (Latin)
  colemak-bay           ph: Colemak (Baybayin)
  dvorak                ph: Dvorak (Latin)
  dvorak-bay            ph: Dvorak (Baybayin)
  ```

- Open these two files by typing:

  ```shell
  gksu gedit /usr/share/X11/xkb/rules/evdev.xml
  ```

  ```shell
  gksu gedit /usr/share/X11/xkb/rules/base.xml
  ```

- Search for:

  ```xml
  <layoutlist>
  ```

- After it add:

  ```xml
  <layout>
    <configItem>
      <name>ph</name>
      <shortDescription>Phi</shortDescription>
      <description>Philippines</description>
      <languageList><iso639Id>eng</iso639Id>
                    <iso639Id>bik</iso639Id>
                    <iso639Id>ceb</iso639Id>
                    <iso639Id>fil</iso639Id>
                    <iso639Id>hil</iso639Id>
                    <iso639Id>ilo</iso639Id>
                    <iso639Id>pam</iso639Id>
                    <iso639Id>pag</iso639Id>
                    <iso639Id>phi</iso639Id>
                    <iso639Id>tgl</iso639Id>
                    <iso639Id>war</iso639Id></languageList>
    </configItem>
    <variantList>
      <variant>
        <configItem>
          <name>qwerty-bay</name>
          <description>QWERTY (Baybayin)</description>
          <languageList><iso639Id>bik</iso639Id>
                        <iso639Id>ceb</iso639Id>
                        <iso639Id>fil</iso639Id>
                        <iso639Id>hil</iso639Id>
                        <iso639Id>ilo</iso639Id>
                        <iso639Id>pam</iso639Id>
                        <iso639Id>pag</iso639Id>
                        <iso639Id>phi</iso639Id>
                        <iso639Id>tgl</iso639Id>
                        <iso639Id>war</iso639Id></languageList>
        </configItem>
      </variant>
      <variant>
        <configItem>
          <name>capewell-dvorak</name>
          <description>Capewell-Dvorak (Latin)</description>
        </configItem>
      </variant>
      <variant>
        <configItem>
          <name>capewell-dvorak-bay</name>
          <description>Capewell-Dvorak (Baybayin)</description>
          <languageList><iso639Id>bik</iso639Id>
                        <iso639Id>ceb</iso639Id>
                        <iso639Id>fil</iso639Id>
                        <iso639Id>hil</iso639Id>
                        <iso639Id>ilo</iso639Id>
                        <iso639Id>pam</iso639Id>
                        <iso639Id>pag</iso639Id>
                        <iso639Id>phi</iso639Id>
                        <iso639Id>tgl</iso639Id>
                        <iso639Id>war</iso639Id></languageList>
        </configItem>
      </variant>
      <variant>
        <configItem>
          <name>capewell-qwerf2k6</name>
          <description>Capewell-QWERF 2006 (Latin)</description>
        </configItem>
      </variant>
      <variant>
        <configItem>
          <name>capewell-qwerf2k6-bay</name>
          <description>Capewell-QWERF 2006 (Baybayin)</description>
          <languageList><iso639Id>bik</iso639Id>
                        <iso639Id>ceb</iso639Id>
                        <iso639Id>fil</iso639Id>
                        <iso639Id>hil</iso639Id>
                        <iso639Id>ilo</iso639Id>
                        <iso639Id>pam</iso639Id>
                        <iso639Id>pag</iso639Id>
                        <iso639Id>phi</iso639Id>
                        <iso639Id>tgl</iso639Id>
                        <iso639Id>war</iso639Id></languageList>
        </configItem>
      </variant>
      <variant>
        <configItem>
          <name>colemak</name>
          <description>Colemak (Latin)</description>
        </configItem>
      </variant>
      <variant>
        <configItem>
          <name>colemak-bay</name>
          <description>Colemak (Baybayin)</description>
          <languageList><iso639Id>bik</iso639Id>
                        <iso639Id>ceb</iso639Id>
                        <iso639Id>fil</iso639Id>
                        <iso639Id>hil</iso639Id>
                        <iso639Id>ilo</iso639Id>
                        <iso639Id>pam</iso639Id>
                        <iso639Id>pag</iso639Id>
                        <iso639Id>phi</iso639Id>
                        <iso639Id>tgl</iso639Id>
                        <iso639Id>war</iso639Id></languageList>
        </configItem>
      </variant>
      <variant>
        <configItem>
          <name>dvorak</name>
          <description>Dvorak (Latin)</description>
        </configItem>
      </variant>
      <variant>
        <configItem>
          <name>dvorak-bay</name>
          <description>Dvorak (Baybayin)</description>
          <languageList><iso639Id>bik</iso639Id>
                        <iso639Id>ceb</iso639Id>
                        <iso639Id>fil</iso639Id>
                        <iso639Id>hil</iso639Id>
                        <iso639Id>ilo</iso639Id>
                        <iso639Id>pam</iso639Id>
                        <iso639Id>pag</iso639Id>
                        <iso639Id>phi</iso639Id>
                        <iso639Id>tgl</iso639Id>
                        <iso639Id>war</iso639Id></languageList>
        </configItem>
      </variant>
    </variantList>
  </layout>
  ```

You're done! Sort of. You need to activate it to actually use it, follow the next few steps to do so.

- Go to: Preferences > Keyboard > Layouts
- Click the "Add…" button
- Search for the new keyboard you installed either "By country" (Philippines) or "By language" (English; Filipino; Cebuano; Philippine Languages; etc.)
- There are different variants that you can choose from:
  - Philippines (default; QWERTY - Latin)
  - Philippines - QWERTY (Baybayin)
  - Philippines - Capewell-Dvorak (Latin)
  - Philippines - Capewell-Dvorak (Baybayin)
  - Philippines - Capewell-QWERF 2006 (Latin)
  - Philippines - Capewell-QWERF 2006 (Baybayin)
  - Philippines - Colemak (Latin)
  - Philippines - Colemak (Baybayin)
  - Philippines - Dvorak (Latin)
  - Philippines - Dvorak (Baybayin)
- Click the "Add" button
- Select the new layout that you added then click the "Move Up" button and place it on top
  {{< image
    type="image"

    height=""
    width=""

    src="https://2.bp.blogspot.com/-s6u_KKylKpg/TMJT_n8RdXI/AAAAAAAAAHw/ErsBqZlFJeg/s1600/Philippines%252520National%252520Keyboard%252520Layout.png"
    link="https://2.bp.blogspot.com/-s6u_KKylKpg/TMJT_n8RdXI/AAAAAAAAAHw/ErsBqZlFJeg/s1600/Philippines%252520National%252520Keyboard%252520Layout.png"
    linkrel="noopener"

    title="Keyboard Preferences"
    caption="Select Philippines Keyboard Layouts"
    alt="Keyboard Preferences - Select Philippines Keyboard Layouts"

    attribalign=""

    licensecode="ccbysa4"
    licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
    licensename="CC BY-SA 4.0 International"

    attribto="I'M YourOnly.One"
    attriburl="https://im.youronly.one/"
    attribrel="noopener"
  >}}

Let's not forget to add the first Baybayin <bdi lang="fil-Tglg">ᜊᜌ᜔ᜊᜌᜒᜈ᜔</bdi>) keyboard layout, it is QWERTY-based. Simply repeat the process above but place it as second in your Layouts list. Then if you want to switch between Philippines Latin and Philippines Baybayin scripts, simply press **Shift+CAPS_Lock**. It is the default shortcut in Ubuntu 10.10 Maverick Meerkat.

The font included in the zip file is a Unicode-only and Website-embed compatible version of [Nordenx](https://nordenx.com)'s Baybayin brush font.

See the [keyboard layout images here]({{% ref "philippines-unicode-keyboard-layout.md" %}} "Philippines Unicode Keyboard Layout").

Official source repository: [https://bitbucket.org/paninap/ph-ukl/](https://bitbucket.org/paninap/ph-ukl/). If you have suggestions or bugs to report, please do not hesitate to [file a ticket here](https://bitbucket.org/paninap/ph-ukl/issues).

The **Philippines Unicode Keyboard Layout** is a project of *Ubuntu Philippines LoCo Team*.

---

{{< image
  type="imagecoverattrib"

  link="https://3.bp.blogspot.com/-IPzJrxh1_vg/TncoS7FQ61I/AAAAAAAAAVQ/65UR2jN6Aes/s1600/Philippines-Dvorak%252520Simplified%252520%252528Latin%252529.png"
  linkrel="noopener"

  title="Philippines-Dvorak Simplified (Latin)"
  caption=""

  licensecode="cc0"
  licenseurl="https://creativecommons.org/publicdomain/zero/1.0/"
  licensename="CC Zero / Public Domain dedication"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"

  cc0country="Philippines"
  cc0countrycode="PH"
  cc0countryurl="https://en.wikipedia.org/wiki/Philippines"
>}}
