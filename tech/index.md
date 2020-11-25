---
layout: main
title: 테크노트
main: true
---

<div class="loading-animation">
<ul class="catalogue">
{% assign sorted = site.pages | sort: 'date' | reverse | where: 'type', 'tech' %}
{% for page in sorted %}
{% include post-list.html %}
{% endfor %}
</ul>
</div>