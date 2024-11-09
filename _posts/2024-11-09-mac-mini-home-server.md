---
title: "Mac Mini Home Server"
tags: [home-lab]
---

I just purchased a new [Mac Mini](https://www.apple.com/mac-mini/) with the intent of setting it up as a home server.

Despite being a pretty typical nerdy tech guy that works professionally in the DevOps world - I don't actually have any kind of home lab or real home server set up right now.
I do have an old gaming desktop that I "converted" to a home server a couple of years ago when I built my new desktop PC, but in practice I haven't used it at all.
Why?
The fans are loud, it's not cheap to leave running 24/7, and I just haven't really had much of a desire to build out a home server - until now.

The Mac Minis have always been interesting, and they've always been popular - being the cheapest entry into the MacOS ecosystem.
But the migration to M-series Apple Silicon made things...**really** interesting.
Suddenly these small boxes weren't limited by the low tier Intel chips.

The latest iteration powered by [Apple M4 chips](https://www.apple.com/newsroom/2024/05/apple-introduces-m4-chip/) are performance powerhouses.
Even the base model M4 has single-core performance that is among the best in the industry, second only to the M4 Pro/M4 Max.
It's no slouch with multi-core performance either.
Apple **finally** doubled the RAM in the base model to 16GB.
And it's packed with Thunderbolt 4 (Thunderbolt 5 in the M4 Pro variant) ports on the back.

In addition, Apple designed an all new, even mini-er case.
It now looks more like a miniature [Mac Studio](https://www.apple.com/mac-studio/).
For a mere $599 ($499 education pricing) you can get a machine with an incredible amount of power packed into a box with a five inch by five inch footprint that sips power - about 5 watts at idle and 20 watts under load.
My gaming desktop idles between 100W-150W and tops out at more than 600W under full load.
Drawing only 5 watts of power - I can run the machine at idle 24/7 for less than five dollars a year.

I opted for the base model - which I think will be perfect for my lower-power home server needs.
And it's a low-cost entry to the great Mac server experiment.
But if you want, you can spec up the Mini with an M4 Pro and up to 64GB RAM to turn it into a true desktop-grade workstation in a tiny box.
A tiny box that will outperform a $4000 Mac Studio with an M2 Ultra chip from just two years ago.

So why now?
What makes me want to build out a home server now?

I've been getting more serious about media preservation and archiving, especially now that we've got a mountain of photos and videos of our young kids.
While I do back these up to a cloud service, I would like to have local copies available on network attached storage.
And with [Tailscale](https://tailscale.com/), I can now easily build out a virtual private network with all of our household devices so that network storage can safely be accessed anywhere.

In addition to media management, I plan on setting up some [self-hosted](https://www.reddit.com/r/selfhosted/) software for use on the network.
Docker makes it trivially easy to run SaaS-style software at home these days.

I am not quite sure how I will like using MacOS as a "headless" server in the traditional sense.
While I am very experienced managing Linux servers remotely, I know that MacOS doesn't have quite the same capabilities.
Yes I can still run a SSH server and access it remotely like that, but there are oddities with MacOS.
Apple does have a full remote desktop feature built into the OS, which I am sure I will try out to see how that goes.

For now the Mac will live on top of my Desk next to my docked Macbooks, but I hope to move it into a closet in my office along with a Thunderbolt 4 RAID storage drive.
Hopefully the tiny power draw and low amount of heat means it will happily live in a closet.

The Mac is due for delivery on Monday.
I'll post an update in a little bit once I start experimenting and settings things up!
