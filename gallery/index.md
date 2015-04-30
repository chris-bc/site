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
	<div class="gallery-thumb">
		<a href="{{ gallery.id }}.html">
			<img alt="{{ gallery.description }}" title="{{ gallery.description }}" src="{{ gallery.imagefolder }}/{{ gallery.images[0].thumb }}" />
			<p>{{ gallery.description }}</p>
		</a>
	</div>
{% endfor %}
</div>
