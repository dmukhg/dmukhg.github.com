---
layout: post
title: This town is a crazy town...
snip: Colours, fonts, responsive-design and easy-reading. An essay on the guidelines I followed while (re)designing this website and a tour of how it all fits together.

---

Often, I have this incredible desire to design something new. Being a student, I rarely get to do this on a project that I can put a lot of time into. My blog takes the bullet, I hope happily.

For this iteration of dmulog.in, I figured I would try some new things. I never had read up on typography before and had never designed a responsive website either. One will find [A List Apart][alistapart] to be a very helpful resource with matters of web-design, especially topics that aren't just tricks or how-tos.

So, typography. Once I started reading up on it, I came across [The Elements of Typographic Style Applied to the Web][webtypography]. It is an attempt to convert topics from a seminal book on typography, The Elements of Typographic Style, into a guide that is more relevant to web designers.

Again, on responsive design [A List Apart: Responsive Design][alaresponse] turned out to be a huge help in introducing the subject and from then on, a search engine is all you need. You see, responsive design has been in for a while now: it just hasn't been on the forefront. You will find helpful tutorials introducing you to the __@media__ query and the whole shebang.

When I started designing this site, (again) I first picked out a colour that would be the base for the palette. I settled on <span style="border-radius: 3px;padding: 0 3px 0 15px;background-color: #0D63BF;color:#ddd">__#0D63BF__</span>. Blue, to me has always been a soothing and trustworthy colour and I found some peace with this shade and it does a pretty cool job of being the accent colour on a page. The other text on the website is a very dark shade of grey. I believe full black draws too much attention to the text even when you aren't focussing on it.

## Fonts

The most important font is always body-copy, for it is what people will spend most of their time reading, especially in a text-heavy setting like a blog. I have found '*Open Sans*' to be very reliable across various screen resolutions and different device types, and I really didn't look much further.

The font for the logo at the very top of the page is '*Rosarivo*'. I found it on Google WebFonts. It has nice, not-too-sharp features, and I love the way the 'j' is designed, almost like a brush-stroke.

For the headings, I find serif fonts to be ablet to draw attention to themselves and then to silently let the user focus on the content once she starts reading. I used '*Gentium Book Basic (Italicised)*', again, from Google WebFonts.

For minor, in-text headings, I wanted to use a font that is sans-serif, like the body-copy, but also the teensiest bit loud so that its arrival is announced just before the previous paragraph ends. I chose '*Viga*', a sans-serif face that is substantially larger in impact than 'Open Sans' but isn't very obstrusive about it, if you know what I mean. :)

The font's being taken care of, I moved to the layout.

## Layout

The layout is extremely simple, because the site has a single requirement. The focus is on getting the text across immaterial of the device or screen-resolution. For screen-sizes larger than 801px, the layout is condensed to 60% of the total browser-width. This allows the user to resize the browser window to get a comfortable _measure_. Measure is the number of characters per line of text. A common comfortable value is 65-70 characters per line. 

A second layout-breakpoint is when the user has increased font sizes substantially. If the screen-size, because of a font-size setting on the user's end causes less than 50 'M's to be displayed per line on a big screen, the layout expands to the full width of the screen. On firefox, this can be tried out with Ctrl + and Ctrl -, but on Chrome and other webkit based browsers, you may have to refresh the page for the changes to kick in.


The page works without using a second stylesheet, on most smartphones and all modern browsers. I hope you like it.

[alistapart]: http://www.alistapart.com/
[webtypography]: http://webtypography.net/
[alaresponse]: http://www.alistapart.com/articles/responsive-web-design/
