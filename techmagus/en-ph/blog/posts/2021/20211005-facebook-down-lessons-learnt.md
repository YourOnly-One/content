+++
title = "Lessons learnt from FacebookDown"
description = "What lessons should we learn from the longest downtime of Facebook, Instagram, Messenger, and WhatsApp?"                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

date = "2021-10-06T06:21:07+08:00"                                        # manually adjust to local timezone
lastmod = "2021-10-06T06:21:07+08:00"                                        # manually adjust to local timezone

#aliases = [""]
slug = "lessons-learned-facebook-down"
translationKey = "lessons-learned-facebook-down-2021279"
relCanonical = "https://im.youronly.one/techmagus/lessons-learned-facebook-down-2021279/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["web"]                                                   # taxonomy
keywords = ["web", "federation", "decentralisation", "decentralization", "web 3.0", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["federation", "decentralization"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://img.youronly.one/p/techmagus/ddfon/decentralisation-01.webp", "https://img.youronly.one/p/techmagus/ddfon/friendica-01-frio-profile.webp", "https://img.youronly.one/p/techmagus/ddfon/hubzilla-01.webp", "https://img.youronly.one/p/techmagus/ddfon/zap-01-logo.svg", "https://img.youronly.one/p/techmagus/ddfon/misskey-01-hashtag.webp", "https://img.youronly.one/p/techmagus/ddfon/pixelfed-01-trending.webp", "https://img.youronly.one/p/techmagus/ddfon/mastodon-01-dashboard.webp", "https://img.youronly.one/p/techmagus/ddfon/peertube-01-discover.webp", "https://img.youronly.one/p/techmagus/ddfon/keybase-01-chat.webp", "https://img.youronly.one/p/techmagus/ddfon/matrix-01-element_client.webp", "https://img.youronly.one/p/techmagus/ddfon/session-01.webp"]                                                       # used by og:images, etc.; first image is cover image

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

The longest downtime in the history of Facebook, Instagram, Messenger, and WhatsApp, should have had triggered meetings in many companies on business continuity and the importance of having a Plan B and a Plan C. This will also be remembered and used in schools and studies as the number one example on how not to setup security systems.

Yet main are asking: what else is there other than Facebook, Instagram, Messenger, and WhatsApp? They cornered the market and are as good as a monopoly. They are *the Internet*. They are *the social web*. Right?

**NO** and *no*.

<!--more-->

It was around 15:40 UTC when trouble began which led to Facebook, Instagram, Messenger, and WhatsApp, to disappear from the Internet.[^a] It was only by 21:28 UTC that their services were reconnected to the Internet[^a], six hours of downtime for four services millions, if not billions, of people rely on.

There are a lot of factors which contributed to the longest downtime of Facebook and its services, one such is even Facebook relies on their own network to be connected to the Internet.[^b]

{{< tweet user="sheeraf" id="1445099150316503057" >}}

But how about you? Do you have an online service which relies on Facebook as your customer's login method? Or, maybe you have an online business and your only platform is Facebook and Instagram? How about communicating with your family, are you only relying on Messenger? There are also those who are using WhatsApp as a communication platform for their critical services, like say emergency response, what happens then if there is another major downtime?

{{< tweet user="nixcraft" id="1445121124912676867" >}}

[^a]: Cloudflare: [Understanding How Facebook Disappeared from the Internet](https://blog.cloudflare.com/october-2021-facebook-outage/)
[^b]: Sheera Frenkel: [… employees unable to enter buildings this morning … because their badges weren't working to access doors](https://twitter.com/sheeraf/status/1445099150316503057)

## Lessons Learnt

It is not only Facebook who should learn from #FacebookDown, #InstagramDown, #MessengerDown, and #WhatsAppDown, all of us should learn from this. Here are some that I think we should all take into consideration.

1. If your online service only offers Facebook as account creation and login method, it is time to add another login method including the traditional username and password.
1. If your online service separate accounts created with Facebook, it is time to give your customers an option to add another login method including setting up a password.
1. If you are part of a critical/emergency response group and WhatsApp is your only communication platform, it is time to look for alternatives, at least as a backup. What is important is the need for the backup service readily available instead of suddenly going through account creation, searching, adding, and learning how to use the app and service.
1. If you have an online business, or you earn through your channels in Facebook and Instagram, it is time to find another platform where your fans can continue to follow you in case another major downtime occurs.
1. If socializing online is the air you breath, better join other platforms lest something happens to you.

There are other lessons we can list but will probably fall in one or two with what we've already listed above. As end-users of someone else's platform and/or service, we should never rely on it solely, we need to be ready when it disappears for whatever reason.

Do I have recommendations? I sure do.

## Federated social media and social network services

Us, and our family and friends, signed up in the same social media and social network platforms because there is no way to communicate with each other if we are on different services. But did you know that this is an outdated model and it already is possible to be on different platforms and services and yet socialize with each other? Yes, this is called "federation" and these federated platforms and services are collectively called as the "fediverse".

If you think that this is new, surprise! Federation has been around since 2008, and for communication or messengers, it has been around since 1999 (called "XMPP" or formerly "Jabber"). With that said, here are some of the services I personally recommend.

### Friendica

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/friendica-01-frio-profile.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/friendica-01-frio-profile.webp"
  linkrel="noopener"

  title="Frio Theme"
  caption="User Profile"
  alt="Frio Theme User Profile"

  attribalign=""

  licensecode="allrightsreserved"
  licenseurl=""
  licensename=""

  attribto="Friendica"
  attriburl="https://friendi.ca"
  attribrel="noopener external nofollow"
>}}

**Friendica**, formerly known as *Friendika*, with project name *Mistpark*), is a distributed and federated social network. It was one of the very first software which started the fediverse.

#### Features

- Post "status updates"
- photos, albums
- hashtags
- privacy
- military encryption
- Calendar
- Show different "profiles" to different people and communities
- follow other profiles and hashtags
- different themes and addons
- can connect with those in: Diaspora, Mastodon, Pleroma, Hubzilla, WordPress, Nextcloud, Pixelfed, PeerTube, Twitter, and more.

If you want to give it a spin, choose one of the servers available [here](https://friendi.ca/#try). Remember, it does not matter which server you choose, you can connect with everyone in the fediverse.

### Hubzilla

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/hubzilla-01.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/hubzilla-01.webp"
  linkrel="noopener"

  title="Hubzilla"
  caption=""
  alt="Hubzilla"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Hubzilla** is similar to *Friendica* in that it was started by the same developer, [Mike Macgirvin](https://macgirvin.com/channel/mike). Macgirvin is a man of vision and a strong advocate and proponent of freedom of choice, decentralization, federation, and anti-censorship. With *Hubzilla*, he developed a unique feature that no other fediverse platform (other than *Zap*) have to this very day: **nomadic identity and cloning**.

#### What is nomadic identity and cloning

Nomadic identity means true ownership of online identity. With Hubzilla, you don't have an account on a server, you own an identity that you can take with you across the grid. You can clone a channel across multiple hubs for resilience against network failures or censorship, or you can completely move a channel from one hub to another, taking your data and connections with you.[^c]

You can have a channel in example.com and then clone it in example.net. While it appears that these are two separate accounts because these are on two different servers, they are actually one and the same. Any platform which understands the underlying technology of nomadic identity will treat both as a single channel, if you login via example.net, you will receive the same communication, connections, and be able to send back replies or create new posts/updates as if you logged-in via example.com.

When it comes to features, Hubzilla shares almost the same set with Friendica but by no means the code are identical. But this part? This is good for developers and server operators, as a user, rest assured that you are in good hands. Besides, nomadic identity sure is a great feature that all other platforms should implement, right?

You can sign-up for a Hubzilla channel (or account if you will) in any of the available servers located [here](https://hubzilla.org/pubsites).

[^c]: Hubzilla: [Nomadic identity and cloning](https://hubzilla.org//page/hubzilla/hubzilla-project)

### Zap

{{< image
  type="image"

  height="50%"
  width="50%"

  src="https://img.youronly.one/p/techmagus/ddfon/zap-01-logo.svg"
  link="https://img.youronly.one/p/techmagus/ddfon/zap-01-logo.svg"
  linkrel="noopener"

  title="Zap"
  caption="logo"
  alt="Zap logo"

  attribalign=""

  licensecode="allrightsreserved"
  licenseurl=""
  licensename=""

  attribto="Zap"
  attriburl="https://zotlabs.com/zap/"
  attribrel="noopener external nofollow"
>}}

**Zap** povides an experience that is familiar and comfortable to Facebook users, with some additional functionality and with some of the best privacy and anti-abuse features available in the Fediverse today.[^d]

[^d]: Zap: [Zap Fediverse Server, an ethical alternative](https://zotlabs.com/zap/)

#### Features

- Groups: public, private, and moderated. It works across nearly all fediverse platforms.
- Events: Calendar and attendance; automatic timezone adjustment; birthday notifications for friends
- Permissions: Granular permissions control over each feature
- Cloud storage: built-in network file storage with social networking access/permissions.
- Editor: supports markdown, html, and bbcode
- Lists: sometimes referred to as *circles* or *aspects*
- Friend Zoom: set the degree of "closeness" with your connections and then use friend zoom to filter your dashboard stream to show only close friends or everyone.
- Nomad protocol: (see "Nomadic identity" above, under *Hubzilla*)

If you are ready to jump in and create your online social web identity, choose any server [here](https://z.macgirvin.com/sites?project=zap).

### Misskey

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/misskey-01-hashtag.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/misskey-01-hashtag.webp"
  linkrel="noopener"

  title="Misskey"
  caption="Stream"
  alt="Misskey Stream"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Misskey** is a decentralized microblogging platform. It exists within the Fediverse and is mutually linked with other social media platforms.[^e] It was started by [しゅいろ (syuilo)](https://misskey.io/@syuilo), a Japanese developer, and were joined by other contributors. Misskey is the platform of choice in Japan when it comes to the fediverse.

[^e]: Misskey: [Let's start Misskey](https://join.misskey.page)

#### Features

- posting or status updates
- reactions
- different UI options
- Misskey Drive
- chat
- photo gallery
- groups
- pages
- private messages
- lists
- channels
- antennas
- Misskey Games

You can find a Misskey community which perfectly fits you [here](https://join.misskey.page/instances).

### Pixelfed

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/pixelfed-01-trending.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/pixelfed-01-trending.webp"
  linkrel="noopener"

  title="Pixelfed"
  caption="Trending view"
  alt="Pixelfed Trending view"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Pixelfed** is a federated, privacy-focused, photo sharing platform part of the fediverse. The user interface of Pixelfed today should be very familiar with fans of Instagram which means it should be a no-brainer to use Pixelfed as a photo sharing platform.[^f]

[^f]: Pixelfed: [A free and ethical photo sharing platform](https://pixelfed.org)

#### Features

- ad-free: no ads in timelines or anywhere
- chronological: timelines properly ordered, no algorithms
- discover: explore new content and creators
- filters: add optional filters to your photos
- photo albums: share your photos, one post at a time
- privacy focused: no third-party analytics or tracking included
- two-factor authentication: secure your account
- content warnings: auto-detection if a photo and/or comment is possibly sensitive and automatically blur/hide it
- disable comments: ability to turn-off comments per post
- license declaration: include photo license information
- hide follower and following count
- mute accounts
- private accounts
- private posts
- unlisted posts: public posts but are not listed in the global public timeline/stream

You can start uploading your photos into the fediverse today by joining any [Pixelfed instance](https://fedidb.org/software/pixelfed).

### Mastodon

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/mastodon-01-dashboard.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/mastodon-01-dashboard.webp"
  linkrel="noopener"

  title="Mastodon"
  caption="Dashboard"
  alt="Mastodon Dashboard"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Mastodon** is a network of thousands of communities operated by different organizations and individuals that provide a seamless social media experience.[^g] It can also connect to other platforms like Friendica, Hubzilla, Zap, Misskey, Pixelfed, PeerTube, Write.as, and any that is connected to the social web standard, ActivityPub, a decentralized social networking protocol.

[^g]: Mastodon: [Social networking, back in your hands](https://joinmastodon.org)

#### Features

- effective anti-abuse tools
- moderators
- 500 characters or more
- emojis and custom emojis
- spoiler tags
- content warning
- status updates

If you are regularly use Twitter and you like its flow, Mastodon is the right platform for you. [Join Mastodon](https://joinmastodon.org/communities) today and connect with everyone in the fediverse.

### PeerTube

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/peertube-01-discover.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/peertube-01-discover.webp"
  linkrel="noopener"

  title="PeerTube"
  caption="Discover view"
  alt="PeerTube Discover view"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**PeerTube**, developed by *Framasoft*, is a free and decentralized alternative to video platforms, providing over 400,000 videos published by 60,000 users, viewed over 15 million times[^h], from all over the fediverse.

PeerTube is not meant to be come a huge platform that would centralize videos from all around the world. Rather, it is a network of inter-connected small videos hosters. Users can still watch videos hosted from another server and their own uploaded videos can be seen in other PeerTube servers.

And because PeerTube is part of the fediverse, anyone from the fediverse can leave a comment on a PeerTube-hosted video directly from their own platform.

[^h]: PeerTube: [A decentralized and free/libre alternative to video broadcasting services](https://joinpeertube.org)

#### Features

- import videos from other platforms
- license information
- hashtags
- channels
- ad-free
- tracker free
- whenever necessary, it can use peer-to-peer (P2P) protocol to broadcast viral videos
- history
- subscriptions
- playlists

Ready to upload your videos and be seen by countless of fediverse citizens? Find the best server that suits your needs in this [page](https://joinpeertube.org/instances#instances-list).

## Communication platforms

### Keybase

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/keybase-01-chat.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/keybase-01-chat.webp"
  linkrel="noopener"

  title="Keybase"
  caption="Chat view"
  alt="Keybase Chat view"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Keybase** is most secured platform and service for messaging, file-sharing, file hosting, web hosting, file encryption, and text encryption. On top of that, Keybase is the easiest way to verify your online accounts and PGP keys.[^k]

Keybase Teams which offers 100 GB of storage per team and if you choose to host your files and website on your personal account, you will get a whopping free 250 GB cloud storage. If you know how to use git, you can use Keybase git and use it as your source file for hosting, like this blog.

[^k]: Keybase: [End-to-end encryption for things that matter](https://keybase.io)

#### Features

- Online identity verification
- End-to-end encrypted chat: direct chatting, private group, and public chatrooms
- Files for both Personal and Teams
- Teams and sub-teams, each with separate end-to-end encrypted chat channels
- Sites or Keybase hosting
- Keybase git: for both Personal and Teams; can also be used to host your website
- Wallet: to store your Stellar Lumens (XLM)
- Encrypt, decrypt, sign, and verify files and text manually. Here are examples:

  - Text encryption (decrypt this using Keybase)

    > BEGIN KEYBASE SALTPACK ENCRYPTED MESSAGE. kiPgBwdlv6bV9N8 dSkCcFVY51MqZ0Z jBhax0vmrFJnfxR fKGP8dQPl4QGdca VXX0fJ5dPQd8LPt fVZZHeiosRH3G2G aHISVcOaSDzkxGO Jzc473w8jfROHLB qjnBybJ7v1lPl2A ahivzqJlEVbdUqF xyOmsy2gw73KGak OLKpm2gHTOSlRA4 lN8JL1hDAoA0zww J6p17kYapfilkG9 0oPJQbYBddvW2oe 8h60aYtaXFkZtuw Upe8JRMEWA8rb9k yGq1rrR1iRZRHqQ N1DNsDkkwYcnOBG 1jVo6qC5s119yei OI0iZzxn0QIonnq EZT1BTXfNV8jLdt LlWUetCYjZX97IV W2WqklHqoCfJckJ 21gyWTDUDVyULET IhTtq6TWebof3zs K45laDdgfMMk8pO hxegpPToTMz0flR DS5D5WQv0scyHyH OlsphN9yzcmp5E4 AsU1hXMQYyeg1g5 k3AaSPpKAKBr1QB nMLA5nKVYMhGRic 0RWgfO1Ka988tVT 2DocXdLvAJhN1W4 o1tE46l2nt9mdPi B0o1fVKJ1ZFv6Pj Sj9HcoTtrwX4Yc1 x4H1vrYn8Iy1ixK m3jvocnQlF4XhLO 0eaeXI4LKh2gRqv aKOzVuQ6d2Tpt1g Y20j1yj8CFFg5Vq EplbHmaVxMDPvZ7 7T6HDZGjZ6MPcIE M9qGktljj3Gtv7a rz4GqOoCAbS733m J6N0gzRCuyKGFqc 15liiR8iPro0HJa QBGFHOTQArzJoNH 3kY7PfX00wJcyGt JC80YSp. END KEYBASE SALTPACK ENCRYPTED MESSAGE.

  - Text signing (confirm I wrote this message by verifying the signature in Keybase)

    > To Amyrei,
    >
    > I'm just a boy, standing in front of a girl, asking her to love him.
    >
    > From your secret admirer,
    >
    > I'M YourOnly.One

    > BEGIN KEYBASE SALTPACK SIGNED MESSAGE. kXR7VktZdyH7rvq v5weRa0zkP4VNyC 8WftM9nW4fgPe6n Zl3jKJsRhCjvlTD OXqz3yNPCDKpvKy Rj1fKVuc1iEn5x6 QyFOb76HQvVRy3B wF50Os0vkSv2Wgz U5nB6WXpanovzVT 5GWjzdQQASbv8O4 h6dPaDRzjtP80eU Uax3jtDZh71OSF3 icWhpVQLYL8QjLm MDDWN19aCn9ICr0 kpt457g7TpuOke7 fnrcIovfAAhGt7l yFfYHtgMMTVrolv DdaPeMRcJCIKh31 DBHqNkdGzeSTKOa dqY6QqKF9wDUHWT l7hRNKprld1GNBd Rng7c9gB2NPny70 yY2CSUBViAf1Pb2 ILvVGpGmz. END KEYBASE SALTPACK SIGNED MESSAGE.

#### Get started with Keybase

- {{< reflangtitle path="20200608-create-keybase.md" >}}

- {{< reflangtitle path="20200609-verify-account-keybase.md" >}}

### Matrix

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/matrix-01-element_client.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/matrix-01-element_client.webp"
  linkrel="noopener"

  title="Matrix"
  caption="Element Web Client"
  alt="Matrix Element Web Client"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Matrix** is a secure, decentralised, real-time communication platform. Conversations in Matrix are replicated over all the servers participating in, there are no single point of control or failure. It also provides state-of-the-art end-to-end encryption which ensures that only the intended recipients can ever decrypt your messages, while giving a warning if any unexpected devices are added to the conversation.[^i]

While there is far more to Matrix than what were mentioned, those great features only concerns the developers and server hosts. If your company is looking for a communication platform and you would like to know more about *Matrix*, visit their [official website](https://matrix.org).

[^i]: Matrix: [An open network for secure, decentralized communication](https://matrix.org)

#### Features

- Apps available in Android
- Apps available in iOS
- Web client
- Desktop clients for Windows, Linux, and Mac
- Commandline clients
- end-to-end encryption
- bridges to other networks

Try Matrix [today](https://matrix.org/docs/projects/try-matrix-now/)!

### Session

{{< image
  type="image"

  height="80%"
  width="80%"

  src="https://img.youronly.one/p/techmagus/ddfon/session-01.webp"
  link="https://img.youronly.one/p/techmagus/ddfon/session-01.webp"
  linkrel="noopener"

  title="Session"
  caption="Linux Client"
  alt="Session Linux Client"

  attribalign=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}

**Session** is an end-to-end encrypted messenger that minimises sensitive metadata, designed and built for people who want absolute privacy and freedom from any form of surveillance.[^j]

[^j]: Session: [Send Messages, Not Metadata](https://getsession.org)

#### Features

- No phone numbers and email addresses: Session accounts are completely anonymous.
- No data breaches: Session doesn't collect data so there's nothing to leak.
- No footprints: Send messages through Session's onion routing network and leave no trace.
- Censorship resistant: With no central point of failure, it's harder to shut Session down.
- Open source: Session's code has nothing to hide. Anyone can view, audit, and contribute.
- Group chats: private and open groups
- Voice messages
- Attachments: don't upload those documents in unencrypted services. Send all your files, images, and attachments through a network that takes your privacy seriously.

[Download and use Session](https://getsession.org/download) in your desktop or mobile phone.

## Final words

I hope that the above list of platforms and services are more than enough to give you a start in building your backup plan. While many would say that you should migrate, and probably even delete your Facebook, Instagram, Messenger, and WhatsApp accounts, here at **YourOnly.One** I am only suggesting that you should have a backup platform and service. You can keep using Facebook, Instagram, Twitter, and WhatsApp, but not having a ready alternative or secondary platform and service after the #FacebookDown, #InstagramDown, #MessengerDown, and #WhatsAppDown we had today is a decision you will regret when, not *if* but **when**, it happens again.

Last but the most important of all, it is time to embrace fully the decentralization, distribution, and federation of data, platforms, and services. What happened today has proven that this is the only logical step to ensure that the Internet, and the services we rely on, will continue to exist and work.

Enjoy and Shalom!

---

{{< image
  type="imagecoverattrib"

  link="https://img.youronly.one/p/techmagus/ddfon/decentralisation-01.gif"
  linkrel="noopener"

  title="Decentralisation"
  caption=""

  licensecode="ccbysa4"
  licenseurl="https://creativecommons.org/licenses/by-sa/4.0/"
  licensename="CC BY-SA 4.0 International"

  attribto="I'M YourOnly.One"
  attriburl="https://im.youronly.one/"
  attribrel="noopener"
>}}
