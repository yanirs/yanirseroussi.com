---
title: You don't need a proprietary API for static maps
author: Yanir Seroussi
type: til
date: 2023-11-21T06:00:00+00:00
url: /til/2023/11/21/you-dont-need-a-proprietary-api-for-static-maps/
summary: For many use cases, libraries like cartopy are better than the likes of Mapbox and Google Maps.
showBreadcrumbs: true
tags:
  - data engineering
  - data science
  - Reef Life Survey
  - software engineering
  - web development
---

In addition to my long-time volunteering as a scuba diver with [Reef Life Survey](https://reeflifesurvey.com/) (RLS), I've been helping them with bits and pieces around data engineering / science / web work ([somewhat reluctantly](https://yanirseroussi.com/2023/10/25/lessons-from-reluctant-data-engineering/)). A few months ago, we discovered an issue in the PDF field guides exported from [Reef Species of the World](https://reeflifesurvey.com/species/): species distribution maps embedded in the PDFs were broken. This was due to a change in [Google's Static Maps API](https://developers.google.com/maps/documentation/maps-static/overview), which became a paid feature.

While paying for the Google API would have been the simplest solution (and fairly cheap with appropriate caching), this was an opportunity to improve the static map functionality while removing the paid proprietary API dependency. For me, it was also an opportunity to learn a bit about geospatial analysis in Python, which I've been curious about.

A bit more context on the problem: Each of the species in the PDF field guides is shown with its distribution map, as recorded in the RLS dataset. Some species are widespread and common, like [_Labroides dimidatus_](https://reeflifesurvey.com/species/labroides-dimidiatus/) (a cleaner wrasse that was recorded in over 4,000 sites). Unlike the maps presented on the web version, PDF maps are meant to fit a box that's about 4.5cm by 3.5cm when printed, so space is limited for on-map labels.

An important limitation of the Google Static Maps API (which is shared by the cheaper Mapbox API) is that of request URL length. This isn't an issue for maps with a few custom features, but requesting a map with thousands of markers isn't feasible without reducing coordinate accuracy and clustering markers to reduce their number. This complicates the code that calls the static mapping API, and can easily lead to unexpected results, like fish found on dry land.  

I suppose that an attractive feature of the Google Static Maps API is the simplicity of embedding maps in pure front-end applications, as it obviates the need to implement a back-end to generate the static maps. However, this feature was irrelevant to the PDF generation task, which happens on the back-end anyway.

Once I understood the downsides of sticking with proprietary static map APIs (including their limited customisability), I realised I could expand the Python data processing code in [the `rls-data` repo](https://github.com/yanirs/rls-data) to pre-generate all the maps whenever new survey data becomes available. The final result was [about 5,000 distribution maps that are committed to the repo](https://github.com/yanirs/rls-data/tree/master/maps). This admittedly stretches the common use cases for Git repos, but at about 15KB per map, it's not terrible. In any case, it'd be easy to store the maps on S3 if needed.

The full code with the change, including the GitHub Action that refreshes the maps, is in [this PR](https://github.com/yanirs/rls-data/pull/36). It's a bit hard to navigate since GitHub doesn't like PRs with thousands of files, but the commit history gives the full picture of my experimentation with Python-based mapping solutions. The map generation code that ended up getting merged starts [here](https://github.com/yanirs/rls-data/blob/ac0eec5988efeaa95347371002226574cc6c7ff9/rls/processor.py#L295).

Python has [a large ecosystem of geospatial packages](https://ecosystem.pythongis.org/), so choosing the right packages for the use case was a bit tricky. However, I heard about [`geopandas`](https://geopandas.org/en/stable/), so I used it for my first round of experiments. I got reasonable-looking maps, but it was a bit slow. I also found the auto-zoom functionality frustrating &ndash; given the space constraints, balancing the zoom level with keeping a constant aspect ratio and the need for legibility seemed non-trivial (at least to me).

Some discussions on zooming with ChatGPT led to it mentioning [`cartopy`](https://scitools.org.uk/cartopy/docs/latest/index.html). I was quickly sold on it [given all the pretty maps in the `cartopy` gallery](https://scitools.org.uk/cartopy/docs/latest/gallery/index.html). It also turned out to be much faster &ndash; generating the maps with cached tiles (using `geopandas` and [`contextily`](https://contextily.readthedocs.io/en/latest/)) was six times slower than [using `cartopy` with Natural Earth features](https://scitools.org.uk/cartopy/docs/latest/gallery/lines_and_polygons/features.html). The `cartopy` solution was also twice as fast as using geopandas with Natural Earth, and I could easily set the colour of the ocean to match the colour used on the RLS website &ndash; definitely a winner! A full run to regenerate all the maps with a standard GitHub Actions runner takes about 3.5 minutes, which is reasonable for something that runs at most daily.

I'm far from a geospatial expert, so the solution I landed on for zooming with a constant aspect ratio isn't great: There are a few hard-coded map areas with recognisable coastlines (Australia, Europe, North America, etc.), which obviates the need for labelling. For each species distribution, the code chooses the minimal area that fits all the sites. I find that it reduces the mental overload in comparison to auto-zoom when looking at a bunch of maps in the context of the PDF, but we may swap this for another solution. For now, it's good enough, and a definite improvement over broken maps.
