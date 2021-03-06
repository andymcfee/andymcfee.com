---
layout: post
title: Responsive Design and UX Tips
tags:
- Blog
status: publish
type: post
published: true
meta:
  _edit_last: "1"
converted: true
---
A few weeks ago, I had the privilege of attending the [WebVisions][http://www.webvisionsevent.com/barcelona/] conference in Barcelona. I decided that for this conference, I would focus primarily on two topics: **User Experience** and **Responsive Design** and attend talks tailored toward either of those two topics. Here is a rundown of some of the the main things I took away from the conference:

###User Experience###

####Test Your Designs####

Web people love data, but we tend not to use it when making design and UX decisions _and we should_. There are tons of way to test your designs: UX testing services, A/B testing, meeting with users, simply reviewing data, etc., but this is step in the process is often neglected. As designers, we have no way of improving if we don’t know how the users are interacting with our designs.

####FAQs Imply Bad Design####

These next two come specifically from Crystal Beasley's [13 Signs Your Site Needs a UX Exorcism][http://skinnywhitegirl.com/blog/13-signs-your-site-needs-a-ux-exorcism/745/] talk. FAQs are the result of a poor UX. If you have an FAQ, you are essentially admitting defeat by saying “I am doing such a poor job of explaining myself to my users that these are all the questions they have that I can’t answer otherwise.” The more Qs you can remove from your FAQ and answer elsewhere more relevantly and clearly through design, the better your UX will become.

####Minimize Using Modals####

A modal will always mean adding at least one unnecessary click or action for a user. There is almost always a way to prevent using a modal; confirm modals can be prevented with undo states and error modals can be prevented by preventing the error in the first place. This will often mean more development work, but it will pay off in the end by creating a smoother, more seamless experience.

####Define and Use User Personas####

A User Persona is an outline of who your users are and what types of actions they will take with your site. For example, an e-commerce site may define two user personas: buyers and sellers. The experience for each would be different and tailored to the actions the user will need to take. After you have defined your personas, they will be used by the entire team from design to content to development in determining how to create an experience that will be suited to each persona.

If you are part of any business development or product team, you should really take the time to read this [http://webdesign.tutsplus.com/articles/user-experience-articles/defining-and-applying-personas-to-ux-design/][great overview of user personas].

###Responsive Design###

I attended two workshops about Responsive Design at WebVisions Barcelona: "Responsive Enhancement" with Jeremy Keith and "The Definitive Guide to Building for the Wide World of Mobile Devices" with Jason Grigsby. Here are the highlights:

####Content Dictates Breakpoints####

One of the most common questions asked about responsive design is "how do you decide on break points?" Too often we design for device widths (480px, 768px, 980px, etc), but these are arbitrary bases for setting break points. Devices come in all different sizes and there's no way to customize a responsive design for each device. Instead, set your break points where your content breaks. For example, if your navigation breaks at 650px and again at 500px, set break points at those intervals and customize your design with media queries and your navigation will work on a device with any width.

####Media Queries in EMs####

Instead of using pixel-based values for media queries (max-width: 500px), try using em-based values (max-width: 24em). Em-based media queries will scale better based on the user's zoom level. It's a bit more than I can explain in a few lines here, but [this article][http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/] from CloudFour's Lyza Gardner does a great job of explaining the how and why of em-based media queries.

####Responsive Images####

Images are getting to be a real pain for web designers. What sucks is that there's not really a perfect solution right now for how to dynamically load images as part of a responsive design. The W3C is [working on a few things][http://www.w3.org/community/respimg/2012/08/04/picture-in-the-html5-spec/] at the moment, but in the mean time we still need a solution to these problems. My favorite answer so far: [Picturefill.js][https://github.com/scottjehl/picturefill/]. Part of the Filament Group's [South Street][https://github.com/filamentgroup/Southstreet] project, picturefill.js is the best solution I've seen for implementing responsive images today. Check it out as well as some of the other tools in South Street.
###Final Thoughts###
All in all, I was very impressed with the WebVisions Conference. The quality of speakers and workshops was right up there with the fantastic Future of Web Design conference in London this past May. Conferences like these are excellent tools for designers and developers to not only learn and sharpen skills, but also to meet one another and discuss and share their work.
