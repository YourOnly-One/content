+++
title = "[How-To] IPv6 is not scary! Connect to next-gen Internet today!"
description = "IPv6 or Internet Protocol version 6 is the answer to our IPv4 problem. What problem? By 2011 or 2012 (according to estimates), there will be no more IPv4…"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

# DATE checked and correct

publishdate = 2009-12-03T10:36:58+08:00                                        # manually adjust to local timezone
lastmod = 2010-03-29T17:53:01+08:00                                     # manually adjust to local timezone

aliases = ["/kb/internet/ipv6-connect-today-2009262", "/2011/09/how-to-ipv6-is-not-scary-connect-now.html"]
slug = "ipv6-connect-today"
translationKey = "ipv6-connect-today"
relCanonical = "https://im.youronly.one/techmagus/kb/internet/ipv6-connect-today/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
disqus_identifier = "ipv6-connect-today-2009262"                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["howto", "linux"]                                                   # taxonomy
keywords = ["how to", "linux", "IPv6", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
#tags = [""]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://img.youronly.one/publicdomain/ball-63527_1280.webp"]                                                       # used by og:images, etc.; first image is cover image

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (Yuki)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

*IPv6* or *Internet Protocol version 6* is the answer to our *IPv4* problem. What problem? By 2011 or 2012 (according to estimates), there will be no more IPv4 addresses left. This means that, anyone with a need to have a static IP address will not be able to get any for their project or service.

When this day comes, someone must start finding IP address owners who does not really need a static address and give it to someone who needs it seriously. We may even see owners starting to sell their extra IPs at a price far more expensive that what it is worth today.

<!--more-->

But that will not happen, because two decades ago, the powers-that-be already started experimenting with IPv6 which will give us 2<sup>128</sup> addresses. That is equivalent to 340,282,366,920,938,463,463,374,607,431,768,211,456 IPv6 Addresses, according to my *Einstein* brain calculation :p Or simply: 340 with 36 zeroes (I admit, I used a calculator).

Compare that to IPv4 which only have 2<sup>32</sup> or 4,294,967,296 IP addresses. It is a huge difference! IPv6 which use 128-bit addresses and IPv4 which is only 32-bit. Each computer in the world can now have its own IP Address and we are only scratching the surface of IPv6. In fact, if we subtract the number of IPv4 addresses we have, we still have 340,282,366,920,938,463,463,374,607,427,473,244,160 IPv6 addresses available.

I know you have plenty of questions but time is not on our side. What I am going to answer for you today is how you can start connecting to the IPv6 Internet without waiting for your ISP to start implementing it.

For this tutorial or How-To Guide, I am going to show you how I setup my <del>Ubuntu Linux 9.10 "Karmic Koala"</del> Linux Mint 11 "Katya" 64-bit (based on Ubuntu 11.04 "Natty Narwhal"). So let's begin!

- Go to Synaptic (System -> Administration -> Synaptic Package Manager)
- Search for: miredo; gogoc; and radvd and install all three.
- Open a terminal (Accessories -> Terminal)
- Type:

  ```shell
  sudo /etc/init.d/radvd stop
  ```

- Type:

  ```shell
  gksu gedit /etc/gogoc/gogoc.conf
  ```

- If your main connection is not `eth0` then change `if_prefix=` accordingly

- If you are setting this up on a workstation computer, then change `host_type=router` to `host_type=host`
- Type:

  ```shell
  sudo /etc/init.d/gogoc restart
  ```

**Update 2010-03-29:** Additional step from Ubuntu 10.04 "Lucid Lynx" and up.

- Still on your terminal, type:

  ```shell
  gksu gedit /etc/default/gogoc
  ```

- Look for `# CHECK_KEYFILE="yes"` and change it to `CHECK_KEYFILE="no"`

**Update 2009-12-23:** An update from <a href="https://mobile.twitter.com/nacnud" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">Jeremy Duncan</a> on setting up your Linux box as a router.

Make sure `IPV6FORWARDING` is set to yes in `/etc/sysconfig/network` like so: `IPV6FORWARDING=yes`.

You are done! To test if your IPv6 is working do or visit the following:

- In your terminal, type:

  ```shell
  ping6 ipv6.google.com
  ```

  it should show something like this:

  ```shell
  ping6 ipv6.google.com
  PING ipv6.google.com(fx-in-x68.1e100.net) 56 data bytes
  64 bytes from fx-in-x68.1e100.net: icmp_seq=1 ttl=50 time=496 ms
  ```

- Open up your favorite browser and visit <a href="https://test-ipv6.com" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">test-ipv6.com</a>

- and/or <a href="https://ipv6-test.com" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">ipv6-test.com</a>
- and/or <a href="https://ip6.me" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">ip6.me</a>

<div class="float_right" style="margin-left: 10px; margin-bottom: 10px;"><script type="text/javascript" src="https://ipv6.he.net/v4ex/sidebar.js"></script></div>

## Why use a Tunnel Broker if we have Miredo/Teredo?

For one, Miredo/Teredo was developed only as a temporary gateway to the IPv6 Internet. In fact, it was set as the last access point when you have other IPv6 implementation like a tunnel broker.

Another reason is to have a static IPv6 address (even if your ISP gives you a dynamic IPv4 address). For this to work, you have to register an account over at Gogo6.com's <a href="https://www.gogo6.com/freenet6" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">Freenet6 service</a> (<a href="https://www.gogo6.com/freenet6/registration" rel="noopener external nofollow" referrerpolicy="strict-origin-when-cross-origin">register here</a>).

Then you have to edit your gogoc.conf, follow the instructions below:

- Open a Terminal again
- Type:

  ```shell
  sudo /etc/init.d/radvd stop
  ```

- Type:

  ```shell
  gksu gedit /etc/gogoc/gogoc.conf
  ```

- Adjust your existing gogoc.conf with this one:

  ```bash
  userid=ENTER_YOUR_FREENET6_USERNAME_HERE
  passwd=ENTER_YOUR_FREENET6_PASSWORD_HERE
  server=authenticated.freenet6.net
  auth_method=any
  ```

- Type:

  ```shell
  sudo /etc/init.d/gogoc restart
  ```

You're done! From now on, you will have the same IPv6 address everytime you connect to Freenet6's network. However, do note that you still get a different static IP depending on which Freenet6 server you are connected. If you really want to connect to the exact same server simply change this configuration in your gogoc.conf

```bash
always_use_same_server=no
```

to:

```bash
always_use_same_server=yes
```

But before you do that, please connect to Freenet6 at least once, so your gogoc daemon will have a list of servers to connect to and be able to choose the "best" one for you. Then set it up as instructed, and you'll be connecting to that same "best" server everytime the gogoc daemon is (re)-started. Easy?

Welcome to the next generation of the Internet - the IPv6 world.

---

{{< image
  type="imagecoverattrib"

  link="https://pixabay.com/en/ball-http-www-crash-administrator-63527/"
  linkrel="noopener external nofollow"

  title="web administrator"
  caption=""

  licensecode="publicdomain"
  licenseurl=""
  licensename="Public Domain"

  attribto="geralt"
  attriburl="https://pixabay.com/en/users/geralt-9301/"
  attribrel="noopener external nofollow"
>}}
