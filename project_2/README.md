# Project  2: Ames Housing Data and Kaggle Challenge

### Introduction

In this project, I will be creating a regression model based on the Ames Housing Dataset with the aim of predicting the sale price of a house in Ames.  The models used include Linear Regression, Lasso and Ridge.  

### Problem Statement 

How can we predict the sale price of a house in Ames?

### About The Data

The Ames Housing Dataset which contains over 80 columns of different features relating to houses. The data set is split into 2 sets, train.csv and test.csv with the corresponding [data description](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).

##### What was fixed?

1. For the train dataset, 3 rows with outliers corresponding to data with large floor areas and very low prices were removed during the Exploratory Data Analysis (EDA)

2. Some of the features that displayed collinearity were also combined or dropped during EDA and Feature Engineering steps

3. Upon comparison of the original data set and the data description many of the null values correspond to the absence of the feature. The categorical features were either one-hot-encoded (nominal features) or ordered (ordinal features).

The test set was also processed in the same way, repeating steps 2 and 3. 

The final test and train data sets can be found as [train_clean.csv](./datasets/train_clean.csv) and [test_clean.csv](./datasets/test_clean.csv) , respectively. 

### EDA, Cleaning and Pre-processing

##### General Approach: 

1. Certain features with no impact on sale price were dropped first. This includes Id and PID which is unique to each house

2. Relationship between sale price and certain continuous and categorical features were analysed

3. Collinear features were eliminated
4. Features with low variance were eliminated as they are deemed to be less useful for discerning the sale price from one house to the other if majority of the houses fall in the same category or had the same value
5. Deal with Null Values 
6. Encoding of Ordinal Features
7. One hot encoding of Nominal Features

##### Some Findings:

<u>Continuous Features</u>

- Positive correlation between Sale Price and Gr Liv Area, Total Basement Sq Ft and Garage Area. This is expected as one will typically have to pay a higher price for larger houses

<u>Discrete Features</u>

- There is a general trend the sale price increases with an increase of the discrete features such as full bath, fireplaces

<u>Categorical Features</u>

- There is a general trend that better overall material and finish of the house leads to a higher sale price
- Newer houses leads to a higher median sale price
- There is a trend that house in certain neighbourhoods yield a higher median sale price

<u>Features with Low Variance</u>

- There were over 20 features where 80% of the data have the same value and these features  which will be excluded from the model. With a large proportion of observations having the same value there will be less information for the model to discern why there is a difference in sale price. The effect of such features in the model will be discussed in the final model analysis and conclusion. 



### Feature Engineering

##### Features:

<u>Cost per Square Foot</u>

Generalise the square foot of each property as sum of Tot Bsmt SF and Gr Liv Area to evaluate cost per sq ft. This feature is purely for visualisation and will not be used as a predictor as the feature takes in SalePrice (which is the target value).

<u>No Remod</u>

Compare the number of houses that were remodified. 

<u>Years Before Sale</u>

Number of years between YearBuilt and YrSold

<u>Total Porch SF</u>

Created from Open Porch SF, Enclosed Porch, 3SsnPorch and Screen Porch 

<u>Total Baths</u>

Created from Full Bath, Half Bath, Bsmt Full Bath, Bsmt Half Bath



### Modeling

##### General Approach: 

1. Run one round of modeling using Linear Regression, Lasso and Ridge

2. Lasso was used for further feature selection and fine-tuning

3. Train-test-split will be applied on train set for model validation and selection

##### Metrics Used to Validate Model:

1. Root Mean Square Error: this metric is used for evaluation on Kaggle 
2. R^2 Score of Model
3. Adjusted R^2 of Model to account for the number of parameter

##### Findings:

1. Lasso comes in handy as it was able to eliminate 50 out of 112 features
2. The top 20 features with the highest Lasso coefficients were picked 
3. Squaring of the top 5 features improved the performance of the model
4. There may be some sort of polynomial relationship between the top 5 features namely Gr Liv Area, Overall Qual, Total Bsmt SF, Neighborhood NridgHt and Exter Qual.

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



Findings: 

The squaring of top 5 features improved the R^2 of the model compared to the earlier rounds (0.901). This indicates there may be some sort of polynomial relationship between the top 5 features namely Gr Liv Area, Overall Qual, Total Bsmt SF, Neighborhood_NridgHt and Exter Qual.

Interpreting the coefficients of the 20 features selected:

- A unit increase in the feature will result in an increase/decrease  by the magnitude of the coefficients
- The + sign indicates an increase whereas the - sign indicates a decrease which suggests a negative relationship . For example, a unit increase in yrs_bef_sale will decrease sale price by \$7258
- In the case of the top 5 features, a unit increase in the square of the feature will increase the sale price by the magnitude of the coefficient. For example, a unit increase in GrLivArea**2 will increase sale price by \$22950

Discussion on the Top 10 Features: 

- Gr Liv Area has the highest weightage from the Lasso model, this makes sense as housing prices are typically a factor of the floor area (i.e. cost per square foot). The weight of this feature is close to double the weight of the second highest (Overall Qual) and it can be concluded that the house area is the major feature that impacts sale price. 
- Overall Qual has the second highest value. During the earlier EDA, it was established that Overall Qual seems to have a significant impact on sale price with higher quality houses having a significantly higher price as seen by the exponential increase in median sale price with increase in overall quality score. The findings from the Lasso coefficients also supports this. 
- Total Bsmt SF is also amongst the top 5 features with the highest Lasso coefficients, in this case the sum of Gr Liv Area and Total Bsmt SF make ups majority of the floor area of most of the houses and it 
- Exter Qual has a Lasso coefficient of 7394, this means that the external quality finish on the house also has significant weightage the sale price.

- Neighborhoods NridgeHt and StoneBr are the neighbourhoods with a significantly higher median price compared to the other estates. In this case, it would mean that a house in NridgeHt would have a \$7398 increase in sale price while a house in StoneBr would have a \$7044 increase in price 
- Years Before Sale was Year Built subtracted from Year Sold, which gives an indication of the age of the house. This relationship is negative as a unit increase in year before sale would reduce sale price by \$7258
- The remaining 3 features with the highest weights are Lot Area, Mas Vnr Area and Garage Area. The lot area refers to the total land area of the property, where sale price increases with presence of lot area. Masonry veneer area refers to the cladded/façade on the structural wall, which again incurs more cost when a feature is present. Lastly, the presence of a garage area would increase the sale price for similar reasons. 
- The remaining 10 features have coefficients ranging from 5614 to 2541 in terms of absolute magnitude. Some interesting observations, having mason veneer type of brick face penalizes sale price and so does kitchen above grade. 

Other observations:

- KitchenAbvGr seems to give a negative penalty on sale price for a unit increase which defies our expectation where more rooms/area gives rise to a higher price. In the earlier EDA, it was observed that the range of houses with 1 kitchen had a wider spread of sale prices and there were a lot more observations of houses with 1 kitchen. One way to improve the model predictions would be to drop this feature as there may be insufficient observations to allow the model to discern the impact on sale price. 



### Conclusion and Recommendations

From the above analysis it can be concluded that the ACT has been outperforming the SAT in terms of participation rates for the year of 2017 and 2018.  The ACT and SAT participation rates also mirror one another with each state choosing one over the other.  

States with consistent participation rates of 100% and high increase in participation rates are due to state policies and College Board should continue to pursue such partnerships to boost participation. 

The mean test scores for each state may not be representative of the education system and average aptitude of the students as the sample size of the participants that took each test by state may not be representative of that population. 

The College Board should consider Ohio as a potential state to increase participation as it is one of the top 5 states with the largest rate of change and room for growth. As Ohio currently requires public schools to give SAT or ACT to all juniors, there is a potential to pursue a partnership to boost participation rates. 