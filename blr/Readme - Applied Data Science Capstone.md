# Introduction and Business Problem:

### The task:
Is it worth the city guests to spend money on rental housing in the city center, or can they save money and choose a different area of the city ?!

### To do this, you will need:
- Find the right area for life with the most public places where you can spend time.
- Cluster the districts of the city of Minsk by the uniqueness of places using the Foursquare API.

This data should help city guests to find areas and find the right place to stay.


# Data section:
- Foursquare venues data - 4049;
- the distance from the center of each neighborhoods is 858 meters - this is half of the average distance between the centers of the neighborhoods which is calculated from their coordinates;
- number of neighborhoods - 122 - post offices of the city;
- coordinates of each post office - 122 - data collected using the Google GEO API and geopy library.


# 