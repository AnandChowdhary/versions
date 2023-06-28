---
date: 2022-10-08
title: "Alameda"
generator: Deno Fresh
archive: "https://web.archive.org/web/20230602043202/https://anandchowdhary.com/"
type: ["System"]
stack: ["React", "TypeScript", "Deno"]
domain: "anandchowdhary.com"
latest: true
---

# Alameda

In some ways, this redesign is the best reflection of the me of 2022. It's named after the county I was in when I was designing it, the Alameda county in the San Francisco Bay Area, and it focused on my life.

Unlike previous iterations of my personal website, this does not focus entirely on my projects or work, but on all aspects my life. When you visit the website, the first thing you will notice is my yearly theme and life metrics (sleep, location, fitness, etc.), which I track in real time on GitHub and display on the website.

As part of this redesign, I open sourced all the data (e.g., blog posts, life metrics) in separate repositories on GitHub, and then I created an aggregate API: https://github.com/AnandChowdhary/everything, that is the single source of truth. This way, the website's repository is focused entirely on the design, while the content is fetched from the API.

## Design

## Emissions

Starting in this redesign, I used [Website Carbon Calculator](https://www.websitecarbon.com/website/anandchowdhary-com/) to estimate the carbon footprint of my personal website. According to them, this site is cleaner than 90-95% of all webpages tested and runs on sustainable energy (thanks GitHub!). Carbon footprint is based on energy usage, so I use a variety of optimizations to keep it low, especially keeping the bundle size lower so the client has to use less energy to load and parse the webpage:

- Send next to no JavaScript to the client (server-rendered React)
- Correctly size images and serve them in a modern format (CDN)
- Use system fonts entirely (no custom fonts)
- Use server caching and CDN caching
- Use a host with a high PUE rating (GitHub)

Since I could not use the fancy calculation done by Website Carbon, I used the following formula to calculate the carbon footprint of this website. I don't consider returning visitors, only new visitors, so the actual footprint should be even lower. We use the global average carbon intensity of electricity (442g/kWh) to calculate the carbon footprint of this website.

- **Energy per visit in kWh (E)** = [Data Transfer per Visit (new visitors) in GB x 0.81 kWh/GB x 0.75]
- **Emissions per visit in grams CO2e (C)** = E x 442 g/kWh (or alternative/region-specific carbon factor)

For example, the homepage transfers 984 kB of data when uncached and 22.8 kB when cached. For the uncached visit, the carbon footprint is 0.0009375 GB * 0.81 kWh/GB * 0.75 * 442 g/kWh ≈ 0.2518 grams of carbon equivalents. Since only text is made available in the source code, I use an approximate value for each loaded image to display the total carbon footprint of the page in the footer of the website.

For more information about digital carbon footprints, read [Calculating Digital Emissions](https://sustainablewebdesign.org/calculating-digital-emissions/) on Sustainable Web Design.
