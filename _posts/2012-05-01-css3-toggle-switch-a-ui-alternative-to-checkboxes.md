---
layout: default
title: CSS3 Toggle Switch - A UI Alternative to Checkboxes
tags:
- adjacent selector
- Blog
- checkbox replacement
- CSS3
- UI
- web design
status: publish
type: post
published: true
meta:
comments: true
---
Recently, the adjacent selector (+) and I have become the best of friends. When first I learned of the adjacent selector back in the day, I found little use for simply targeting the element next to another element in my markup.  However, once I realized that, when used with psudeo-class selectors such as :checked, the adjacent selector can be quite powerful, a whole world of opportunities opened up.

One idea I had was to make a toggle switch using a checkbox, a label and an adjacent selector. Here is what I came up with:

<pre class="codepen" data-height="530" data-type="result" data-href="rlntf" data-user="andymcfee" data-safe="true"> <code> </code> <a href="http://codepen.io/andymcfee/pen/rlntf">Check out this Pen!</a> </pre>
<script src="http://codepen.io/assets/embed/ei.js"> </script>

What's going on up there?
=========================

Basically, I have a slider built with 3 parts:
1. slider-viewport: a declared width window (with overflow: hidden) through which we view the slider.
2. slider: 200% width relative to the viewport.
3. slider-content: two slider children each set to 50% width relative to the slider.
Also, a purely aesthetic slider-button.

The whole slider is in a label tag that immediately follows an input checkbox. When the checkbox is unchecked, it displays the first slider-content div.  When the checkbox is checked, the CSS targets the adjacent label (and it's children) to slide the slider div to the left and display the second slider-content.  Since it's all in a label with a "for" attribute, the whole thing can be clicked to toggle the checkbox, which is hidden with "display:none;"

If it sounds a bit complicated, just dig into the Dabblet above and mess around a bit.

But...
===================

Now, a disclaimer: it looks best in Firefox. BOOO! HISSS! Y U NO CROSS-BROWSER!? YOU SUCK!  ...done? Well, let's back up for a second.

This is the first time I have EVER used ONLY a -moz selector without matching -webkit, W3C, etc selectors.  And there's a reason for it: there's a [nasty little bug](https://bugs.webkit.org/show_bug.cgi?id=54189 "webkit bug") in webkit where an element with a border-radius and "overflow: hidden" will not clip children content outside the rounded corners.

Want to test the bug out?  Uncomment the border-radius and border declarations in the Dabblet CSS above in Chrome of Safari. You'll see it.

Anyway, the bug only effects my nice rounded corners and has nothing to do with the actual toggle effect so really it's more of a progressive enhancement.  Shame on webkit nevertheless. Fix this bug please!

Well, I hope this has been educational.
