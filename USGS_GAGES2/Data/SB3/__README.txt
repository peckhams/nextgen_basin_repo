
S.D. Peckham
2024-01-09

The GAGES-II Selected Basins (version 3) dataset contains information for
1947 basins.  These basins are a subset of the GAGES-II Reference basin
dataset, which has a total of 2057 basins.  More information can be found
in the paper:

Over, T.M., Farmer, W.H., and Russell, A.M. (2018)  Refinement of a regression-based method for prediction of flow-duration curves of daily streamflow in the conterminous United States: U.S. Geological Survey Scientific Investigations Report 2018–5072, 34 p.  (Key paper on GAGES-II.)

In the GAGES-II Selected Basin filenames:
   - "SB3" stands for Selected Basins version 3.
   - "transf" stands for log10 "transformed" variables
   - "untransf" stands for untransformed variables.

Info for the GAGES-II SB3 basin variables is stored in Microsoft Excel
files that contain multiple sheets, one for each of 19 different
regions.  These Excel files have "transf" or "untransf" in their names.

The info in these 19 sheets was saved from Excel into 19 separate CSV
files, one for each region. Region numbers are 1 to 9, 10L, 10U, and
11 to 18.  These 19 extracted CSV files are in the folder:
   USGS_GAGES2/_New/SB3

For the purpose of computing the 3 parameters needed to classify each
basin using the Seasonal Water Balance method of Berghuijs et al. (2014),
the untransformed values of variables were used.

