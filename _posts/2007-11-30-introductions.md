---
author: Chris Holmes
comments: true
date: 2007-11-30 00:32:48+00:00
layout: post
link: http://blog.geoserver.org/2007/11/29/introductions/
slug: introductions
title: Introductions
wordpress_id: 79
categories:
- Announcements
---

Though they've been with us for awhile, I realized the other day that some new developers in the GeoServer community never got introduced properly.  They started working for [The Open Planning Project](http://topp.openplans.org) (TOPP) a couple months ago, and have been working on some great stuff since then.  Their primary goal is to combine TOPP's two main software projects - GeoServer and [OpenPlans](http://www.openplans.org/), a free (and ad free) collaborative platform providing wikis, email lists, task trackers and blogs, built entirely on open source software.  It's been evolving nicely lately, so feel free to try it out and give feedback.

But the part that should be of great interest to this crowd is that the newest tool is going to collaborative mapping, allowing groups to do wiki type editing on maps, and eventually to be able to make and improve new base layers.  This will be built completely on GeoServer and [OpenLayers](http://openlayers.org), with the new [versioning WFS](http://docs.codehaus.org/display/GEOS/Versioning+WFS) improvements.  This should push the bounds of GeoServer and bring stability to the new features.  We've just put up an [early demo](http://artois.openplans.org/annotation_demo), which lets you create and edit pop-ups, and also comment on them in a sidebar.  The base map on the demo is also all served by GeoServer, with a huge debt of gratitude to the Portland's [TriMet](http://trimet.org/), who shared the SLD files from their [new map](http://maps3.trimet.org/public/map/map) (which we should do a full post on soon, as it's some great work).

[Tim Coulter](http://www.oneofthewolves.com/) and Sebastian Benthall are the ones who have done most all the work on the front end, building the application on top of OpenLayers.  Eventually we hope to turn it in to a more generic tool for others to make similar maps.  They've been working against a [nice](http://www.openplans.org/projects/opencore/google-maps-in-openplans) [specification](http://www.openplans.org/projects/opencore/maps-part-1) from TOPP's great interaction designer, [Mouna Andraos](http://www.missmoun.com/), which should evolve to full on wiki editing (current target just tracks history).  Eventually we should have some nice blog posts on how they've gone about building a new application on top of OpenLayers.

On the backend David Winslow and Arne Kepp have been taking the lead, and thus have been more active on the GeoServer lists and irc's.  They've stood up the GeoServer for it, and are putting in the hooks and improvements to have OpenPlans utilize it as a backend, including making a module that can authenticate OpenPlans users, a REST API to create new layers on the fly, and caching improvements so it will perform better.

Arne has done a great job tackling more of the sys admin side of setting things up and deploying, and adapting TriMet's SLD's to the new york data set.  In the process of doing that he's had some promising experiments with [Varnish](http://varnish.projects.linpro.no/) to do _extremely_ fast tile caching.  Following up the caching angle he's now working to improve and incorporate [JTileCache](http://code.google.com/p/jtilecache/), Chris Whitney's Google Summer of Code project, as a community module that can drop in to GeoServer.   He reported on IRC today that he's got response times from it down to under 2 milliseconds, about as fast as [TileCache](http://tilecache.org) under mod_python.  Arne's also helped out on the [REST configuration](http://docs.codehaus.org/display/GEOSDOC/RESTful+Configuration+API) interface, and done some nice bug fixes and improved the WMS reflector, which will get blogged soon.

David has become the resident REST and [RESTlet](http://restlet.org) expert, starting with a [REST User Management API](http://docs.codehaus.org/display/GEOSDOC/RESTful+User+Management+API) to query and create users on the new [security subsystem](docs.codehaus.org/display/GEOS/GSIP+16+-+Security+subsystem) based on [Acegi](http://www.acegisecurity.org/).  After that he's taken on the lead coding up the [REST configuration API](http://docs.codehaus.org/display/GEOSDOC/RESTful+Configuration+API), which will replace the incredibly hacky '[alternate for reloading the catalog](docs.codehaus.org/display/GEOSDOC/Alternative+for+reloading+the+Geoserver+catalog)' to enable programmatic manipulation of GeoServer.  Recently he refactored his work to make it easy to plug in alternate output formats, starting with html and json, and soon xml.  He's also done some nice bug fixing, improving KML output with the lookAt tag to zoom in to the data automatically, and tweaking the pop-ups to be easier to click on.  David also took the read on hooking the security sub system up to the OpenPlans way of authenticating, which he will hopefully blog soon, as it's a nice example of how to use the tools in GeoServer to work with an existing security system.