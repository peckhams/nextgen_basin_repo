
S.D. Peckham
2024-01-15

The directory:  "NOAA_RFCs/Data/Shapefiles_by_RFC_for_Basins/"
contains shapefiles for the basins in each of the 13 RFCs.

QGIS was used to save the shapefile attribute table for each of
these 13 shapefiles to this directory in CSV format.  The CSV
files all have names of the form: "b_<rfc>.csv".  QGIS also
created a QMD file for each CSV file.

Notice that the file "b_wgrfc.csv" is empty for some reason.
Found info for the WGRFC on an ArcGIS Online website in JSON
format and converted it to CSV with convert_json_to_csv() in
rfc_utils.py.