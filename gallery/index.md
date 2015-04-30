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

<div style="overflow: auto;">
{% for gallery in site.data.galleries %}
{% assign random = site.time | date: "%s%N" | modulo: gallery.images.size %}
	<div class="gallery-thumb">
		<a href="{{ gallery.id }}.html">
			<img alt="{{ gallery.description }}" title="{{ gallery.description }}" src="{{ gallery.imagefolder }}/{{ gallery.images[random].thumb }}" />
			<p>{{ gallery.description }}<br/>{{ gallery.images | size }} images</p>
		</a>
	</div>
{% endfor %}
</div>
