---
layout: media
category : index
---

<!-- markdownlint-disable -->

<!-- media -->
<h1>Media</h1>

<!-- Music -->
<div>
<h2>Music</h2>
{% assign documents = site.media | sort: 'updated' | reverse | where:"category","Music" %}
{% for item in documents %}
  <li>
    <a href="{{ item.url }}">
      {{ item.created }} [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
    </a>
  </li>
{% endfor %}
</div>

<!-- Book -->
<div>
<h2>Book</h2>
{% assign documents = site.media | sort: 'updated' | reverse | where:"category","Book" %}
{% for item in documents %}
  <li>
    <a href="{{ item.url }}">
      {{ item.created }} [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
    </a>
  </li>
{% endfor %}
</div>