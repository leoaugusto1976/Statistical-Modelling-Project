# Final Project: Statistical Modelling with Python

## Objective
The objective of this project is to select bike stations from a city using the City Bikes API. For each station, based on its latitude and longitude, we send requests to both Foursquare and Yelp APIs. With the data collected, we aim to apply Linear Regression to determine the correlation between the number of bikes at a station and the rating of nearby places.

## Project Goals
For this project, we have chosen Greenville city in South Carolina and collected data from 13 stations. We sent these 13 stations to Foursquare and Yelp to retrieve the following information for each station:
- ID
- Name
- Address
- Rating
- Price
- Phone
- Distance
- Latitude
- Longitude

After collecting, cleaning, exploring, and saving the database, we applied Linear Regression to a total of 118 places. All data has been stored in the project's data folder.

The code for this project is saved in the notebook folder, and Python was used for coding.

## References
- [City Bikes API](http://api.citybik.es/v2/)
- [Yelp API Documentation](https://docs.developer.yelp.com/reference)
- [Foursquare API](https://location.foursquare.com/developer/reference/api-overview)


## Process

### Retrieving the Greenville's Stations from City Bikes API
The City Bikes API is freely accessible without the need for an API key or authentication. By simply providing the city name, we obtain the city's ID and retrieve information about its bike stations. The resulting data has been saved in the `stations.csv` file.

**Code:** `city_bikes.ipynb`

### Collecting Information from Foursquare and Yelp APIs
We established the following criteria for our search:
- Query: "restaurant"
- Radius: 1000 meters

We iterated through the stations, sending their respective latitude and longitude coordinates to the APIs, applying the specified filters.

### Data Cleaning
For data obtained from Foursquare, we implemented the following cleaning techniques:
- Removal of rows with duplicate latitude and longitude entries
- Elimination of rows with missing values in the price, distance, or rating columns

For data retrieved from Yelp, our data cleaning process included these steps:
- Removal of rows with duplicate latitude and longitude entries
- Elimination of rows with missing values in the price, distance, or rating columns
- Conversion of data types:
    - Price:
        - Yelp uses values like $, $$, $$$, and $$$$.
        - Foursquare employs numerical values from 1 to 4.
        - To align the data, we reclassified Yelp's price symbols into numerical equivalents used by Foursquare.
    - Rating:
        - Yelp's rating ranges from 1 to 5.
        - Foursquare's rating spans from 0.0 to 10.0.
        - To facilitate comparison, we reclassified Yelp ratings to the same 1 to 10 scale as Foursquare.

The code for data collection and cleaning can be found in the `yelp_foursquare_EDA.ipynb` notebook.


## Visualization
To visualize the results, I combined the data into one dataframe and plotted it on a map. Foursquare places are denoted in blue, while Yelp places are marked in green. Additionally, for comparison purposes, I created bar graphs that illustrate the number of places retrieved from each API.

## Modeling
At this stage, I successfully gathered the data and applied Linear Regression. The primary goal was to assess the correlation between the number of bikes and the rating.

## Results
I was able to apply Linear Regression to a total of 118 places, with Yelp contributing 90 places and Foursquare contributing 28 places. The abundance of data from Yelp allowed for robust statistical analysis. The results were promising, indicating a strong and significant correlation between the number of bikes and the rating.

## Challenges
Several challenges were encountered during this project. Initially, I had to familiarize myself with each API, starting with City Bikes. Although City Bikes is user-friendly, my initial encounter was slightly confusing because it's common to require an API key for public APIs. I later realized that City Bikes did not require such authentication.

Yelp and Foursquare, on the other hand, offered good documentation and the convenience of API keys. This enabled me to test and compare results directly on their respective documentation websites. Consequently, I could discern the differences between each API and determine the best approach for data cleaning and standardization. Visualization played a crucial role in comparing the results.

Ultimately, Linear Regression provided valuable insights by confirming the correlation between the number of bikes and the rating.

## Future Goals
Given more time, I would explore additional correlations between variables such as price and distance, price and rating, and the number of bikes and price. While I conducted a Linear Regression analysis, I could further investigate these relationships using Multivariate Linear Regression to test various scenarios.