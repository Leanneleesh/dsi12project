# Project  3: Web APIs & Classification

### Introduction

A leading online grocery platform aims to make use of trending topics on 2 subreddits, [r/Cooking](https://www.reddit.com/r/Cooking/) and [r/AskBaking](https://www.reddit.com/r/AskBaking/) in line with their upcoming marketing campaign to promote groceries and food items to consumers based on the trending topics. During their data collection, they mistakenly collected posts without identifying which subreddit the post originated from. My task would be to help them accurately classify the posts into the correct subreddits to eliminate the need to manually classify them.

Both subreddits are similar in the sense that the posts covers food items and recipes. I will be using Natural Language Processing (NLP) to train two classification models to correctly classify the Reddit posts.  

### Problem Statement 

Given a post from either r/Cooking and r/AskBaking, how can I correctly identify which subreddit is it from?

### About The Data

A total of 786 r/Cooking posts and 988 r/AskBaking posts were obtained from reddit to train the model. The title and selftext of each post were combined as a single feature for analysis. 

**Features Extracted from Reddit Posts****

| S/N  | Feature |            Description             |
| ---- | ------- | :--------------------------------: |
| 1    | title   |        Title of reddit post        |
| 2    | text    |         Text body of post          |
| 3    | name    |       Unique ID of each post       |
| 4    | author  |           Author of post           |
| 5    | target  | 1 for r/Cooking, 0 for r/AskBaking |

You may refer to my codes to take a look at the actual posts obtained. 

##### What was fixed?

1. Posts that were stuck onto the top of the subreddit thread were removed; this include the top 2 posts from r/AskBaking
2. After combining the title and selftext, there were no null observations 
3. The data was also checked for duplicate posts

### Modeling

##### General Approach: 

1. 2 models were used Logistic Regression, Multinomial Naive Bayes (NB)
2. Grid Search was performed to optimise the parameters for Count Vectorizer and applied on the Multinomial NB
3. Train-test-split was applied for model validation and selection

##### Metric Used to Validate Model:

Accuracy score was use as improperly classifying a subreddit post is equally bad in this case.

##### Outcome:

The final model was able to accurately classify 91.8% of the posts which serves as good start as the baseline accuracy was 55.6%. 

##### Observations:

<u>Similar Words in Both Subreddits</u>

- Words like 'recipe','make','would' and 'like' were common to both subreddits



### Conclusion & Recommendations 

- The current Multinomial NB model was able to accurately classify 91.8% of the posts according to the subreddit and hence the model can be deployed for use. Further work includes, deploying the model on more unseen posts to further validate its accuracy.
- To improve the accuracy of the predictions other models such as Random Forests Classifier, Ensemble Techniques can be explored. 
- In addition, during the EDA, we noticed that lemmetization did not reduce words to the similar root word. For example, 'make' and 'making' were both present in the word cloud and we may want to consider employ stemming during the pre-processing phase. 
- Lastly, when comparing the top 10 words for r/Cooking and r/AskBaking, similar words such as 'would', 'like', 'recipe' and 'make' appeared for both and it would be worthwhile excluding them as stopwords as they are unlikely to help in classification. Alternatively, the use of Tf-idf can also be considered for feature extraction to see if the model score improves.