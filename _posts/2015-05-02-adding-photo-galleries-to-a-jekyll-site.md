---
layout: post
title: "Adding Photo Galleries to a Jekyll Site"
modified:
categories: posts
excerpt: A short guide on adding a sexy (if I say so myself) photo gallery to a Jekyll site (this one)
tags: [development, web, html, css, javascript]
image:
  feature: gallery-title.jpg
date: 2015-05-02T07:11:24+10:00
---

As you can probably tell I use the [Jekyll](http://jekyllrb.com) static site processing engine as the basis for this site. I switched to Jekyll only a few months ago when, after ignoring my site for some time, I wanted to add some content and discovered that my Drupal database had been broken into and all content deleted. This came on the back of years of continued Wordpress patching (or lack of patching followed by defacing of my site), and finally I'd had enough and felt a yearning for the good old days when sites were simple and didn't need dynamic content or databases.

After some Googling I found Jekyll, which fit the bill perfectly and dead simple to create great-looking pages to boot.

But then came the day I wanted to add a photo gallery.

It turned out that was dead simple too, but was an interesting process. And from the research I did I think I approached it slightly differently (and I think - of course) with slightly better results than other sites I found describing how to do the same thing.

So without further ado:

#### Step 1. Define your data
Create a YAML data file describing your galleries in your jekyll _data directory.

{% highlight yaml %}
- id: gilli-diving
  description: Diving on Gilli Air
  imagefolder: /images/2015-gilli
  images:
  - name: gilli-1.jpg
    thumb: thumb-1.jpg
    text: Hanging at the bungalow drinking coconuts
  - name: gilli-2.jpg
    thumb: thumb-2.jpg
    text: View from our room
- id: perp-anzac
  description: Point Perp
  imagefolder: /images/2015-perp
  images:
  - name: perp-1.jpg
    thumb: thumb-1.jpg
    text: Brittany's first ever trad lead
  - name: perp-2.jpg
    thumb: thumb-2.jpg
    text: On my way up
{% endhighlight %}

#### Step 2. Add a galleries link to your navigation
Add an entry to `_data/navigation.yml` directing to your galleries page (we'll create it next).

#### Step 3. Create your galleries page
Create a new page wherever your galleries link was pointing - For me that was `/gallery/index.md`. This page creates thumbnail links to each gallery, using a gallery image (randomised each time the site is re-generated).
{% highlight html %}{% raw %}
---
layout: page
title: "Galleries"
---
<div style="overflow: auto;">
{% for gallery in site.data.galleries %}
{% assign random = site.time | date: "%s%N" | modulo: gallery.images.size %}
	<div class="gallery-thumb">
		<a href="{{ gallery.id }}.html">
			<img alt="{{ gallery.description }}" title="{{ gallery.description }}" src="{{ gallery.imagefolder }}/{{ gallery.images[random].thumb }}" />
			<p>{{ gallery.description }}<br />{{ gallery.images | size }} images</p>
		</a>
	</div>
{% endfor %}
</div>
{% endraw %}{% endhighlight %}

Don't worry about the CSS, we'll deal with that later.

#### Step 4. Define a gallery layout
You'll need a (mostly-blank) markdown page for each gallery, but first we're going to define the layout template used to display a gallery.
Create `_layouts/gallery.html` using something like:
{% highlight html %}{% raw %}
---
layout: page
---
<link href="/assets/css/extra.css" rel="stylesheet" />

{% for gallery in site.data.galleries %}
	{% if gallery.id == page.galleryid %}
		<h1>{{ gallery.description }}</h1>
		<div class="list-gallery">
		{% for image in gallery.images %}
			<a href="{{ gallery.imagefolder }}/{{ image.name }}" itemprop="url" title="{{ image.text }}">
				<img alt="{{ image.text }}" title="{{ image.text }}" src="{{ gallery.imagefolder }}/{{ image.thumb }}" />
			</a>
		{% endfor %}
		</div>
	{% endif %}
{% endfor %}
{% endraw %}{% endhighlight %}

#### Step 5. Create your gallery pages
This step is trivial but, because Jekyll generates static pages, needs to be done. Create a new markdown page in your gallery's `imagefolder` for each gallery. My `gallery/gilli-diving.md`, for example, is:
{% highlight yaml %}
---
layout: gallery
galleryid: gilli-diving
---
{% endhighlight %}

#### Step 6. Make it pretty
A few SASS niceties largely finish things off. I created a new file `_sass/extra.scss`, importing it into `assets/css/main.scss' with
{% highlight  sass %}
@import "extra"
{% endhighlight %}
_sass/extra.scss:
{% highlight sass %}
%gallery img {
	padding: 3px !important;
	margin: 1px 1px 0 0;
	height: 150px;
}

%gallery img:hover {
	border: #009999 solid 3px !important;
	padding: 0px !important;
}

.list-gallery {
	@extend %gallery;
	line-height: 0;
}

.gallery-thumb {
	@extend %gallery;
	text-align:center;
	display:block;
	margin: 3px;
	float: left;
	vertical-align: middle;
}
{% endhighlight %}

#### Step 7. Add Lightbox support
I also added [Lightbox](http://lokeshdhakar.com/projects/lightbox2/) support when I was initially building this, and then became extremely confused about why I had two Lightbox-like photo slideshows layered atop one another. It looks like Jekyll already comes bundled with Lightbox, making this unnecessary.

So there you have it. Done, and it looks like [this](/gallery/).
