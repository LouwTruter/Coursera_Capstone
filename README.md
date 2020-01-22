# Coursera_Capstone
### ML Truter, January 2020
*Capstone project for IBM data science professional certificate on Coursera.* 

## Problem Introduction
This section will provide an introduction of the problem being solved and also introduce the most relevant target market. 

Canada has continually increased its immigration targets over the last few years. To illustrate, Canada plans for the arrival of 1.3 million new residents between 2018 and 2021. Deciding on where to put down their roots is one of the most significant decisions these residents will have to make. This forms the backdrop of this project. 

This projects will collate the data for different Candadian cities and cluster them in such a way as to provide decision-support to new permanent residents on where to stay. People have different value models for deciding where they would like to stay, the clustering will therefore provide structure to their search by grouping cities into similar clusters and different clusters will consist city groups that are distinct from each other. 

The model will assist new residents in the following way:
 1. New residents decide on how their ideal city should look like (establish their own value model).
 2. The different clusters are then evaluate for closeness to the user's value model and the most similar cluster selected.
 3. The user can then deep-dive into further analysing the cities in the cluster and make a decision of where to stay.
 
This process should provide structure their search and even provide some rare insights that would have not been identified with general Google searches. 

## Data Description
The data identification and understanding is described in this section. 

The clustering that was introduced in the previous section will rely on data to quantify the attractiveness of various Candadian cities from the perspective of new residents. Complete data was only obtainable for **24 of the largest Canadian cities**. Location and population data of the different Canadian cities can be found here: [[source]](https://simplemaps.com/data/ca-cities). The following data will be used together with the location and population data for the clustering. 

| **Attribute**                                   | **Data source**    | **Quantification method**                                                           |
|---------------------------------------------|----------------|------------------------------------------------------------------------------|
| Availability of work opportunities          | Foursquare API | Number of tech startups and corporate office amenities within 35 km of city center.                    |
| Cost of living                              | Data scrapped from Numbeo [[source]](https://www.kaggle.com/debdutta/cost-of-living-index-by-country#Cost_of_living_index.csv)               | Use data as is. Includes *Purchase Power Index* (PPI), rent index and cost of living index                                                              |
| Availability of restaurants and shops       | Foursquare API | Number of restaurants and shops within 30 km of city center.                 |
| Proximity to recreational outdoor locations | Foursquare API | Number of recreational outdoor locations within 30 km of city center.        |
| Remoteness of city                          | Foursquare API | Number of airport terminals within 60 km of city. |
| Availability of entertainment                         | Foursquare API | Number of bars, clubs within 7 km of city centre. |


The resulting cities within clusters would therefore be similar in these listed attributes whereas different clusters will be different in terms of these attributes.

<!-- Possible sections: One of food, drinks, coffee, shops, arts, outdoors, sights, trending, nextVenues (venues frequently visited after a given venue), or topPicks -->

## Methodology Followed
Prior to building the models it is first required to perform exploratory data analysis. This section documents this process. 

The purpose of this project is to serve as an exploratory analysis to identify cities that should be evaluated further; clustering is therefore the obvious solution. Since the dataset is relatively small (24 cities) k-means would not necessarily be suitable, after doing some research it was determined that **agglomerative, or additive clustering would be more suitable**.

Prior to the clustering three main questions needed to be answered:
1. What features to use, 
2. what attribute scaling/normalization to implement, and
3. how many clusters to group the cities in.

### Feature Selection
For clustering it is important that the features are as independent as possible in order to avoid "double counting" the importance of some features. If the data is high-dimensional (many attributes) it is common to employ dimensionality reductions techniques. For this project, there is less than 20 possible attributes so the selection could be done manually. 

In order to do the feature selection it is required to reevaluate the purpose of the clustering: To quantify the attractiveness of various cities. The attractiveness can be quantified through the following measures:

- Financial attractiveness (work opportunities, cost of living, salary purchasing power *etc.*)
- Leisure attractiveness (availability of outdoor activies and entertainment locations)
- Ease of living (proximity to airport terminals and work opportunities)

The attributes were therefore grouped into these 3 categories and qualitatively determined to be independent and exhaustive enough to capture the differences between cities for the purposes of this project. 

### Feature Engineering
The order of magnitude of the features differ by a lot, to illustrate, work opportunities are in the range 0--6, whereas rent index can be anywhere from 30--110. The different features needed to be scaled/normalized to ensure that the importance that they contribute to the eventual clusters are equal. 

The **selection scaling was Min-Max scaling since the data is not necessarily normally distributed** and to ensure that distance measures to contribute equally across all features. 

### Number of Clusters Selection
A Dendogram was used to determined the number of clusters for the Agglomotive clustering. 

![](https://github.com/LouwTruter/Coursera_Capstone/blob/master/Dendogram%20of%20cities.png?raw=true)

From this figure the relative closeness of the cities are indicated on the y-axis. For example, it can be seen that Vacouver is the closest city to Toronto, which is expected from the employed attributes - both are expensive cities and have a similar number of amenities. 

It was decided to use 5 clusters for the modelling. Although 2 clusters will maximize the intra-cluster distance, we still need to maintain a level of granularity to ensure that the insights can be valuable to the use *i.e.* we do not want too few clusters, since the value added would be less compared to having more clusters to choose from and, resultantly, less cities to evaluate further. 

## Analysis Results
This section presents the results of the models and presents some first-order insights. 

The excerpt below indicates the city clusters and provides a color map of the relative magnitude of the attributes. A description is also provided to synthesize the cluster groupings into meaningful insights. 
![](https://github.com/LouwTruter/Coursera_Capstone/blob/master/cluster_insights_screenshot.PNG?raw=true)

The next image shows how the clusters are positioned throughout Canada. It can be clearly seen that absolute city locations were not one of the decision attributes.
![](https://github.com/LouwTruter/Coursera_Capstone/blob/master/screenshot_city_clusters_map.PNG?raw=true)

In order to implement this system as a decision-support system it would be beneficial to establish the value model of the end-user *i.e.* what is the relative importance of the different attributes to him/her. This relative user importance should then serve as input to the feature engineering step in order to ensure that the eventual clustering takes the user's values into account. The new clusters will therefore be more valuable to this user. One possible method would be to use the *Analytical Hierarchy Method* (AHM) to elicit the user importance weights and then add these results to the modelling step. This is left for future work.  

## Conclusion
This project developed a data science approach in order to help a prospective new Canadian immigrant find a suitable city to settle down. The project was specifically tailored towards data science immigrants that like the outdoors. 
