---
layout: page
title: Writing Code and Other Shenanigans 
tagline: 
---
{% include JB/setup %}

This is my blog! It's brand new and still under construction, so a lot will change. (Mostly the front-end design and the addition of blog posts)

### All Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

#####Check back in a while if it's too ugly for you- I promise it will look beautiful soon enough!
