# Open a Successful Restaurant in Madrid Center

<p align="center">
  <img width="800" height="350" src="https://media-exp1.licdn.com/dms/image/C4D12AQFMkaf0Y6KKyA/article-cover_image-shrink_600_2000/0?e=1593648000&v=beta&t=Gbekq4ktLtGeh8Z40ZvYetFhR1Qcr9QksGhaECclLh0">
</p>


## 1. Introduction

### 1.1. Overview of the problem

The pandemy of coronavirus came strong and a consequence of it was the obligatory close of all restaurants from a bunch of different countries all around the world. Since the owners of many restaurants were small businessmen many of them are unable to keep paying their employees and keep their businesses up.

On the other hand, there are some with the hope of opening new restaurants but in places that have a lot more probabilities of being successful once life goes back to normal such as the ones nearby tourist attractions.

### 1.2. Goal

This project is based on that last statement and it's goal is to help businessmen and investors find ideal locations for opening different types of restaurant in the center of Madrid, nearby tourist attractions.

### 1.3. Data

* Foursquare API (https://api.foursquare.com)


## 2. Methodology

For the purpose of this project, as said before, I'll use the Foursquare API and by defining the geolocation of Madrid Center and functions that will provide dataframes that after a bit of cleaning and wrangling will give us data to proceed with unsupervised learning, by using the K-means algorithm.

The first step was to define the Madrid Center coordinates (lat=40.4165000, long=-3.7025600) so afterwards we could write a function to get a dataframe with the nearest venues, using the method explore available for venues provided by the foursquare’ api (https://api.foursquare.com/v2/venues/explore). I designed the limit as **500 venues** and the radius **1000 meters** from the Madrid Center coordinates. From all those venues categories we wanted to select only the tourist attractions like Art Museum, Monument/Landmark, Art Gallery, Church, Palace, Opera House, Theaters, Plazas. Below is displayed the dataframe with Venues name, category, latitude and longitude information.

<p align="center">
  <img width="450" height="450" src="https://media-exp1.licdn.com/dms/image/C4D12AQFQLrOIMf7utw/article-inline_image-shrink_1000_1488/0?e=1593648000&v=beta&t=fyqwk1a2onqVbio2hB85u4L4Dau6HZwPQQsNDHr-0u0">
</p>

There were in total **14 points of interest** located in Madrid Center: 6 Plazas, 2 Theaters, 2 Art Museum, 1 Monument, 1 Indie Movie Theater, 1 Movie Theater and 1 Historic Site.

The next step was to define a function that would give us the nearest venues located nearby all of those tourist attractions we just defined, in this case I used a radius of **500 meters**. We cleaned the resulting dataframe, since we only wanted the restaurant categories. The neighborhoods were the tourist points of interest to visit and the venues were each restaurant nearby the correspondent neighborhood.

The resulting dataframe had a total of **366 restaurants** in Madrid Center, which seems a lot but let’s remind that Madrid is an overpopulated city, receives a lot of tourist every week of the year and most importantly, it’s in the culture of spanish people eating out most days of the week.

<p align="center">
  <img width="850" height="150" src="https://media-exp1.licdn.com/dms/image/C4D12AQF0cz4vdrHB1g/article-inline_image-shrink_1000_1488/0?e=1593648000&v=beta&t=xvTukS7UCWeO28EzWTtHL2Fbq0NoUvMCFIUr7Ws8V0Q">
</p>

In this particular part of the project, it was important to take a look at a map and see how distributed were the restaurants around each tourist point. For that matter, I used **folium** library to visualize the geographic details: green points represent the restaurants, red points represent the tourist attractions and the blue point defines the Madrid Center.

<p align="center">
  <img width="750" height="450" src="https://media-exp1.licdn.com/dms/image/C4D12AQFz9a-Hgly7ig/article-inline_image-shrink_1000_1488/0?e=1593648000&v=beta&t=7Y4tzWgSq2stmZY9kgHkfGS40to6yYGy_Q7F6ZpqbFE">
</p>

On the other hand, it would be also interesting to have a clue of how many restaurants there were of each type in Spain’s Capital. Below, as expected, we can see that Spanish Restaurants and Tapas Restaurants (a kind of Spanish Restaurant) are the most frequent ones. The lowest frequent restaurants are the Greek and South American types, so here could be another opportunity of supporting those types of restaurants by opening a new one, this statement should be confirmed based on the choice options of the clients.

<p align="center">
  <img width="650" height="550" src="https://media-exp1.licdn.com/dms/image/C4D12AQFZxgWMysLAPA/article-inline_image-shrink_1000_1488/0?e=1593648000&v=beta&t=33brbI4C3aj0TkZZpPijIyZlEITV_62S1-EtolPpYx4">
</p>

In summary of this graph **14** unique categories were returned by Foursquare, then I created a table which shows a list of top 10 venue category for each tourist attraction, as seen in table’s below.

<p align="center">
  <img width="650" height="200" src="https://media-exp1.licdn.com/dms/image/C4D12AQH2x8zisznRzA/article-inline_image-shrink_1000_1488/0?e=1593648000&v=beta&t=SNABliq22lcLfWGcPMzoXcxfHPbiOzNZ_XAWh6MemJE">
</p>

The last step was to use one of the most common cluster method of unsupervised machine learning called **K-means algorithm** to create a different cluster for each tourist attraction to see which types of restaurant were more common nearby that exactly tourist point to see which types of restaurant were a good opportunity to open nearby that place.

This way we could help new investors that want to open new restaurants having a more knowledge were they should open each type of restaurant and where.

## 3. Results

For each cluster defined, a dataframe was obtained like the one seen bellow. Each dataframe had the name of the touristic point of interest and the **top 10 most common restaurants**.

<p align="center">
  <img width="650" height="200" src="https://media-exp1.licdn.com/dms/image/C4D12AQGtScCPUcytZg/article-inline_image-shrink_1000_1488/0?e=1593648000&v=beta&t=fVkqmMAcSIbOrntFKQBIziODx3OZfaeH570ajgfuBy8">
</p>

After concatenating all clusters dataframes, was observed that the 1st Most Common Venue in each cluster was **Spanish Restaurants** followed by **Tapas Restaurants** which is according with the first graphic which shows these two restaurants has been the most common ones in Madrid Center.


<p align="center">
  <img width="650" height="550" src="https://media-exp1.licdn.com/dms/image/C4D12AQHHiH9zCCCkEw/article-inline_image-shrink_1000_1488/0?e=1593648000&v=beta&t=gE_tBoYeASwxeUBG9ni7cuRYwt3XOoNLKgC49U9t0w8">
</p>

Based on the graphic, it’s clear to see that investing in a Spanish Restaurant in Madrid Center can be kind of adventurous since it’s the most common type of restaurant nearby all of the tourist attractions.

We can also see a clustered map with the most important tourist attractions in Madrid Center and which ones shares the most common types of restaurants. For example, cluster 1 (Teatro de La Zarzuela) and cluster 13 (Plaza de Santa Ana) share 90% of the same first 10 most common restaurants, that’s why both have color red. Almost the same happens with cluster 6 (Plaza de la Villa) and cluster 7 (Teatro de la Comedia) that share 80% of the same first 10 most common restaurants, both have similar green color.

<p align="center">
  <img width="750" height="450" src="https://media-exp1.licdn.com/dms/image/C4D12AQEFWgIMlPfabw/article-inline_image-shrink_1000_1488/0?e=1593648000&v=beta&t=51uos6RJDIKHyY-ZBkZXu1Nl1cOtGvkepgK_9CP9nHY">
</p>

For cluster 1, which corresponded to "Teatro de La Zarzuela", it’s possible to report that there aren't any mexican, american, greek, japonese or vegetarian/vegan restaurants. For cluster 2, which corresponded to "Plaza Mayor", it’s possible to report that there aren't any mediterranean, seafood, greek, japonese or vegetarian/vegan restaurants. For cluster 3, which corresponded to "Plaza de Antón Martin", it’s possible to report that there aren't any mexican, american, greek, japonese or vegetarian/vegan restaurants. For cluster 4, which corresponded to "Plaza del Callao", it’s possible to report that there aren't any argentinian, greek, japonese, american or vegetarian/vegan restaurants. For cluster 5, which corresponded to "Plaza de Isabel II", it’s possible to report that there aren't any mediterranean, argentinian, greek, japonese, american, vegetarian/vegan or peruvian restaurants. For cluster 6, which corresponded to "Plaza de la Villa", it’s possible to report that there aren't any mediterranean, asian or peruvian restaurants. For cluster 7, which corresponded to "Teatro de la Comedia", it’s possible to report that there aren't any asian, american, vegetarian/vegan or peruvian restaurants. For cluster 8, which corresponded to "Puerta del Sol", it’s possible to report that there aren't any japonese, greek, american, mediterranean or vegetarian/vegan restaurants. For cluster 9, which corresponded to "Cine Doré", it’s possible to report that there aren't any greek, vegetarian/vegan, american restaurants. For cluster 10, which corresponded to "Museo Thyssen-Bornemisza", it’s possible to report that there aren't any american, greek, vegetarian/vegan or peruvian restaurants. For cluster 11, which corresponded to "Sala Equis", it’s possible to report that there aren't any japonese, greek or argentinian restaurants. For cluster 12, which corresponded to "Palacio de Gaviria", it’s possible to report that there aren't any mediterranean, vegetarian/vegan, Greek, japonese or peruvian restaurants. For cluster 13, which corresponded to "Círculo de Bellas Artes", it’s possible to report that there aren't any vegetarian/vegan, American restaurants. For cluster 14, which corresponded to "Plaza de Santa Ana", it’s possible to report that there aren't any American, vegetarian/vegan, Japonese or Peruvian restaurants.


## 4. Discussion

From the **14 categories of restaurants** nearby the tourist attractions, the top 2 most common ones are Spanish and Tapas Restaurants. In that case, these two types of restaurants shouldn't be the chosen ones from the investors to open right after the coronavirus pandemic gets over, because even though Madrid is an overpopulated city, if we want the restaurant to be succeed we don’t want to come up with something common or ordinary, sometimes being distinct and creative can be the key to success. In that matter, it’s also important to know the preferences of the clients, maybe there aren’t a lot of Greek restaurants in Madrid Center because it’s not something that most of Spanish people enjoy eating. That way, it’s crucial to join the results from this study with their opinion to have a result more accurate.

On the other hand, with this project we can also get knowledge of **which types of restaurants are missing in which areas** and nearby each tourist points of interest, as described in the last paragraph of results, and this is the most important information that can be given to businessmen and let them decide which type of restaurant are they interested in opening and where.

I ended the study by visualizing the data and clustering information on the Madrid Center map that showed how similar some places where in the type of restaurants that they shared.


## 5. Conclusion

As a result of the coronavirus pandemic with most establishments closed, restaurants are one of those establishments that were really affected. On that note, the purpose of this project was to help businessmen which had to close down their restaurants due to lack of funding on paying their employees but still have some savings and want to find new solutions.

The solutions provided were to guide them on where was the ideal place to open a restaurant and which type of restaurant should they open in which location.

To the future,

Ana Santos
