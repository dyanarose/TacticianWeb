---
layout: post
title: "Integrating with the Guild Wars 2 API"
date: 2015-05-19 01:36:35 +0100
comments: true
categories: 
---

Some MMOs have very permissive access to the running game, granting access to character information, allowing macros, enabling "offline" access to in game chat. Guild Wars 2 is not one of those MMOs.
<!--more-->
ArenaNet has made available two [APIs (versions 1 and 2)](http://wiki.guildwars2.com/wiki/API:Main) for accessing game information and Mumble Link which enables a limited access to character information and location. 

The API is (currently) concerned primarily with facts about game assets (or entirely about game assests if you also think of PvP match information as an asset). You are able to [query recipes](http://wiki.guildwars2.com/wiki/API:2/recipes), but not which recipies the logged in character knows. You are able to [query dyes](http://wiki.guildwars2.com/wiki/API:2/colors), but not which dyes the current account has unlocked. You are able to [query map information](http://wiki.guildwars2.com/wiki/API:2/maps), but not which vistas the current character hasn't discovered yet. You get the drift. 

There are two current endpoints that allow you access to a small set of account information; you can [retrieve trading post transactions](http://wiki.guildwars2.com/wiki/API:2/commerce/transactions) and [account name and home world](http://wiki.guildwars2.com/wiki/API:2/account).

(API v2 does specifically allow you to [query quaggan images](http://wiki.guildwars2.com/wiki/API:2/quaggans), for which I am forever grateful. Damn I love those little guys)

The question I'm left with is, how to best use the asset information to inform the design of Tactician.

The first thing I see is the map information. Using the [map endpoint](http://wiki.guildwars2.com/wiki/API:2/maps) in API v2, I can get access to waypoint and POI ids and coordinates. 

If, when setting up an encounter, you would, say, select the closest POI, I could then show the closest waypoints. You could then easily associate a waypoint with an encounter or a fight.

With the map information stored against the encounter, Mumble Link could be used to filtered encounters down to those in your current map.

I need to do a full exploration of the APIs, but I don't see a way to access dungeon and world boss information. Both of which would be very useful.

I think I'll give it a good bit of thought and look into proposing these endpoints as, perhaps, extensions of the map endpoint.