---
layout: page
permalink: /search/
---

<h1 class="post-title">Search Results</h1>

<div id="search-results"></div>

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
