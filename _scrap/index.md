---
layout: scrap
category : index
---

<!-- markdownlint-disable -->

<!-- Scrap -->
<h1>Scrap</h1>

<!-- TODO:: make category -->
<div>
<h2>Scrap</h2>

{% assign documents = site.scrap | sort: 'updated' | reverse %}
{% for item in documents %}
  <li>
    <a class="main" href="{{ item.url }}">
      [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
    </a>
  </li>
{% endfor %}
</div>