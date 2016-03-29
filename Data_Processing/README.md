## Data Processing

In this section, detailed information is provided below on the kind of data sources used, extraction methods employed and different data cleaning techniques applied for data processing phase of the social impact project. For data sources like traffic collisions and 311 call data, geo-spatial analysis was performed by assinging each of these incident locations within a school neighborhood of 300 foot radius. In the case of NYPD Summons data, since this is available only at precinct level each school is mapped to their respective precinct and then summons data is assigned to each school. Similarly for census data, first each school is mapped to their respective census tract and the respective census data of each census tract is then assigned to school.

__NYC Schools__<br>
Data for both public and private schools are obtained from the open data sources provided by ESRI. 
These data tables contained information like unique school id, name, address, zip, county, city, location details, enrollment, start grade, end grade etc. 
After accounting only for elementary and middle schools, the final number of schools that are used in this analysis were 1, 658. The final data output from this task is extracted in the form of csv files for public and private along with details like school id, name, address, location, enrollment, average class size etc. These files are further used for the final analysis.

_Sources:_ http://opendata.arcgis.com/datasets/1f74a16c80e949c0adfd7866684b83c5_0?geometry=-199.66%2C-16.973%2C162.746%2C72.074 <br>
http://opendata.arcgis.com/datasets/36695bf035fb4e98a88dbdcbaca2c40d_0<br>

__Traffic Collisions__<br>
Traffic collisions is gathered from NYC Open Data portal which contains some general details with information on location of the incident. 
Motor collisions data is available from 2012 and contained complete annual information for the years 2013, 2014 and 2015. 
The filters applied for this study were exclusion of holiday months i.e. July, August, inclusion of only weekdays and certain time periods within a day like 7-9 AM and 2-6 PM. 
In terms of the decision related to the which year of data should be used for the analysis, all individual years information was analyzed 
for varying trends in traffic collisions and common trends were noted. All three years of data were used and also once the required filters 
were applied, the final subset of motor collisions were plotted on ArcGIS along with the schools locations. The end results of this 
exercise would be that each school would have aggregated number of traffic collisions and aggregated number of injuries/fatalities for the 
years 2013, 2014 and 2015 within in each school neighborhood. Radius used to define school neighborhood region is 300 foot becasuse at this distance 
alone the overlap region of schools was minimum in the city. The final output from this exercise would be traffic collisions aggregated based on geo-spatial analysis and assigned respectively for each school neighborhood. 

_Sources:_ https://data.cityofnewyork.us/Public-Safety/NYPD-Motor-Vehicle-Collisions/h9gi-nx95

__NYPD Moving Summons Data__<br>
Summons data present on the NYPD site is extracted to be used as proxy for speeding attributes in the analysis. 
Since this data is at precinct level, first schools are geo-spatially mapped to their respective precincts and then 
summons data are linked up. In order to keep the years of data consistent, summons data from the NYPD site for the years 2013, 
2014 and 2015 were extracted, aggregated and normalized at overall level for each school. Further, 
only significant causes of summons like Cell Phone, Disobey Steady Red Signal, Disobey Traffic Control Device, 
Improper Turn, Safety Belt and Tinted Windows which have highest distribution share amongst the total moving summons 
issued in the aggeragated data. The final output from this exercise includes two files: 
1. a school level precinct mapping based on geo-spatial location analysis <br> 
2. 2. a precinct level aggregated data for moving summons issued by NYPD. The python code used for the process involved in creation of 2nd file is __Precinct_Summons_Mapping.ipynb__.

_Sources:_ http://www.nyc.gov/html/nypd/html/traffic_reports/traffic_summons_reports.shtml<br>

__311 Call Data__<br>
311 complaints data was gathered from the NYC Open Data site for the years 2013, 2014 and 2015.  All the 311 requests were filtered for the complaint type being “Street Condition”, and are geo-spatially associated with 
the schools based on location details and neighborhood radius around schools was kept at 300 foot. The python code for initial processing of overall 311 calls is shown in the file __311_Data_Mapping.ipynb__.
The final output of this exercise would be similar to that of traffic collisions as in each school will have assigned corresponding aggregated 311 calls made in the neighborhood region.

_Sources:_ https://nycopendata.socrata.com/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9

__Census Data__<br>
Additional features were extracted related to demographics, education and income from the census database across each school. 
Similar to the methodology adopted in the precinct mapping, census tract is assigned for each school based on the geo-spatial location and proximity. Once schools are identified under each census tract, all the associated characteristics of census tract like 
demographics, income and education are aggregated for each school. The final output from this exercise includes four files: 
1. a school level census tract mapping based on geo-spatial location analysis <br>
2. a census tract level aggregated data for demographics <br>
3. a census tract level aggregated data for income <br>
4. a census tract level aggregated data for education <br>

_Sources:_ http://www.census.gov/
