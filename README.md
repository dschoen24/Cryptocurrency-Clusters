# Cryptocurrency-Clusters

![Cryptocurrency Image2](https://user-images.githubusercontent.com/82673788/136615133-cc67a062-e7a0-47a2-8d22-9b667d5cb26b.jpg)

_____________________________________________________________________________________________________________________________________________________________________

## Background

A client from a prominent investment bank is interested in offering a new cryptocurrency investment portfolio for its customers.  The company has asked me to create a report that includes what cryptocurrencies are on the trading market and determine whether they can be grouped in order to create a classification system for this new investment.

___________________________________________________________________________________________________________________________________________________________________

### Preprocessing

I have been handed raw data and in order to create a classification system, I will be using unsupervised machine learning.

### Data Preparation

1. I read the data (crypto_data.csv) into Pandas.  This dataset was obtained from CryptoCompare.
2. I discarded all cryptocurrencies that were not being traded.
3. I them dropped the IsTrading column from the dataframe.
4. I removed all rows that had at least one null value.
5. I then filtered the dataset for cryptocurrencies that have been mined (any coins mined that are greater than zero).
6. I transposed the dataset into a numerical dataset so that a machine learning algorithm can be used.
7. The column "CoinName" was deleted from the original dataframe since it does not contribute to the analysis.
8. I then converted the remaining text values (Algorithm and ProofType) into numerical data using Pandas to create dummy variables.
    - Examining the Number of Rows & Columns in the dataset, the original dataset held 532 Rows & 4 Columns.  When turning the dataset into Numerical Values, the new dataset now holds the same 532 Rows but jumped to 98 Columns.
9. I then standardized the dataset so that any columns that contain larger values do not unduly influence the outcome.

_______________________________________________________________________________________________________________________________________________________________________

### Dimensionality Reduction

 - Creating dummy variables in the above data preparation dramatically increased the number of features in the dataset.  Because of this, I performed dimentionality reduction using PCA preserving 90% of the explained variance.

    - The above step resulted in a new dataframe (532 rows & 74 columns)

- I next further reduced the dataset dimentions using t-SNE which resulted in 532 rows and 2 columns
- I then created a Scatter Plot on the t-SNE output in order to observe whether there are disticnt clusters

![T-SNE Scatter Plot](https://user-images.githubusercontent.com/82673788/136614228-7a324de0-f56b-4113-9dc1-eef3ad7ee683.PNG)

#### Observation

From my observation of the Scatter Plot, there appears to be 3 distict clusters with a possibility of 4. 

### Cluster Analysis

- By using k-Means, I created an elbow curve plot to identify the best number of clusters.

![Elbow Curve](https://user-images.githubusercontent.com/82673788/136614736-c5890116-9d82-4311-a396-2daa3a84a9ff.PNG)

#### Observation

Elbow Curve showing at k-4 which means that there are 4 prominent clusters.

### Recommendation

Based on the above Elbow plot, we can see that the curve starts to level out (plateau) at K-4 giving us the assumption that there are in fact 4 prominent clusters.  The Scatter Plot is also in line with this assumption showing 4 clusters.  However, I also see a very small bend at k-5 so one would have to work off clustering with 4 as well as 5 to make an acurate analysis.  We might be able to see this a bit better with a 3-D Scatter plot rather than 2-D.  I would recommend a little bit more analysis will need to go into this but the cryptocurrency can be clustered togehter, it will just depend on if there will be 4 or 5 clusters to group together.



