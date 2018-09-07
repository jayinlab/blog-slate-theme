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
    <a class="main" href="{{ item.url }}">
      {{ item.updated }} [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
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
    <a class="main" href="{{ item.url }}">
      {{ item.updated }} [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
    </a>
  </li>
{% endfor %}
</div>

<!-- Docu -->
<div>
<h2>Docu</h2>
{% assign documents = site.media | sort: 'updated' | reverse | where:"category","Docu" %}
{% for item in documents %}
  <li>
    <a class="main" href="{{ item.url }}">
      {{ item.updated }} [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
    </a>
  </li>
{% endfor %}
</div>

<!-- Game -->
<div>
<h2>Game</h2>
{% assign documents = site.media | sort: 'updated' | reverse | where:"category","Game" %}
{% for item in documents %}
  <li>
    <a class="main" href="{{ item.url }}">
      {{ item.updated }} [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
    </a>
  </li>
{% endfor %}
</div>