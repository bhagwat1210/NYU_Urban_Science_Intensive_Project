### Analysis & Results

All the data files from data processing phase are merged into a single file across each school. This master dataset contains individual 
schools at row level and corresponding neighborhood factors like number of traffic collisions, number of traffic incidents (fatalities and 
injuries), number of 311 calls made related to street quality complaints, precinct level moving summons issued and census tract level 
attributes like demographics, education and income. All the data with temporal aspect was limited only for the years 2013, 2014 and 2015.
In this phase, the merger dataset is then subjected to tasks as mentioned below: <br>

__1.__ Defining Traffic Risk <br>
__2.__ Clustering school into 3 groups based on census data <br>
__3.__ Logistic Regression analysis across each cluster of schools <br>
__4.__ Rank-Ordering of school based on traffic risk probabilities <br>
__5.__ Fund Allocation based on enrollment attribute for finally selected top 37 schools <br>
