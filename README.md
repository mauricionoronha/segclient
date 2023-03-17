# Customer Segmentation
This project aims to develop an unsupervised Machine Learning model to group customers who visit a shopping mall into groups with similar characteristics, facilitating the creation of marketing campaigns for specific consumer groups.

The dataframe used was obtained from Kaggle:
https://www.kaggle.com/shwetabh123/mall-customers

The dataframe is composed of the following attributes:

* CustomerID: customer identification.
* Genre: gender.
* Age: age.
* Annual Income (k$): annual income.
* Spending Score (1 to 100): spending score.
The following is the order of treatment and creation of models using different clustering algorithms:

# 1º - Importing initial libraries and csv data
The first step is to import the Pandas and Numpy libraries and load the CSV file data into an initial dataframe simply named "df".

Note: The mall-customers.csv file was previously loaded onto Google Drive to facilitate access.

# 2º - Data visualization
Using the Plotly library, we can visualize the data in the form of interactive graphs. In this step, a histogram was used to visualize the age variation in the dataframe, as well as the gender distribution..

# 3º - Data exploration and treatment
In the treatment of data, unnecessary attributes such as CustomerID, which only enumerates customers in ascending order, were analyzed, not representing relevance for the model. Next, the names of the attributes (columns) were renamed to names that are easier to understand and identify null values (NAN), which fortunately did not exist in this dataframe.

Descriptive statistics were used to identify parameters such as mean, median, minimum and maximum values, and quartiles.

Finally, boxplot graphs were used to locate outliers, or discrepant data.

# 4º - Pre-processing
Pre-processing is a fundamental step that can improve the performance of analysis algorithms, through dimensionality reduction and elimination of noise that interferes with the functioning of the algorithms.

In this step, the CustomerID attribute was excluded and the categorical data of the gender attribute (Female, Male) was transformed into numerical data (0, 1).

In this step, data scaling was also performed, making data from different scales normalized to a uniform scale between attributes.

# Finally, clustering algorithms will be used:

# 5º - K-means
K-means is a clustering algorithm available in the Scikit-Learn library.

It is an unsupervised learning algorithm (meaning it does not require external confirmation inputs) that evaluates and clusters data based on their characteristics, such as:

* Stores/logistic centers
* Customers/similar products or services
* Customers/similar characteristics
* TV series/genre or age range
* Social media users/influencer users
* Patients/symptoms or similar characteristics

An important aspect of k-means is the correct configuration of the number of clusters we want to use.

The Elbow Curve or Method is a technique used to find the optimal number of clusters K. This method tests the variance of the data relative to the number of clusters. The ideal value of K is the one that has the lowest Within Sum of Squares (WSS) and at the same time the lowest number of clusters. We call it the elbow curve because from the point that would be the "elbow" there is not such a significant discrepancy in terms of variance. Thus, the best number of clusters K would be exactly where the elbow is.

After determining the optimal number of clusters, we create the training and clustering of the data.

The k-means algorithm in this model was used:

* With 2 attributes, allowing visualization through a scatter plot
* With all attributes
* Using PCA, reducing the dimensionality of the dataframe to 2 attributes created by the PCA algorithm

# 6º - Hierarchical Clustering (Agglomerative Hierarchical Clustering)
Hierarchical clustering analysis is an "unsupervised" method of recognizing "natural patterns" of behavior in samples based on multivariate data.

The technique's goal is to group samples (objects) based on their "closeness" (similarity), reducing the "dimensionality" of the data and allowing the visualization of multidimensional data through a two-dimensional graph called a dendrogram.

The Hierarchical algorithm in this model was used:

* With PCA to reduce the number of attributes, allowing visualization through a scatter plot
* With all attributes

# 7º - DBSCAN - Density-Based Spatial Clustering of Applications with Noise
DBSCAN, or Density-Based Spatial Clustering of Applications with Noise, is a non-parametric density-based clustering method proposed by ESTER et al (1996), which is significantly effective in identifying clusters of arbitrary shapes and different sizes, identifying and separating noise from data, and detecting "natural" clusters and their arrangements within the data space, without any prior information about the groups.

The method requires only one input parameter, but supports determining an appropriate value for it.

The DBSCAN algorithm in this model was used:

* With PCA to reduce the number of attributes, allowing visualization through a scatter plot.
It is possible to identify a considerable amount of noise (-1) in the creation of the PCA model.
* With all data

# 8º - Mean-Shift
Mean-Shift is a clustering technique that aims to infer the mean of clusters according to a density function, in which within a window of interest (range of data comprising the circle) calculates the area where there is higher density, and at that point the central point of the Mean-Shift is determined, and the window of interest is moved to this new central point.

This process is performed successively and only ends when the Mean-Shift is equal to the previous inference.

The Mean-Shift algorithm, in this model, was used:

* With PCA to reduce the number of attributes, allowing visualization through a scatter plot.
* With all attributes.

# 9º - K-PROTOTYPES
K-Means is one of the most used (if not the most used) clustering algorithms, which is not surprising. It is fast, has a robust implementation in sklearn, and is intuitively easy to understand.

K-Prototypes is a less well-known sibling, but offers an advantage of working with mixed data types. It measures the distance between numerical features using Euclidean distance (like K-Means), but also measures the distance between categorical features using the number of matching categories. Therefore, K-Prototypes works with both numerical and categorical data.

In this model, PCA was not used, and categorical data did not require treatment.

# 10º - And finally, a CSV file was created for each algorithm.
Some models showed better results such as scaled K-Means, DBSCAN with all attributes, and K-Prototypes using numerical and categorical data.

Here is the list of created files:

* df3 - K-means with 2 attributes (income and score)
* df4 - Scaled K-Means with all attributes
* df5 - K-Means with PCA reducing attributes to 2
* df6 - Hierarchical Clustering with PCA reducing attributes to 2
* df7 - Hierarchical Clustering with all attributes
* df8 - DBSCAN with PCA reducing attributes to 2
* df9 - DBSCAN with all attributes
* df10 - Mean-Shift with PCA reducing attributes to 2
* df11 - Mean-Shift with all attributes
* df_final - K-Prototypes using numerical and categorical data.
