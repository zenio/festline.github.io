---
layout: article
permalink: /contacts
title: "Demo assignments"
comments: false
image:
  teaser: assignments-demo-teaser.png
---

<div class="tiles">
{% for post in site.posts %}
	{% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->
