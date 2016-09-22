---
layout: page
title: Categories
date: 2016-03-18T11:18:46+08:00
modified:
excerpt:
tags: []
image:
  feature:
share: false
---

{% for category in site.categories %}
  <div markdown="0"><a href="/categories/{{ category[0] }}/" class="btn">{{ category[0] }} <sup>{{ category[1].size }}</sup></a></div>
{% endfor %}
