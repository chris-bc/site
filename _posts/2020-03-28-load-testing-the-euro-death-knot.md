---
layout: post
title: "Load Testing the Euro Death Knot (flat overhand)"
modified:
categories: posts
excerpt: Can a flat overhand knot (aka Euro Death Knot) undo itself under high load?
tags: [Climbing, Abseiling]
image:
  feature:
date: 2020-03-28T18:15:57+11:00
---
As climbers, we all know that the flat overhand knot, or Euro Death Knot (EDK), is preferred over the double fisherman's bend when joining ropes for a long rappel because its flat profile makes it much less likely to get snagged when pulling the rope. We also know that we should make sure to have 30 - 50cm of tail in the knot because it slips under tension, and we don't want it to come undone.

*Right?*

Have you ever seen any data to back that up?
I haven't, and after discussing this recently I thought it would be interesting to perform some pull tests to see how this stacks up.

Before going any further I should be very clear that this is **not conclusive**. This was two tests of two scenarios, performed _once_. It's impossible to draw conclusions from this of all ropes, and knots tied, dressed and set in all different ways. Personally, I will still be using 30-50cm tails when I rap on an EDK, but I'll be much less concerned about the length of the tails.

## Setup ##
* Loads were measured using a Rock Exotica enForcer load cell, running at two samples per second;
* One end of the load cell was attached to an anchor constructed of 4 strands of 25mm tube tape;
* The other end of the load cell was attached to one of the ropes being tested using a bowline;
* The second rope being tested was attached to an 8:1 mechanical advantage system (a compound system of three 2:1 systems), again using a bowline;
* Maximum load was applied for at least 10 seconds.
<figure class="half">
	<a href="/images/2020-edk/test.jpg"><img src="/images/2020-edk/test-thumb.jpg" /></a>
	<a href="/images/2020-edk/haul.jpg"><img src="/images/2020-edk/haul-thumb.jpg" /></a>
	<figcaption>Backyard testing</figcaption>
</figure>

## Notes ##

* To "set" a knot is to hand-tighten it. The usual way of doing this is to hold the knot in one hand, and with the other pull each of the four strands in turn, repeating until the knot is firm and the tails no longer move.
* Bear in mind that this shows the results from **a single test** of four different scenarios. It would be inappropriate and unsafe to draw conclusions from this.
* A key reason for this is that I've been tying knots in a particular way for 20 years. Your method of dressing and setting knots, or your rope, could have wildly different results.
* **What's "kgf"?** kN are a measure of force, kg are a measure of mass. *kgf* is a common notation to represent *a force equivalent to this many kilograms*. You can read this as kg.

## Results ##
<table><thead><tr class="header">
<th>Rope</th><th>Knot<br/>set?</th><th>Tail length<br/>Start (cm)</th><th>Force</th><th>Tail Length<br/>End (cm)</th><th>Tail Loss (cm)</th></tr></thead>
<tbody>
<tr class="odd">
<td class="left">Sterling Fusion Nano 9.2mm<br/>Dynamic, manfd. 2012</td>
<td>Yes</td><td>12.5<br/>12</td><td>3.52kN<br/>(360kgf)</td><td>10.5<br/>10</td><td><strong>2<br/>2</strong></td></tr>
<tr class="even">
<td class="left">Sterling Fusion Nano 9.2mm<br/>Dynamic, manfd. 2012</td>
<td>No</td><td>10<br/>7.5</td><td>2.78kN<br/>(282kgf)</td><td>7<br/>3.3</td><td><strong>3<br/>4.2</strong></td></tr>
<tr class="odd"><td class="left">Edelrid 10.5mm<br/>Dynamic, manfd. 2002</td><td>Yes</td><td>10.5<br/>10</td><td>3.04kN<br/>(310kgf)</td><td>10.5<br/>10</td><td><strong>0<br/>0</strong></td></tr>
<tr class="even"><td class="left">Edelrid 10.5mm<br/>Dynamic, manfd. 2002</td><td>No</td><td>8<br/>8</td><td>2.96kN<br/>(302kgf)</td><td>6.9<br/>6.7</td><td><strong>1.1<br/>1.3</strong></td></tr>
</tbody></table>

## Photos ##
{:refdef: style="display: block; text-align: center; margin-bottom: 2em;"}
<figure class="half">
	<a href="/images/2020-edk/nano-set-before.jpg"><img src="/images/2020-edk/nano-set-before-thumb.jpg" style="float: none;"/></a>
	<a href="/images/2020-edk/nano-set-after.jpg"><img src="/images/2020-edk/nano-set-after-thumb.jpg" style="float: none;"/></a>
	<figcaption>Sterling Fusion Nano 9.2, knot dressed and set, before and after</figcaption>
</figure>
{: refdef}

{:refdef: style="display: block; text-align: center; margin-bottom: 2em;"}
<figure class="third">
	<a href="/images/2020-edk/nano-set-load-cell.jpg"><img src="/images/2020-edk/nano-set-load-cell-thumb.jpg" style="float: none;"/></a>
	<a href="/images/2020-edk/nano-set-after-top.jpg"><img src="/images/2020-edk/nano-set-after-top-thumb.jpg" style="float: none;"/></a>
	<a href="/images/2020-edk/nano-set-after-bottom.jpg"><img src="/images/2020-edk/nano-set-after-bottom-thumb.jpg" style="float: none;"/></a>
	<figcaption>A closer look at the knot after loading</figcaption>
</figure>
{: refdef}

{:refdef: style="display: block; text-align: center; margin-bottom: 2em;"}
<figure class="half">
	<a href="/images/2020-edk/nano-loose-before-1.jpg"><img src="/images/2020-edk/nano-loose-before-1-thumb.jpg" style="float: none;"/></a>
	<a href="/images/2020-edk/nano-loose-before-2.jpg"><img src="/images/2020-edk/nano-loose-before-2-thumb.jpg" style="float: none;"/></a>
	<figcaption>Sterling Fusion Nano 9.2, knot loose, before</figcaption>
</figure>
{: refdef}

{:refdef: style="display: block; text-align: center; margin-bottom: 2em;"}
<figure class="half">
	<a href="/images/2020-edk/nano-loose-load-cell.jpg"><img src="/images/2020-edk/nano-loose-load-cell-thumb.jpg" style="float: none;"/></a>
	<a href="/images/2020-edk/nano-loose-after.jpg"><img src="/images/2020-edk/nano-loose-after-thumb.jpg" style="float: none;"/></a>
	<figcaption>Sterling Fusion Nano 9.2, knot loose, after</figcaption>
</figure>
{: refdef}


{:refdef: style="display: block; text-align: center; margin-bottom: 2em;"}
<figure class="third">
	<a href="/images/2020-edk/eddy-loose-before-1.jpg"><img src="/images/2020-edk/eddy-loose-before-1-thumb.jpg" style="float: none;"/></a>
	<a href="/images/2020-edk/eddy-loose-before-2.jpg"><img src="/images/2020-edk/eddy-loose-before-2-thumb.jpg" style="float: none;"/></a>
	<a href="/images/2020-edk/eddy-set-load-cell.jpg"><img src="/images/2020-edk/eddy-set-load-cell-thumb.jpg" style="float: none;"/></a>
	<figcaption>Testing the Edelrid 10.5mm</figcaption>
</figure>
{: refdef}

