---
layout: page
title: "Galleries"
date: 
modified:
excerpt:
tags: []
image:
  feature:
---

{% for gallery in site.data.galleries %}<div>
	<a href="{{ gallery.id }}.html">
		<img alt="{{ gallery.description }}" title="{{ gallery.description }}" width="150" src="{{ gallery.imagefolder }}/{{ gallery.images[0].thumb }}" />
<br/>		{{ gallery.description }}
	</a></div>
{% endfor %}
