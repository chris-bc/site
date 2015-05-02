---
layout: post
title: "The New Android Emulator You Have to Try"
modified:
categories: posts
excerpt:
tags: [development, android, mobile]
image:
  feature: 2015-genymotion/genymotion-title.jpg
date: 2015-05-03T05:49:13+10:00
---
Anyone who has ever [developed Android applications](http://developer.android.com) will agree that the single most frustrating aspect of Android development is the painstaking poor performance and bugginess of Google's official Android emulator. Networking and file storage don't work as they should (I once spent about four hours debugging an issue with file storage - Turned out it was only an issue on the official emulator; other emulators and actual devices worked fine), frequent use will inevitably get you into an "insufficient storage" cycle requiring you to re-create your virtual device over and over again. And all of this in a tool that is so. slow. it. hurts. And has a serious impact on your coffee consumption thanks to the never-ending *"I'll just grab a coffee while the emulator's restarting"*.

So it's quite possible the folks at [Genymotion](http://www.genymotion.com) saved my life.

<figure>
	<img class="centered-image" src="/images/2015-genymotion/logo.png" alt="Genymotion Logo" />
</figure>

These guys have taken the AndroVM open source project, added some significant wow factor, and made it freely available for personal use.

The stats are:

* Available on Mac, Windows and Linux
* Built on [VirtualBox](http://www.virtualbox.org) (need to download separately on Mac, I think the VirtualBox Runner comes with the downloads for the other platforms)
* Brilliantly fast
* Integrates with Eclipse and AndroidStudio
* Did I mention how fast it was?

So do your heart a favour to and check it out.

<figure>
	<img alt="Genymotion comic" src="/images/2015-genymotion/comic.png" />
	<figcaption>This is how Genymotion explain their product</figcaption>
</figure>
