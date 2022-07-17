+++
title = "[How-To] Access Google Sites and Services via IPv6"
description = "IPv6 is here but how do we access Google services via IPv6 anyway? In this short tutorial, I am going to show you in simple steps how to do just that."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = "2009-12-03T21:31:19+08:00"                                        # manually adjust to local timezone
lastmod = "2010-09-20T17:53:01+08:00"                                     # manually adjust to local timezone

aliases = ["/2009/12/how-to-access-google-sites-and-services.html"]
slug = "access-google-ipv6"
translationKey = "access-google-ipv6-2009337"
relCanonical = "https://im.youronly.one/techmagus/kb/internet/access-google-ipv6-2009337/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["howto", "linux"]                                                   # taxonomy
keywords = ["how to", "linux", "google", "IPv6", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
#tags = [""]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://4.bp.blogspot.com/-h6sAKgKjLWA/XrBAaaYaHtI/AAAAAAAAhe8/Rv-FK3as0hICWlYSC2U2JwizFb0q0IKYACLcBGAsYHQ/s1600/ball-63527_1280.jpg"]                                                       # used by og:images, etc.; first image is cover image

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

Google, the largest search engine today (and the "Microsoft" of the cyberworld), is slowly deploying <abbr class="popper animate" data-popper="Internet Protocol version 6">IPv6</abbr> across their sites. But even if you are already [connected to IPv6](connect-ipv6.md "IPv6 Is Not Scary!! Connect to Next-Gen Internet Now"), you will still not get an IPv6 Google.

Why? Their current IPv6 implementation is currently in its testing phase. All IPv6 access must come from a reliable network that they have to pre-approve, this is the <i>Google over IPv6</i> project.

<!--more-->

## How it works

<figure class="quote_box qbs_generic qbc_lime">
  <div>
    <p>Google over IPv6 uses the IPv4 address of your DNS resolver to determine whether a network is IPv6-capable. If you enable Google over IPv6 for your resolver, IPv6 users of that resolver will receive AAAA records for IPv6-enabled Google services …</p>
    <p>Normally, if a DNS resolver requests an IPv6 address for a Google web site, it will not receive one…</p>
  </div>
  <div class="center"><img src="//web.archive.org/web/20120524193018/https://www.google.com/intl/en/ipv6/images/howitworks1.png" alt="" /></div>
  <div>
    <p>… but a DNS resolver with Google over IPv6 will receive an IPv6 address, and its users will be able to connect to Google web sites using IPv6.</p>
  </div>
  <div class="center"><img class="center" src="//web.archive.org/web/20120524193018/https://www.google.com/intl/en/ipv6/images/howitworks2.png" alt="" /></div>
  <figcaption class="attribution_name txt_right">
    <cite><a href="https://www.google.com/intl/en/ipv6/" rel="noopener external nofollow">Google over IPv6</a></cite>
  </figcaption>
</figure>

So unless you are using a <abbr class="popper animate" data-popper="Domain Name Server">DNS</abbr> with <i>Google over IPv6</i> enabled, the only IPv6 Google website you will be able to use is <a href="https://ipv6.google.com" rel="noopener external nofollow">ipv6.google.com</a>. That's sad! Especially if most of the sites you visit are still hosted on non-IPv6 enabled servers.

Fortunately, there are many good-hearted people and corporations in the world today offering free access to their IPv6 DNS. We have <a href="https://gogo6.com" rel="noopener external nofollow">Gogo6.com</a>'s <a href="https://www.gogo6.com/freenet6" rel="noopener external nofollow">Freenet6</a> DNS and Hurricane Electric's <a href="https://tunnelbroker.net/" rel="noopener external nofollow">Tunnelbroker.net</a> DNS.

But how do we use these IPv6 DNS? Let me show you how.

## Ubuntu Linux way

- Go to Synaptic (System -> Administration -> Synaptic Package Manager)

- Search for "dnsmasq" and install it
- Open a Terminal (Accessories -> Terminal)
- Type:

  ```shell
  gksu gedit /etc/dnsmasq.conf
  ```

- Look for:

  ```bash
  #listen-address=
  ```

- Change it to:

  ```bash
  listen-address=127.0.0.1
  ```

- Look for:

  ```bash
  #server=/localnet/192.168.0.1
  ```

- Add the following after/below it:

  ```bash
  server=/google.com/2001:470:20::2
  server=/google.com/74.82.42.42
  server=/www.google.com/2001:470:20::2
  server=/www.google.com/74.82.42.42
  server=/youtube.com/2001:470:20::2
  server=/youtube.com/74.82.42.42
  server=/www.youtube.com/2001:470:20::2
  server=/www.youtube.com/74.82.42.42
  ```

- Save and close the file

- Still in the Terminal, type:

  ```shell
  gksu gedit /etc/dhcp3/dhclient.conf
  ```

- Look for:

  ```bash
  #prepend domain-name-servers 127.0.0.1;
  ```

- Uncomment that line by removing the sharp ('#') sign

- Save and close the file
- Still in the Terminal, type:

  ```shell
  gksu gedit /etc/resolv.conf
  ```

- Before any other nameserver entries, add this:

  ```bash
  nameserver 127.0.0.1
  ```

- Save and close the file

- Still in the Terminal, type:

  ```shell
  sudo /etc/init.d/dnsmasq restart
  ```

What happens is this: we are using dnsmasq to reroute all queries to google.com to HE's IPv6 DNS which has been confirmed to be <i>Google over IPv6</i> enabled. Any Google services that are not yet using IPv6 or not yet part of the project will simply use IPv4, like the YouTube entry we added (read: <a href="https://www.networkworld.com/article/2238936/lan-wan/google-adding-ipv6-to-youtube.html" rel="noopener external nofollow">YouTube is the IPv6 team's number one priority right now)</a>.

But if you are not using DHCP, then the DHCP edits you did previously will not work. Or if you are using <i>NetworkManager</i> to manage your connection settings, then it will only overwrite your resolv.conf file. Here's what you should do to solve this:

- Open your NetworkManager and go to your network/connection profile (example: eth0)
- Open/edit it and go to the "IPv4 Settings" tab
- In the "DNS servers:" field, simply add this before any other DNS entries you may have:

  ```bash
  127.0.0.1
  ```

- Click "Apply", then close it.

  This way, every time the NetworkManager connects and overwrites the resolv.conf file, it will always add 127.0.0.1 to the file. Just like in the DHCP edits you did above, it ensures that the listening IP being used by dnsmasq is the first DNS your system will check when you are browsing.

In your terminal type:

```shell
ping6 www.google.com
```

You should see something like this:

```shell
ping6 www.google.com
PING www.google.com(tx-in-x68.1e100.net) 56 data bytes
64 bytes from tx-in-x68.1e100.net: icmp_seq=1 ttl=59 time=231 ms
```

These are the Google sites and services tested to be accessible via IPv6 (as of this article):

- Google Sites: <a href="https://sites.google.com" rel="noopener external nofollow">https://sites.google.com</a>
- Google Translate: <a href="https://translate.google.com" rel="noopener external nofollow">https://translate.google.com</a>
- Google Earth: <a href="https://www.google.com/earth/" rel="noopener external nofollow">https://earth.google.com</a>
- Google Moderator: <span class="popper animate removed_link" data-popper="https://moderator.appspot.com">https://web.archive.org/web/20150621104346/https://moderator.appspot.com/</span>
- Google FeedBurner: <a href="https://accounts.google.com/ServiceLogin?service=feedburner&amp;continue=https%3A%2F%2Ffeedburner.google.com%2Ffb%2Fa%2Fmyfeeds&amp;gsessionid=u9hHPZko-UNXqdtUCdPKIg" rel="noopener external nofollow">https://feedburner.google.com</a>
- Google YouTube: <a href="https://www.youtube.com/supported_browsers?next_url=%2F" rel="noopener external nofollow">https://youtube.com</a>
- Google App Engine: <a href="https://appengine.google.com" rel="noopener external nofollow">https://appengine.google.com</a>
- Google Code: <a href="https://code.google.com" rel="noopener external nofollow">https://code.google.com</a>
- Google Docs: <a href="https://docs.google.com" rel="noopener external nofollow">https://docs.google.com</a>
- Google Health: <a href="https://www.google.com/intl/en_us/health/about/" rel="noopener external nofollow">https://health.google.com</a>
- Google Mail ("gmail"): <a href="https://mail.google.com" rel="noopener external nofollow">https://mail.google.com</a>
- Google Wave: <a href="https://support.google.com/answer/1083134?hl=en" rel="noopener external nofollow">https://wave.google.com</a>
- Google Blogs: <span class="popper animate removed_link" data-popper="https://blogsearch.google.com">https://web.archive.org/web/20140819225340/https://blogsearch.google.com/</span>
- Google Images: <a href="https://images.google.com" rel="noopener external nofollow">https://images.google.com</a>
- Google News: <a href="https://news.google.com" rel="noopener external nofollow">https://news.google.com</a>
- Google Maps: <a href="https://maps.google.com" rel="noopener external nofollow">https://maps.google.com</a>
- Google Picasa: <a href="https://picasa.google.com" rel="noopener external nofollow">https://picasa.google.com</a>
- Google Picasa Web Albums: <a href="https://picasaweb.google.com" rel="noopener external nofollow">https://picasaweb.google.com</a>
- Google Accounts: <a href="https://myaccount.google.com" rel="noopener external nofollow">https://www.google.com/accounts</a>
- Google Ad Manager: <a href="https://www.google.com/dfp/" rel="noopener external nofollow">https://www.google.com/admanager</a>
- Google AdSense: <a href="https://www.google.com/adsense/" rel="noopener external nofollow">https://www.google.com/adsense</a>
- Google Analytics: <a href="https://www.google.com/analytics/" rel="noopener external nofollow">https://www.google.com/analytics</a>
- Google Calendar: <a href="https://www.google.com/" rel="noopener external nofollow">https://www.google.com/calendar</a>
- Google Finance: <a href="https://www.google.com/finance" rel="noopener external nofollow">https://www.google.com/finance</a>
- iGoogle: <a href="https://www.google.com.ph/webhp" rel="noopener external nofollow">https://www.google.com/ig</a>
- Google Reader: <a href="https://www.google.com/reader/about/" rel="noopener external nofollow">https://www.google.com/reader/</a>
- Google Search: <a href="https://www.google.com" rel="noopener external nofollow">https://www.google.com</a>
- Google Alerts: <a href="https://www.google.com/alerts" rel="noopener external nofollow">https://www.google.com/alerts</a>
- Google Apps: <a href="https://apps.google.com/" rel="noopener external nofollow">https://www.google.com/apps</a>
- Google Chrome: <a href="https://www.google.com/chrome/" rel="noopener external nofollow">https://www.google.com/chrome</a>
- Google Directory: <span class="popper animate removed_link" data-popper="https://www.google.com/dirhp">https://web.archive.org/web/20111109041904/https://www.google.com:80/dirhp</span>
- Google Mars: <a href="https://www.google.com/mars/" rel="noopener external nofollow">https://www.google.com/mars</a>
- Google Mobile: <a href="https://www.google.com/intl/en/mobile/" rel="noopener external nofollow">https://www.google.com/intl/en/mobile</a>
- Google Moon: <a href="https://www.google.com/moon/" rel="noopener external nofollow">https://www.google.com/moon</a>
- Google Sky: <a href="https://www.google.com/sky/" rel="noopener external nofollow">https://www.google.com/sky</a>
- Google and Space: <span class="popper animate removed_link" data-popper="https://www.google.com/space">https://web.archive.org/web/20110925082258/https://www.google.com:80/space/</span>
- Google Talk: <a href="https://hangouts.google.com/unsupported" rel="noopener external nofollow">https://www.google.com/talk</a>

Not yet accessible via IPv6:

- Google AdWords: <a href="https://www.google.com/adwords/" rel="noopener external nofollow">https://adwords.google.com</a>
- Google Scholar: <a href="https://scholar.google.com" rel="noopener external nofollow">https://scholar.google.com</a>
- Google Orkut: <a href="https://web.archive.org/web/20120515201005/https://www.orkut.com/" rel="noopener external nofollow">https://www.orkut.com</a>

As far as I know, it is not possible to host a "sub-folder" in another server, thus we can safely assume that all Google sites with this URL format: www.google.com/{sitename} are IPv6 enabled. However, Google sites and services that are using a subdomain.google.com URL or any other, can either be IPv6 already or not. Subdomains can easily be pointed to a totally different server somewhere in cyberspace.

## How about Windows users?

For those who are still using Windows XP, you are out-of-luck. Even if you can add an IPv6 DNS, it will not work, I tried it myself and it was confirmed by <a href="https://www.gogo6.com/forum/topic/listForContributor?user=266ea6iid0945" rel="noopener external nofollow">Mikael Lind</a> <a href="https://www.gogo6.com/forum/topics/i-want-to-access-google-in?page=1&amp;commentId=3731159%3AComment%3A24011&amp;x=1#3731159Comment24011" rel="noopener external nofollow">here</a>.

<del>Update for Windows XP users: I found a way to do it and I will be posting it here soon! The life of your too old OS just got a little bit longer.</del>

<del>For Windows 7 users, you will have to wait until I can get a Win7 OS or a machine that I can break. Or better ask the experts in IPv6 like the guys and gals of the <a href="https://www.gogo6.com/main" rel="noopener external nofollow">gogo6 Community</a>.</del>

<b>Update 2010-02-25</b>: Sorry WinXP users you really have to upgrade to Windows 7. The method works but it is not consistent - sometimes it works, sometimes not. It is also <i>very</i> different per machine (it is weird!) even if you have everything duplicated perfectly.

It will only invite frustration and plenty of questions. Again, I recommend upgrading to Windows 7 if you want a consistent and stable IPv6 capability.

<b>Update 2010-09-20</b>: Google Sites, Google Translate, Google Earth, Google Moderator, and Google FeedBurner, are now all IPv6 enabled.

---

{{< image
  type="imagecoverattrib"

  link="https://pixabay.com/en/ball-http-www-crash-administrator-63527/"
  linkrel="noopener external nofollow"

  title="Ball, Crash, Administrator"
  caption=""

  licensecode="pixabay"
  licenseurl="https://pixabay.com/service/license/"
  licensename="Pixabay License"

  attribto="geralt"
  attriburl="https://pixabay.com/en/users/geralt-9301/"
  attribrel="noopener external nofollow"
>}}
