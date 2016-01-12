---
layout: post
title: "Router Mod With DD-WRT"
modified:
categories: posts
excerpt: An overview of installing and configuring the DD-WRT open source router firmware.
tags: [Development, Infrastructure, VPN]
image:
  feature:
date: 2015-05-05T11:16:20+10:00
---
> I've been interested in custom and open-source router firmware since the early noughties, when Linksys and NetComm began using GPL  components and subsequently were required to publish their source code, and did so in an incredibly-difficult-to-compile manner.
> On and off over the past couple of years I've looked at DD-WRT and OpenWRT, two of the more popular open source router firmware distributions, but never had a compelling reason to mess with them. The passage of the Metadata Retention Act into Australia, I think, changes that and makes encapsulating everything I do in a VPN much more compelling. Since I'll be messing with router settings anyway, why not mess properly?

### Why bother?
The answer used to be *"because you can"*. When Linksys first published the source code for their firmware it took the world by storm.

OK, let me rephrase. It took the Linux-using, free software-loving portion of the software development community by storm. But, you know, that's still pretty significant.

At the time it was little more than an enforced release because they were using some GPL'd libraries (and my half-hearted attempts to even get it to compile were fruitless).  But over time cleverer people and cross compilers put together [DD-WRT](http://www.dd-wrt.com) and [OpenWRT](https://openwrt.org) custom firmware releases. Over time they developed and diverged, and were joined by a lot of other options. 

Currently the three biggies are DD-WRT (feature rich), OpenWRT (package-based, essentially a Linux distro for your router) and [Tomato](http://www.polarcloud.com/tomato) (Pretty and user-friendly). Each of them let you tweak router configuration and do things you can't do from a typical router configuration interface. So the big reasons to use one are to gain extra control, functions or analytics from your router.

### Which firmware?
I don't have a lot of time and (I assume) picking and choosing packages will take a bit of that, so OpenWRT is out.

I want the capacity to play and tweak, and want solid VPN configuration and performance, which makes me lean more toward DD-WRT than Tomato. Decision made.

There are [lots](https://vpncritic.com/tomato-vs-dd-wrt-vs-openwrt/) [of](http://securerouter.org/tech-tips/dd-wrt-or-tomato-or-openwrt-or/) [sites](http://vpnpick.com/dd-wrt-vs-tomato-vs-open-wrt/) offering comparisons so take a look and decide for yourself.

### Which router?
The obvious choice is the router plugged into your wall right now. The obvious consequence of that, however, is that you'll be out of Internet during the upgrade. Possibly longer if things don't go to plan.

In any event, in my case my current router is about four years old, was cheap at the time, struggles to stream things to my Apple TV and, if it started having to tunnel all traffic through a VPN, would probably have a heart attack. All in all a good set of excuses to get a new router.

I spent some time Googling, comparing and reading reviews and ended up with the [Netgear R7000 Nighthawk](http://www.netgear.com.au/home/products/networking/wifi-routers/R7000.aspx?gclid=CN2VlNvCsMUCFdcjvQoduXAATA).

<figure>
	<img class="centered-image" alt="Netgear R7000 Nighthawk" src="/images/2015-ddwrt/nighthawk.jpg">
	<figcaption>Netgear R7000 Nighthawk. Almost like a batmobile</figcaption>
</figure>

### Getting ready
Now it's time to download firmware versions and a copy of the DD-WRT installation instructions just in case things don't go to plan. Normally this is simply a case of looking up your router in the [supported routers database](http://www.dd-wrt.com/site/support/router-database) and downloading the initial ROM and, possibly, an additional recommended ROM. It turns out the NightHawk is a special case here, however, and isn't listed in the database. Hmmmm...

But it's far from unsupported. Useful documentation is still relatively prevalent, and if you look around there are loads of good resources. But the one you should pay attention to if you're using a NightHawk (it's updated every couple of weeks) is [this forum post](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=264152).

Otherwise:

* [General DD-WRT installation instructions](http://www.dd-wrt.com/wiki/index.php/Installation)
* [General DD-WRT tutorials](http://www.dd-wrt.com/wiki/index.php/Tutorials)
* [Someone else's NightHawk installation blog entry](http://www.tweaking4all.com/hardware/netgear-r7000-dd-wrt/)

And of course, the ROMS:

* [ftp://ftp.dd-wrt.com/betas/2015/](ftp://ftp.dd-wrt.com/betas/2015/)
* [NightHawk Only - http://www.desipro.de/ddwrt-ren/K3-AC-Arm/](http://www.desipro.de/ddwrt-ren/K3-AC-Arm/)
* [NightHawk Only - http://desipro.de/ddwrt/K3-AC-Arm/](http://desipro.de/ddwrt/K3-AC-Arm/)

Which ROM to install isn't so straightforward if you're using a NightHawk and nobody seems willing to give advice. If you're not using a NightHawk, just download whatever the supported routers database tells you to. The detailed forum post says the last build with working bridge mode was 26125, but that is **very** old, and it also lists several problems fixed in February and March 2015. So what the hey, maybe the very latest build is the best idea?

For me that's 2015-05-19, so down it comes. As does the latest stock firmware from NetGear, just in case it all goes wrong I want to have that handy.

###Flashing DD-WRT
Time to install it.

Connect your computer to your router with an ethernet cable and, if it's not a brand new router, clear your web browser's cache.

Log into your router's management page, find the page to upload a new firmware version, and upload the DD-WRT initial firmware. Continue through any warnings you get and wait for the process to complete in full. Do what's necessary for a factory reset to clear NVRAM, for the NightHawk this is easy - Just go to its management page (you'll need to set an initial username and password first), then:
<figure>
	<img class="centered-image" alt="Administration-Factory-defaults" src="/images/2015-ddwrt/factory-restore.jpg">
	<figcaption>Administration section, Factory Restore tab</figcaption>
</figure>

This will result in a reboot and you'll need to again set an initial username and password. Configure the router as you need to, but here are some tidbits

### WiFi settings
It seems like setting an upper-upper extension channel makes a considerable difference - I have't yet had time to trial different combinations of settings, but this is what I'm currently using.

<figure>
	<img class="centered-image" alt="Wireless settings" src="/images/2015-ddwrt/wireless-settings.jpg">
	<figcaption>Current wireless settings for my 5GHz interface</figcaption>
</figure>

### Testing performance
On a Mac, you can get some useful information on your network connection by option-clicking on the wireless icon in the menu bar:

<figure>
	<img class="centered-image" alt="Detailed wireless connection info" src="/images/2015-ddwrt/wireless-status.jpg">
	<figcaption>Detailed network connection information is available on a Mac by option-clicking the wireless icon</figcaption>
</figure>

As you can see, the current connection speed is nearly 900MB/s, so I'm not too worried about testing different combinations of settings at the moment.
