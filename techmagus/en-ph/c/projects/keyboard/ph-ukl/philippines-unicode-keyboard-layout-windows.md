+++
title = "Philippines Unicode Keyboard Layout for Windows is Out!"
description = "Philippines Unicode Keyboard Layout for Microsoft® Windows™ users is now available."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

date = "2010-10-25T21:10:37+08:00"                                        # manually adjust to local timezone
lastmod = "2018-03-20T17:53:01+08:00"                                     # manually adjust to local timezone

aliases = ["/p/philippines-unicode-keyboard-windows.html"]
slug = "philippines-baybayin-windows"
translationKey = "philippines-baybayin-windows-2010298"
relCanonical = "https://im.youronly.one/techmagus/projects/keyboard/philippines-baybayin-windows-2010298/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["unicode", "windows"]                                                   # taxonomy
keywords = ["unicode", "windows", "keyboard", "philippines", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
#tags = [""]                                                         # taxonomy

comments = true
#weight = "30"                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://1.bp.blogspot.com/-CPWwSnkvJ5o/TncoS0gmAkI/AAAAAAAAAVQ/t_XosFtEEl4/s1600/Philippines-Colemak%252520%252528Latin%252529.png"]                                                       # used by og:images, etc.; first image is cover image

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

I finished the port of the [Philippines Unicode Keyboard Layout for Linux]({{% ref "philippines-unicode-keyboard-layout-linux.md" %}} "Philippines Unicode Keyboard Layout for Linux") to Windows much earlier than I hoped! Rejoice Microsoft® Windows users!

Get it now and start typing all the Filipino characters!

<!--more-->

The process is simple:

<ol>
  <li>Download the file PH-UKL-Windows (available in 7-zip, exe, and zip formats) <a href="https://bitbucket.org/paninap/ph-ukl/downloads" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">here</a></li>
  <li>Extract the file anywhere and go to the "PH-UKL-Windows" folder</li>
  <li><del>Install the Baybayin (Alibata) font so your system can display the characters</del> Update 2018-03-20: Removed the fonts from the package as I do not have permission to redistribute the Unicode-only versions. <a href="https://bitbucket.org/paninap/ph-ukl/wiki/Fonts" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">Check our font wiki here instead.</a></li>
  <li>Open the "kbdph" folder</li>
  <li>Install one or all of the Latin keyboard layouts:
    <ul class="custom_liststyle omark-black list-red">
      <li>QWERTY (Latin): kbdph01l_setup.exe</li>
      <li>Capewell-Dvorak (Latin): kbdph02l_setup.exe</li>
      <li>Capewell-QWERF 2006 (Latin): kbdph03l_setup.exe</li>
      <li>Colemak (Latin): kbdph04l_setup.exe</li>
      <li>Dvorak (Latin): kbdph05l_setup.exe</li>
    </ul>
  </li>
  <li>Install one or all of the Baybayin keyboard layouts:
    <ul class="custom_liststyle omark-black list-red">
      <li>QWERTY (Baybayin): kbdph01b_setup.exe</li>
      <li>Capewell-Dvorak (Baybayin): kbdph02b_setup.exe</li>
      <li>Capewell-QWERF 2006 (Baybayin): kbdph03b_setup.exe</li>
      <li>Colemak (Baybayin): kbdph04b_setup.exe</li>
      <li>Dvorak (Baybayin): kbdph05b_setup.exe</li>
    </ul>
  </li>
  <li>Windows automatically activates your newly installed keyboard layout. Simply press (Left) Alt+Shift to switch between layouts. You type the ₱eso sign by pressing (RightAlt)/AltGr+p. ñ by (RightAlt)/AltGr+n; Ñ by (RightAlt)/AltGr+N and so on.</li>
</ol>

You're done!

<del>The font included in the zip file is a Unicode-only and Website-embed compatible version of <a href="https://nordenx.com" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">Nordenx</a>'s Baybayin brush font.</del> Update 2018-03-20: Removed the special font in the package as I do not have permission to redistribute the Unicode-only version. <a href="https://bitbucket.org/paninap/ph-ukl/wiki/Fonts" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">Check our font wiki here instead.</a>

See the [keyboard layout images here]({{% ref "philippines-unicode-keyboard-layout.md" %}} "Philippines Unicode Keyboard Layout").

<ul class="custom_liststyle checkmark list-green">
  <li>Official source repository: <a href="https://bitbucket.org/paninap/ph-ukl/" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">https://bitbucket.org/paninap/ph-ukl/</a></li>
  <li>If you have suggestions or bugs to report, please do not hesitate to <a href="https://bitbucket.org/paninap/ph-ukl/issues" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">file a ticket here</a>.</li>
</ul>

The **Philippines Unicode Keyboard Layout** is a project of *Ubuntu Philippines LoCo Team*.

---

{{< image
  type="imagecoverattrib"

  link="https://1.bp.blogspot.com/-CPWwSnkvJ5o/TncoS0gmAkI/AAAAAAAAAVQ/t_XosFtEEl4/s1600/Philippines-Colemak%252520%252528Latin%252529.png"
  linkrel="noopener"

  title=""
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
