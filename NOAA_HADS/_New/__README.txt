
S.D. Peckham
2024-01-20

The files "new_hads_info.tsv" and "new_hads_info_sorted.tsv" contain
information that was extracted from the file:
    "NOAA_HADS/Data/ALL_USGS-HADS_SITES.txt"
and other files in the current folder, using the function create_hads_tsv()
in rfc_utils.py.

The text files that start with "NWMv3_basin_type" classify many of
the RFC basins according to their hydrograph type as modeled with the
National Water Model version 3.  These, and the file "usgsMasterMeta.txt"
were obtained from Wanru Wu, but I don't know the original source.

The files ending in ".pkl" are Python "pickle" files that contain
Python dictionaries that are created and read by functions in rfc_utils.py.
