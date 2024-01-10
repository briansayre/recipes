---
title: Sayre Recipes
layout: default
---
<script type="text/javascript">
  function filterUsingCategory(selectedCategory) {
    var id = 0;

    {% for post in site.posts %}
    var cats = {{ post.tags | jsonify }}
    var postDiv = document.getElementById(++id);
    postDiv.style.display = (selectedCategory == 'All' || cats.includes(selectedCategory)) ? 'unset' : 'none';
    {% endfor %}
  }
  function filterUsingSearch(searchText) {
    var id = 0;

    {% for post in site.posts %}
    var title = "{{ post.title }}"
    var postDiv = document.getElementById(++id);
    postDiv.style.display = (searchText == '' || title.toLowerCase().includes(searchText.toLowerCase())) ? 'unset' : 'none';
    {% endfor %}
  }
</script>

<div class="block">
  <div class="is-flex is-flex-direction-row	is-flex-wrap-wrap	is-justify-content-space-between is-align-content-flex-start">
    <div class="buttons">
      <button id="All" class="button is-success-dark" onclick="filterUsingCategory('All')">
          Show All Posts
      </button>
      {% assign tags = site.tags | sort %}
      {% for category in tags %}
      {% assign cat = category | first %}
      <button id="{{ cat }}" class="button is-success-dark" onclick="filterUsingCategory(this.id)">
          {{ cat }}
      </button>
      {% endfor %}
    </div>
    <div class="">
      <div class="field has-addons">
        <div class="control">
          <input class="input" type="text" id="search-text" placeholder="Search recipes">
        </div>
        <div class="control">
          <a class="button is-info has-background-success-dark" id="search-button" onclick="filterUsingSearch(document.getElementById('search-text').value)">
            Search
          </a>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="block columns is-multiline is-mobile">
    {% assign id = 0 %}
    {% for post in site.posts %}
    {% assign id = id | plus:1 %}
    <div class="column is-full-mobile is-one-third-tablet is-half-desktop is-one-quarter-widescreen is-one-quarter-fullhd" id="{{id}}">
        <a href="{{ site.baseurl }}{{ post.url }}">
            <div class="card">
                <div class="card-image">
                    <figure class="image">
                        <img src="{{ site.baseurl }}{{ post.img }}" class="card-img" alt="image">
                    </figure>
                </div>
                <div class="card-content">
                    <div class="media-content">
                        <p class="title is-4 has-text-success-dark" id="post-title">{{ post.title }}</p>
                    </div>
                    <div class="content">
                        <br>
                        {% for tag in post.tags %}
                        <span class="tag"> {{ tag }} </span>
                        {% endfor %}
                        <br>
                        <time datetime="{{ post.date }}">{{ post.date }}</time>
                    </div>
                </div>
            </div>
        </a>
    </div>
    {% endfor %}
</div>