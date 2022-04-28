+++
title = "[How-To] Add DISQUS Manually on Blogger/BlogSpot"
description = "A guide on how to add DISQUS comments in your Blogger Blogspot blog. This tutorial is for those using the XML template."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

date = "2008-05-23T12:12:48+08:00"                                        # manually adjust to local timezone
lastmod = "2008-05-23T12:12:48+08:00"                                        # manually adjust to local timezone

aliases = ["/2008/05/how-to-add-disqus-manually-on-blogger.html"]
slug = "add-disqus-blogger-blogspot"
translationKey = "add-disqus-blogger-blogspot-2008144"
relCanonical = "https://im.youronly.one/techmagus/kb/webdev/add-disqus-blogger-blogspot-2008144/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["howto"]                                                   # taxonomy
keywords = ["disqus", "blogger", "blogspot", "comments", "comment system", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["bloggercom"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

featured = true
#math = true
toc = true

#videos = [""]                                                       # used by og:video, etc.
#audio = [""]                                                        # used by og:audio, etc.
images = ["https://4.bp.blogspot.com/-g0D8KJDIhYA/XqVTmie0X2I/AAAAAAAAhY8/aYSBg3dpOzYlHLAV60sJdXgYMNRua4RQQCPcBGAYYCw/s1600/Blog-01.jpg"]                                                       # used by og:images, etc.; first image is cover image

type = "article"                                                           # article, sitepage, review

#draft = true

#license = ""                                                       # only set if the post license is not the same as the site license

[[authors]]
  person = "yuki"
  #id = ""
  name = "ᜌᜓᜃᜒ (Yuki | 雪亮)"
  url = "https://im.youronly.one/techmagus/"
  avatar = "https://rsc.youronly.one/img/y/techmagus-Architetto-Esperiment-chimico.webp"
  #rel = "noopener external nofollow"
+++

{{% sembox boxstyle="qbs_generic" qmarkstyle="" boxcolour="qbc_yellow" attribalign="txt_right" srctitle="" srclink="" srcrel="noopener external nofollow" attribto="" attriblink="" attribrel="noopener external nofollow" %}}
  This guide was last updated on 2008 and since then Disqus created an automated method. It is strongly suggested to use it by visiting [this link](https://disqus.com/admin/settings/blogger/) and then switch to the correct site.
{{% /sembox %}}

If like me you are using <a class="popper animate" href="https://disqus.com" target="_blank" rel="noopener" data-popper="DISQUS">DISQUS</a> for your blog or site comments system, then maybe you've encountered a problem with integrating it to your custom theme/template. In this simple tutorial, I will show you which code bits to edit to successfully integrate Disqus into your Google Blogger/BlogSpot XML-based template. (Basically it is the same with any theme/template regardless of your blog platform or CMS.)

But if you have a Classic Template, then read my [HOW TO: Integrate DISQUS on Blogger/BlogSpot Classic Template]({{% ref "integrate-disqus-blogger-classic.md" %}} "HOW TO: Integrate DISQUS on Blogger/BlogSpot Classic Template") instead.

<!--more-->

Check for updates below this guide. Latest update: Saturday, 2008-08-23.

{{% sembox boxstyle="qbs_generic" qmarkstyle="" boxcolour="qbc_red" attribalign="txt_right" srctitle="" srclink="" srcrel="noopener external nofollow" attribto="" attriblink="" attribrel="noopener external nofollow" %}}
  **WARNING**: Be sure to back-up your *working* template before you overwrite it! Last but not the least, you should be comfortable with editing HTML and CSS, otherwise, you might get frustrated, confused, and end up with a non-working blog/site.
{{% /sembox %}}

With that said, let's begin!

## Step 1

This step is for the "0 Comment"; "1 Comment"; "10 Comments" link that shows on your main page.

- 1.1: Add this to your CSS area or CSS file

  ```css
  /* Depending on your template, sometimes on some browsers, disqus doesn't auto-width 100% */
  #disqus_thread, #disqus_thread #dsq-content {
      width: 100%;
  }
  ```

## Step 2

- 2.1: Look for:

  ```html
  <b:if cond='data:post.allowComments'>
      <a expr:href='data:post.addCommentUrl' expr:onclick='data:post.addCommentOnclick'><data:post.numComments/> Comments<;/a>
  </b:if>
  ```

- 2.2: Change it to:

  ```html
  <b:if cond='data:post.allowComments'>
      <!-- <a expr:href='data:post.addCommentUrl' expr:onclick='data:post.addCommentOnclick'><data:post.numComments/> Comments</a> -->
      <!-- +disqus -->
      <a class='comment-link commentslink' expr:href='data:post.url + "#disqus_thread"'>View Comments »</a>
      <!-- -disqus -->
  </b:if>
  ```

## Step 3

Step 3 is for the "0 Comment"; "1 Comment"; "10 Comments" text that shows when viewing a specific post. Some templates do not have this, so if you can't find it, skip to Step 4.

- 3.1: Look for:

  ```html
  <b:if cond='data:post.numComments == 1'>
          1 <data:commentLabel/>:
      <b:else/>
          <data:post.numComments/> <data:commentLabelPlural/>:
  </b:if>
  ```

- 3.2: Change it to:

  ```html
  <!-- <b:if cond='data:post.numComments == 1'> -->
          <!-- 1 <data:commentLabel/>: -->
      <!-- <b:else/> -->
          <!-- <data:post.numComments/> <data:commentLabelPlural/>: -->
  <!-- </b:if> -->
  Comments:
  ```

## Step 4

- 4.1: Look for:

  ```html
  <div id='backlinks-container'>
  ```

- 4.2: Usually, above the code bit in 4.1, you will find this:

  ```html
  <p class='comment-footer2'>
    <a expr:href='data:post.addCommentUrl' expr:onclick='data:post.addCommentOnclick'><data:postCommentMsg/></a>
  ```

It may be enclosed on a DIV tag instead of a P element. Additionally, sometimes you may find that it's arranged differently, if so, just look for any bits similar to 4.1.

- 4.3: Once you find it, change it to:

  ```html
  <!-- <p class='comment-footer2'> -->
      <!-- <a expr:href='data:post.addCommentUrl' expr:onclick='data:post.addCommentOnclick'><data:postCommentMsg/></a> -->
  <!--  -->
  ```

## Step 5

- 5.1: Look for:

  ```html
  <div id='backlinks-container'>
  ```

- 5.2: Above it add:

  ```html
  <!-- BGN: disqus -->
  <div id="disqus_thread"></div>
  <div id='disqus_post_title' style='display:none;'><data:post.title/></div>
  <div id='disqus_post_permalink' style='display:none;'><data:post.url/></div>
  <script type="text/javascript">
      /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
      var disqus_shortname = 'DISQUS-SHORT-NAME'; // required: replace example with your forum shortname
      var disqus_title = document.getElementById('disqus_post_title').innerHTML;
      var disqus_url = document.getElementById('disqus_post_permalink').innerHTML;
      /* * * DON'T EDIT BELOW THIS LINE * * */
      (function() {
          var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
          dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
          (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
      })();
  </script>
  <noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
  <a href="https://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>
  <!-- END: disqus -->
  ```

Note: If above the code bit shown in 5.1 there is a &amp;lt;/b:if&amp;gt;, then put the code bit in 5.2 <b>before</b> &amp;lt;/b:if&amp;gt;. If it isn't there, as in some templates, you probably have to add it.

- 5.3: From Step 5.2, change the <b>DISQUS-SHORT-URL</b> to your blog's DISQUS URL.<br />Example, if your DISQUS URL is <i>libresoftware.disqus.com</i> then change DISQUS-SHORT-URL to <i>libresoftware</i>. There are <b>two</b> to change!

## Step 6

- 6.1: Look for:

  ```html
  </body>
  ```

- 6.2: Add above:

  ```html
  <!-- BGN: disqus -->
  <script type="text/javascript">
      /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
      var disqus_shortname = 'DISQUS-SHORT-NAME'; // required: replace example with your forum shortname

      /* * * DON'T EDIT BELOW THIS LINE * * */
      (function () {
          var s = document.createElement('script'); s.async = true;
          s.type = 'text/javascript';
          s.src = '//' + disqus_shortname + '.disqus.com/count.js';
          (document.getElementsByTagName('HEAD')[0] || document.getElementsByTagName('BODY')[0]).appendChild(s);
      }());
  </script>
  <!-- END: disqus -->
  ```

- 6.3: In Step 6.2, change the <b>DISQUS-SHORT-URL</b> to your blog's DISQUS URL.<br />Again, if your DISQUS URL is <i>libresoftware.disqus.com</i> then change DISQUS-SHORT-URL to <i>libresoftware</i>, there is only <b>one</b> to change.

## Step 7

- 7.1: Copy your final code to your Blogger's template and save it.

## Step 8

- 8.1: Force refresh your blog and blog-post (usually CTRL+F5) to see the changes.<br />* Force refresh tells your browser to discard your current cached copy of your site and instead fetch a new copy from the server.

At this point, you are done when all is working fine. Congratulations!

Some things to remember. This how-to was designed to still show the comments posted on your built-in comment system (usually Blogger's) while at the same time disabling any new comments from being posted using the built-in comment system, by removing the link to do so. However, if your visitors knows the direct link to Blogger's built-in comment system, they can still leave comments the old way.

To effectively disable it without hiding all earlier comments, you need to edit the Post Options of each of your posts and change it to "Don't allow, show existing". Later, Disqus will introduce an import feature, so all old comments will be copied to your Disqus as well. Until then, this is the solution that I can think of.

For the adventurous, you can find information on the Disqus API by visiting the official <a href="https://help.disqus.com/">developers webpage</a>.

Hope that helps!

---

## Updates

- Friday, 2013-08-02: Updated the JavaScript code to reflect the latest disqus script in steps 5 and 6

- Saturday, 2008-05-24: Thanks to Disqus' <a class="popper animate" href="https://disqus.com/by/danielha/" target="_blank" rel="noopener" data-popper="Daniel Ha on Disqus">Daniel Ha</a> for featuring this how-to article on the official website! Glad to be of help.
- Monday, 2008-05-26: Chinese (Taiwan) version <a class="popper animate" href="https://black-tale.blogspot.com/2008/05/bloggerdisqus_26.html" target="_blank" rel="noopener" data-popper="[教學]Blogger如何手動安裝Disqus">[教學]Blogger如何手動安裝Disqus</a> with screenshots by <a class="popper animate" href="https://disqus.com/by/blacktale/" target="_blank" rel="noopener" data-popper="Blacktale on Disqus">Joyce Wu</a>.
- Saturday, 2008-06-14: I updated step 6. I missed to change a Disqus URL to DISQUS-SHORT-URL, it was previously pulling data from "highstreet5". Please check your codes on step 6.
  - Thanks to the classic Blogger code provided by <a class="popper animate" href="https://disqus.com/by/davidalvarez/" target="_blank" rel="noopener" data-popper="David Alvarez on Disqus">David Alvarez</a>, you can find his blog at <a href="https://balazos.blogspot.com" target="_blank" rel="noopener">balazos.blogspot.com</a>. I was helping him integrate Disqus and that was when I caught the code I missed on Step 6.

- Saturday, 2008-08-02: The tutorial was added at <a href="https://web.archive.org/web/20100428045802/https://disqus.disqus.com:80/help_using_disqus_with_custom_blogger_templates/" target="_blank" rel="noopener">Disqus help forums</a> by <a class="popper animate" href="https://disqus.com/by/Badr/" target="_blank" rel="noopener" data-popper="Andrew on Disqus">Andrew</a> (from Disqus). Thank you very much and I'm glad to be of help to the community!
- Saturday, 2008-08-23: Changed /{YOUR-DISQUS-URL}/ to /DISQUS-SHORT-URL/ to avoid confusion. Thanks to hackcrack.

If you have other questions, don't hesitate to post a reply in our Disqus powered comments system.

---

{{< image
  type="imagecoverattrib"

  link="https://www.flickr.com/photos/manoftaste-de/14045819341"
  linkrel="noopener external nofollow"

  title="Blog"
  caption=""

  licensecode="ccbysa2"
  licenseurl="https://creativecommons.org/licenses/by-sa/2.0/"
  licensename="CC BY-SA 2.0"

  attribto="www.manoftaste.de"
  attriburl="https://www.manoftaste.de"
  attribrel="noopener external nofollow"
>}}
