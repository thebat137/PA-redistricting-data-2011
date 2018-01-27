# Guide to this repository

This repository contains two categories of data.


## Directory: "redistricting data"

This directory holds the official GIS redistricting data used by the Pennsylvania State Legislature to draw the 2011 congressional district maps for the state.  This data was first made public as a result of discovery during the _Agre et al. v. Wolf et al. (2:17-cv-04392)_ federal lawsuit challenging partisan gerrymandering in Pennsylvania's 2011 congressional map.

In January 2018, in response to a lawsuit in the state court system (_League of Women Voters of Pennsylvania et al. v. Commonwealth of Pennsylvania et al. (No. 159 MM 2017)_), the Pennsylvania Supreme Court declared the 2011 congressional map to be a partisan gerrymander in violation of the PA state constitution.  The enormous volumes of partisan election results and voter registration tallies present in the dataset were used to enable this gerrymandering.  More information about the data contained in these files is given in README.md in the shapefile directory.

This data is in ESRI Shapefile format.


## Directory: "proposed maps"

This directory shows one possible alternative PA congressional district map drawn using the official legislative redistricting data and applying traditional neutral districting principles.  These principles are explicitly described in the PA state constitution in the context of legislative districts (and in historical redistricting legislation in many other states and at the federal level) and were quoted in the PA state Supreme Court's order in _LWV v. PA_:

> "... to comply with this Order, any congressional districting plan shall consist of: congressional districts composed of compact and contiguous territory; as nearly equal in population as practicable; and which do not divide any county, city, incorporated town, borough, township, or ward, except where necessary to ensure equality of population."

To ensure compliance with these criteria, and in light of the population equality standard suggested in _Vieth v. Jubelirer (541 U.S. 267 (2004))_, the proposed map has district populations which are equal to within 1 person (5 districts with 705,687 residents and 13 districts with 705,688 residents, according to the legislative redistricting data).  The present author does not pretend to expertise in legal interpretation of the Voting Rights Act, but one district in this map, the 2<sup>nd</sup>, has a majority-minority (specifically, majority-black) voting age population, as in the 2011 congressional map.

The districts in the proposed map are significantly more compact than those in the 2011 maps and split many fewer counties (16 _vs._ 28) and municipalities (21 _vs._ 68).  The 21 split municipalities consist of 17 municipalities divided when splitting their respective counties, to equalize populations between adjacent districts, and 4 boroughs divided because the two halves of the borough are in counties assigned to different districts.

In addition, in the proposed map, no county except Philadelphia is divided between more than 2 districts, and Philadelphia is divided among only 3 districts.  This contrasts strongly with the 2011 map, in which Montgomery County was divided among 5 districts, Berks County was divided among 4 districts, and 5 other counties (Allegheny, Chester, Dauphin, Philadelphia, and Westmoreland) were each divided among 3 districts.

The provided data includes ESRI shapefiles, map images, and some statistics for the proposed districts.  Additional information on the process of drawing the map and how to use the map data is provided in the README.md file in this directory.
