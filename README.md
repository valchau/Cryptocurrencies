# Cryptocurrencies Analysis
## Overview 
This task's scenario tells us that I have an important investment bank as a client and this bank wants to offer a new cryptocurrency. Persoanlly, I would never suggest that anyone, especially a US bank, invest in such a thing because they are unregulated as well as not backed by any real assets such as gold or even a government. My MBA in Finance does not predict a good outcome for anyone who is not controlling such unregulated and non collateraized 'investments.' However, this task asks me to pretend that I am willing to work with such an scenario and provide a bank with advice relating to currently traded and mined cryptocurreinces. 

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
Preparing the raw cyptocurrency data <br>

Before an unsupervised machine process is started, it is always important to ensure that the input data is suitable for this analysis. Therefore, an initial analysis and cleanup of the raw data was performed.

Here is the data file at the start: 
<br>
<img src="https://github.com/valchau/Cryptocurrencies/blob/main/crytoDataAtStart.PNG" alt="data to start" width="500" height="500" >
<br>



1. The raw data, provided in a csv file was read into a Python pandas DataFrame, whose columns (features or variables) were reviwed along with determing the datatype of each column.
2. The file was checked for duplicate rows; there were none, but if there had been, duplicate data rows would be dropped. Each row represents a different cryocurrency. 
3. Cryptocurrencies not marked as 'trading' were dropped, because this analysis is designed to focus on cyptocurrencies that are currently being traded. Following this step, the column that marked whether a currency was being traded was removed as it is no longer needed.
4. Unnecessary columns for our chosen analysis such as the 'unnamed' column were also removed.
5. Columns with 1 or more missing or null values were removed so that data being used for computations has no missing or out of range values.
6. Because this analysis will focus and cryptocurrenies that are both being traded and also being mined, rows whose totalcoinsmined is not > 0 were dropped. 
7. The coinname column was dropped since it won't be used in the numeric analysis.
8. The Algorithm and ProofType columns with string values were converted to integer values using the 'getdummies()' method of DataFrame objects
9. The data at this point contained only columns (features/variables) with numeric values, but these could not be compared accurately since they were not all scaled the same. So a StandardScaler object from Python's sklearn.preprocessing library was used to rescale all variables to standardized normal distributions.
10. Finally, the preprocessing steps culminated in creation of a new clean data file to be used for Principal Component Analysis, containing only the numeric data values and column headings were saved in a separate DataFrame to be used later.

Using Principal Component Analysis <br>

We use transformations when we need to take raw data and make it easier to understand. Transformations also can help prepare data so that it can be used for other machine learning algorithms such as clustering. With a large number of variables, the data matrix may be too large to study and interpret properly. There would be too many pairwise correlations between the variables to consider. Graphical displays may also not be particularly helpful when the data set is very large.  

Thus, one way to interpret the data in a more meaningful way is to reduce the number of variables to a few linear combinations of the variables that each contain unique parts of the whole data. Each linear combination will correspond to a principal component in PCA. In this task, we were told to use 3 Principal Components. However, in many real world situation, the data analyst will need to try out different numbers of Principal Components in order to account for as much of the data's overall variance as the task requires. it isn't always 3. 

1. The first principal component is the linear combination of x-variables that has maximum variance (among all linear combinations).  This first Principal Component accounts for as much variation in the data as possible. 
2. The second principal component is the linear combination of x-variables that accounts for as much of the remaining variation as possible, with the constraint that the correlation between the first and second component is 0, i.e. they are mathematically orthogonal .
3. For our third component, again it is a linear combination of the given x-variables, but must be orthogonal mathematically to both the first and second principal components. In general: all principal components have this same property – they are linear combinations that account for as much of the remaining variation as possible and they are not correlated at all with the other principal components.
4. to achieve this PCA analysis with 3 principal components using Python, we create a PCA object from the sklearn.decomposition library and then invoke that object's fit_transform() method, passing in our data. 
5. Finally a new pandas DataFrame was created from this data, using the column headings PC 1, PC 2, PC 3, so that each of the cryptocurrencies in the DataFrame has its resulting data shown as a linear combination of the three principal components.


Clustering the remaining variables using K Means <br>

After transforming our many variables into 3 principal component variables, the sklearn.cluster object KMeans was used to create an interesting 3 dimensional visualization of the data. K-means clustering is one of the most used clustering algorithms in data science. To successfully implement the K-means algorithm, we need to identify the number of clusters we want to create using the K-means. 

One way to do this is called the elbow curve. This is a graphical representation of finding the optimal ‘K’ in K-means clustering for a set of data. It works by finding WCSS (Within-Cluster Sum of Square) i.e. the sum of the square distance between points in a cluster and the cluster centroid. The elbow curve shows WCSS values(on the y-axis) corresponding to the different values of K(on the x-axis). When we see a bend that looks like an elbow in the graph, we pick the K-value where the elbow gets created. We can call this point the elbow point since after this point in the graph, increasing the value of ‘K’ does not lead to a significant reduction in WCSS. Now, not all data will show a clear elbow bend, but this data does. 
1. An elbow curve was created to show that 3 principal components is likely to explain suffiently most of the variance
2. a KMeans object was created asking for 4 clusters, and its fit() method was used to fit the 3 PC data into its model and then
3. the KMeans object's predict() method was called so that it would predict the clusters of data for us
4. A new pandas DataFrame was created from the PCA resulting data, along with the Algorithm, Prooftype, TotalCoinsMined, TotalCoinsSupply and the prediction data.
5. This new DataFrame was then used to create a 3-Dimenional Scatterplot. 

Wrapping up<br>

1. the hvplot object from pandas was used to create a new table of the tradable crytopcurrencies and gives us the total tradable currencies as 532 from this data. 
2. Finally a simplifed DataFrame, consisting only of the cryptocurrency name, its TotalCoinsMined, TotalCoinsSupply, CoinName and prediction we created 
3. a ScatterPLot was made of this simple information to help the bank decide.

