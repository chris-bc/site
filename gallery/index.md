{% for gallery in site.data.galleries %}
- [{{ gallery.description }]]({{ gallery.id }})
{% endfor %}

