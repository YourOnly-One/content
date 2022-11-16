+++
title = "Google Public DNS vs. OpenDNS"
description = "Google DNS vs. Open DNS, which is faster anyway? From where I am, Google DNS showed up as the winner. Test it yourself!"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

# DATE checked and correct

publishdate = "2009-12-07T17:43:23+08:00"                                        # manually adjust to local timezone
lastmod = "2009-12-07T17:43:23+08:00"                                        # manually adjust to local timezone

aliases = ["/2009/12/google-public-dns-vs-opendns.html"]
slug = "google-open-dns"
translationKey = "google-open-dns-2009341"
relCanonical = "https://im.youronly.one/techmagus/google-open-dns-2009341/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
#categories = [""]                                                   # taxonomy
keywords = ["reviews", "google", "dns", "opendns", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["reviews"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://2.bp.blogspot.com/-My6VQMwrbWw/XrFatMOpyCI/AAAAAAAAhfU/SNcOBNQsm8cqpGfY60VVSYYMrNKXdKHuACPcBGAsYHg/s1600/GoogleDNS-vs-OpenDNS.png"]                                                       # used by og:images, etc.; first image is cover image

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

Last week, the search giant **Google** launched yet another new service to the public - *Google Public DNS* ("GoogleDNS"). This new service rocked the Internet and everyone, regardless of his/her location, felt the disturbance in cyberspace.

Immediately, netizens dug it, highly questioned Google's Privacy Policies (especially the hardcore Google haters), security, and so on (and we are not going to talk about that). It even prompted an article from the world's number one alternative DNS service <a href="https://blog.opendns.com/2009/12/03/opendns-google-dns/" rel="noopener external nofollow">*OpenDNS*</a> (which I stopped using almost a month ago).

The question is, who wins when it comes to speed? GoogleDNS or OpenDNS? The winner is GoogleDNS, I'll show you why…

<!--more-->

While doing some research on running my own caching DNS I stumbled on <a class="popper animate" href="https://www.manu-j.com/blog/opendns-alternative-google-dns-rocks/403/" rel="noopener external nofollow" data-popper="Google DNS vs OpenDNS: Google Rocks for International Users">Google DNS vs OpenDNS: Google Rocks for International Users</a>, and clearly showed that GoogleDNS is the fastest for non-Western countries.

Using the script posted on the blog I tried it out myself. Here's my result testing from Makati City, Philippines, using Globe Innove (DSL/Broadband).

<figure class="figure_box">
  <div class="separator" style="clear: both; text-align: center;"><a href="https://2.bp.blogspot.com/-My6VQMwrbWw/XrFatMOpyCI/AAAAAAAAhfU/SNcOBNQsm8cqpGfY60VVSYYMrNKXdKHuACPcBGAsYHg/s1600/GoogleDNS-vs-OpenDNS.png" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img loading="lazy" border="0" src="https://2.bp.blogspot.com/-My6VQMwrbWw/XrFatMOpyCI/AAAAAAAAhfU/SNcOBNQsm8cqpGfY60VVSYYMrNKXdKHuACPcBGAsYHg/s1600/GoogleDNS-vs-OpenDNS.png" data-original-width="528" data-original-height="504" /></a></div>
  <figcaption class="attribution_copyright txt_center">
    <p xmlns:dct="http://purl.org/dc/terms/" xmlns:vcard="http://www.w3.org/2001/vcard-rdf/3.0#">
      <small>"<a href="https://2.bp.blogspot.com/-My6VQMwrbWw/XrFatMOpyCI/AAAAAAAAhfU/SNcOBNQsm8cqpGfY60VVSYYMrNKXdKHuACPcBGAsYHg/s1600/GoogleDNS-vs-OpenDNS.png" rel="dct:title noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">GoogleDNS-vs-OpenDNS</a>" by <a href="https://iam.youronly.one" rel="dct:creator noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">Yahuhanan Yukia Sese Cuneta</a> is licensed under <a href="https://creativecommons.org/licenses/by-sa/4.0/" rel="license noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">CC BY-SA 4.0 International</a>.</small>
  </figcaption>
</figure>

As you can see above there is a more or less 96ms difference between GoogleDNS and OpenDNS from my location. Is it big? For me it is. The fastest I can reach my choice of Domain Name System ("DNS"), the fastest I will be pointed to the location of the website I want to load. That is what DNS servers are for, it resolves the domain names to an IP address.

This test gives me a clear reason why I should switch to GoogleDNS and suggest it to other people too. As for privacy issues, here's what Google has to say about it:

<figure class="quote_box qbs_generic qbc_lime">
  <blockquote cite="https://code.google.com/speed/public-dns/faq.html#privacy">
    Google Public DNS complies with Google's main privacy policy, which you can view at our <a href="https://www.google.com/intl/en/policies/privacy/" rel="noopener external nofollow">Privacy Center</a>. With Google Public DNS, we collect IP address (only temporarily) and ISP and location information (in permanent logs) for the purpose of making our service faster, better and more secure. Specifically, we use this data to conduct debugging, to analyze abuse phenomena and to improve our prefetching feature. After 24 hours, we erase any IP information. For more information, read the Google Public DNS <a href="https://developers.google.com/speed/public-dns/privacy?csw=1" rel="noopener external nofollow">privacy page</a>.
  </blockquote>
  <figcaption class="attribution_name txt_right">
    <cite><a class="popper animate" href="https://developers.google.com/speed/public-dns/faq?csw=1#privacy" rel="noopener external nofollow" data-popper="What information does Google log when I use the Google Public DNS service?">What information does Google log when I use the Google Public DNS service?</a></cite>
</figure>

There are other reasons like GoogleDNS is being operated based on the standards for DNS operations. Not like OpenDNS, they break the standards by not returning NXDOMAIN ("Non-eXistent Domain"). Instead, if you enter a non-existent domain you are redirected to OpenDNS search page. Some top-level domain owners do that and many ISPs too. Not to mention the reason I stopped using OpenDNS was because someone registered or failed to release a range of dynamic IPs which prevented me from accessing some sites.

Switching is easy, just point your DNS to **8.8.8.8** and **8.8.4.4**. For a more detailed instruction, if you do not know where to do the change, visit Google's <a href="https://developers.google.com/speed/public-dns/docs/using?csw=1" rel="noopener external nofollow">instruction page</a>.

However, the choice is up to you. We differ in our needs and criteria. As I have said earlier, I am researching about running my own DNS which might give better results. Besides, if you really want speed and you do not trust Google or OpenDNS or any other public DNS service, then running your own local DNS is really the only solution. Your desktop or laptop or even your netbook is more than enough to run your own!

<del datetime="2021-10-09T14:35:23+08:00">Anyway, here is the bash script that you can use to run the test yourself if you have a GNU/Linux or Mac machine.</del>

---

Further reading:

- <a class="popper animate" href="https://www.manu-j.com/blog/opendns-alternative-google-dns-rocks/403/" rel="noopener external nofollow" data-popper="Google DNS vs OpenDNS: Google Rocks for International Users">Google DNS vs OpenDNS: Google Rocks for International Users</a>
- <a class="popper animate" href="https://googlecode.blogspot.com/2009/12/introducing-google-public-dns-new-dns.html" rel="noopener external nofollow" data-popper="Introducing Google Public DNS: A new DNS resolver from Google">Introducing Google Public DNS: A new DNS resolver from Google</a>
- <a class="popper animate" href="https://blog.opendns.com/2009/12/03/opendns-google-dns/" rel="noopener external nofollow" data-popper="Some thoughts on Google DNS">Some thoughts on Google DNS</a>
- <a class="popper animate" href="https://developers.google.com/speed/public-dns/?csw=1" rel="noopener external nofollow" data-popper="Google Public DNS">Google Public DNS</a>

---

{{< image
  type="imagecoverattrib"

  link="https://2.bp.blogspot.com/-My6VQMwrbWw/XrFatMOpyCI/AAAAAAAAhfU/SNcOBNQsm8cqpGfY60VVSYYMrNKXdKHuACPcBGAsYHg/s1600/GoogleDNS-vs-OpenDNS.png"
  linkrel="noopener"

  title="GoogleDNS vs OpenDNS"
  caption=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
