
S.D. Peckham
2023-11-27

-------------------------------
 Save HLR Code Grid to GeoTIFF
-------------------------------
1. Change directories to:
   ~/nextgen_basin_repo/USGS_HLR/arctar00000/hlrus/

2. Right click on the file "w001001.adf" and open with QGIS.

3. In the Layers panel, right click on "hlrus" and select: Open Attribute Table

4. In the top right of the attribute table, choose "HLR" from Classification
   droplist, then click on the Classify button.

5. Color image will change to show the HLR Codes (from 1 to 20).

6. From Layer menu at top of screen, choose "Save As...".

7. From the "Format" droplist, choose "ENVI .hdr Labelled".

8. Click on the "..." to right side of "File name" text box.
   In "Save As:" textbox, type: "HLR_Code_Grid_9106x6855_1k" (no extension).
   From the "Where" droplist, choose "Downloads"; click Save button.

9. From the "CRS" droplist, choose "Layer CRS: unnamed".

10. Notice that Extent is given in "Lambert Azimuthal Equal Area" coordinates.

12. Notice in the Resolution panel that Horizontal/Vertical is checked
    and both are 1000 meters.

13. Skip other panels and click the "OK" button at bottom right.
    This creates 2 files:
       HLR_Code_Grid_9106x6855_1k.hdr
       HLR_Code_Grid_9106x6855_1k.*
    Change the ".*" extension to ".img" (ENVI).
    
14. Right click on new ".img" file and choose "Get Info".
    Notice that filesize = 249,686,520 = 9106 x 6855 x 4.

15. Start RiverTools.  From File menu choose Import DEM > ENVI Binary Raster.
    Choose the new ".img" file just created.  Click the OK button.
    Get error message right away:
    "Attempt to subscript ARRAY with <INT ( 7)> is out of range.
     Execution halted at: RT_READ_ENVI_KEYWORD"
     Likely some unsupport ENVI HDR keyword.

16. Manually create an RTI (.rti) file for this .img file.
    See full RTI file at bottom of this file.
    But something is wrong with the values.

17. Instead try the following (using the GeoTIFF file):

    from topoflow.utils.ngen import hlr_tools as hlr

==================================================================================
RiverTools Info File
 
;----------------------
; Description of Grid
;----------------------
DEM filename:  HLR_Code_Grid_9106x6855_1k.img
DEM source:    QGIS and USGS HLR project.
 
;------------------------
; Grid dimensions, etc.
;------------------------
Number of columns:  9106
Number of rows:     6855
Data type:          LONG
Byte order:         LSB
 
;----------------------
; Pixel geometry info
;----------------------
Pixel geometry code:  1
Pixel x-resolution:   1000.0000
Pixel y-resolution:   1000.0000
Pixel z-resolution:   1.0000000
Z-resolution units:   METERS
 
;----------------------------------------------------
; Bounding box coordinates (degrees lat/lon or UTM)
;----------------------------------------------------
South edge y-coordinate:  -2530809.600000000093
North edge y-coordinate:  4324190.400000000373
East  edge x-coordinate:  2930983.399999999907
West  edge x-coordinate:  -6175016.599999999627
Measurement units:        METERS
 
;----------------------
; Min and max values
;----------------------
DEM minimum:  1.00000
DEM maximum:  44594.0
 
;-----------
; UTM zone
;-----------
UTM zone: UNKNOWN
 
 
;------------------------------------
; Notes About RiverTools Info Files
;------------------------------------
;(1)  RiverTools grid info filenames end with '.rti'.
;(2)  The first line should be:  RiverTools Info File
;(3)  Lines starting with a semi-colon are ignored.
;(4)  Colons are used to delimit labels from values.
;(5)  The order of the numbers above is important.
;(6)  Number of rows and columns are required.
;(7)  Pixel geometry codes are: 0=Fixed-Angle, 1=Fixed-Length.
;(8)  Pixel x-resolution and y-resolution are required.
;(9)  Measurement units must be METERS or DEGREES.
;(10) Elevation data type is required.
;     Allowed types are BYTE, INTEGER, LONG, FLOAT, DOUBLE,
;     UINT, ULONG, LONG64 and ULONG64.
;(11) Byte order is required; either LSB or MSB.
;     (LSB = Least Significant Byte = little-endian)
;     (MSB = Most Significant Byte  = big-endian)
;(12) For 'fixed-angle' pixels, bounding lats and lons
;     are required to compute lengths and areas correctly.
;(13) Latitudes south of equator are negative and
;     longitudes west of prime meridian are negative.
;(14) This file is best modified with the View DEM Info
;     dialog in the File menu.













