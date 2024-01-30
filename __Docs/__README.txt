
S.D. Peckham
2024-01-09

The USGS distributes its data via NWIS, the National Water Information
System.

The USDA distributes its data via STEWARDS.

The EPA distributes its data via WQX (also called STORET).

The Water Quality Portal can be used to download data from NWIS, STEWARDS,
or WQX.  The portal URL is:  https://www.waterqualitydata.us/

NWIS data is often provided in an older format called RDB.
RDB files follow a number of conventions for headers, etc., but
individual data records (for a given gage) are separated by newline
characters and the fields of each records are separated by tab
characters.  CITE REFERENCE FOR RDB FORMAT.

Since USGS site names may contain commas, new (tabular) files created
with the repo utilities are saved in TSV (tab-separated values) vs.
CSV (comma-separated values) format.  Spreadsheet programs like Numbers
(on a Mac) or Microsoft Excel can import both TSV and CSV files.
However, the Numbers spreadsheet app on Macs will only load the first
one million lines or records in a CSV or TSV file.

See the Wikipedia page for "Decimal Degrees", in the section titled
"Precision" for important information on the use of significant digits
in latitudes and longitudes.  More that 5 digits after the decimal is
generally not warranted.
    https://en.wikipedia.org/wiki/Decimal_degrees

For an explanation of how USGS site numbers are assigned, see:
https://help.waterdata.usgs.gov/faq/sites/do-station-numbers-have-any-particular-meaning

For an explanation of how NOAA site identifiers are assigned, see the file:
"NWS_Site_Identifiers_Explained.pdf" in this directory.

QGIS is an open-source GIS program that was used for some of this work.
The folder "QGIS_Tips" in this directory has tips for various tasks.

It seems that most USGS sites collect information on water quality vs. flow
variables.

Many USGS sites/gages are no longer actively collecting data.

