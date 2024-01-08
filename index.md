---
title: Sayre Recipes
---
## Welcome
Welcome to Brian Sayre's recipe collection.

## Posts
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>