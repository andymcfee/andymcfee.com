---
layout: post
title: Icon Fonts
tags:
- Blog
status: draft
type: post
published: false
meta:
  _edit_last: "1"
converted: true
---
Icon Fonts are [awesome][http://css-tricks.com/examples/IconFont/].  Revolutionary even.  And there are [plenty of them][http://css-tricks.com/flat-icons-icon-fonts/], but building your own font can be hard to perfect.

I've been using icon fonts for a while now, but I've never actually built a custom icon font. But after reading GitHub's in-depth look at how they [designed][https://github.com/blog/1106-say-hello-to-octicons] and [built][https://github.com/blog/1135-the-making-of-octicons] their new Octicons font, I'm dying to give building one a try.

#### SCALING ICONS IS HARD ####

One of the challenges in creating an icon font is that they tend to scale poorly at smaller font-sizes (or larger if the font was built specifically for smaller font-sizes).

The GitHub team solved this problem by creating two different icon fonts: one optimized for smaller font-sizes between 16px and 31px and one with more detailed icons designed for 32px and up.  Designing and developing two matching fonts with pixel-perfect detail is no simple task and the GitHub team's work on Octicons is phenomenal.

I especially love that GitHub established a minimum font-size of 16px because regardless of the amount of effort that goes into designing for a smaller sizes, tiny icons are not useful to the user.

#### ICON OF A DIFFERENT COLOR ####

With icon fonts, you can make your icons any color you want, but they can only be one color at a time. Multi-colored, layered or textured icons are just not possible with the current state of browser support for multi-colored text styling.  So while your icons can be any color for any state (active, hover, etc), you're limited to only one color at a time.

That being said, there is support for [gradient text fills][http://css-tricks.com/snippets/css/gradient-text/] which would allow for icons with gradients, but this is only possible with webkit for now.  So you're still pretty much stuck with single color icons.

#### IN THE REAL WORLD ####

At Official.fm, we use a custom icon font for all of our icons on our site and in our HTML5 players. Allowing our users to customize their player's colors just wouldn't be possible without an icon font. We wouldn't be able to dynamically change the color of our icons without a font.  A sprite just doesn't allow for that kind of flexibility.

And I need an ending... And a beginning too.  I'm answering a question I haven't really asked.
