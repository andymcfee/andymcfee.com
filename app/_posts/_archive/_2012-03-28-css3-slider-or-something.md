--- 
layout: post
title: CSS3 Slider or something
tags: 
- front-end development
status: draft
type: post
published: false
meta: 
  _edit_last: "1"
---
So here's what I

Basically, what I wanted was a two-state slider that slides left and right showing different content in each state.  Easy enough.  The catch is that I wanted the button to be part of the slider AND I want it to work regardless of the size of it's parent i.e. no fixed widths.

Ok so how did I do it?  Well I started with a container.  This container can be any size, but let's make it 500px wide.

[css]#container {
  width: 300px;
  height: 50px;
  overflow: visible;
}
[/css]
