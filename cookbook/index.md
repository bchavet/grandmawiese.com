---
layout: page
title: Cookbook
permalink: /cookbook/
---

{% assign pages = site.recipes | group_by: "page" | sort: "name" | uniq %}

<ul class="cookbook-pages">
<!--
    <li>
        <img src="/assets/cookbook-page-1.jpg" class="cookbook-page__thumbnail" />
    </li>
-->

    {% for page in pages %}
        <li>
            <img src="/assets/cookbook-page-{{ forloop.index | plus:1 }}.jpg" class="cookbook-page__thumbnail" />
            <ul class="cookbook-page--recipe-list">
                {% assign recipes = page.items | sort: "index" %}
                {% for recipe in recipes %}
                    <li>
                        <a href="{{ recipe.url | relative_url }}">{{ recipe.name | escape }}</a>
                    </li>
                {% endfor %}
            </ul>
        </li>
    {% endfor %}
</ul>
