---
layout: wiki
category : index
---

<!-- markdownlint-disable -->

<!-- wiki -->
<h1>Wiki</h1>

<!-- TODO:: make category -->
<div>
<h2>Wiki items</h2>

{% assign documents = site.wiki | sort: 'updated' | reverse %}
{% for item in documents %}
  <li>
    <a href="{{ item.url }}">
      [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
    </a>
  </li>
{% endfor %}
</div>