# World Weather Analysis Challenge

Our challenge this week was to enhance the programming we created in the modules. Specifically, we created the programming for an app that would be called "PlanMyTrip" where users choose a range of temperatures they would like for their proposed vacation locations and the app suggests possible cities to travel to that fit the criteria.  We expanded that programming to include the current weather description in the results that are reported back to the user. There are three parts to the challenge this week:  retrieving weather data, creating a custom travel destinations map, and creating a travel itinerary map.

## Retrieve Weather Data

In the first part of the assignment, in a Jupyter notebook entitled Weather_Database.ipynb, we generated 2,000 sets of random longitude and latitude pairs. The the goal was to have around 670 possible travel locations, since 2/3 of the latitude/longitude pairs will end up over water since our planet is 1/3 land and 2/3 water.   Next, we used the citipy dependency to associate a city with each coordinate set that fell on the land. Our random coordinates resulted in 708 possible travel destination cities. After that, we queried the Open Weather API to capture current weather conditions for each of the cities we identified.  We put the data in a Pandas DataFrame and also saved it to an output CSV file, WeatherPY_database.csv, that will be used to draw all the potential travel destinations for our app in the next two parts of the challenge.

## Create a Customer Travel Destinations Map

In this part of the challenge, in a Jupyter notebook called Vacation_Search.ipynb, the user is prompted to enter a temperature range that they would like their destination cities to have.  The programming then uses this range to select a subset of the cities in the Weather_database.csv file and save it as a new Pandas DataFrame that contains only cities whose weather is in the desired temperature range.  We dropped any rows that have incomplete data. Then, we queried the Google maps API for hotels in each of the cities in our new, subset DataFrame.  If a hotel could be found, its name was added to the DataFrame, and otherwise the city was dropped from the data.  Finally, we used the Google maps API again to create a map of all cities that meet the temperature criteria and have a hotel, with markers that show the hotel name, city and country names, and current weather and maximum temperature. We output the possible cities for the user to a CSV file called WeatherPY_vacation.csv, and saved an image of the marker map under the file name WeatherPY_vacation_map.png.  Here's the map:

![all possible locations vacation map](https://github.com/mgsrichard/World_Weather_Analysis/blob/main/Vacation_Search/WeatherPY_vacation_map.png)



## Create a Travel Itinerary Map

Finally, in another Jupyter notebook named Vacation_Itinerary.ipynb, we chose four cities from our potential travel destinations csv file from the previous step, and created a sample itinerary for a trip.  The four cities I chose were in Uganda and are located around Lake Kyoga: Mayuge, Katakwi, Kitgum, and Gulu. We created a DataFrame for each city and used to_numpy() to extract the latitude and longitude of each of the four cities chosen. With the four coordinate sets, we called the Google maps API to create a driving map for our trip.   Lastly, we called the Google maps API to create another map showing the hotel names and current weather conditions for each of the 4 cities.  Here are the maps:
### Driving Map
![Driving Map](https://github.com/mgsrichard/World_Weather_Analysis/blob/main/Vacation_Itinerary/WeatherPy_travel_map.png)

### Map with Markers of Hotel/City information
![Hotel Marker Map](https://github.com/mgsrichard/World_Weather_Analysis/blob/main/Vacation_Itinerary/WeatherPy_travel_map_markers.png)
