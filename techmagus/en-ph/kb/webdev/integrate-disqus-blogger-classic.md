+++
title = "[How-To] Integrate DISQUS on Blogger/BlogSpot Classic Template"
description = "A short guide on how to integrate Disqus on Google Blogger / Blogspot websites. This tutorial is for those using the Classic Template."                                                    # For Schema.org; OpenGraph; Twitter Cards; and post summary

publishdate = "2008-05-25T02:45:39+08:00"                                        # manually adjust to local timezone
lastmod = "2008-05-25T02:45:39+08:00"                                        # manually adjust to local timezone

aliases = ["/2008/05/how-to-integrate-disqus-on-blogger-blogs.html"]
slug = "integrate-disqus-blogger-blogspot-classic"
translationKey = "integrate-disqus-blogger-blogspot-classic-2008146"
relCanonical = "https://im.youronly.one/techmagus/kb/webdev/integrate-disqus-blogger-blogspot-classic-2008146/"                                                   # the actual URL of the post; also used for disqus ID and url
#disqus_url = ""                                                    # automatic in YourOnly.One setup
#disqus_identifier = ""                                             # highly recommended by Disqus; automatic in YourOnly.One setup

channels = ["techmagus"]
categories = ["howto"]                                                   # taxonomy
keywords = ["disqus", "how to", "comment system", "comments", "blogger", "blogspot", "techmagus", "YourOnlyOne", "YourOnly.One"]                                                     # meta keywords
#series = [""]                                                       # subset of series taxonomy
tags = ["bloggercom"]                                                         # taxonomy

comments = true
#weight = ""                                                        # post weight, if we want granular control of post order

#featured = true
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
  This only applies to "first-generation classic themes" or "traditional templates".
{{% /sembox %}}

Maybe you have read my [HOW TO: Add DISQUS Manually on Blogger/BlogSpot](add-disqus-blogger.md "HOW TO: Add DISQUS Manually on Blogger/BlogSpot") but found it is for XML-based templates. Fret not, in this how-to, we are going to integrate DISQUS on your Blogger/BlogSpot Classic/Custom Template!

<!--more-->

Check for updates below this guide. Latest update on Tuesday, 2009-04-28.

But first, thanks to <a href="https://disqus.com/by/nathos/" target="_blank" rel="noopener">Nathan</a> <a href="https://nathos.com/" target="_blank" rel="noopener">Henderson</a> for sharing the changes he did. I then added a few more edits to give the finishing touch. Last but definitely not the least, read this warning.

{{% sembox boxstyle="qbs_generic" qmarkstyle="" boxcolour="qbc_red" attribalign="txt_right" srctitle="" srclink="" srcrel="noopener external nofollow" attribto="" attriblink="" attribrel="noopener external nofollow" %}}
  **WARNING**: Be sure to back-up your *working* template before attempting to overwrite it! This guide is also recommended to be followed by those comfortable with editing HTML/CSS.
{{% /sembox %}}

## Step 1

- 1.1: Add this to your CSS area or CSS file:

  ```css
  /* Depending on your template, sometimes on some browsers, disqus doesn't auto-width 100% */
  #disqus_thread, #disqus_thread #dsq-content {
      width: 100%;
  }
  ```

## Step 2

Step 2 is for the "0 Comment"; "1 Comment"; "10 Comments" link that shows on your main page.

- 2.1: Look for:

  ```html
  <a class="comment-link" href="<$BlogItemCommentCreate$>"<$BlogItemCommentFormOnclick$>><span style="text-transform:lowercase"><$I18NNumComments$></span></a>
  ```

  OR

  ```html
  <a class="comment-link" href="<$BlogItemCommentCreate$>"<$BlogItemCommentFormOnclick$>><$BlogItemCommentCount$> Comments</a>
  ```

- 2.2: Change it to:

  ```html
  <!-- <a class="comment-link" href="<$BlogItemCommentCreate$>"<$BlogItemCommentFormOnclick$>><span style="text-transform:lowercase"><$I18NNumComments$></span></a> -->
  <!-- +disqus -->
  <a class='comment-link commentslink' href='<$BlogItemPermalinkUrl$>#disqus_thread'><span style="text-transform:lowercase">View Comments »</span></a>
  <!-- -disqus -->
  ```

  OR

  ```html
  <!-- <a class="comment-link" href="<$BlogItemCommentCreate$>"<$BlogItemCommentFormOnclick$>><$BlogItemCommentCount$> Comments</a> -->
  <!-- +disqus -->
  <a class='comment-link commentslink' href='<$BlogItemPermalinkUrl$>#disqus_thread'><span style="text-transform:lowercase">View Comments »</span></a>
  <!-- -disqus -->
  ```

## Step 3

This step is for "0 Comment"; "1 Comment"; "10 Comments" text that shows up when viewing a single post. Also note that this piece of code is not present in some templates by-design, so skip to Step 4.

- 3.1: Look for:

  ```html
  <$I18NNumComments$>:
  ```

  OR

  ```html
  <$BlogItemCommentCount$> Comments:
  ```

- 3.2: Change it to:

  ```html
  <!-- <$I18NNumComments$>: -->
  Comments:
  ```

  OR

  ```html
  <!-- <$BlogItemCommentCount$> --> Comments:
  ```

## Step 4

- 4.1: Look for:

  ```html
  <$BlogItemCreate$>
  ```

- 4.2: Change it to:

  ```
  <!-- <$BlogItemCreate$> -->
  ```

- 4.3: Look for:

  ```
  <$BlogItemFeedLinks$>
  ```

- 4.4: Change it to:

  ```html
  <!-- <$BlogItemFeedLinks$> -->
  ```

## Step 5

- 5.1: Look for:

  ```
  </BlogItemCommentsEnabled>
  <BlogItemBacklinksEnabled>
  ```

- 5.2: Add above/before:

  ```html
  <!-- BGN: disqus -->
  <div id="disqus_thread"></div>
  <div id='disqus_post_title' style='display:none;'><$BlogItemTitle$></div>
  <div id='disqus_post_permalink' style='display:none;'><$BlogItemPermalinkUrl$></div>
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

- 5.3: In Step 5.2, change the <b>DISQUS-SHORT-NAME</b> to your blog's DISQUS URL.<br />Example, if your DISQUS URL is <i>libresoftware.disqus.com</i> then change DISQUS-SHORT-NAME to <i>libresoftware</i>. There is <b>one</b> to change.

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

- 6.3: In step 6.2, change the DISQUS-SHORT-NAME to your blog's DISQUS URL.<br />Again, if your DISQUS URL is <i>libresoftware.disqus.com</i> then change DISQUS-SHORT-NAME to <i>libresoftware</i>. Only <b>one</b> to change here.

## Step 7

- 7.1: Copy your updated code to your Blogger's Template editing section and save it.

## Step 8

- 8.1: Force refresh your blog and blog-post (usually CTRL+F5) to see the changes.
  Force refresh tells your browser to fetch a new copy of the site from the server.

You're done! Congratulations!

Some notes to remember. This how-to guide was designed to still show the comments posted via your built-in comment system (Blogger's in this case), while at the same disabling the ability to post new comments using the old system by removing the link.

For the adventurous, you can also find the <span class="popper animate removed_link" data-popper="https://disqus.disqus.com/developers/">DISQUS API here</span>.

---

## Updates

- Friday, 2013-08-02: Updated the JavaScript code to reflect the latest disqus script in steps 5 and 6

- Saturday, 2008-06-14
  - Updated the instructions to include the older Classic Template codes
  - Updated Step 6. The reason the ## Comments was not showing up was because I missed to change one instance of DISQUS-SHORT-NAME, which was pulling data from "highstreet5". Please check your codes on Step 6
  - Thanks to the classic blogger code provided by <a href="https://balazos.blogspot.com" target="_blank" rel="noopener">David Alvarez</a>. I was helping him integrate DISQUS and that's when I caught the error.
- Saturday, 2008-08-02: The tutorial was added at <a href="https://web.archive.org/web/20100428045802/https://disqus.disqus.com:80/help_using_disqus_with_custom_blogger_templates/" target="_blank" rel="noopener">DISQUS help forums</a> by <a href="https://disqus.com/by/Badr/" target="_blank" rel="noopener">Andrew</a> (from Disqus). Thank you very much and I'm glad to be of help to the community!
- Saturday, 2008-08-23: Changed /{YOUR-DISQUS-URL}/ to /DISQUS-SHORT-URL/ to avoid confusion. Thanks to hackcrack for the suggestion.
- Tuesday, 2009-04-28: Corrected Steps 5.2 and 6.2. Hat tip to chrisdfeld for catching the errors.
- Tuesday, 2011-07-06: Fixed typographical error in Step 5.2, thanks to <a href="https://the-randomizer.blogspot.com" target="_blank" rel="noopener">lil-bee</a> for bringing it to my attention

If you have other questions, don't hesitate to reply in our Disqus-powered comments or the <a href="https://web.archive.org/web/20100428045802/https://disqus.disqus.com:80/help_using_disqus_with_custom_blogger_templates/" target="_blank" rel="noopener">official Disqus forums</a>!

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
