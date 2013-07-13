---
layout: default
title: Embedding CodePens into Jekyll Blogs
slug:
tags:
- blog
status: published
type: post
published: true
comments: true
---

I love [CodePen][1].  I also love [Jekyll][2].  But apparently, they don't play well together out of the box. This was one of the few frustrations I had when moving my blog from WordPress to Jekyll.  But fear not, for I have found a way to embed CodePens once more!

Out of async
=================================
Well, the problem isn't Jekyll _specifically_, it's actually Markdown.  If your Jekyll blog is all in `.html` files, then (I assume) you won't have this problem.  But you write all you posts in Markdown now because it's 2013 and that's what all the cool kids are doing these days, right?

Anyway, if you go to CodePen, copy your embed code and paste it into your post, it should look something like this:

    <pre class="codepen" data-height="470" data-type="result" data-href="kjmBd" data-user="andymcfee" data-safe="true"><code></code><a href="http://codepen.io/andymcfee/pen/kjmBd">Check out this Pen!</a></pre>
    <script async src="http://codepen.io/assets/embed/ei.js"></script>

Pretty simple, right?  The problem is, when you try to generate your \_site, you will get a parsing error that says:

    REXML could not parse this XML/HTML:
    <script async src="http://codepen.io/assets/embed/ei.js"></script>

I don't know enough about how Markdown parses HTML and script tags to explain what's wrong here, but I do know that if you remove `async` from the script tag, your REXML parsing problem will be solved.

I need some space
========================

Ok so now your page will render, but everything on your page after your newly embedded content will be broken.  This is the result of [issue with the Maruku markdown engine][3], but there's an easy fix here too: just add a space inbetween **all*** of your embedded tags (`<pre>`, `<code>`, `<script>` and `<a>`) like so:

    <pre class="codepen" data-height="470" data-type="result" data-href="kjmBd" data-user="andymcfee" data-safe="true"> <code> </code> <a href="http://codepen.io/andymcfee/pen/kjmBd">Check out this Pen!</a> </pre>
    <script src="http://codepen.io/assets/embed/ei.js"> </script>

And there you go! Your CodePen is now embedded and should work just fine on your site.

tl;dr
==========
To embed CodePens onto your Jekyll-based blog using markdown syntax
- Remove `async` from the script tag
- Put a space between **every** embedded tag like so: `<code> </code>`

Now, enjoy this HTML/CSS Calculator Pen I've been working on:

<pre class="codepen" data-height="470" data-type="result" data-href="kjmBd" data-user="andymcfee" data-safe="true"> <code> </code> <a href="http://codepen.io/andymcfee/pen/kjmBd">Check out this Pen!</a> </pre>
<script src="http://codepen.io/assets/embed/ei.js"> </script>

[1]: http://codepen.io
[2]: http://jekyllrb.com/
[3]: https://github.com/mojombo/jekyll/wiki/Markup-Problems