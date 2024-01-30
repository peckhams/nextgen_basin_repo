
S.D. Peckham
January 30, 2024

This file is supposed to contain the following files which belong
to the HYDRO1K North America DEM dataset, but the filesizes of the
.bil and .tif files (even when zipped) exceed the 25 MB GitHub limit.
This GTOPO30 / HYDRO1K DEM dataset was used to create the HLR dataset.

na_dem.bil
na_dem.blw
na_dem.hdr
na_dem.prj
na_dem.stx

na_dem.tif

However, you can download this DEM dataset from either the USGS
EarthExplorer site or from DataONE, as follows.

-------------------------------------
 How to Download from EarthExplorer
-------------------------------------
(1) Go to: https://earthexplorer.usgs.gov/

(2) Click on the "Login" link in the upper right corner and log in.
    If you don't have an account, you must create one.

(3) Click on the tab labeled "Data Sets" on the left-hand side.

(4) Click on "Digital Elevation" and then check the box labeled:
    GTOPO30 HYDRO 1K

(5) Click on the "Results >>" button near the bottom.

(6) Scroll down to the dataset that says "Continent: NORTH AMERICA".

(7) Click on the small icon with the green arrow.

(8) Click on the Download button to download a zip file called:
    gt30h1kna.zip.

(9) Unzip the file and copy the contents to this folder.
  
(10) Examine the file "na_dem.prj" with a text editor.  Notice that
     the projection is:  "Lambert Azimuthal Equal Area",
     latitude of origin is: 45.0, central meridian is: -100.0,
     and the ellipsoid is: "Clarke 1866 Authalic Sphere", with a
     radius of:  6370997 meters.
  
(11) Examine the file "na_dem.hdr" with a text editor.  Notice that
     this DEM has 9102 columns, 8384 rows and stores the elevations
     as 2-byte integers .

(12) Use the first 5 files listed above to create a GeoTIFF file
     for this DEM using QGIS or other GIS software.

-------------------------------
 How to Download from DataOne
-------------------------------
Alternately, you can download the key files (na_dem.bil, na_dem.hdr,
na_dem.blw, na_dem.stx) from DataOne at this URL:

https://search.dataone.org/view/doi%3A10.5063%2FAA%2Ftao.11656.3#doi%3A10.5063%2FAA%2Fhydro1k.200735414443186.1

then rename the downloaded (.data) file to TEST.zip and unzip it.



