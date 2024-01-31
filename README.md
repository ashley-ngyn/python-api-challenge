# python-api-challenge

Instructions:
Part 1: WeatherPy
    - Requirement 1: Create Plots to Showcase the Relationship Between Weather Variables and Latitude
        - Latitude vs. Temperature
        - Latitude vs. Humidity
        - Latitude vs. Cloudiness
        - Latitude vs. Wind Speed
    - Requirement 2: Compute Linear Regression for Each Relationship
        - Northern Hemisphere: Temperature vs. Latitude
        - Southern Hemisphere: Temperature vs. Latitude
        - Northern Hemisphere: Humidity vs. Latitude
        - Southern Hemisphere: Humidity vs. Latitude
        - Northern Hemisphere: Cloudiness vs. Latitude
        - Southern Hemisphere: Cloudiness vs. Latitude
        - Northern Hemisphere: Wind Speed vs. Latitude
        - Southern Hemisphere: Wind Speed vs. Latitude
Part 2: VacationPy
    - Create a map that displays a point for every city in the city_data_df DataFrame
    - Narrow down the city_data_df DataFrame to find your ideal weather condition
    - Create a new DataFrame called hotel_df to store the city, country, coordinates, and humidity.
    - For each city, use the Geoapify API to find the first hotel located within 10,000 meters of your coordinates.
    - Add the hotel name and the country as additional information in the hover message for each city on the map


list of sources used:
- 01: https://openweathermap.org/current#data
- 02: https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.from_dict.html
- 03: https://docs.python.org/3/library/datetime.html
- 04: regression_solution
- 05: https://hvplot.holoviz.org/reference/geopandas/points.html
- 06: https://stackoverflow.com/questions/34682828/extracting-specific-selected-columns-to-new-dataframe-as-a-copy
- 07: https://apidocs.geoapify.com/docs/places/#categories
- 08: restaurants_solution
- 09: https://stackoverflow.com/questions/59678780/show-extra-columns-when-hovering-in-a-scatter-plot-with-hvplot
- 10: https://stackoverflow.com/questions/70994916/hvplot-points-with-geo-true-does-not-show-the-map
- 11: https://hvplot.holoviz.org/user_guide/Viewing.html

source 01 was used for the api url and the units=metric (WeatherPy)
    city_url = url + "appid=" + weather_api_key + "&q=" + city + "&units=metric"

source 02 was used for pd.DataFrame.from_dict to create a dataframe from a dictionary (WeatherPy)
    city_data_df = pd.DataFrame.from_dict(city_data)

source 03 was used for datetime.now(), formatting, and import (WeatherPy)
    from datetime import datetime
    date_now = datetime.now()
    date = date_now.strftime('%Y-%m-%d')

source 04 for linear regression functions (WeatherPy)
    (slope, intercept, rvalue, pvalue, stderr) = linregress(x_value, y_value)
    regress_values = x_value * slope + intercept
    line_eq = "y = " + str(round(slope,2)) + "x + " + str(round(intercept,2))

source 05 for hvpoints formatting (VacationPy)
    map_plot = city_data_df.hvplot.points(...)
    hotel_map_plot = hotel_df.hvplot.points(...)

source 06 to copy specific columns from one dataframe to another (VacationPy)
    hotel_df = ideal_weather_df[['City', 'Country', 'Lat', 'Lng', 'Humidity']].copy()

source 07 to look ar params/categories for geoapify (VacationPy)
    categories = 'accommodation.hotel'

source 08 to iterate through hotel_df and find hotels(VacationPy)
    for index, row in hotel_df.iterrows():
    ...
    name_address = name_address.json()

source 09 to create hover message on hvplot (VacationPy)
        (good to note that a learning assistant helped with the code)
    hover_cols = ["Hotel Name", "Country"]

source 10 to open hvplot in another broswer and save as html to view hover message (VacationPy)
    hvplot.show(hotel_map_plot)
    hvplot.save(hotel_map_plot, 'fig_vacation.html')