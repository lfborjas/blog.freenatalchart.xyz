+++
title = "Soft Launch"
date = 2020-10-26
+++

Last week, on 10/17 we soft-launched [freenatalchart.xyz](https://freenatalchart.xyz)! My wife, who runs [Labyrinthos](https://labyrinthos.co) included it in a newsletter, and we've had 1.6K querents since. 

Here's the ["natal chart" for the moment](https://freenatalchart.xyz/full-chart?location=Borough+of+Queens%2C+New+York%2C+United+States+of+America&month=10&day=17&year=2020&hour=11&minute=24&day-part=pm&lat=40.6815&lng=-73.8365) when we first went live:

{{ figure(src="/launch-chart.svg", style="max-width: 600px", caption="Sat, 17 Oct 2020 23:24:00 - Queens, New York") }}

From what I can gather, the site was snappy: ~2 second average time to fullfill requests, with less than a fraction of a second to get the "first byte" back, which means no one sat there staring at a blank loading page wondering what this site was about! Also, there have been no crashes,thanks to the choice of language and approach, which I'll expand on in a technical post soon; which means that no one got excited to see their chart just to see a sad error page!

To re-state what the [About page](https://freenatalchart.xyz/about) says, the purpose of [freenatalchart.xyz](https://freenatalchart.xyz) is, kinda like it says on the tin, to give people free access to their natal chart drawn using vector graphics so one can zoom in and really check out positions/aspects, with enough raw, high-quality data (planet positions and house cusps,) as well as some interpretation clues to make sense of all that was happening astrologically when they were born. There's more complete tools out there, but this one's free, should be very accessible both in terms of information: it's all there, for you to interpret, and technology: I went out of my way to make sure it's all simple content that adheres to accessibility standards, and it should render quickly and correctly in the vast majority of browsers and devices -- no fancy styles or scripting making the download slower or the page jumpy! As for the actual astrological data, we use the same [calculations library](https://www.astro.com/swisseph/swephinfo_e.htm) that the good people over at [astro.com](https://astro.com) use: they made it open source!

As I put more work into the tech, and learn more about [psychological astrology](https://en.wikipedia.org/wiki/Psychological_astrology), I'll endeavor to add other cool things like **transits** or options to see charts in different house systems, with different aspects or with different bodies like more asteroids or points like the Part of Fortune. It all depends on 

You'll notice that the landing page may ask for permission for you location, this is simply to be able to link you to a _chart of the moment_ for the time and place you're currently visiting; this is a "hidden" feature: since we give you a chart of the current moment, you can use the planet positions to glean information about current transits -- I personally have been checking out the chart of the moment daily, seeing how certain planets are hanging out in signs that matter a lot in my own chart!

Since your natal chart is a simple page where all the data is in the URL (we don't store/hide __anything__ server-side), you can print it or bookmark it and come back to it whenever, no need to worry about filling in a form all over again, or some obscure link that may become invalid later on. You may 
 
If you're a programmer, you can [peruse the source code](https://github.com/lfborjas/freenatalchart.xyz), and freely host your own copy (or suggest fixes!)

I'll try to do write ups of the tech and the astrology involved in this project soon, but for now, thanks for reading!
