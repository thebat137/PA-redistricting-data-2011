# Guide to the Pennsylvania State Legislature's 2011 GIS Redistricting Data

This is the redistricting data used by the Pennsylvania state legislature in 2011 to design the new congressional and legislative districts.  This data was first made public as a result of discovery during the _Agre et al. v. Wolf et al. (2:17-cv-04392)_ federal lawsuit challenging partisan gerrymandering in Pennsylvania's 2011 congressional map.

There are 39 total files in this dataset, comprising 13 complete ESRI Shapefile formatted map layers.  The files have names of the form "Turzai - 016xx.yyy", where "xx" is a number which in the original data ranged sequentially from 40 to 78 and "yyy" is a file name extension which is one of "SHX", "DBF", or "SHP".  In the original dataset the file names were mangled by the legislative defendants' legal discovery software in a way that prevented standard GIS software from opening them correctly, but here they are renumbered as described in the spreadsheet "file list.xlsx".  The most interesting shapefiles and their data fields are described below.

- _shapefile:_"Turzai - 01652":
  - _features:_ PA counties
  - _notable attributes:_
    - 17 columns of miscellaneous geographic identification data for each county (name, geographic identification codes, land and water area, latitude and longitude, etc.).
    - 24 columns of population data for each county, including total population, population breakdowns by various standard Census racial categories, and population breakdowns by Hispanic/Latino status.  All column names begin with "TA" (referring to the total number of members of each racial group) or "TN" (referring to the total number of non-Hispanic or Latino members of each racial group).  This data was most likely sourced from the official 2010 U.S. Census.
    - 24 columns of data on the voting age population of each county, for the same racial groupings as the total population data.  These column names all begin with "VA".  This data was also most likely from the 2010 U.S.
    - 99 columns of partisan voting results and partisan voter registration data for each county for all 33 even-year statewide, legislative, and Congressional elections from 2004 to 2010.  Each column is labeled according to the pattern "xxxxx\_Pyy".  Here, "xxxxx" is a 3-5 character identifier indicating the elective office in question or spring/fall voter registration, "P" is a party identifier ("R" for Republican, "D" for Democratic, and "O" for other), and "yy" is the election year (last two digits).  The offices and voter registration tabulation timepoints are listed below with their dataset identifiers and the years for which those data are present.  This data was most likely sourced from the Pennsylvania Department of State's official election records.
      - Voter registration:
        - "SP\_RG": voter registration count for each party at the spring elections (2004, 2006, 2008, 2010)
        - "FL\_RG": voter registration count for each party at the fall elections (2004, 2006, 2008, 2010)
      - Federal offices:
        - "PRES": President of the United States (2004, 2008)
        - "USSEN": Senator in the United States Senate (2004, 2006, 2010)
        - "USCNG": Representative in the United States House of Representatives (2004, 2006, 2008, 2010)
      - State level offices:
        - "GOV": PA state governor (2006, 2010)
        - "ATGEN": PA state Attorney General (2004, 2008)
        - "AUDGN": PA state Auditor General (2004, 2008)
        - "STRES": PA state Treasurer (2004, 2008)
        - "STSEN": Senator in the PA state Senate (2004, 2006, 2008, 2010)
        - "REPGA": Representative in the PA state House of Representatives (2004, 2006, 2008, 2010)
    - 10 columns of computed partisan voting indices for each county.  The column headers are:
      - PREZ04, PREZ08, SEN10, CNG10, STHS10, GOV10, ATGEN08: Each of these columns was computed by subtracting the Democratic votes in each county for a particular election from the corresponding Republican votes.  The elections used to compute these columns were, respectively: Presidential 2004, Presidential 2008, U.S Senate 2010, U.S. House of Representatives 2010, PA House of Representatives 2010, PA Governor 2010, and PA Attorney General 2008.
      - REG10: This column was created by subtracting total fall 2010 Democratic registration from total fall 2010 Republican registration for each county.
      - INDEX04, INDEX08: It is not clear how these columns were computed, and the formulae behind them were not disclosed by the legislature.  Their values seem to generally track the values in the other computed columns, in terms of sign and approximate magnitude, but do not quite match any of them.  It seems likely from the column names and similarities to the other partisan data that these are partisan voting preference indicators computed from some kind of averages of the 2004 and 2008 voting and registration data included in this dataset, or from other similar sources.
- _shapefile:_"Turzai - 01643"
  - _features:_ Pennsylvania minor civil divisions (MCDs), i.e., cities, towns, boroughs, townships, and the single-county portions of boroughs divided by a county line
  - _notable attributes:_ This shapefile has the same attributes as the county-level data file, with the exception of a few differences in the types of geographic entity identification data used at this level of geographical refinement.  All of the same partisan data and computed partisan indices are present at this level as at the county level.
- _shapefile:_"Turzai - 01673":
  - _features:_ PA voting tabulation districts (VTDs), i.e. the finest-grained geographical scale at which voting data is recorded.  In Philadelphia, for example, these VTDs are called "precincts" and are grouped into 66 "wards", which together comprise the entirety of the city of Philadelphia.  In other parts of the state, the finest-grained electoral entities may be locally referred to as "precincts", "divisions", "districts", "wards", or other comparable terms, and may, as in Philadelphia, be grouped together into one level of larger entities (also having a variety of local names, including "precincts", "districts", and "wards") which together comprise the municipality.
  - _notable attributes:_ This shapefile has the same attributes as the county-level and MCD-level data files, with the exception of a few differences in the types of geographic entity identification data used at this level of geographical refinement.  All of the same partisan data and computed partisan indices are present at this level as at the county and MCD levels.
- _shapefile:_"Turzai - 01640"
  - _features:_ U.S. Census blocks in PA.  These are the finest-grained geographical regions for which the U.S. Census will normally provide complete demographic data, e.g., population counts and racial breakdowns.
  - _notable attributes:_ This shapefile has most of the same attributes as the county-level, MCD-level, and VTD-level data files.  The exceptions are as follows:
    - There are a few differences in the types of geographic entity identification data used at this level of geographical refinement.
    - All of the same partisan voting and voter registration data columns are present at this level as at the county, MCD, and VTD levels.  This is unusual, because voting data is not _collected_ at this level of refinement, and voter registration data is not published at this level of refinement.  Both are generally available only at the VTD level and higher.  The formula by which this data was produced was not disclosed, but it most likely resulted from taking the partisan vote or voter registration counts from each VTD, assuming that each census block in the VTD has the same partisan composition as the entire VTD, and distributing the partisan vote or voter registration counts of the VTD amongst its census blocks according to their proportions of the total or voting age population of the VTD.
    - The 10 partisan voting index columns are not provided at this level of refinement (but would be trivial to generate on the fly in standard GIS software using a map coloring rule).
    - There is one apparently spurious column called "NEWFIELD1", which is populated almost entirely with zeros and null values, except for a single block (Block 5009 of Tract 210100, which is in Voting District 03 Division 01 of Springfield Township in Montgomery County), which has a value of 1.  This column was presumably created by mistake.
- _shapefile:_"Turzai - 01646":
  - _features:_ PA 2002 Congressional districts
  - _attributes:_ 2002 district numbers
- _shapefile:_"Turzai - 01649":
  - _features:_ PA Congressional representatives' homes, 112th Congress (i.e., the incumbents at the time the plan was produced)
  - _attributes:_
    - Number, Street, City, Zip\_Code: These are the components of 19 street addresses.  White Pages searches for the names of persons currently or formerly residing at these addresses, and comparison with the known home cities of the members of the Pennsylvania delegation to the 112th Congress (2011-2013), indicate that these are the home addresses of the 19 incumbent PA Congressional Representatives at the time of the 2011 redistricting, arranged in order by their district numbers.
    - Status, Score, Match\_type, Side, Match\_addr, ARC\_Street, Arc\_Zone: Typical result columns created by ArcGIS during geolocation (i.e., finding the map coordinates) of a street address.
- _shapefile:_"Turzai - 01661":
  - _features:_ Philadelphia wards
  - _attributes:_
    - WARD: The ward number.
    - COUNT: The number of precincts in each ward.
    - TAPERSONS: The total number of people in each ward.  This is most likely official U.S. Census data from the 2000 Census, as the file's "last modification" date is from 2003, and these numbers (and the ones below) are generally slightly different from their counterparts in the 2010 Census data.  Note that 2000 Census data was actually _inappropriate_ to use in drawing the 2011 districts, as these districts should have been drawn based on the official 2010 Census results.
    - TAWHITE, TABLACK, TNHISPANIC: The total number of white, black, and non-white Hispanic or Latino identified people in each ward.  This data is also most likely from the 2000 U.S. Census.

The remaining 6 shapefiles contain the names, locations, and other basic identifiers of major and minor roads and highways, major and minor bodies of water, and current and former railway routes in the state of Pennsylvania.
