
S.D. Peckham
2024-01-18

The folder "NOAA_RFCs/Data/" contains a shapefile called "ba12my15.shp"
that contains information for all of the RFC basins (that is, for all 13
RFCs) in one file.  The attribute table for this shapefile was saved
using QGIS to the CSV file: "NOAA_RFCs/_New/ba12my15.csv", and includes
the attributes:
    NWS loc ID, Name, CWA, RFC, Lon, and Lat
for 9370 sites/basins.  Using the function: create_rfc_tsv() in rfc_utils.py,
this shapefile was scanned to determine the geographic bounding box for each
basin.  (This was similarly done for the GAGES2 and MOPEX basins.)
The file "NOAA_RFCs/_New/new_rfc_info.tsv" contains all basin attributes in
ba12my15.csv as well as the bounding box info (minlon, maxlon, minlat, maxlat).

The folder "NOAA_RFCs/Data/Shapefiles_by_RFC_for_Basins/" contains one shapefile
for each of NOAAs 13 River Forecast Centers (RFCs).  Using QGIS, the attribute
table for each of these shapefiles was saved to a CSV file.  These 13 new CSV
files are in: "NOAA_RFCs/_New/CSVs_for_each_RFC/".  The attribute table for the
WGRFC was empty, but the missing information was found on an ArcGIS online site
in JSON format.  It was converted to CSV and is included in the same folder.
Each of these 13 CSV files also includes the geographic bounding box for each
basin via the headings "MIN_X_AXIS_", "MAX_X_AXIS_", "MIN_Y_AXIS_", and
"MAX_Y_AXIS_" (minlon, maxlon, minlat, maxlat).
Data from these 13 separate CSV files was merged together into one TSV file
called "new_rfc_info2.tsv" in the "NOAA_RFCs/_New/" folder.  This new TSV file
was created with the function "merge_rfc_basin_info()" in rfc_utils.py.






