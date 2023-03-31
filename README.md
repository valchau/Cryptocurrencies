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
####Preprocessing the raw cyptocurrency data 
Before an unsupervised machine process is started, it is always important to ensure that the input data is suitable for this analysis. Therefore, an initial analysis and cleanup of the raw data was performed.
1. The raw data, provided in a csv file was read into a Python pandas DataFrame, whose columns (features or variables) were reviwed along with determing the datatype of each column.
2. The file was checked for duplicate rows; there were none, but if there had been, duplicate data rows would be dropped. Each row represents a different cryocurrency. 
3. Cryptocurrencies not marked as 'trading' were dropped 

#### We use transformations when we need to take raw data and make it easier to understand. Transformations also can help prepare data so that it can be used for other machine learning algorithms. One method we used is Principle Component Analysis.

#### After transforming raw data into machine learning usuable format (standardized numeric values), we used K-Means Clustering to create visualizations of the data.

