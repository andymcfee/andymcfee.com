---
layout: post
title: CSS3 Flip Cards
tags:
- Blog
status: publish
type: post
published: true
meta:
  _edit_last: "1"
converted: true
---
Every friday afternoon at Official.fm, we get to work on open source projects and things that interest us.  The goal here is to take a mental break from the daily grind and put our skills to new uses.

For my most recent project, I decided to make CSS "Flip Cards."  My goal was to create re-useable card-like elements that flip on hover (or tap!). Check it out:

<pre class="codepen" data-type="result" data-href="eyahr" data-user="andymcfee">````</pre>
<script async src="http://codepen.io/assets/embed/ei.js"></script>

The HTML markup is fairly straight forward: each card is a container div (``.flip-card``) with two children: ``.card-front`` and ``.card-back``.

The CSS is where this party really starts... There are a two main things happening here: ``backface-visibility`` and ``transform: rotate``.

Oh, and before you go on, be aware that I'm just going to use the standard non-prefixed CSS3 properties in my examples. Check out the Codepen CSS for the Compass/SCSS version of what I'm talking about here.

###Baby got no back###

Imagine a book sitting on a table in front of you. You pick up that book and set it down so that you can read the back.  Now, imagine that the back of the book is invisible so you just see the table.

This is exactly what the CSS3 property ``backface-visibility`` allows you to do with any element.  When set to ``backface-visibility: hidden;`` the user will see the element as they normally would until the element is flipped around using a CSS transform.

In my Flip Cards example, both ``.card-front`` and ``.card-back`` are set to ``backface-visibility: hidden;`` and absolutely positioned to be on top of one another, but ``.card-back`` is rotated 180 degrees along the Y-axis so its invisible back is showing.  When you flip them both around simultaneously, ``.card-front`` becomes invisible at the exact moment that ``.card-back`` becomes visible.

Sweet.

###Every now and then I get a little bit lonely###

Ok, so I lied a bit in that last part when I said that ``.card-back`` was rotated 180° along the y-axis. It's actually rotated -180°.

"But Andy, Algebra 101! -180° is the same thing as 180°!"

How dare you take that tone of voice with me.  Rotating an object from 180° to 0° along a y-axis rotates in the opposite direction that rotating from -180° to 0° would. Still confused? Here:

<pre class="codepen" data-type="result" data-href="wvhmy" data-user="andymcfee">````</pre>
<script async src="http://codepen.io/assets/embed/ei.js"></script>

I've made the boxes wider and decreased the ``perspective`` a bit to make it a bit more obvious what's going on here, but you should be able to tell that the back sides (``.card-back``) in the "bad" examples rotate the wrong direction, breaking the illusion of a physical "card" rotating.

Subtle, but important!

###But can I use it?###

Yes. But don't expect it to work everywhere. It does degrade gracefully though. For the full 3D flip effect, you're going to need a Webkit browser like Chrome and Safari. In Firefox & IE10, the cards flip, but without any 3D effect. IE9 and down, the back side of the cards should just display by on hover because of the increased ``z-index`` of ``.card-back`` on hover.

So there you have it.  It's a neat little effect with plenty of potential uses.  Now, go forth and start flipping some shit!
