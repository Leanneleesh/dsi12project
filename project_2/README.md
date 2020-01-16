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

##### <u>Cost per Square Foot</u>

Generalise the square foot of each property as sum of Tot Bsmt SF and Gr Liv Area to evaluate cost per sq ft. This feature is purely for visualization and will not be used as a predictor as the feature takes in Sale Price.

##### <u>No Remod</u>

Compares Year Built and Year Remod/Add to find the number of houses that were remodified. 

##### <u>Years Before Sale</u>

Number of years between YearBuilt and YrSold to determine age of house at time of sale.

##### <u>Total Porch SF</u>

The sum of Open Porch SF, Enclosed Porch, 3SsnPorch and Screen Porch 

##### <u>Total Baths</u>

The sum of Full Bath, Half Bath, Bsmt Full Bath, Bsmt Half Bath



### Modeling

##### General Approach: 

1. Run one round of modeling using Linear Regression, Lasso and Ridge
2. Lasso was used for further feature selection and fine-tuning, 2 other models were created using the Top 20 and Top 30 features for comparison 
3. Final regression model was created using the Top 20 features where the Top 5 features were squared
4. Train-test-split will be applied on train set for model validation and selection

##### Metrics Used to Validate Model:

1. Root Mean Square Error: this metric is used for evaluation on Kaggle 
2. R^2 Score of Model
3. Adjusted R^2 of Model to account for the number of parameter

##### Findings:

1. Lasso comes in handy as it was able to eliminate 50 out of 112 features

2. The top 20 features with the highest Lasso coefficients were picked 

3. Squaring of the top 5 features improved the performance of the model

4. There may be some sort of polynomial relationship between the top 5 features namely Gr Liv Area, Overall Qual, Total Bsmt SF, Neighborhood NridgHt and Exter Qual

   

### Kaggle Scores

| S/N  | Description                                                  | Public Score |
| ---- | ------------------------------------------------------------ | :----------: |
| 1    | Final Model  (Lasso: Top 20 Features where Top 5 were squared) |    26638     |
| 2    | Model (Ridge: Top 30 Features)                               |    27369     |
| 3    | Model (Lasso: Top 20 Features)                               |    38035     |
| 4    | Model (Ridge: 112 Features)                                  |    36061     |



### Conclusion & Recommendations 

1. The use of Lasso and Ridge performed better at the onset when there were too many features (100 over) which resulted in the Linear Regression Model overfitting 

2. Gr Liv Area stood out as the feature with the greatest weightage on sale price

3. As seen from the improvement in R^2 scores when the top 5 features were squared, it may be worth exploring polynomial features for other specific features to see if it improves the model

##### Recommendations: 

- Neighborhood seems to have a significant effect on sale price and can be studied in further detail
- Considering further combining similar features such as exter qual and  overall qual to form an overall quality score
- Exclude KitchenAbvGr as almost all of the houses have 1 kitchen and this may not be useful for the model to discern how this feature affects sale price. This is corroborated from the findings where the Lasso coefficient for this feature was negative

