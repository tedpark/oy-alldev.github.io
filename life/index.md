---
layout: main
main: true
title: 소소한 이야기
description: 개발팀의 소소한 소로그
---

<ul class="catalogue">
{% assign sorted = site.pages | sort: 'date' | reverse %}
{% for page in sorted %}
{% if page.type == 'life' %}
{% include post-list.html %}
{% endif %}
{% endfor %}
</ul>
