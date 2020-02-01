# Coursera_Capstone
Coursera 'Applied Data Science Capstone' project

# 1. Introduction and Business Problem:

### The task:
Is it worth the city guests to spend money on rental housing in the city center, 
or can they save money and choose a different area of the city ?!

### To do this, i need to :
- find the right area for life with the most public places where you can spend time.
- cluster the districts of the city of Minsk by the uniqueness of places using the Foursquare API.

This data should help city guests to find areas and find the right place to stay.


# 2. Data section:
- Foursquare venues data - 4049;
- the distance from the center of each neighborhoods is 858 meters - 
this is half of the average distance between the centers of the neighborhoods 
which is calculated from their coordinates;
- number of neighborhoods - 122 - post offices of the city;
- coordinates of each post office - 122 - data collected using the 
Google GEO API and geopy library.


# 3.1 Work with data:
- 122 post offices were parsed from the html page using Beautifulsoup.
- See attached file - <a href="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/find_post_offices.ipynb" target="_blank">find_post_offices notebook</a>;
- <img src="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/imgs/zip_codes_minsk_list.png" alt="zip_codes_minsk_list">
- Using Foursquare API, 4049 points were collected, after filtering unnecessary data, 2187 points remained, which give 310 unique points (places).
- See attached file - <a href="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/minsk_venues.ipynb" target="_blank">minsk_venues notebook</a>;
- Duplicate data and noise points like [Trail, Bus Stop, Bus Station, Moving Target, Bus Line, Platform] were excluded;
- <img src="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/imgs/minsk_venues.png" alt="minsk_venues">
- I used the k-means clustering method, the number of clusters is 5;
- <img src="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/imgs/minsk_cluster.png" alt="minsk_venues">
- Each cluster contains the top 10 most common locations in the area;
- The number of elements in each cluster slightly changed, here are the limits of change:
    - cluster 1: 80 - 110;
    - cluster 2: 7 - 20;
    - cluster 3: 2 - 7;
    - cluster 4: up to 2;
    - cluster 5: up to 2.


# 4.1 Intermediate conclusions:
- The most popular places are:
    - Coffee Shop, Gym, Department Store, Food & Drink Shop;
- Unexpected result: before filtering, in the top 3 there was a 'Bus Stop' in each cluster! 
It is nice to confirm that public transport is very developed in the city!
- After many iterations, it turned out that fluctuations in cluster sizes are due to a small amount of data.
- It can be concluded that k-means clustering is not enough to solve the busies problem.

# 3.2 Work with additional data:
- I found a way to increase the amount of data I need. 
- <a href="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/Minsk_flats_data.ipynb" target="_blank">Minsk_flats_data notebook</a>.
- This is the price of apartments in different parts of the city.
- I parsed 21 pages of a some local site and found around 900 rental offers 
(everything was done purely for scientific purposes).
- The data was: the price of apartments, the number of rooms and their address.
- Using Google GEO API I found their coordinates.
- Also I created geojson for each district of the city with their names. 
Combined these names with apartment data.
- <img src="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/imgs/minsk_flats_dataframe.png" alt="minsk_flats_dataframe">
- I averaged the price of each apartment to the rental price as for a one-room apartment.
- This is how it looks on the map:
- <img src="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/imgs/minsk_avg_flat_price.png" alt="minsk_avg_flat_price">


# 4.2 Final results:
- <a href="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/Final%20result.ipynb" target="_blank">Final result notebook</a>
- <img src="https://github.com/Valentin-Golyonko/Coursera_Capstone/blob/master/blr/imgs/final_result.png" alt="final_result">
- Round colored dots - clusters with top 10 popular spots within a radius of 860 meters from them. 
- Blue lines - two metro (subway) lines.


The cluster with the largest number of venue points was distributed in the city center and along the metro lines.
 
As you can see, city guests can find _some_ places to stay not far from the city center with good apartments prices.

_The price indicated on the graphs and tables is the average price for one-room apartments per month!_
