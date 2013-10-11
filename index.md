---
layout: page
title: ZoZo's blog
tagline: Work in progress
---



I will post security and low level related pages. Stay tuned.


[Jekyll tutorial](http://www.andrewmunsell.com/tutorials/jekyll-by-example/index.html)



## List all the posts:

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>