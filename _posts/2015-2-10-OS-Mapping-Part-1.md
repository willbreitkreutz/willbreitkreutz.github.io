---
layout: post
title: OS Mapping Part 1
---

# Open Source Web Mapping - Part 1!

### What exactly is a "web-map"?

There are a ton of different ways of putting mapping data on the web.  These range from simple images to PDF's that the user has to download, to dynamic and complex web mapping applications.

> In our context a **web-map** is an interactive mapping application generally using a JavaScript framework to facilitate the basic pan, zoom and identify workflows native to interactive web mapping.

We're also going to break the web-map into it's individual building blocks in order to better understand how it is put together and how to implement our own.

I break down web maps into two major components, **Data** and the **Mapping Framework**.  Let's start with the data.

#### Building Block 1 - Data

I divide data used on web-maps (and in any other kind of map for that matter) into roughly two groups, contextual and topical.  Contextual data generally provides the backdrop giving the map user context, both spatially and topically.  Topical data is the primary focus of the map, the data that is used to tell a story or get a point across.

##### Contextual Data

Base-maps are the most commonly used type of contextual data.  Services such as Google Maps, MapQuest and MapBox provide base-maps with varying levels of cartographic customizability.  These services pull their data (roads, cities, etc...) from large-scale commercial data aggregators such as TeleAtlas and Navteq, or from open data sources such as [OpenStreetMap](www.openstreetmap.org).

Because of the relatively static nature of the base-map data, it is usually served up in image tile format.

###### Tiles

Pre-rendered maps of the base data layers are divided up into image tiles that are 256x256 px images, usually in .png format, but they can be .jpeg or .tif among others.  Image tiles are used because they make it very efficient to display large amounts of base data since it is all rendered prior to being requested for use in the web-map (usually). The most commonly used convention of tiling maps starts at zoom level 0 (z0).  

![z0 example]({{ site.baseurl }}/images/z0_tile.png)

z0 is made up of a single 256x256px tile that covers the entire world.  Each subsequent zoom level (down to 22 on average) is calculated by breaking up each tile from the previous zoom level into four equally sized tiles, rendered at 256x256px.  Check out zoom level 1 (z1) as an example:

![z1 example]({{ site.baseurl }}/images/z1_tile.png)

While most maps use image tiles for their background, there is a growing number of new technologies that let map makers give the users much more interactivity with the base data.  Vector tiles, primarily pioneered by MapBox, are basically what they say they are; tiled vector data.  Pre-processors take the base vector data and crunch it into tiles that are basically the same size as the tile schemes used for the image tiles, simplifying vector shapes at smaller scales so that a relatively consistent amount of data is transfered to the user at any scale.  The web-map can then allow users to interact with the base data as if it were vector data in the browser.

Another use for vector tiles is as a consistent base layer for rendering vector tiles.  The new MapBox studio software does this by allowing users to consume the general MapBox vector tiles layer, style it to their liking, and then render custom image tile sets from that stylesheet.  Newer (ok, so new to us in web-mapping) technologies like WebGL can be used to consume and render styled vector tiles on the fly.

See the MapBox documentation to get [more information about tiles](https://www.mapbox.com/foundations/how-web-maps-work/).

##### Topical Data

A successful map (web or otherwise) tells a story.  This story is usually told using what I call topical data that is displayed on top of the contextual base-map.  Formats and styles of topical data can vary widely depending on the story to be told.  Static datasets can be mapped showing a condition at a certain time, or temporal dimensions can be used to create animated maps showing changing conditions over time.  

Topical data can be integrated into the tile base-map images, as it's own tile based service, or as vector data that is drawn on top of the map in the browser.

Some common formats topical data comes in include:

* WMS (web mapping service)
* WFS (web feature service)
* kml services
* csv
* GeoJSON

###### GeoJSON

One of the more popular formats used for rendering data on the map in the browser is GeoJSON.  JSON (JavaScript Object Notation) is a way of organizing data piggy-backing on the way JavaScript handles objects.  JSON is becoming ubiquitous on the web for transferring data from server to client and back.  GeoJSON is a specification built on top of JSON specifically for organizing geographic data.

Check out the GeoJSON specification for [more information about GeoJSON](geojson.org).

#### The Mapping Framework

The mapping framework is the glue that takes all of the data we talked about earlier and puts it on the web page in the right place, allowing you the user to pan around, zoom in and out and interrogate the mapped data.

All of the widely used modern web-mapping client libraries are JavaScript based.  These are some of the more popular options:

* Google Maps JavaScript API
* ESRI ArcGIS JavaScript API
* MapBox JavaScript API
* Leaflet
* OpenLayers
* [many others...](http://techslides.com/50-javascript-libraries-and-plugins-for-maps/)

The best way to get to know the web-mapping framework is to actually make a map, stay tuned for the next post where we start to make our first web-map.

