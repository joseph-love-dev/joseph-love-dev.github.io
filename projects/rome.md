---
layout: project
title: "Map of Rome"
date: "Jul 2026"
subtitle: "Interactive Map of Roman History"
permalink: /projects/rome/
---

Map of Rome is an interactive map that lets you scrub through the entire history of the Roman Empire, from the founding of the city in 753 BC to the fall of the West in AD 476. You can play with it live right here, or open the full site at [mapofrome.com](https://mapofrome.com).

<div class="live-embed">
  <iframe src="https://mapofrome.com" title="Map of Rome live site" loading="lazy"></iframe>
</div>

<a href="https://mapofrome.com" target="_blank" rel="noopener noreferrer" class="showcase-link">Open mapofrome.com in a new tab</a>

## Why I built it

My favorite podcast of all time is *The History of Rome* by Mike Duncan. It does an incredible job of covering the rise and fall of the Roman Empire. It's seventy three hours long across 179 episodes, but Mike goes year by year through the events of the entire empire, down to the little things that happened throughout its long history. While relistening to it, I came up with the idea of building a map that shows the rise and fall of Rome along with the major milestones and events that happened along the way.

This was just a for fun project. I built it in one weekend so I could have a map to look at while I relisten to the podcast. It's based on many historical maps, so I tried to be accurate with the actual land and borders, although that's pretty hard since, you know, Rome was a long time ago.

## What it does

The map lets you go year by year and see what happened in each one. You can see the famous battles, the buildings that went up, the big political events, all the significant things that led to the next year. It works the same way as Google Maps, so you can zoom all the way in and see the actual city layout of Rome, then zoom out and see the full outline of the empire.

I added some extra features along the way. Some of the battles are clickable, so you can see the formations and the storylines behind them. You can also click on famous people throughout Rome's history and follow where they went and the impact they had during their time. Julius Caesar is a great one to click on. You can really see how he went all around the empire to claim it for himself. In total there are around 590 events, 70 territory snapshots, 31 battle deep dives, and 31 people you can follow.

## How it works

The site is not that complex. It's Next.js with a static export, so there's no backend at all. Everything ships as static files and Cloudflare serves them. The map itself is MapLibre GL with a custom parchment style I made so it looks like an old atlas instead of a modern street map.

All the geometry gets precomputed by a few Node scripts that run before the site builds. Coastlines come from Natural Earth, and the borders come from DARE (Digital Atlas of the Roman Empire), which has polygons for every Roman province. Each year on the map is basically the union of whatever provinces Rome held that year, stitched together and clipped to the coastline with Turf.js. The city view of Rome is built from real elevation data plus the Tiber from OpenStreetMap, and those files only load once you zoom in far enough.
