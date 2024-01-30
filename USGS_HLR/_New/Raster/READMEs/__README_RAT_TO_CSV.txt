
S.D. Peckham
2023-06-05

Used TopoFlow util: hlr_tools/convert_vat_adf_to_csv() to convert
the raster attribute table (RAT) in vat.adf to vat_adf.csv.

% conda activate tf36
>>> python
>>> from topoflow.utils import hlr_tools as hlr
>>> hlr.convert_vat_adf_to_csv()

It seemed to work, but got this error message:
ERROR 5: OSRCalcInvFlattening(): Wrong input values


