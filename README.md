# TRI_Site_Identification

## Earth Challenge 2020:

A global citizen science initiative that will demonstrate how small digital acts of science can help monitor and improve environmental and human health.

## TIDEs database has a map of volunteer waste cleanup site: 

https://www.arcgis.com/home/webmap/viewer.html?url=https://services8.arcgis.com/iSk8OjfdllV32jzx/ArcGIS/rest/services/TIDES_EC2020_DataKindDC/FeatureServer&source=sd

While volunteers can cleanup certain kinds of waste, hazardous waste sites need to be cleaned with caution.  Volunteers need to be protected from exposure to dangerous chemicals and unknown hazardous waste sites need to be identified.

## Data Description
The target data comes from the 2017 Toxic Release Inventory (TRI):

https://www.epa.gov/toxics-release-inventory-tri-program/tri-basic-data-files-calendar-years-1987-2017.  

Target data is 0 or 1, if a census block group contains a 2017 TRI site or does not.  ~6,600 of 220,000 census block groups contained a TRI site.  Data geocodes were given FIPs codes from this API:

https://geo.fcc.gov/api/census/

The explanatory data comes from the 2010 Census and 2013-2017 American Census Survey at the block group level.  This information can be accessed from the 2019 Planning Database (PDB): 

https://www.census.gov/topics/research/guidance/planning-databases.html

Datasets were merged using FIPs codes

## Pre-Processing and Data Cleaning
Variables with more than 15% missing data were dropped.  Integer data was imputed with mode and numerical data was imputed with mean.  Categorical variables were dummied.  All explanatory variables were standardized before being split into training and testing data.  

## Data Science Model
Best Model was XGBoost with a slow learning rate and tree depths no less than 10.

## Results
Goal for this project was to create a heatmap of waste site location probabilities.  Predictions were good but could be improved.  Best model achieved Accuracy : 0.9580 | Sensitivity 0.6126 | Specificity: 0.3802

## Takeaway:  
Investigate known sites that have reported toxic waste release.  Use heatmap to identify unreported locations that are collecting hazardous waste.

