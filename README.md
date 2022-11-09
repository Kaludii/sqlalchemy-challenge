# Unit 10 Homework: Surf’s Up

### Part 1: Climate Analysis and Exploration

In this section, I used Python and SQLAlchemy to perform basic climate analysis and data exploration of the climate database.

#### Precipitation Analysis

To perform an analysis of precipitation in the area, the following was done:

* Found the most recent date in the dataset.

* Using this date, retrieved the previous 12 months of precipitation data by querying the 12 previous months of data.

* Selected only the `date` and `prcp` values.

* Loaded the query results into a Pandas DataFrame, and set the index to the date column.

* Sorted the DataFrame values by `date`.

* Ploted the results by using the DataFrame `plot` method.

* Used Pandas to print the summary statistics for the precipitation data.

![alt text](https://github.com/Kaludii/sqlalchemy-challenge/blob/main/Images/Precipitation%20analysis.png?raw=true)

#### Station Analysis

Performed an analysis of stations in the area:

* Designed a query to calculate the total number of stations in the dataset.

* Designed a query to find the most active stations (the stations with the most rows).

    * Listed the stations and observation counts in descending order.

    * Found which station id has the highest number of observations

    * Using the most active station id, calculated the lowest, highest, and average temperatures.

* Designd a query to retrieve the previous 12 months of temperature observation data (TOBS).

    * Filtered by the station with the highest number of observations.

    * Queried the previous 12 months of temperature observation data for this station.

    * Ploted the results as a histogram with `bins=12`.
    
![alt text](https://github.com/Kaludii/sqlalchemy-challenge/blob/main/Images/station-histogram.png?raw=true)    

### Part 2: Design Your Climate App

Designed a Flask API based on the queries that were just developed from above.

Used Flask to create the routes:

* `/`

    * Homepage.

    * Listed all available routes.

* `/api/v1.0/precipitation`

    * Converted the query results to a dictionary using `date` as the key and `prcp` as the value.

    * Returned the JSON representation of the dictionary.

* `/api/v1.0/stations`

    * Returned a JSON list of stations from the dataset.

* `/api/v1.0/tobs`

    * Queried the dates and temperature observations of the most active station for the previous year of data.

    * Returned a JSON list of temperature observations (TOBS) for the previous year.

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`

    * Returned a JSON list of the minimum temperature, the average temperature, and the maximum temperature for a given start or start-end range.

    * Calculated `TMIN`, `TAVG`, and `TMAX` for all dates greater than or equal to the start date when only given start date.

    * Calculated the `TMIN`, `TAVG`, and `TMAX` for dates from the start date through the end date (inclusive) when given both start and the end date.
