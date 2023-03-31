# Cryptocurrencies Analysis
## Overview 

### Concepts
Module 19 teaches us about unsupervised machine learning; there are two key differences from supervised machine learning:
* There are no paired inputs and outcomes.
* The model uses a whole dataset as input.
<br>

Unsupervised learning is often used in one of the following two ways:
* To transform the data to create an intuitive representation for analysis or to use in another machine learning model; or
* To cluster or determine patterns in a grouping of data, rather than to predict a classification.
<br>

### Steps
Preprocessing the raw cyptocurrency data <br>

Before an unsupervised machine process is started, it is always important to ensure that the input data is suitable for this analysis. Therefore, an initial analysis and cleanup of the raw data was performed.
1. The raw data, provided in a csv file was read into a Python pandas DataFrame, whose columns (features or variables) were reviwed along with determing the datatype of each column.
2. The file was checked for duplicate rows; there were none, but if there had been, duplicate data rows would be dropped. Each row represents a different cryocurrency. 
3. Cryptocurrencies not marked as 'trading' were dropped, because this analysis is designed to focus on cyptocurrencies that are currently being traded. Following this step, the column that marked whether a currency was being traded was removed as it is no longer needed.
4. Unnecessary columns for our chosen analysis such as the 'unnamed' column were also removed.
5. Columns with 1 or more missing or null values were removed so that data being used for computations has no missing or out of range values.
6. Because this analysis will focus and cryptocurrenies that are both being traded and also being mined, rows whose totalcoinsmined is not > 0 were dropped. 
7. The coinname column was dropped since it won't be used in the numeric analysis.
8. The Algorithm and ProofType columns with string values were converted to integer values using the 'getdummies()' method of DataFrame objects
9. The data at this point contained only columns (features/variables) with numeric values, but these could not be compared accurately since they were not all scaled the same. So a StandardScaler object from Python's sklearn.preprocessing library was used to rescale all variables to standardized normal distributions.
10. Finally, the preprocessing steps culminated in creation of a new clean data file to be used for Principal Component Analysis. 

Using Principal Component Analysis <br>
We use transformations when we need to take raw data and make it easier to understand. Transformations also can help prepare data so that it can be used for other machine learning algorithms. One method we used is Principle Component Analysis.

Clustering the remaining variables using K Means <br>
After transforming raw data into machine learning usuable format (standardized numeric values), we used K-Means Clustering to create visualizations of the data.

