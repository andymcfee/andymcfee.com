---
layout: default
title: Icon Fonts, Pseudo-Elements and IE8
tags:
- Blog
- CSS3
- HTML5
- Icon Font
- IE8
- UI
status: publish
type: post
published: true
meta:
  _edit_last: "1"
comments: true
---



I love icon fonts. Who doesn't? Nobody. That's who. They are just super and they pretty much work in every browser ([IE has supported @font-face since IE 4](http://www.webfonts.info/wiki/index.php?title=@font-face_browser_support)! Chew on that for a while.) and I could talk about them for hours, but that's not why I'm writing this post. No, I'm writing this because of an oddly prominent bug I've encountered with icon fonts and IE8 and pseudo elements.


ICON FONTS 101
==============

But first, let's set the stage. Like I said, icon fonts are just swell. For example, once I have created my icon font, I just use @font-face to include my font files on my site and create a class to use it:


    @font-face {
      font-family: 'MyIconFont';
      src: url('MyIconFont.eot?') format('eot'),
           url('MyIconFont.woff') format('woff'),
           url('MyIconFont.ttf') format('truetype');
    }
    .icon {font-family: 'MyIconFont';}

And I'm good to go. Now let's say, for example, that I have made the letter "A" in my font display an "Apple" icon. This would then create an "Apple" icon on my page:

    <span class="icon">A</span>

And it works. Like a charm. On just about any browser. Even IE8. SUPER!

ENTER PSEUDO-ELEMENTS
========================

Ok, great. But this font is for icons and not normal text so you don't want random letters in your markup do you? No, of course you don't. It's messy and unnecessary and just plain wrong. So, as you probably already guessed, you should do something like this:


    .icon {
      font-family: 'MyIconFont';
      font-size: 20px;
      color: #FF0;
    }
    .icon.apple:before    {content: 'A';}
    .icon.twitter:before  {content: 'B';}
    .icon.facebook:before {content: 'C';}
    .icon.email:before    {content: 'D';}

...where each icon that is defined in your font ("Apple") has its own semantic class name (.apple) which appends the corresponding letter ("A") using the :before pseudo-element. This can also be done using data-attributes, but I prefer this method. Personal preference. So now, your markup should look like this:

    <span class="icon apple"></span>

And you are left with an apple icon. This is more or less the basic technique for using icon fonts. But don't take my word for it, check out this [fantastic icon font demo page](http://css-tricks.com/examples/IconFont/ "Icon Fonts are Awesome") built by CSS-Trick's Chris Coyier.


THE PSEUDO-ELEMENT/FONT CONFLICT
====================================

So what's the problem? IE8. Yes, IE8 supports @font-face and IE8 supports the :before pseudo-element. But IE8 does NOT like when you try to use them together. Don't believe me? Why don't you just fire-up IE8 (to Browserstack!) and head over to the [fantastic icon font demo page](http://css-tricks.com/examples/IconFont/ "Icon Fonts are Awesome") I mentioned above.

What's that? It works for you? Great. It worked for me to. Now click on the refresh button. HAH! You SEE!? Try leaving your mouse outside browser frame. Now hover your mouse over the body. Are you seeing this too!?

For those of you not following along at home, let me explain what's happening: when the user loads the page in IE8 for the first time, the page more than likely renders just fine with all of the icons appearing normally like this:

![ie8 icons good](/img/icons-good.jpg)
###### This is how the page looks in IE8 on the initial page load. All the icons appear normally.

But when the user refreshes the page, the icons disappear and only the :before pseudo-element letters appear (see image below) UNTIL the user hovers back over the body of the page. Then all the icons magically reappear.

![Bad IE8 Font Icons](/img/icons-bad.jpg)
###### If the user refreshes the page and leaves the cursor outside of the body of the page, icons won&#39;t render. Once the user hovers over the page again, all fonts will reappear.

WTF, MATE?
================

Honestly, I don't know. From what I can tell, IE8 waits to render a font after the whole page has loaded (or at least all font files have downloaded). And when the page is reloaded, the cached page loads faster than the font and IE8 doesn't trigger loading the font until the user interacts with the page i.e.(pun totally intended) the user hovers over the body of the page. Best case scenario, this creates a Flash of Unstyled Content when the user refreshes via a keyboard shortcut. Worst case, well you have random letters all over the place.

This is a problem I've been struggling with for weeks at Official.fm. Our HTML5 player relies heavily (read: entirely) on an icon font for everything. Play/skip/back buttons, social icons, navigation icons, etc.  And when you try to reload (or even just load sometimes) the player in IE8, well...

![LETTERS EVERYWHERE](http://i.qkme.me/3om838.jpg)

The only "solution" we've come up with is not using the :before pseudo-class in IE8 and instead, dynamically injecting the letters via JS. It's a ridiculous work around but it's the only way we can get the icons to render properly in IE8.

So there you go. With the recent rise in the popularity of icon fonts, I don't know why I haven't heard of more people having this problem. Fortunately, IE8 is on it's way out and every single day, this becomes less and less of an issue as more and more people dump IE8 and transition to truly modern browsers (IE9, don't get too excited, I'm not talking to you).
