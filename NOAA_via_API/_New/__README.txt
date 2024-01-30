
S.D. Peckham
2024-01-18

The file "USGS_NWIS_WQP3_Site_Info_via_API.tsv" was created with the function "create_tsv_via_api()" in rfc_utils.py.  This function uses a beta version of a new API at:
    "https://preview-api.water.noaa.gov/v1/gauges/" + gauge_id
When this function was called with the base_key = 'USGS_NWIS_WQP3', it took 9.56 hours to run due to the time to retrieve info from the API.

Each USGS Site ID in the set of 145,375 IDs associated with the key "USGS_NWIS_WQP3" was submitted to the API.  Of these, the API is currently able to return info for 7319 of them.  All of the others return an error code ("could not find gauge ID").

Note that the API does not return HSA_ID or GOES_ID, but these are available for many sites in the USGS-HADS crosswalk.  This "crosswalk" is in the file:
"NOAA_USGS_HADS/Data/ALL_USGS-HADS_SITES.txt".
The function get_usgs_rfc_dict_v1() in rfc_utils.py creates a Python dictionary with information in this crosswalk.


