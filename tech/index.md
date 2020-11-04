---
layout: main
title: Blog
description: 올리브영에서 사용중인 기술들
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
