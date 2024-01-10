---
title: Sayre Recipes
layout: home
---
<script type="text/javascript">
  function filterUsingCategory(selectedCategory) {
    var id = 0;
    {% for post in site.posts %}
      var cats = {{ post.tags | jsonify }}

      var postDiv = document.getElementById(++id);
      postDiv.style.display =
        (selectedCategory == 'All' || cats.includes(selectedCategory))
          ? 'unset'
          : 'none';
    {% endfor %}
  }
</script>

<div class="container">
    <button id="All" onclick="filterUsingCategory('All')">
        Show All Posts
    </button>
    {% assign tags = site.tags | sort %}
    {% for category in tags %}
    {% assign cat = category | first %}
    <button id="{{ cat }}" onclick="filterUsingCategory(this.id)">
        {{ cat }}
    </button>
    {% endfor %}

{% assign id = 0 %}
{% for post in site.posts %}
  {% assign id = id | plus:1 %}
    <div class="post" id="{{id}}">
        <a href="{{ post.link }}"><img src="{{ site.BASE_PATH }}{{ post.img }}" class="post-img"/></a>
        <a href="{{ post.link }}" class="post-title">{{ post.title }}</a>
        <div class="post-tags">
            {% for tag in post.tags %}
            <span class="post-tag"> {{ tag }} </span>
            {% endfor %}
        </div>
    </div>
{% endfor %}

</div>
