## Data Processing

In this section, more details are provided below on the kind of data sources used, extraction methods employed and different data cleaning techniques applied.
Code file .....Process of aggregation and used for analysis

__NYC Schools__<br>
Data for both public and private schools are obtained from the open data sources provided by ESRI. 
These data tables contained information like unique school id, name, address, zip, county, city, location details, enrollment, start grade, end grade etc. 
After accounting only for elementary and middle schools, the final number of schools that are used in this analysis were 1, 658.

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
alone the overlap region of schools was minimum in the city.

_Sources:_ https://data.cityofnewyork.us/Public-Safety/NYPD-Motor-Vehicle-Collisions/h9gi-nx95

__NYPD Moving Summons Data__<br>
Summons data present on the NYPD site is extracted to be used as proxy for speeding attributes in the analysis. 
Since this data is at precinct level, first schools are geo-spatially mapped to their respective precincts and then 
summons data are linked up. In order to keep the years of data consistent, summons data from the NYPD site for the years 2013, 
2014 and 2015 were extracted, aggregated and normalized at overall level for each school. Further, 
only significant causes of summons like Cell Phone, Disobey Steady Red Signal, Disobey Traffic Control Device, 
Improper Turn, Safety Belt and Tinted Windows which have highest distribution share amongst the total moving summons 
issued in the aggeragated data. Distribution of normalized values across each of the summon cause are 
shown in the below figure

_Sources:_ http://www.nyc.gov/html/nypd/html/traffic_reports/traffic_summons_reports.shtml<br>
_Data Processing Code:_ __Precinct_Summons_Mapping.ipynb__


__311 Call Data__<br>
Similar to other data sources, even 311 complaints data was gathered from the NYC Open Data site for the years 2013, 2014 and 2015 
respectively.  All the 311 requests were filtered for the complaint type being “Street Condition”, and are geo-spatially associated with 
the schools based on location details and neighborhood radius around schools was kepy at 300 foot. 
The distribution of 311 calls across schools can be seen in the figure below which showcases low percentage of 311 complaints 
related to the school neighborhood regions.

_Sources:_ https://nycopendata.socrata.com/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9

__Census Data__<br>
Additional features were extracted related to demographics, education and income from the census database across each school. 
Similar to the methodology adopted in the precinct mapping, census tract is assigned for each school based on the geo-spatial location 
and proximity. Once respective schools are identified under each census tract, all the associated characteristics of census tract like 
demographics, income and education are aggregated for each school.

_Sources:_ http://www.census.gov/
