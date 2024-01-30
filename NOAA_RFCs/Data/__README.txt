
S.D. Peckham
2024-01-11

This dataset has a shapefile called "ba12my15.shp" with information for
all NOAA RFC basins. The dataset web page says there are 6371 records/basins,
but the file actually contains 9370 records/basins.

The shapefile attribute table provides 6 key attributes for each basin:
   ID (NWS site ID, 5 to 8 characters),
   NAME (not the USGS name)
   CWA (County Warning Area, 3-letter code same as WFO name/code),
   RFC (River Forecast Center 5-letter identifier)
   LON (longitude of basin centroid, decimal degrees)
   LAT (latitude of basin centroid, decimal degrees)

The ABRFC often adds a few letters after the 5-character NWS site ID, such as:
LWR (lower), UPR (upper), GL, LG, NG, UG, FLO, FUP, LOC 

The CBRFC almost always adds extra letters after the 5-character NWS site ID,
such as:
L, U, X, XL, XU,
LLF, LMF, LUF, LOF,
HLF, HMF, HUF, HOF,
LLH, LMH, LUH, LMH, LOH,
HLH, HMH, HUH, HMH, HOH
 
The MBRFC almost always uses a 3 or 4 digit number for the site ID, with
numbers ranging from 101 to 3297.  However, many IDs occur multiple times
in this file: e.g. 201, 206, 217, 221, 223.

THE NCRFC sometimes adds ROR, or NON to the 5-char site ID.

The NERFC also adds its own letters to the 5-char site ID.

An RFC identifier is provided for every basin, but the CWA code is missing
for about 2343 basins.

===================================================
 Saving the Shapefile Attribute Table to CSV File
===================================================
The shapefile attribute table has been saved to a CSV file using QGIS as follows.
1. Open the file "ba12my15.shp" with QGIS.
2. In the Layers panel (lower left), right click and choose:
   Export > Save Features As...
3. Provide a filename (and path) in the "File name" text box.
      NOAA_RFCs/_New/All_NWS_River_Basins/ba12my15.csv
4. Click on the OK button (bottom right).
5. Note that a QGIS file with extension ".qmd" is also created.

====================================
 Info from the USGS-HADS Crosswalk
====================================
See NOAA_RFCs/Data/All_USGS-HADS_Sites/ALL_USGS-HADS_SITES.tsv
* There are 8902 HADS basins with type "Stream"
* There are 9109 HADS basins with type "Stream: xxxx'

=============================
 Info from the New NOAA API 
=============================
See APIs_or_Services/NOAA_OWP_Swagger_API_beta.
https://preview-api.water.noaa.gov/v1/docs/#/Gauges/Gauges_ListGauges
* Obtained info for 7319 NWIS USGS Stream gauges via API,
  including RFC name, NWS loc ID, USGS ID, elevation, etc.

=====================================================
 Number of RFC Sites from RFC Websites (2023-11-08)
=====================================================
Note:  The number found in the RFC shapefiles from here:
   https://www.nohrsc.noaa.gov/gisdatasets/
are given in parentheses.

ABRFC - All: 424, Forecasts: 208  (Shapefile: 495)
   https://water.weather.gov/ahps/region.php?rfc=abrfc

APRFC - All: 344, Forecasts: 118  (Shapefile: 325)
   https://water.weather.gov/ahps/region.php?rfc=aprfc

CBRFC - All: 359, Forecasts: 284  (Shapefile: 508)
   https://water.weather.gov/ahps/region.php?rfc=cbrfc

CNRFC - All: 691, Forecasts: 218  (Shapefile: 514)
   https://water.weather.gov/ahps/region.php?rfc=cnrfc

LMRFC - All: 874, Forecasts: 304  (Shapefile: 543)
   https://water.weather.gov/ahps/region.php?rfc=lmrfc

MARFC - All: 899, Forecasts: 225  (Shapefile: 167)
   https://water.weather.gov/ahps/region.php?rfc=marfc

MBRFC - All: 1185, Forecasts: 467  (Shapefile: 1412)
   https://water.weather.gov/ahps/region.php?rfc=mbrfc

NCRFC - All: 1299, Forecasts: 484  (Shapefile: 1190)
   https://water.weather.gov/ahps/region.php?rfc=ncrfc

NERFC - All: 488, Forecasts: 240  (Shapefile: 239)
   https://water.weather.gov/ahps/region.php?rfc=nerfc

NWRFC - All: 696, Forecasts: 339  (Shapefile: 562)
   https://water.weather.gov/ahps/region.php?rfc=nerfc

OHRFC - All: 1050, Forecasts: 381  (Shapefile: 723)
   https://water.weather.gov/ahps/region.php?rfc=nerfc

SERFC - All: 1452, Forecasts: 327  (Shapefile: 457)
   https://water.weather.gov/ahps/region.php?rfc=serfc

WGRFC - All: 671, Forecasts: 335  (Shapefile: 624)
   https://water.weather.gov/ahps/region.php?rfc=wgrfc

Totals - All: 10432, Forecasts: 3930

