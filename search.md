---
title: Search
permalink: /search/
---

<form action="/search/" method="get">
  <input type="text" id="search-box" name="query" placeholder="Looking for a specific page or article? Search here..">
  <input type="submit" value="search">
</form>

<ul id="search-results"></ul>

<script>
  window.store = {
    {% for post in site.recipes %}
      "{{ post.url | slugify }}": {
        "id": "{{ post.url | slugify }}",
        "title": "{{ post.title | xml_escape }}",
        "content": {{ post.content | strip_html | strip_newlines | jsonify }},
        "url": "{{ post.url | xml_escape }}"
      }
      {% unless forloop.last %},{% endunless %}
    {% endfor %}
  };
</script>

<script src="/assets/javascript/lunr.js"></script>
<script src="/assets/javascript/search.js"></script>
