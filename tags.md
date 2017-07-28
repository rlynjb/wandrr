---
layout: page
title: Tags
permalink: /tags/
---

<div class="tags-wrapper">
  <h4>i blog about..</h4>
  {% capture site_tags %}{% for tag in site.tags %}{{ tag[1].size }}#{{ tag | first | downcase }}#{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
  {% assign tag_hashes = site_tags | split:',' | sort %}
  <ul class="list-group">
    {% for hash in tag_hashes reversed %}
      {% assign keyValue = hash | split: '#' %}
      {% capture tag_word %}{{ keyValue[2] | strip_newlines }}{% endcapture %}
      <li class="list-group-item">
        <a href="/tags/#{{ tag_word }}">
          {{ tag_word }}
          <span class="badge pull-right">{{ site.tags[tag_word].size }}</span>
        </a>
      </li>
    {% endfor %}
  </ul>
</div>

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

  <h4 id="#{{ t }}">
    {{ t | downcase }}
  </h4>
  <ul>
    {% for post in posts %}
      {% if post.tags contains t %}
        <li>
          <a href="{{ post.url }}">{{ post.title }}</a>
          <span class="date">{{ post.date | date: "%B %-d, %Y"  }}</span>
        </li>
      {% endif %}
    {% endfor %}
  </ul>
{% endfor %}
