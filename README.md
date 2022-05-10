# Table Of Contents

### 1) Introduction

### 2) Business Problem

### 3) Data Understanding 

### 4) Data Exploration and Analysis

### 5) Classification Modeling
   - 5a Modeling with seasonality amd analysis
   - 5b Modeling without seasonality* and analysis
   - 5c Modeling weekly trends
   
### 6) Time series modeling and forecasting

### 7) Further Considerations with species analysis

### 8) Conclusion

### 9) Appendix

### 10) References



----

# *Houston, We Have an Allergy Problem:*
## Pollen Count Predictions for Allergies in Houston, Tx
### Nicholas Kennedy May, 2022
![pollen spores](images/Misc_pollen_colorized_wikipedia.jpg)

# 1) Introduction and Business Understanding 
Allergies are a impact lives  everywhere, but esepcially in Texas, US. Central texas is notorious for severe allergies, but in reality this problem affects the whole state. The surprising thing about this is that most of texas is a desert without much flora to speak of. Houston, however is uniquly positioned in texas being relatively near the desert, the ocean, marshland and forest. 

Allergy seasons occur with consistent regularity throughout the year. Spring and fall are universally known as the worst times of the year for allergies due to high pollen counts. It therefore stands to reason that using basic climate data, like wind speed, temperature and precipitation, seasonal in nature themselves, could be used to estimate and forecast pollen counts

Yet, while very possible, using weather and climate data to predict pollen counts is not particularly ground-breaking, because this data is also subject seasonal fluctuation. However, if seasonality is removed from the equation, does information such as local precipitation, temperature and wind speed still have an effect? 


# 2) Business Problem
The past 2 years, ravaged by the Covid-19 global pandemic, has made much of the world wary of the tiniest sniffle for fear they have contracted the highly infectious disease that has killed so many. Additionally the broad variety and severity of symptoms across the board has had many confuse their sympotons with allergies and vice versa, thus bringing a much greater attention to Allergies in general. 

Knowing when healthcare systems can expect more patient visits due to allergies can help brace not only providers for the impact of higher case-loads, but also pharmacies for medicine stocking. With the National Allergy Bureau and the CDC working with medical providers and pharmacies, these organizations can not only prepare these kinds of entities, but also help bring awareness and understanding to individual allergy-sufferers among the general population. 

Lastly, in the further considerations a collaberation between public health organizations, pharmacies and members of the public is proposed in order to develop an application that can compare allergy medication purchases with species specific pollen data to use as a diagnostic support tool in identifying people's individual allergens.

<img src = "images/oak_cbs_austin.jpg">


# 3) Data Understanding and Preparation

The data used in this report comes from two sources: 
- Pollen data comes from The <a href="https://www.houstontx.gov/health/Pollen-Mold/pollen-archives.html">Houston Health Department website</a>
- Climate data comes from the the <a href="ncei.noaa.gov"> National Oceanic and Atmospheric Administration's (NOAA) National Center for Environmental Information (NCEI) </a>

Pollen Data was compiled from individual monthly spreadsheets from 2013 to 2022 consisting of pollen counts measured in parts per cubic meter. It consists of species specific daily pollen counts collected throughout the month except on weekends and holidays. It also distinguishes between tree, grass and weed pollen. The data was collected by three different technicians. 

Climate data was obtained for three testing sites, 2 located in Houston (suffixed '18' and '60'), and one located in Shreveport, LA (suffixed S), roughly 200 miles away in a highly vegetated area in order to see if its climate has an impact on the airborne pollen levels in Houston. Climate data consists of daily precipitation `PRCP`, average temperature `TAVG` and average wind speed `AWND`. For Shreveport, fastest 2 minute wind speed `WFD2` was also included in an attempt to see if wind currents from the nearby city had any role in Houston's pollen problem. 

Pollen counts were weighted differently for grass, weed, and tree problem based off of their differing classifications for severity levels as explained by the <a href ="https://www.houstontx.gov/health/Pollen-Mold/numbers.html"> Houston Health Department </a>

these adjusted counts were then tallied into one variable, `pollen_weighted`, which itself was used to create 3 distinct classification for daily pollen intensity: `high`, `very_high` and `super_high`

3,372 days in total, just shy of 10 years comprise this time series data. 

The details of this data cleaning and preparation can be found <a href="https://github.com/nikennedy/pollen_forecasting/blob/main/Auxilliary%20Notebooks/Data%20Cleaning.ipynb"> here in another notebook in this repo</a>


# 4) Data Exploration
the bulk of preliminary data exploration can be found <a href='https://github.com/nikennedy/pollen_forecasting/blob/main/Auxilliary%20Notebooks/EDA.ipynb'> here in a separate notebook.</a> Below shows the highlights as well as the most pertinent findings for this report. 

For the purpose of modeling the individual species will be ignored for now and explored in "Further Considerations" Towards the end of the report.


