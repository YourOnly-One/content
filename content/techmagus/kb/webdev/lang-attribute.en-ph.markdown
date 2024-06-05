+++
title = "The LANG attribute"
description = "The LANG attribute is a powerful piece of code when designing websites. Let me show you how to correctly use the LANG attribute."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

# DATE checked and correct

publishdate = 2009-06-21T00:20:37+08:00                                        # manually adjust to local timezone
lastmod = 2009-06-21T00:20:37+08:00                                        # manually adjust to local timezone

aliases = ["/kb/webdev/lang-attribute-2009172", "/2009/06/the-lang-attribute.html"]
slug = "lang-attribute"
translationKey = "lang-attribute"
relCanonical = "https://im.youronly.one/techmagus/kb/webdev/lang-attribute/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
disqus_identifier = "lang-attribute-2009172"                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["howto"]                                                   # taxonomy
keywords = ["lang", "language", "multilang", "multi-language", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
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
  name = "ᜌᜓᜃᜒ (Yuki)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

In my previous post I talked about "Baybayin - the Forgotten Pre-Hispanic Writing of the Filipino". It was added in version 5.0 of the [Unicode Standard](https://unicode.org) together with Buhid, Hanunoo, and Tagbanwa under the "Philippine Scripts" group. But how should we properly write or mark our content written in another language and script?

For this post, I will talk about how to correctly declare the language of your content, this way you are being friendly with translation software and helper applications, and other technologies that rely on this often taken-for-granted HTML attribute. As is shown in our image, everyone can see the writing script used, but in the digital world there are people who do not have the fonts you are using. There are also people who do not use the same browser as you and me use - it could be a text-only browser, a speech browser, or a Braille browser.

It is then only appropriate that we properly and correctly tag our content with the language and script we are using. Get ready to use the LANG attribute a lot.

<!--more-->

When creating websites, it is important to properly declare the language being used on the webpage. For example, I use the following for my sites:

```html
<html lang="en-PH">
```

It is also important to declare the character set especially when you are going to use any characters beyond the scope of ASCII. This is how it looks like:

```html
    <meta charset="UTF-8" />
```

Putting it all together, our basic HTML should be.

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

Now let's dig-in…

## The *lang* attribute

The HTML lang attribute defines the language of the content enclosed within the element it was declared. The codes are called *subtag*, and for my Filipino readers, there are only three subtag types you should worry about: language-Script-REGION. The full format: language-extended_language-Script-REGION-variant-extension-privateuse.

See the table below:
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
      <th style="min-width: 15%; width: 15%;">Code</th>
      <th>Language</th>
      <th>Subtag Placement</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>en</td>
      <td>(Generic) English</td>
      <td>language</td>
    </tr>
    <tr>
      <td>en-PH</td>
      <td>Philippine English</td>
      <td>language+REGION</td>
    </tr>
    <tr>
      <td>fil-Tglg</td>
      <td>Filipino in Baybayin</td>
      <td>language+Script</td>
    </tr>
    <tr>
      <td>bik-cts-Tglg</td>
      <td>Bikolano of the Pandan (Northern Catanduanes) dialect in Baybayin script</td>
      <td>language+extended_language+Script</td>
    </tr>
    <tr>
      <td>phi-Tglg-tsg</td>
      <td>Tausug Philippine language written in Baybayin script</td>
      <td>language+Script+variant</td>
    </tr>
  </tbody>
</table>
<p></p>

If you want to find the subtags for a particular language, previously we have to check different websites and plenty of official code lists. A time-consuming task (although normally you only have to do this once), right? Well, the latest official subtags can now be found in the [IANA Language Subtag Registry](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry). It is now the universal source for all valid subtags.

According to the latest list (as of this writing), the subtags that are related to the Philippines are the following (if I missed anything, please leave a comment below):

### Languages

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

### Region

- Philippines
  - Type: region
  - Subtag: PH
  - Description: Philippines
  - Added: 2005-10-16

### Scripts

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

Now that we have the subtags we need we can start coding the correct `lang` value for any Philippines language and script. See these examples:

- If you grew and learned English in the Philippines, more likely than not, you are using English words that are exclusive to the Philippines, as well as, following strict language rules that are taught only in Philippine English. This is the correct `lang` value for your website: `lang="en-PH"`
- If you are writing in Filipino, not Tagalog, use this: `lang="fil"`
- If you are writing in Tagalog, not Filipino, use this: `lang="tl"`
- For Bikolano, use this: `lang="bik"`
- In Cebuano, use this: `lang="ceb"`
- Hiligaynon, use this: `lang="hil"`
- In Iloko, use this: `lang="ilo"`
- In Pangasinense: `lang="pag"`
- Kapampangan: `lang="pam"`
- Waray: `lang="war"`
- For Philippines languages with no corresponding [ISO-639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php) code, you have to use the generic subtag: `lang="phi"`

Then if you want to write something in Baybayin script you have to enclose it correctly with the script subtag "Tglg". Remember, the format is: language-Script, like so:

- If writing in Filipino and Tagalog using Baybayin script, use: `lang="fil-Tglg"`
- In Bikolano but Baybayin script: `lang="bik-Tglg"`
- Cebuano using Baybayin script: `lang="ceb-Tglg"`
- All other Philippine languages without an ISO-639-2 subtag should use: `lang="phi-Tglg"`

<del datetime="2021-09-24T18:32:17+08:00">Why do we have no `lang="tl-Tglg"` subtag code? Because of *Suppress-Script: Latn* , in the IANA Language Subtag Registry as was shown earlier. If I understood it correctly, it means that the Tagalog language as per the official standard should always be written in the Latin script. I assume then that lang="tl-Tglg" is wrong and applications have the option to ignore it or drop the "Tglg" script subtag. In this case, just use "fil-Tglg".</del>

## ISO-639-3 Languages

There is another subtag that you should learn if you want to target [dialects and macrolanguages](https://web.archive.org/web/20130218160105///www.sil.org:80/iso639-3/macrolanguages.asp). You can find a list from the ISO standard [ISO-639-3](https://web.archive.org/web/20130217113439///www.sil.org:80/iso639-3/codes.asp?). Let's use Bikolano as an example. The format to use is: language-extended_language-Script.

- If you are writing in Central Bikolano, use: `lang="bik-bcl"`
- If writing in Albay Bikolano / Buhi-Daraga: `lang="bik-bhk"`
- If in Iriga Bikolano using the Baybayin script: `lang="bik-bto-Tglg"`
- If in Pandan (Northern Catanduanes) using the Baybayin script: `lang="bik-cts-Tglg"`

The language-***extended_language***-Script is, as of this article, still not yet implemented. The basis for the lang attribute is always the [IANA Language Subtag Registry](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry), once it has been updated to include *extended_language*s then we can start using it where needed.

### The *phi* language subtag

Next is if your language have an ISO-639-3 code and is under or part of the language code "phi" in ISO-639-2, then the *phi* subtag is to be used. This subtag code is considered a **collective language**. Good examples are:

- Kinaray-a language: `lang="phi-krj"`
- Maguindanao language: `lang="phi-mdh"`
- Maranao language written in Baybayin script: `lang="phi-Tglg-mrw"`
- Tausug language written in Baybayin script: `lang="phi-Tglg-tsg"`

As you probably have noticed the format I used was *language-Script-variant* and not *language-extended_language-Script*. My reasoning is simple - the *phi* language code is not really a language, it is accurately called a "collective" language entry in ISO-639-2 for all other Philippine languages **not found** in this version of the ISO language standard. Compare that to the *bik* language code, it was clearly marked as a "macrolanguage" both in ISO-639-2 and ISO-639-3.

Additionally, according to the [World Wide Web Consortium](https://www.w3.org/International/articles/language-tags/) or W3C, **dialects** of macrolanguages are considered/should be written **immediately after** the language subtag. In other words, if your ISO-639-2 code is considered a macrolanguage then you should use the *extended_language* subtag position like `lang="bik-cts-Tglg"`. If it wasn't defined as a macrolanguage, then you should use the *variant* subtag position as is the case in `lang="phi-Tglg-tsg"`.

## Examples, examples, and more examples…

If you website is mainly about Iriga and you write in your own language, then you should adjust your website's header files accordingly:

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

If you want to write "Happy Father's Day" in Baybayin, this is how you do it:

```html
  <bdi lang="fil-Tglg">ᜋᜎᜒᜄᜌᜅ᜔ ᜀᜍᜏ᜔ ᜈᜅ᜔ ᜋᜅ ᜀᜋ</bdi>
```

Simple? Cool! Just remember that when writing language tags, keep it as simple and as short as possible. If you do not have a need to be very specific like say `lang="bik-bcl"` then don't be! Simply use `lang="bik"`. This is especially true for blogs. So if your blog is in Filipino language (!not Tagalog!) then you use:

```html
<html lang="fil">
```

Only be specific when you need it or when your site caters mainly to that particular audience and/or region. Additionally, if you are going to use (which you probably will) other languages and scripts, enclose it always in a span or div element as I've shown in my Baybayin example above.

Easy? Yes it is. It takes time to get used to it, and yes, it is confusing at first. But you will get the hang of it eventually. Go on and update your websites now and start practising marking your content with the correct language and script.

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
