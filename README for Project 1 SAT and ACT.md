# Project  1: SAT and ACT Analysis Executive Summary 

### Introduction

In this project, I will be looking at the trends of the ACT and SAT participation rates and scores for 2017 and 2018 with the aim of gleaning insights on how the College Board can improve the SAT participation rates. 

### Problem Statement 

How can we increase the participation for states with a low participation rate? 

### About The Data

I worked with 4 data sets, namely the 2017 and 2018 data for the SAT and ACT which are provided as .CSV files. 

The SAT data has 51 rows and 5 columns. Each row corresponds to 1 state. 

The ACT data has 52 rows and 7 columns. Each row corresponds to 1 state and there was a national average row. 

##### What was fixed?

The additional row for National in ACT was removed.  

Upon comparison of the data with external sources, 3 errors were corrected.

1. The SAT 2017 Math Score for Maryland was incorrectly reflected as 52 instead of 524. 
2. The ACT 2017 Science score for Maryland was amended from 2.3 to 23.2.
3. The ACT 2017 Composite score for Wyoming was amended from 20.2x to 20.2. 

The participation rates and ACT composite scores were converted to float.  

The 4 data sets were eventually merged into a single final.CSV file for subsequent analysis. 



### Data Dictionary 

The following is a data dictionary to summarize the features:

| Feature                                     | Type   | Dataset | Description                                   |
| :------------------------------------------ | :----- | :------ | :-------------------------------------------- |
| sat_2017_state                              | object | SAT     | SAT scores by State for the year of 2017      |
| sat_2017_participation                      | float  | SAT     | SAT participation rates in 2017               |
| sat_2017_evidence-based_reading_and_writing | int    | SAT     | Average SAT Reading and Writing score in 2017 |
| sat_2017_math                               | int    | SAT     | Average SAT Math score in 2017                |
| sat_2017_math                               | int    | SAT     | Total SAT score in 2017                       |
| act_2017_state                              | object | ACT     | ACT scores by State for the year of 2017      |
| sat_2017_participation                      | float  | ACT     | ACT participation rates in 2017               |
| sat_2017_english                            | float  | ACT     | Average ACT English score in 2017             |
| sat_2017_math                               | float  | ACT     | Average ACT Math score in 2017                |
| sat_2017_reading                            | float  | ACT     | Average ACT Reading score in 2017             |
| sat_2017_science                            | float  | ACT     | Average ACT Science score in 2017             |
| sat_2017_composite                          | float  | ACT     | Average score of 4 ACT tests in 2017          |



### Exploratory Data Analysis

##### The following was explored: 

1. States with the highest and lowest participation rates for each of the test 
2. States with the highest and lowest mean/total composite scores 
3. Any rate change for states with 100% participation rates in 2017 
4. Are there states with more than 50% participation rates for both tests in either year

##### Findings:

##### <u>Participation rates</u>

It was observed that D.C, Michigan, Connecticut and Delaware have 100% SAT participation rates for 2017. While states such as North Dakota, Mississippi, Iowa have low SAT participation rates of 2% for the same year. 

In 2018, Colorado, Connecticut, Delaware, Michigan, Idaho have 100% SAT participation rates. North Dakota (2%) is observed to have the lowest participation rate once again.  With the same states topping the list for participation rates for 2 consecutive years it may be worthwhile exploring the role of state policies on the participation numbers.

In the case of the ACT, there are 17 states with 100% ACT participation rates for 2017 which is significantly higher than SAT with only 4 states achieving a full score. It is also notable that the ACT seems to have a higher minimum participation rate in general. Apart from Maine with a 8% participation rate, the next lowest state (New Hampshire at 18%) which is significantly higher than the low participating SAT states. This can possibly imply that the SAT may not be relevant in certain states or that the ACT is doing better than the SAT as the choice standardised test. Some possible reasons may also be due to the different structure of the tests as the ACT includes a Science reasoning subject and the test formats for both are also different. 

##### <u>Mean total/composite scores</u>

The states with high mean scores for the SAT includes Minnesota, Wisconsin, Iowa and Kansas for both 2017 and 2018. Missouri and North Dakota also achieved the top 5 mean total SAT scores in 2017 and 2018 respectively. Interestingly, the above list also coincide with the list of states with low participation rates for the SAT. It is likely that the small group of students that bother to take the SAT scores are also the top performers that intend to apply for colleges that require SAT scores. As such these scores may not be representative of the education system and performance of the state.  

The trend is similar between ACT scores and participation rates.

##### <u>Rate of change</u>

For the SAT, the top 5 states with the largest rate of change includes Illinois (100%), Colorado (80%), West Virgina (10%), Askansas (6.7%) and Ohio (5%). This trends and states will be worthwhile exploring. 

##### <u>States with more than 50% participation rates for both tests</u>

Florida, Georgia and Hawaii have participation rates that are above 50% for both the ACT and SAT. Upon further inspection, the participation rates for Georgia are within 6% of each other while the rates of Florida are within 10% of each other. One possibly reason for this could be that the students taking part in the SAT are also taking the ACT tests. This can be evaluated by correlating the mean total scores and the composite scores to see if they correspond to the same band. 

### Data Visualisation 

##### <u>Observations from the Correlation Heat Map:</u>

- Participation rates for the SAT and ACT are negatively correlated and there is a strong correlation (r) of approximately -0.84. 
- Mean scores the SAT and ACT are highly negatively correlated with r=-0.87. 
- Mean scores for the same subject for the SAT and ACT tests are negatively correlated. However this correlation is moderate with r in the range of -0.4.

##### <u>Key observations for average SAT and ACT participation rates:</u>

- The distribution of participation scores for the SAT looks similar over the 2 years. It can be observed that there is a large number of states that have low participation rates (under 10%).
- The distribution for the ACT looks similar from 2017 to 2018 and it can be seen that a large number of states have high participation rates in the range of 90 to 100%. 
- The above gives an indication that the ACT is outperforming the SAT in terms of participation rates.

##### <u>Key observations for mean SAT and ACT Math scores:</u>

- The mean math scores for the SAT appears to have 1 distinct peak with a lower peak and this indicates that there are 2 clusters of scores for the states, one around the 525 to 550 range and another at the 600 to 650 range. 
- A similar trend is observed over the distribution of ACT Math scores over the 2 years. There is a similar trend of 2 peaks, or some degree of bimodality.

##### <u>Observations for mean SAT and ACT reading scores:</u>

- The mean reading scores for the SAT appears to have 2 peaks that clusters around the 540 range and another at the 640 range.
- A similar trend is observed over the distribution of ACT scores over the 2 years.

##### <u>Correlation between test scores:</u>

- From the first 3 scatterplots, there seems to be a weak correlation between the SAT and ACT subject tests as well as the overall mean score. There seems to be a negative correlation (where lower SAT scores correspond to higher ACT scores for the same test) but the trend is not that distinct. The weak correlation was also derived from the correlation heatmap earlier. 
- A positive relationship can be observed for the scatterplot of the SAT composite scores from 2017 and 2018, possibly indicating a similar aptitude of students year on year, except for the outliers. However one would have to consider if there is any significant change in participation rates which may influence how representative the score is of the state's performance. 

### Additional Visualisations 

The scatter plots above are aimed at determining the correlation between the participation rates and total/composite scores for the respective test. There seems to be a negative correlation between the 2, indicating that higher participation rates correspond to lower total/composite scores for the state. States with low participation rates tend to see only the best students taking the SATs and this may lead to an artificially higher score. States of Iowa and Missouri have 2% & 3% participation rates and are also the top 5 in terms of the highest SAT 2017 total score. 

The ACT and SAT participation distributions roughly mirror each other, with states tending to prefer one test or the other.

### Descriptive and Inferential Statistics 

The mean participation rates of ACT achieving 65.3% and 61.64% in 2017 and 2018 whereas the SAT rates are 39.8% and 45.7% in the same period.

The analysis seems to indicate a negative relationship between participation  rates and mean state scores and the trend is consistent for both tests. The mean scores for each test may not be reflective of the education system and average aptitude of the students in each state as the participants that took each test may not be representative of the population of students within each state. 

Limitations of the data - the data provided may not be sufficient due to the sample size; this is apparent in the case of states with a low participation rates, as the statistics may not provide a good indication of the population parameters. State level data is also aggregated and having data at a granular level (such as local district or county) may allow us to derive more insights or better validate our hypothesis testing.

### Additional Research

Partnerships between the college board and the various states have a positive effect on SAT participation rates giving rise to to rates that are close to 100%. 

For states with participation rates greater than 50% for both tests in the same year, there could be an indication that  the same candidates are taking both tests. This was achieved by correlating SAT and ACT scores and deducing that the scores are in similar banding for each tests.

### Conclusion and Recommendations

From the above analysis it can be concluded that the ACT has been outperforming the SAT in terms of participation rates for the year of 2017 and 2018.  The ACT and SAT participation rates also mirror one another with each state choosing one over the other.  

States with consistent participation rates of 100% and high increase in participation rates are due to state policies and College Board should continue to pursue such partnerships to boost participation. 

The mean test scores for each state may not be representative of the education system and average aptitude of the students as the sample size of the participants that took each test by state may not be representative of that population. 

The College Board should consider Ohio as a potential state to increase participation as it is one of the top 5 states with the largest rate of change and room for growth. As Ohio currently requires public schools to give SAT or ACT to all juniors, there is a potential to pursue a partnership to boost participation rates. 