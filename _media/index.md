---
layout: media
category : index
---

<!-- media -->
<div>
<h2>Media</h2>
{% assign documents = site.media | sort: 'updated' | reverse %}
{% for item in documents %}
  <li>
    <a href="{{ item.url }}">
      [{{ item.category }}]  {{ item.title }}  {{ item.summary }}
    </a>
  </li>
{% endfor %}
</div>