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
  function filterUsingSearch(searchText) {
    var id = 0;
    {% for post in site.posts %}
      var title = {{ post.title }}
      
      var postDiv = document.getElementById(++id);
      postDiv.style.display =
        (searchText == '' || title.toLowerCase().includes(searchText.toLowerCase()))
          ? 'unset'
          : 'none';
    {% endfor %}
  }
</script>

<div class="container">
    <a  href="{{ site.baseurl }}/" class="navbar-item">
        <h1 class="title block">{{ site.title }} </h1>
    </a>
    <div class="block">
        <button id="All" class="button" onclick="filterUsingCategory('All')">
            Show All Posts
        </button>
        {% assign tags = site.tags | sort %}
        {% for category in tags %}
        {% assign cat = category | first %}
        <button id="{{ cat }}" class="button" onclick="filterUsingCategory(this.id)">
           {{ cat }}
        </button>
        {% endfor %}
    </div>
    <div class="block">
      <div class="field has-addons">
        <div class="control">
          <input class="input" type="text" id="search-text" placeholder="Search recipes">
        </div>
        <div class="control">
          <a class="button is-info" onclick="filterUsingCategory(document.getElementById('search-text').value)">
            Search
          </a>
        </div>
      </div>
    </div>
    <div class="block columns is-multiline is-mobile">
        {% assign id = 0 %}
        {% for post in site.posts %}
        {% assign id = id | plus:1 %}
        <div class="column" id="{{id}}">
            <a href="{{ site.baseurl }}{{ post.url }}">
                <div class="card">
                    <div class="card-image">
                        <figure class="image">
                            <img src="{{ site.baseurl }}{{ post.img }}" class="card-img" alt="image">
                        </figure>
                    </div>
                    <div class="card-content">
                        <div class="media-content">
                            <p class="title is-4">{{ post.title }}</p>
                        </div>
                        <div class="content">
                            {% for tag in post.tags %}
                            <span class="tag"> {{ tag }} </span>
                            {% endfor %}
                        </div>
                    </div>
                </div>
            </a>
        </div>
        {% endfor %}
    </div>
</div>
