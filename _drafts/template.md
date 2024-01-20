---
layout: default
title: "Title Here"
date: YYYY-MM-DD
tags: TODO
imgfolder: title-here
---

{% include postbuttons.html %}
  
# {{ page.title }}  

<img class="recipe-img" src="{{ site.baseurl }}/assets/img/{{ page.imgfolder }}/1.jpg" alt="{{ page.title }} Image">

## Ingredients

-
  
## Directions

1.

## Notes

## Source

[Title](link)

## Images

{% include postimages.html %}

## To Do (delete when done)

- Copy this file into /_posts
- Name file appropiately (YYYY-MM-DD-title-here.md)
- Create a folder at assets/img/ with the title as the name (title-here)
- Upload at least 1.jpg to the folder
- Update front matter
- Fill out ingredients, directions, etc.