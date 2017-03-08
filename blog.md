---
layout: page
title: Blog (IFT6266 project)
---

This will be my blog for the IFT6266-H2017 project.

{% for post in paginator.posts %}
	{% include post.html %}
{% endfor %}
