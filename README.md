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

The clustering that was introduced in the previous section will rely on data to quantify the attractiveness of various Candadian cities from the perspective of new residents. Location and population data of the different Canadian cities can be found here: [[source]](https://simplemaps.com/data/ca-cities). The following data will be used together with the location and population data for the clustering. 

| **Attribute**                                   | **Data source**    | **Quantification method**                                                           |
|---------------------------------------------|----------------|------------------------------------------------------------------------------|
| Availability of work opportunities          | Foursquare API | Number of relevant companies within 30 km of city center.                    |
| Cost of living                              | Data scrapped from Numbeo [[source]](https://www.kaggle.com/debdutta/cost-of-living-index-by-country#Cost_of_living_index.csv)               | Use data as is.                                                              |
| Availability of restaurants and shops       | Foursquare API | Number of restaurants and shops within 30 km of city center.                 |
| Proximity to recreational outdoor locations | Foursquare API | Number of recreational outdoor locations within 60 km of city center.        |
| Remoteness of city                          | Foursquare API | Euclidean distance to predetermined major hubs (capital cities) or airports. |

The resulting cities within clusters would therefore be similar in these listed attributes and different clusters, on the other hand, will be different in terms of these attributes.

<!-- Possible sections: One of food, drinks, coffee, shops, arts, outdoors, sights, trending, nextVenues (venues frequently visited after a given venue), or topPicks -->

## Methodology Followed
Prior to building the models it is first required to perform exploratory data analysis. This section documents this process. 

## Analysis Results
This section presents the results of the models and presents some first-order insights. 

## Discussion and Synthesis
A synthesis of the results is presented in this section which includes practical insights and recommendations. 

## Conclusion
