---
layout: main
title: 테크노트
main: true
---

<ul class="catalogue">
{% assign sorted = site.pages | sort: 'date' | reverse %}
{% for page in sorted %}
{% if page.type == 'tech' %}
{% include post-list.html %}
{% endif %}
{% endfor %}
</ul>
