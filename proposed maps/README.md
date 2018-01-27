# Guide to the proposed map

## Proposed map shapefiles

The files districts.shp, districts.shx, and districts.dbf comprise an ESRI shapefile for the 18 proposed districts, with demographic, election, and voter registration data aggregated from the census block level data file included in the official legislative redistricting data.

In addition, the file "census block district assignments.csv" gives the district assignment for each of the 421,745 census blocks in the state, using the unique identifier "geoid10" for each.  This data table can be used to explore the details of the proposed map by joining it with the census block level dataset (layer name "Turzai - 01640") in the official legislative data.  The "geoid10" column in the district assignment spreadsheet matches the shapefile's "GEOID10" field.


## Proposed map statistics

The "stats" directory includes three PDF files summarizing compactness scores for the proposed districts, as well as the same scores for the gerrymandered 2011 districts and for a particularly well-designed historical districting plan: 1972.  The 1972 map was drawn under slightly different constraints, having 25 districts rather than the current 18 and not needing to achieve population equality at the &plusmn;1 person level.  Yet it nonetheless provides an excellent model for how to follow traditional neutral districting criteria (specifically, compactness and respect for political subdivisions) in designing congressional districts.

Additionally, this directory includes a spreadsheet enumerating all of the political subdivision splits present in the proposed map, as well as the district assignments for each county.


## Proposed map images

What it says on the tin.


## How this map was drawn

The territory for each district was assigned by manual selection, using the open-source GIS program QGIS.  The process was performed in its entirety by a single human map designer working on an aging laptop computer, and required only a few working days to complete.  A similar manual process could be followed far more quickly using specialized redistricting software and more advanced hardware, and a completely automated design process could possibly take only minutes to complete.

The dataset used was the Pennsylvania state legislature's official 2011 redistricting data, also included in this repository.  It contains identifiers, boundaries, demographics, and partisan preference data for Pennsylvania political subdivisions as of the 2011 redistricting.  Note that, unlike the PA state legislature's process, the partisan preference data was _not_ consulted during the design of this map.

### Traditional neutral criteria

The principles guiding the design of this map were the traditional neutral districting principles stated in the Pennsylvania constitution for legislative districts and mandated by the PA Supreme Court for use in redrawing the 2011 districts.  The Court's order states:

> "... to comply with this Order, any congressional districting plan shall consist of: congressional districts composed of compact and contiguous territory; as nearly equal in population as practicable; and which do not divide any county, city, incorporated town, borough, township, or ward, except where necessary to ensure equality of population."

Thus the principles used in designing this map were:

 - Absolute contiguity (each district consists of a single connected piece; point contiguity is disallowed)
 - Exact population equality (5 districts with 705,687 residents and 13 districts with 705,688 residents, to ensure compliance with the _Vieth_ standard)
 - Subject to exact population equality, dividing each county no more times than necessary and no more counties than necessary
 - Subject to exact population equality and minimization of county splits, dividing each municipality (city, borough, incorporated town, or township) no more times than necessary and no more municipalities than necessary to achieve population equality
 - Subject to exact population equality and minimization of county and municipal splits, dividing each ward or precinct no more times than necessary and no more wards or precincts than necessary to achieve population equality
 - Subject to exact population equality and minimization of political subdivision splits, maximization of compactness (a visual test was used during map design and its effectiveness was confirmed afterwards using computed compactness scores)

To achieve the required minimization of political subdivision splits while maximizing compactness and achieving exact population equality, county split lines were constructed as follows:

 - For any county with a population greater than a single district, as many districts as possible should be constructed solely from pieces of the county, ideally leaving only a single "remainder" piece to be attached to another county or counties.  (Currently, this affects only Philadelphia, Allegheny, and Montgomery counties.)
 - No county with a population smaller than a single district should be divided between more than two districts.
 - In any case where a county must be divided, its territory should be aggregated into adjoining districts beginning with municipalities contiguous with the county border and proceeding towards the center of the county only after all bordering territory has been used.
 - When balancing populations between any two adjacent districts:
    - Only a single county should be split to balance any given district pair.
    - The choice of which county to split and what split line to use should be made in such a way as to _improve_ the compactness of the two districts.
    - The population balance should ideally be perfected to &plusmn;1 by splitting a single precinct in a single ward of a single municipality along the county split line, down to the census block level.  Extreme circumstances may very rarely necessitate an extra split or two.

### Additional criteria

Racial demographic data was not consulted during map design, only total populations.  Subsequent analysis showed a single majority-black district (the 2<sup>nd</sup>), encompassing similar but not identical regions to the majority-black 2<sup>nd</sup> voting district in the present map.  Since the Philadelphia region is the only area with a large enough and concentrated enough minority population to bring Voting Rights Act considerations into play, additional local adjustments could be made to the map at the final design stage if this is considered desirable for VRA purposes.

Although partisan indicator data was present in the official legislative redistricting dataset, this information was not used (and should not be used) to inform map design in any way.  Subsequent analysis using the legislature's data suggests that the resulting map is nevertheless well balanced between the two major parties, comparable to the overall partisan balance of the state and in strong contrast to the present congressional map.

Incumbency protection, either at the level of not moving two incumbents into the same district, or at the level of ensuring a certain partisan advantage for each incumbent, was also not considered.

The first type of incumbency protection (avoiding incumbent contests) could easily be incorporated into an otherwise neutral process if desired and with appropriate data, at some possible cost in compactness and splits of political subdivisions.  However, "protecting" incumbents in this way does pose some challenges to the neutrality of the process, as it has the potential to help lock in the effects of past gerrymandering and otherwise open the door to partisan considerations.  Thus, this is an area to enter only with extreme caution and is better avoided if possible.

The second type of incumbency protection (creating "safe" districts for incumbents) poses an enormous threat to neutrality.  To apply this criterion, consultation of partisan data would be required at every stage of the districting process, and designers would then need to decide "how much is too much" consideration of partisan advantage.  Picking and choosing territory for each district based on how residents vote, to the detriment of neutral standards, becomes not only tempting but required.  This author considers such practices to be completely beyond the pale for any responsible redistricter.


### Map design process

Design for this map began with a rough assignment of counties to districts.  Previous analysis had suggested that population equality to within about &plusmn;5% was attainable by splitting only 4 counties.  Therefore, the first design stage for the proposed district map simply applied the county assignments from this 4-split map, slightly modified to improve compactness.  Counties larger than a single district were combined with selected neighbors into two- or three-district sized "super districts", which were divided into single districts at the next stage.

The second map design stage was to assign these roughed-out district numbers to the minor civil divisions (MCDs) of each county (i.e., cities, boroughs, towns, and townships, or the parts thereof that are inside a single county) and the wards of Philadelphia (necessary to determine how to divide Philadelphia County).  These assignments were then refined, according to the traditional neutral districting principles described above, to equalize district populations to within about &plusmn;1% of the ideal district size.  In equalizing populations, it was useful to begin with the most tightly constrained regions (counties larger than a single district, which must be divided and should completely contain one or more districts), and then work outward from there, dividing additional counties only as necessary and only in a compact fashion.

Once district populations were refined to the MCD/Philadelphia ward level, these assignments were propagated down to the precinct level and then the census block level.  At this point, it became easy to equalize district populations down to the level of &plusmn;1 person.  Along each county split line, a single MCD, and, generally, a single precinct from that MCD, was selected for division to the census block level.  With careful choice of the MCD and precinct to split and some trial and error, it was usually easy to group the census blocks from this single precinct into two contiguous (albeit sometimes less compact) halves in such a way as to equalize district populations.

In the present map, regions with relatively lower population density have been preferred for these census block level precinct splits wherever possible, to minimize the number of residents affected.  Split lines were never permitted to divide any MCD (except Philadelphia), ward, or precinct into more than two contiguous pieces, and the shapes of these split pieces were made as compact as possible given the exact population equality constraint.

In two exceedingly challenging parts of the map, slight exceptions were made to the guideline of generally splitting one precinct of one MCD per county split.  Along the border between the 7<sup>th</sup> and 16<sup>th</sup> districts, a second municipality, Birmingham township in Chester County, was split because it contains two census blocks that are discontiguous from the rest of Chester County, due to a bend in Brandywine Creek.  These two census blocks had no official residents listed in the 2011 redistricting data and were assigned to the new 7<sup>th</sup> district for the sole purpose of creating contiguous districts.  The border between the 8<sup>th</sup> and 13<sup>th</sup> districts was also troublesome because the municipalities there have a high concentration of large-population census blocks which were difficult to distribute in exactly the right way to achieve the necessary population balance.  Thus, three voting districts of Montgomery township were divided along the congressional district boundary rather than adhering to the ideal of dividing a single voting district.

Once all census blocks were assigned into contiguous districts in this fashion, the block shapes and demographic/political data contained in the legislature's dataset were aggregated by district to produce the district shapefile included in this dataset, along with its associated attribute table.


## Conclusion

The proposed district map in this repository is offered to the public for three reasons.

First, in the author's considered opinion, this map shows a reasonable set of congressional districts which comply in every particular with the guidelines ordered by the Pennsylvania Supreme Court in _LWV v. PA_ and can potentially remedy the harm caused by the 2011 partisan gerrymander.

Second, this map and the process by which it was designed show that it is absolutely possible to draw maps in compliance with these guidelines, and that such maps should be significantly more compact and show significantly more respect for the political subdivisions of the state than the present, gerrymandered map.  At very least, any map proposed in response to the Court's order should carry the burden of justifying any ways in which it is significantly worse than this map in terms of compactness and county and municipal splits.

Third, this map shows that it is _easy_ to draw maps in compliance with the Court's requirements.  Using no special tools other than an open-source GIS program (QGIS) and the already existing legislative redistricting dataset, this map was designed by a single person over the course of a few working days, using an older laptop computer.  Better hardware, more human power, and automated assistive algorithms could speed this process considerably.  Given the timetable for the upcoming elections, which the Court has ordered must be held under a new map, there is no excuse for delay.

This author, of course, makes no representation that the map presented here is the absolute best possible congressional district map for Pennsylvania or that the legislative dataset used to design it is without error.  Corrections to the map, suggestions for improvement of the map or its design process, and even full alternate map designs are welcome and can be submitted via the Github repository.

Share and enjoy!
