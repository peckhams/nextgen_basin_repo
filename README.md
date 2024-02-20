
<img src="__Docs/__Station_Venn_Diagram_v2.png"
     style="align: right; margin-right: 10px; height: 250px"  />
     
### Introduction

There are many different river basin data collections that have been used for hydrologic monitoring or modeling studies. 
Many have been created by federal agencies like the USGS, NOAA, EPA, and USDA.  Some have been created in connection with
NSF-funded projects like the CZOs (Critical Zone Observatories), LTER (Long-Term Ecological Research) and NEON (National
Ecological Observatory Network).  Yet others, usually subsets of the federal agency collections, have been created to
support other modeling objectives (e.g., MOPEX and CAMELS).  Sometimes a federal agency creates a new collection to
supersede an existing collection.  Several of these collections are briefly summarized in the next section.  As might
be expected, each of these data collections provide a different set of basin attributes, usually in the form of CSV or
TSV files (comma or tab separated values), and sometimes also with ESRI shapefiles for all the basins in the collection. 
Unfortunately, there is a huge amount of heterogeneity across these basin collections, such as different attributes,
different column headings/abbreviations for the same attributes, different measurement units, different methods of
organizing files by region, and missing data.  While some data sets are available on nice websites or through APIs,
it can be surprisingly difficult to obtain some of these collections, especially the older ones, which may no longer
be available at their original URL (e.g., MOPEX).  It is also unclear to most potential users how these various basin
collections relate to one another, or the extent to which they contain the same basins, and the sea of acronyms is daunting.
A given basin, associated with a given stream gauge at its outlet, typically has many different IDs, such as a USGS
8-to-15-digit ID, a 5-character NOAA NWS location ID, a GOES satellite ID, and so on.

In order to address some of these issues, many of these data sets were acquired and then a set of Python utilities
were developed, one set for each data collection, to help with collating, cleaning, augmenting, and extracting
information from them.  These Python utilities currently reside in a folder within the TopoFlow 3.6 repo, at:
     https://github.com/peckhams/topoflow36/tree/master/topoflow/utils/ngen
and make use of some of the TopoFlow utilities.  This ngen folder contains Python source code files with names like: 
camels_utils.py, mopex_utils.py, gages2_utils.py usgs_utils.py, and rfc_utils.py that contain functions for working
with the CAMELS, MOPEX, GAGES2, USGS NWIS, and NOAA RFC datasets, respectively.  These utilities were used to prepare
augmented TSV (tab-separated value) files for each of the datasets.  They make use of functions in the files:
data_utils.py (for general data processing tasks) and shape_utils.py (for scanning ESRI shapefiles to extract
information such as the geographic bounding box (i.e., minlat, maxlat, minlon, maxlon).  After preparing an augmented
TSV file for each dataset with these utilities, the collate() function in the file collate_basins.py was used to create
a single TSV file with selected attributes from all of the datasets.  This TSV file is in the folder called "__Collated"
in this repo.

QGIS, an open-source GIS application, was used to view ESRI shapefile attribute tables and to save them to CSV format.
It was also used to investigate oddities in the datasets.

### How the NextGen Combined Basin Repo is Organized

Most of the folders in the repo are named to reflect a specific dataset, often associated with a particular federal agency.
For example, several folder names start with a federal agency name like:  "NOAA_", "NSF_", "USDA_" or "USGS_".
Within a dataset folder, there will usually be a folder called "Data".  The Data folder will contain a Mac-based
shortcut (.webloc) to the website that the dataset was downloaded from, starting with "__".  Often it will also contain
a file called "__README.txt" with helpful information specific to that dataset.  If the dataset is not too large (since
GitHub has a filesize limit) it is also included in this Data folder (possibly zipped), or at least key portions of it.
Files uploaded by browser to GitHub have a limit of 25 MB, while files uploaded by command line can be up to 100 MB.
The dataset folder will usually also contain a folder called "_New" that contains files generated from the datasets by
the set of Python utilities or by QGIS.  In many cases, the dataset folder will also contain folders called "Docs"
(with additional documentation relating to the dataset), "Papers" (with PDF files for key papers that describe or use
the dataset), and "URLs" (with additional Mac-based shortcuts to related websites).  If there is a GitHub repo associated
with the dataset, there may also be a folder called "GitHub" with a link to that repo.

If you intend to use the Python utilities to re-create or augment files in the "_New" folders, you should first check the
"_New" folder for each dataset and unzip any ".zip" files you find there.  These will typically be Python dictionaries or
datasets that speed up computation, saved into .pkl (pickle) or ".npy" (numpy) files.    

In addition to the dataset folders, there are a few other folders such as:
"__Collated" (with combined, selected information for many of the datasets)
"__Docs" (with general docs that apply across multiple datasets)
"__Extras" (with extras such as shapefiles for the US states, for plotting)
"APIs_or_Services" (with links to websites that provide an API or service)
"SWB" (with information about the Seasonal Water Balance basin classification method)

Not all of the datasets with a folder in the repo have been merged into the final, collated TSV file, in the "__Collated"
folder.  Some have only been included for reference, such as the "Caravan" and "HYSETS" dataset folders.

### What Information is Included in the Collated TSV File?

Site_ID      = USGS site ID, 8 to 15 digits <br>
NWS_Site_ID  = NOAA NWS location ID, 5 to 8 alphanumeric characters <br>
RFC          = 5-letter abbrevation for a NOAA River Forecast Center <br>
Site_Name    = Original USGS site name, often with many abbrevations <br>
Site_Type    = The USGS site type (e.g. Stream, Lake, Atmosphere, Well, etc.) <br>
Stage_Data   = c for continuous, i for intermittent, followed by <br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
A for active, I for inactive, or N for never recorded <br>
State_Code   = 2-letter US state code <br>
Country_Code = country code <br>
Lon          = longitude of basin/gage outlet <br>
Lat          = latitude of basin/gage outlet <br>
Elev         = elevation of basin/gage outlet <br>
Elev_Units   = elevation units <br>
Area         = drainage area above basin/gage outlet <br>
Area_Units   = area units <br>
Horiz_Datum  = horizontal datum <br>
Vert_Datum   = vertical datum <br>
Minlon       = westernmost longitude of geographic bounding box <br>
Maxlon       = eastermost longitude of geographic bounding box <br>
Minlat       = southernmost longitude of geographic bounding box <br>
Maxlat       = northernmost longitude of geographic bounding box <br>
Long_Name    = expanded USGS site name, without abbreviations <br>
Closest_Site_ID = the closest USGS site ID <br> 
Closest_Site_Dist = distance to the closest USGS site ID <br>
Site_URL     = URL associated with the USGS site ID <br>
HUC_URL      = URL associated with basin's Hydrologic Unit Code <br>
Status       = status of the gage (active or inactive), if known <br>
Start_Date   = start date for data collection, if known <br>
End_Date     = end date for data collection, if known <br>
HLR_Code     = USGS Hydrologic Landscape Region code (0 to 20) <br>
SWB_Class    = Seasonal Water Balance class (of 10 classes), if computable <br>
Hgraph_Type  = Hydrograph type from NWM 3 work, if known <br>

Is_USGS_NWIS_Web = Is site in dataset from official NWIS website? <br>
Is_GAGES2_Any    = Is site in the USGS GAGES-II dataset? <br>
Is_FPS           = Is site in Federal Priority Streamgage dataset? <br>
Is_HCDN          = Is site in Hydro Climatic Data Network dataset? <br>
Is_RFC           = Is site in NOAA River Forecast Center dataset? <br>
Is_CAMELS        = Is site in the CAMELS dataset? <br>
Is_MOPEX         = Is site in the MOPEX dataset? <br>
Is_CZO           = Is site in the NSF CZO dataset? <br>
Is_LTER          = Is site in the NSF LTER dataset? <br>
Is_NEON          = Is site in the NSF NEON dataset? <br>
Is_ARS           = Is site in the USDA ARS experimental watershed dataset? <br>

### Oddities in the Datasets

Most of these are documented in the "__README.txt" files that are included
in many of the dataset folders.  

#### Non-standard NWS Location IDs for MBRFC
The Missouri Basin RFC (MBRFC), one of the 13 NOAA River Forecast Centers, often
provides the NWS location ID as a 3 or 4 digit number instead of following the
usually 5-character scheme.  By comparing outlet lons and lats, it was found
that a large fraction of these also have a standard 5-character NWS location ID.
The associated shapefile has many basins appearing twice, once for each of
these two alternate (but equivalent) IDs.  It remains unclear why the MBRFC
did not follow the standard method for assigning alphanumeric NWS location IDs.
Note that a few other RFCs add additional letters after the 5 standard
alphanumeric characters as a means of grouping nearby sites.

#### Missing Data for NWS River Forecast Centers
Four of the dataset folders that start with "NOAA_" contain alternate datasets
for the basins associated with the 13 NOAA RFCs.  For example, one gets info from
a beta version of a new API, and one gets info from a USGS-HADS crosswalk for
gages in the HADS/GOES network.  Some utilities in rfc_utils.py attempt to utilize
these different datasets to fill in missing information.




