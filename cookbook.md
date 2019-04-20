---
layout: page
title: Cookbook
permalink: /cookbook/
---

{% assign pages = site.cookbook-pages | group_by: "name"  %}

<ul class="cookbook-pages">
    {% for page in pages %}
        <li>
            <a href="/cookbook/{{ page.name }}"><img src="/assets/cookbook-page-{{ page.name }}.jpg" class="cookbook-page__thumbnail" /></a>
            <ul class="cookbook-page--recipe-list">
                {% assign recipes = site.recipes | where: "page", page.name | sort: "name" %}
                {% for recipe in recipes %}
                    <li>
                        <a href="{{ recipe.url | relative_url }}">{{ recipe.name | escape }}</a>
                    </li>
                {% endfor %}
            </ul>
        </li>
    {% endfor %}
</ul>
