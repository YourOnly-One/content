+++
title = "Philippine ISPs caught hijacking connections"
description = "Philippine ISPs ordered to hijack connections to certain websites."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = "2021-07-25T11:37:38+08:00"                                        # manually adjust to local timezone
lastmod = "2021-07-25T11:37:38+08:00"                                        # manually adjust to local timezone

aliases = ["/2021/07/philippine-isps-caught-hijacking.html"]
slug = "philippines-isp-hijack-connection"
translationKey = "philippines-isp-hijack-connection-2021206"
relCanonical = "https://im.youronly.one/techmagus/philippines-isp-hijack-connection-2021206/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

syndications = ["https://www.facebook.com/techmagus/posts/1856761857860076", "https://www.facebook.com/YourOnly.ONE.ofcl/posts/467888601047042"]

channels = ["techmagus"]
categories = ["internet"]                                                   # taxonomy
keywords = ["internet", "privacy", "security", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["privacy","security"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["images/m/mediafire-no-vpn-ph-gov-isp-ssl-hijack-03.png", "images/mediafire-no-vpn-ph-gov-isp-ssl-hijack-01.png", "images/mediafire-ssl-cert-comparison-01.png"]                                                       # used by og:images, etc.; first image is cover image

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

A friend of mine noticed that Philippine ISPs started to hijack connections to certain websites and they are also using a fake SSL certificate. If a user choose the option to continue despite the warning about an invalid SSL certificate, they will see a Philippine government warning and the related Republic Act explaining why they--our ISPs--are hijacking our connection.

Let's take a look at an example.

<!--more-->

**MediaFire** is a popular file sharing and cloud storage. A file sharing and/or cloud storage service by itself is not "evil" as most governments, politicians, and the corporate world is painting it to be. Unfortunately, as with all services and technologies, there are people who use it for "evil purposes". This was the basis for the Philippine government [supposedly] ordering Philippine ISPs to hijack the connection to **MediaFire**, as shown in the screenshot below.

{{< image
  type="image"

  height=""
  width=""

  src="images/m/mediafire-no-vpn-ph-gov-isp-ssl-hijack-01.png"
  link="images/m/mediafire-no-vpn-ph-gov-isp-ssl-hijack-01.png"
  linkrel="noopener"

  title=""
  caption="Hijacked connection"
  alt=""

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

Based on the message shown in the screengrab above, **MediaFire** <q>is a suspected child sexual abuse or exploitation material (CSAEM)</q>. They then explained that they will <q>initiate decryption of traffic for possible CSAEM content and block access as mandated by Republic Act No. 9775 or the Anti-Child Pornography Act of 2009.</q> In other words, they admit that your connection to **MediaFire** was hijacked and their all-seeing eye is watching you closely.

This is a very bad reality. There is now no doubt that all it takes for Philippine ISPs to intercept our Internet connection is an order from the Philippine government suspecting services and websites of CSAEM and/or whatever other laws they can use to justify breaking the privacy and security of the people.

Google Drive, OneDrive, and Dropbox, probably does not have "illegal content" because they can police their users. But you have to ask the question, how? Could it be they can read all the files uploaded to their storage? We will never know but at least one of those mentioned admitted that they do (it's even in their Terms).

**It is understandable** why they are doing this, no good person would tolerate child abuse and child pornography, that is a line no sane human being should ever cross. However, the way they are doing this policing is never acceptable, this is a clear violation of the user's privacy and hijacking connections is a clear act of compromising the user's security. No one can guarantee what these ISPs will do with the data they can see. They usually can not be held accountable if one of their "trusted" employee leaks confidential information he or she saw while searching for CSAEM materials. It is easy to say they will never do anything else other than to watch out for CSAEM but clearly, all it takes is a government order and we will never know what they are doing with all the other data.

We all know that we can never trust ISPs, government order or not, so let this be a lesson for everyone in the Philippines: encrypt your files before uploading; and use only services which offers end-to-end encryption; and always use [Tor](https://www.torproject.org) (The Onion Router) or better yet a highly reputable VPN. Our **privacy** *and* **security** matters.

{{< image
  type="image"

  height=""
  width=""

  src="images/m/mediafire-ssl-cert-comparison-01.png"
  link="images/m/mediafire-ssl-cert-comparison-01.png"
  linkrel="noopener"

  title=""
  caption="Left: Hijacked connection SSL cert; Right: Encrypted connection and correct SSL certificate"
  alt=""

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

{{% quotebox boxstyle="qbs_generic" qmarkstyle="qbm_doublequotationmark" boxcolour="qbc_red" attribalign="txt_right" srctitle="Re: ISP can still hijack #1790" srclink="https://github.com/DNSCrypt/dnscrypt-proxy/discussions/1790#discussioncomment-1052610" srcrel="noopener external nofollow" attribto="dapphp" attriblink="https://github.com/dapphp" attribrel="noopener external nofollow" %}}
  It looks like your ISP is using gear from Palo Alto networks to intercept your SSL traffic based on the common name in the SSL certificate.
{{% /quotebox %}}

**MediaFire** was also informed and they are looking into addressing this.

---

{{< image
  type="imagecoverattrib"

  link="images/m/mediafire-no-vpn-ph-gov-isp-ssl-hijack-03.png"
  linkrel="noopener"

  title=""
  caption="Warning: Potential Security Risk Ahead"

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
