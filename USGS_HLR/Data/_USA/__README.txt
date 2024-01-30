
S.D. Peckham
2024-01-12

The HLR (Hydrologic Landscape Regions) data set from USGS has
some metadata, including HLR codes in {0,...,20}, for what is
claimed to be 43931 basins.
See:  https://www.sciencebase.gov/catalog/item/
4f4e4786e4b07f02db485758

However, the HLR shapefile in the "hlrshape" folder of this
dataset may be a draft version because it has several problems,
such as:
   * 47479 features/basins (3548 more than 43931)

   * 659 basins with invalid HLR code of 0.
     These have COUNT=0, VALUE=-9999

   * Multiple features/basins with the same VALUE field, which
     is supposed to be a unique watershed ID.

   * 3391 basins w/ area < 1e7 sqm = 10 km2, even though it is
     claimed that the pruning threshold is 100 km2.

   * Strange coordinates for the points on the basin boundaries.

To save the shapefile attribute table to a CSV file in QGIS:
   - Right click on the layer in the Layers panel
   - Choose Export > Save Features As...
   - Choose Comma Separated Values (.csv) from Format droplist

There is a "raster" version of the HLR dataset that consists of
a set of ESRI ADF files in the arctar00000/hlrus folder.  This
dataset has fewer problems (e.g. 43931 basins) and seems more
consistent with a "final" version than the shapefile/vector
dataset.  While attributes for the HLR shapefile are included
in the shapefile attribute table, the attributes of the HLR
raster dataset are in the file: vat.adf.  The function called:
convert_vat_adf_to_csv() reads attributes from the vat.adf file
and writes them to a CSV file: vat_adf.csv.  The resulting CSV
file has 43931 rows, no HLR codes of 0, and (it appears) no
repeated values in the VALUE (watershed ID) column.  It seemed
to work but got this error message at the end:
ERROR 5: OSRCalcInvFlattening(): Wrong input values
##########################################################

A new HLR shapefile (hlrus4.shp) was created by reading the
raster version of the HLR data set into QGIS and then using
its raster to vector conversion tool as follows:
   Raster > Conversion > Polygonize (Raster to Vector).
   Change DN to VALUE.
   The resulting shapefile attribute table has only one column:
   VALUE (watershed ID). 
The new shapefile was saved into the HLR shapefiles folder. 
To add the (raster) attribute table (vat_adf.csv; see above)
to this new shapefile, QGIS was again used and the steps are 
described in the text file:
"__HLR_shapefile_notes.txt" in the hlrshape folder.

###############################################################
 NOTE:  When the attribute table of this new shapefile was
 saved to CSV (see above), it had many of the same problems
 as the original shapefile.
###############################################################

Note that neither the vector or raster version of the HLR data
attribute tables provide names for the basins.  However, it is
likely that many of them are also USGS gauged basins, so it
may be possible to get names and USGS basin IDs from outlet
lons and lats.  Wolock is retiring soon but plans to generate
an updated version of the HLR data set in the near future.

Note that neither the vector or raster version of the HLR data
attribute tables provides the coordinates of the basin outlet
nor the geographic bounding box coordinates.  These are needed
for modeling these watersheds in NextGen.  The set of utilities
in this file attempt to rectify these omissions.  First, the
coordinates of each watershed polygon are read from the (new)
shapefile so that the min & max of lon & lat can be found for
each basin.  These bounds are padded slightly larger.  Second,
the HYDRO1K DEM for North America --- which was used to create
the HLR data set in the first place --- is used in an effort to
determine the outlet coordinates (lon/lat) for each basin.  The
elevation values for every grid cell on the basin boundary are
found, and the outlet is assumed to be the grid cell with the
lowest elevation.  However, this elevation is not always unique.

The source DEM is the GTOPO30 HYDRO1K DEM and uses a Lambert
Azimuthal Equal Area projection as described in its PRJ file.
        
In all of these utilities, we use GDAL and the PRJ files to
convert coordinates (e.g. Lambert Azimuthal Equal Area) to WGS84
lon/lat.  See the "convert_coords()" function in shape_utils.py.

Many code comments are for original (old) shapefile, that exhibit
that exhibits the numerous issues listed above.  The "new"
shapefile (hlrus4.shp) comes from QGIS work described above.

--------------------------------------------------------------
The source DEM is the GTOPO30 HYDRO1K DEM and uses a
Lambert Azimuthal Equal Area projection as described above.
Can index this 1-km DEM with the Lambert xy coords
to get an elevation, then compare to MINELE attribute
as a way to get the outlet xy.  Or just find the xy
pair for each polygon with the lowest elevation.
But the DEM will be pretty big.  The HYDRO1K DEM for
North America includes Alaska, CONUS, PR, etc. but not
Hawaii. It has 9102 cols and 8384 rows.  Need to
convert Lambert xy coords to DEM column and row.
See: http://www.ncgia.ucsb.edu/SANTA_FE_CD-ROM/
           sf_papers/verdin_kristine/santafe2.html
HYDRO1K DEM:  https://d9-wret.s3.us-west-2.amazonaws.com/
       assets/palladium/production/s3fs-public/atoms/files/
       HYDRO1kDocumentationReadMe.pdf



