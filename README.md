# project-Kastomaa
a project creating a customer segmentation to cluster wholesale customers with the aim of identifying effective business actions to promote the products.

here is a link to the dataset: https://raw.githubusercontent.com/sik-flow/new_data1/refs/heads/main/Wholesale%20customers%20data.csv

The dataset contains information on wholesale customers buying milk, groceries, fresh products, frozen products, detergents and delicassen. The customers are also grouped in regions and the channel they used to purchase the products.
The regions are either 1, 2, or 3, while the channels are either 1 or 2.

I first explored the dataset for cleaning and any data wrangling required, checking for null values, and the details of the columns.
I was interested with the relationship between the products and the region, as I thought the region column could be an interesting target variable. The Channel column seemed interesting at first, but I figured the choice of mode of payment may not be of high concern of we are looking at promoting sales. This was also because there did not seem to be much of a difference between the two channels anyway.

I decided to make the product columns my columns of interest to create clusters among the customers.

With the columns of interest identified and a new dataframe with them defined, I scaled the data, and instantilized a  KMeans algorithm to cluster the new dataset. 

I then used the elbow plot, silhouette score and PCA plot to determine the best value of k to create meaningful and stable clusters. I tried using tSNE, but the plot did not seem to explain much of how the dataset had been clustered.

I also used a great visualization code from The scikit-learn developers, SPDX-License-Identifier: BSD-3-Clause, to plot out the various outputs when different k values are considered in clustering the dataset from the columns of interest.

From all these metrics, I identified the k value of 5 as the best value, mostly because it captured the outlying data points well.

Adding a clusters column to the original dataset justified my choice for the k value, as the clusters explained the customers pretty well. The customers are grouped in clusters 0, 1, 2, 3, and 4. 

I then evaluated each cluster for stability and meaningfulness, and observed the relationship between each column of interest and the clusters. I also created a new column having the total number of products each customer purchased. This was really helpful in creating summary statistics and visualizations that helped explain how each cluster differs from another.


CONCLUSION

Looking at the relationships between the Clusters and the products, we can see that cluster 4 has generally has the highest number of purchases at averagely 158,280, followed by cluster 2 with an average 128,332 purchases. These two clusters have a very high number of purchases compared to the rest(the next cluster, 1, has less than 50% of the purchases cluster 2 has), which explains why they are the outliers in the PCA plot. The two clusters also have the lowest number of customers (11 and 2 for Cluster 2 and 4) respectively. 

However, while cluster 2 has relatively high number of purchases in all the products, highest in Milk, Grocery and Detergents_Paper, cluster 4 has high purchases in all products except Detergents_Paper. It has the lowest purchases for Detergents_Paper.

Cluster 1, has the third highest average number of purchases, 55,572. It is generally mid-level in the purchases of each product but second-highest in purchasing Fresh and Frozen products.

The fourth highest average number of purchases are made by cluster 0, with 42,821 purchases. This cluster have generally low purchases in most of the products except for Detergents_Paper, in which the cluster had the second most purchases.

Cluster 3, the cluster with the most number of customers, has the lowest average number of purchases, and generally low purchases all through the products.


SUGGESTIONS

One way to improve sales would be to advertise more the products to customers in clusters 3 and 0. This would help increase the purchases of the products from these clusters.

We can also introduce an offer for Detergents_Paper, targeting the high purchasing Cluster 4 who had the lowest purchases of the product.
