---
layout:post
title:Open Source Web Mapping - Part 2
---

## Let's Make a Map!

### Basemaps

Let's start by building a good-looking base map to use in our new web-map.  Now we could use any number of free basemap tile services that are available from Google, MapQuest, Stamen, ESRI and other vendors.  These services vary in cartographic quality, speed and support. Or we could get ahold of TileMill or Mapbox Studio, or just build out our own toolchain to render map tiles and serve them ourselves.  

Instead, we're going to take a middle lane.  Mapbox, the maker of TileMill and Mapbox Studio also offer free hosting of custom tile sets styled in the browser, by you!  Free accounts can access up to 50,000 [map views](https://www.mapbox.com/plans/) per month, if you happen to need more than that, A. you're running a very successful mapping site and B. they offer tierd pricing all the way up to enterprise level. (I don't work for Mapbox, I just really like their service).

Under the hood, the Mapbox hosted tile services use their vector tile basemap that is continuously updated from Open Streetmap to render image tiles based on the simple style that you can build in the browser.  Each tile gets generated on the first request and is cached for future requests to increase speed over time.  Areas that are updated are purged from the cache and replaced the next time a tile gets requested.

Ok, let's go to [mapbox.com](www.mapbox.com) and get started.  After you create your free account, go to the projects section of your profile.

![Projects link]({{ site.baseurl }}/images/mapbox_links.png)

You can create a bunch of projects here each styled differently to use in any of your web-maps.  If you want to really customize the look of your map you can download the Mapbox Studio software and build out stylesheets that you can upload for Mapbox hosting.

![New Project]({{ site.baseurl }}/images/new_project.png)

Click on the New Project button.

![Basemap Options]({{ site.baseurl }}/images/base_map_options.png)

The folks at Mapbox give you a bunch of options for basemap styles to start with, play around with the different styles and pick one that you want to use for your project.

Once you find a style you like, save your project so we can use it in our map.

The Data section allows you to add your data directly into the basemap for hosting in the Mapbox service.  This is really handy if you have a simple dataset that you want to publish without the hastle of building your own map app or hosting the data yourself.  You could add data on top of the transparent basemap to create a service that would show just your data that you could then overlay any other basemap in your web-map.  We're going to skip this option and host our own as part of this exercise.

> In the past you could customize the look and feel of the tiles in the browser, but they now require that you use Mapbox Studio to customize your basemap.

![Project Section]({{ site.baseurl }}/images/project_section.png)

You have a couple options for using your basemap, if you look at the info tab of the Project section, you can copy out your map ID for use in your own web site, you can copy a link to share your map with others using the Mapbox web site or you can just copy out an iframe that you can imbed in another site to show your map.

We're going to use the map in a fully custom web site so we will need the map ID in the next section.  We also need to go grab our individual token that Mabox will use to authenticate our application (so no-one uses our map ID and pulls too many images without us knowing).

![Token]({{ site.baseurl }}/images/token.png)

Get your token from your profile page.

Stay tuned as we host our own web map using the tile service that we just set up in Mapbox.
