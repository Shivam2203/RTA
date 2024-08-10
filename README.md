# Ramen-Rating-Analysis
An analysis on how ramens are rated by The Ramen Rater. <br>
Potential factors of positive Ramen ratings are identified. <br>
A complete walkthrough of the process can be found in each of the 4 notebooks.

## Dependencies / Prerequisites
These are the required libraries and frameworks to run the notebook and code.
```
pandas
numpy
matplotlib
seaborn
sklearn
```

## Dataset
Data is obtained from [The Ramen Rater - The Big List](https://www.theramenrater.com/resources-2/the-list/)

## Contents
1. Part I: Data collection and cleaning
2. Part II: Feature extraction, visualisation, and statistics
3. Part III: Feature engineering and data preparation
4. Part IV: Machine learning model training

## Part I: Data collection and cleaning
Cleaned dataset by removing unneccesary variables and ensuring that useful variables are in a consistent format.

## Part II: Feature extraction, visualisation, and statistics
Tokenised the Variety variable. <br>
Split flavors based on frequency:
- Spicy
- Chicken
- Beef
- Seafood

Visalised (bar graphs, histograms, count plots) trends:
- Brands
- Styles (Pack, Bowl, Cup, Tray, Others)
- Countries
- Stars (ratings)
- Flavors

Answered these questions:
1. Which brand has the highest stars? - find highest median using boxplot
2. Which country has the highest stars? - find highest median using boxplot
3. Which noodle has higher Stars - spicy or non-spicy? - check p-value of Mann-Whitneyu Test

## Part III: Feature engineering and data preparation
Split Brands into 30 distinct values + Others. <br>
Split Style into 4 distinct values + Others. <br>
Split Country into 10 distinct values + Others. - top 19% accounts for about 80% of dataset <br>
Used `get_dummies()` to convert catergorical variables into numerical values.

## Part IV: Machine learning model training
Establish the cut-off for a "good" rating. - above median <br>
Used `qcut()` to bin Star ratings. <br>

## Conclusion
| Model                    | F1 Score |
| ------------------------ | -------- |
| DummyClassifer           |  0.52    |
| <b>LogisticRegression<b>       |  <b>0.65<b>    |
| DecisionTreeClassifier   |  0.61    |
| RandomForestClassifier   |  0.62    |
  
The most important factors picked out by LogisticRegression model:
- MyKuali and Master Kong brands
- From Indonesia, Singapore, Taiwan and Malaysia
- Not served as a Pack, Bowl, Cup or Tray

The most detrimental factors picked out by LogisticRegression model:
- Ve Wong, Acecook and Ottogi brands
- From Thailand
