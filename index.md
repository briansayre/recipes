---
title: Sayre Recipes
layout: home
---
<div class="container">
    {% for post in site.posts %}
    <div class="post">
        <a href="{{ post.link }}"><img src="{{ post.img }}" class="post-img"/></a>
        <a href="{{ post.link }}" class="post-title">{{ post.title }}</a>
        <div class="post-tags">
            {% for tag in post.tags %}
            <span class="post-tag"> {{ tag }} </span>
            {% endfor %}
        </div>
    </div>
    {% endfor %}
</div>