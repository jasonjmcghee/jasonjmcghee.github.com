---
layout: post
title: "Simple CSS Game"
description: ""
category: "GameDev"
tags: [css, js, html, game]
---
{% include JB/setup %}

A recently made a [small game](https://jasonjmcghee.github.io/LightsGame), graphically CSS-based, and powered by Javascript.
The general or "normal" mode of the game is very similar to that of the popular puzzle game "Lights Out," however by adding
a single style option to the list elements (visually, squares in the grid) we have an entirely different game! (I dubbed this
hardcore mode, as there is no way to undo your moves easily- specifically, squares disappear instead of lighting up.)

Specifically this style option is:
{% highlight css %}
  backface-visibility: hidden;
{% endhighlight %}

Now, I did change the transformation to rotating only 90 degrees for aesthetic appeal (it looks like it's disappearing that
way), but by simply adding a single style option, it's fun how drastically different the puzzle becomes. I began developing
the game by writing only CSS; I made it feel and look nice, then implemented the logic with Javascript. I think it'd be fun
to try my luck at building a game using at little javascript as possible. The best route might be to use SCSS as I could
implement some more logic- but the game would have some tight restrictions as we can't (for example) even check to see if
a DOM element was clicked (only if it's currently being clicked or hovered over). CSS isn't as limiting as I once thought,
however. There are quite a few selectors like 'nth-child' which are rather useful for dynamic CSS and have great potential
for pure (or mostly) CSS projects.

On a random note- I haven't been posting recently due to midterm season, my jobs and my applying for internships for the summer
and the interviews for said potential internships. I know I need to expand my portfolio drastically, however (I don't think my
collection of projects reflects on my ability in the slightest and that needs to change) and blog posts are a great supplement
to completing random projects, web apps or games. I think that'll be all for now- but as a sneak peek, I think I'll be working
towards some pure (or nearer to) CSS examples/demos, and maybe diving into WebGL and shaders.

