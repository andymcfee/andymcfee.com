---
layout: default
title: CSS Columns in the Wild
slug:
tags:
  - blog
custom_css:
  - cols.css
status: published
type: post
published: true
comments: true
---

From a UX perspective, CSS3 columns can be dangerous.  People instincitively want to layout content in columns because "that's how newspapers do it." And it works for newspaper and magazines because their medium has a fixed width and columns help to make content more readable on a page.  However, in the digital world, when a user reads to the bottom of a column they have to scroll back to the top to continue reading. That's a bad UX.

Which has led me to wonder: when _could_ I use CSS columns?  Well, I think I've found my first reasonable use case for them.

Too Much Space
====================

Responsive grids are great.  The main idea behind a responsive grid is that you have a column-based grid which stacks the columns at smaller viewport widths.

Take this three column layout:

<div class="grid-contain">
  <div class="grid-col">
    <h6>First</h6>
    <ul>
      <li>Hi, I'm list item 1</li>
      <li>Hi, I'm list item 2</li>
      <li>Hi, I'm list item 3</li>
      <li>Hi, I'm list item 4</li>
    </ul>
  </div>
  <div class="grid-col">
    <h6>Second</h6>
    <p>I'm the second column</p>
  </div>
  <div class="grid-col">
    <h6>Third</h6>
    <p>And I'm the third grid column.</p>
  </div>
</div>

Given enough room, the columns stack side-by-side. At smaller viewports, your layout will look more like this:

<div class="grid-contain stack">
  <div class="grid-col">
    <h6>First</h6>
    <ul>
      <li>Hi, I'm list item 1</li>
      <li>Hi, I'm list item 2</li>
      <li>Hi, I'm list item 3</li>
      <li>Hi, I'm list item 4</li>
    </ul>
  </div>
  <div class="grid-col">
    <h6>Second</h6>
    <p>I'm the second column</p>
  </div>
  <div class="grid-col">
    <h6>Third</h6>
    <p>And I'm the third grid column.</p>
  </div>
</div>

...well, the columns are now stacked, but there's a quite a bit of empty space in the First section, especially since my `li` content is very short. It'd be great if we could somehow magically spread that content across the container...

    ul {
      -webkit-column-count: 2;
      -moz-column-count: 2;
      -ms-column-count: 2;
      -o-column-count: 2;
      column-count: 2;
    }

Boom.  CSS Columns.  

<div class="grid-contain stack">
  <div class="grid-col cols">
    <h6>First w/ CSS Cols</h6>
    <ul>
      <li>Hi, I'm list item 1</li>
      <li>Hi, I'm list item 2</li>
      <li>Hi, I'm list item 3</li>
      <li>Hi, I'm list item 4</li>
    </ul>
  </div>
  <div class="grid-col">
    <h6>Second</h6>
    <p>I'm the second column</p>
  </div>
  <div class="grid-col">
    <h6>Third</h6>
    <p>And I'm the third grid column.</p>
  </div>
</div>

Combined that with a media query to drop back down to one column when your viewport gets small enough, and you've successfully used CSS3 columns!

**NOTE** CSS Columns are supported in:

- IE10+
- Chrome/Safari 
- Firefox
- iOS Safari
- Android

So sorry, IE9 and down. My demos are going to look a little odd to you.  

But in the REAL World...
=========================

OK, I cheated a bit.  I used very short and simple content in my list items.  When things aren't so clean you can end up with something like this:

<div id="curtain1" class="grid-contain stack">
  <div class="grid-col cols">
    <h6>First w/ CSS Cols</h6>
    <ul>
      <li>Hi, I'm list item 1</li>
      <li>Hi, I'm list item 2 and I'm obnoxiously long. Really, obnoxiously long.</li>
      <li>Hi, I'm list item 3</li>
      <li>Hi, I'm list item 4</li>
    </ul>
  </div>
</div>

Ouch.  Nobody likes a list item that breaks across columns. It's ok, we can fix that by giving the `li` a style of `display: inline-block`

<div id="curtain2" class="grid-contain stack">
  <div class="grid-col cols">
    <h6>First w/ CSS Cols</h6>
    <ul>
      <li>Hi, I'm list item 1</li>
      <li>Hi, I'm list item 2 and I'm obnoxiously long. Really, obnoxiously long.</li>
      <li>Hi, I'm list item 3</li>
      <li>Hi, I'm list item 4</li>
    </ul>
  </div>
</div>

Better. The `display: inline-block` prevents the `li` from breaking over columns, but we've lost our bullet points (which came from the default styling of an `li` to `display: list-item`). But it's cool cause we all know how to use `:before` and `content`, right?

<div id="curtain3" class="grid-contain stack">
  <div class="grid-col cols">
    <h6>First w/ CSS Cols</h6>
    <ul>
      <li>Hi, I'm list item 1</li>
      <li>Hi, I'm list item 2 and I'm obnoxiously long. Really, obnoxiously long.</li>
      <li>Hi, I'm list item 3</li>
      <li>Hi, I'm list item 4</li>
    </ul>
  </div>
</div>

And there you have it.  Nice, clean list columns with CSS.  Just be sure your weary of the type/amount of content you use in columns. I swear, if I catch you using this on a list with 100 items...  If the user has to scroll when you are using columns, don't use columns.  

