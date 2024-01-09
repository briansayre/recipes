---
title: Sayre Recipes
layout: home
---
{% for post in site.posts %}
<div class="post">
    <img src="{{ post.img }}" class="post-img"/>
    <a href="{{ post.link }}" class="post-title">{{ post.title }}</a>
    <div class="post-tags">
    {% for tag in post.tags %}
        <span class="post-tag"> {{ tag }} </span>
    {% endfor %}
    </div>
</div>
{% endfor %}