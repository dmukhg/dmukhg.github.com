---
layout: post-without-title
title: About | dmulog.in 
---

## About the author

Writing an introduction to an introduction of yourself is a pretty hefty task.  I will set that aside and dig right in.

I am a programmer.  I primarily work on client-side development using javascript and HTML/CSS etc.  I also love to use [django][django] and [python][python] on a variety of projects that keep me busy.  Of late, I have also begun working on [Spiking Neural Networks][snn] and am writing a [simulator][moment] based on CUDA.

On a side note, I am becoming increasingly interested in Typography for the web.

If you want to employ me or work with me, here is a link to my [resume][resume] and my [email][email].

## About this site

This site is spit by [jekyll][jekyll] from a template that I designed to work on small as well as big screens using CSS only.  A few notes about the design principles for this website:

### Measure

Measure is the average number of characters per line in a body of text.

On this site, if the user is on a big screen, she can select a comfortable measure by increasing the font-size (Ctrl + '+') or by resizing the window.  If the user is on a small screen, the font-size of the root HTML element is increased so that the website adopts a mobile-friendly interface.

### No absolute font-size units

The CSS for this site uses only 'ems' as a font-sizing unit.  If the user has previously set a default font-size, the CSS respects that and hopefully, there are no adverse effects on the layout.

### Adapt to decreased measure

If the measure, because of increasing font-size on a big screen decreases way too much, the 60% left-aligned layout adapts to become a full-width layout.  This is done because increasing the font-size to values as high as this may indicate a vision impaired user and we want the site to look as visible as possible.


[django]: http://djangoproject.com/
[python]: http://www.python.org/
[snn]: http://en.wikipedia.org/wiki/Spiking_neural_network
[moment]: http://github.com/schatten/moment
[jekyll]: http://github.com/mojombo/jekyll
[resume]: /resume
[email]: mailto:dipanjan.mu@gmail.com
