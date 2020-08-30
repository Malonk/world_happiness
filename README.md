<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100"/>

# Data Thieves

*Group Paella*: 
    
    -Malon Kraaijvanger
    -Hannah Reber
    -Charlotte Velilla
    
  *28.08.2020*

*[DATA ANALYSIS 08-20 Cohort, Berlin]*

## Content
- [Project Description](#project-description)
- [Questions & Hypotheses](#questions-hypotheses)
- [Breakdown of steps](#breakdown-of-steps)
- [Dataset](#dataset)
- [Workflow](#workflow)
- [Organization](#organization)
- [Links](#links)
- [File Structure](#file-structure)


## Project Description

As part of the Data Analysis Boot camp, we are requested to work as a team to access data using: APIs, Web Scraping or direct download methods (CSV files). We have selected to access the data of the World Happiness Report via direct download (https://www.kaggle.com/unsdsn/world-happiness) and to access historical weather data from https://dev.meteostat.net/ via the API. As of obstacles encountered, a direct CSV download from https://www.ncdc.noaa.gov/cdo-web/datasets was later used. Then we have organized and "cleaned" this data according to our needs to try to understand if there's a correlation between the happiness ranking and weather conditions of selected countries. The project focuses more on the process of error facing and problem solving rather than arriving at conclusions.

## Questions & Hypotheses

The question with which the project is approached is the following: 

Are a country's weather conditions correlated to its happiness ranking?

Hypothesis is as follows:

    Since multiple factors are considered by the World Happiness Report like: levels of GDP, life expectancy, generosity, social support, freedom, and corruption. We assume the weather conditions are not a big influence for the highest Happiness rankings.


## Breakdown of steps

- Work with World Happiness report and understand the Data
- Check the available countries and end with a list of countries which are available for all 5 years
- Countries should all have a happiness rank and happiness score
- Narrow down the country list
- Merge the tables for the seperate countries to have all available data in one table
- Further clean the data
- Going through the API documents and understanding the requirements to request data
- Access the API with an API key to request specific weather data
- Add weather information to the table
- Analyse the effect of the weather (sunshine, wind, temperature) to the happiness ranking

## Dataset


### Dataset World Happiness Report = '2015.csv', '2016.csv', '2017.csv', '2018.csv', '2019.csv'-

https://www.kaggle.com/unsdsn/world-happiness

Description of Dataset: 

These are tables with the following shape: '2019.csv' = 156 rows x 9 columns, '2018.csv' = 156 rows × 9 columns, '2017.csv' = 155 rows × 12 columns, '2016.csv' = 157 rows × 13 columns and '2015.csv' = 158 rows × 12 columns.

The name of the columns range as follow: Country, Region, Happiness Rank, Happiness Score, Lower Confidence Interval, Upper Confidence Interval, Economy (GDP per Capita), Family, Health (Life Expectancy), Freedom,	Trust (Government Corruption), Generosity, Dystopia Residual

### Dataset: Meteostat

https://dev.meteostat.net: 

Description of Data set 'Finding Stations' part of the API: 

 API Data retrieving step one:

 The data to send requests for each country is structured as follows:

    id: weather station ID
    country
    region
    national
    wmo: wmo ID of the weather station
    icao: icao ID of the weather station
    iata: iata ID of the weather station
    latitude
    longitude
    elevation
    timezone
    active


 API Data retrieving step two:

 The data obtained when request was sent:

 if status of weather station = active:
 -Country: Latitude
 -Country: Long
 
  Description of Data set for 'Daily Data' part of the API: 

 The data obtained from the API request: 

     tavg: temperature average,
     tmin: temperature minimum,
     tmax: temperature maximum,
     prcp: precipitation,
     dsnd: number days with snow depth > (25.4 mm),
     wdir: wind direction,
     wspd: wind speed,
     wpgt: wind percentage,
     pres: pressure,
     tsun: daily total sunshine


### Data set: NCDC

https://www.ncdc.noaa.gov/cdo-web/datasets: 

 Description of Data set: CSV direct download

 The data obtained for the top 3 countries of the World Happiness Report on 2015, 2016, 2017, 2018 and 2019 was structured as follows:

     station: weather station id,
     name: name station + location,
     date: year,
     dsnd: number days with snow depth > (25.4 mm),
     dx32: days with temperature below,
     dx70: wind direction,
     dx90: wind speed,
     prcp: precipitation,
     tavg: temperature average,
     tmin: temperature minimum,
     tmax: temperature maximum


## Workflow

For more information and description of each step taken please see the Jupyter Notebooks included.

The following is a general overview of the structure: 

    Project Management and organization:  Malon Kraaijvanger
    Presentation: Malon Kraaijvanger [28.08.20]
    World Happiness Report Data Cleaning: Hannah Reber [26.08.20-28.08.20]
    API Request Meteostat: Malon Kraaijvanger[26.08.20-27.08.30] + Charlotte Velilla[27.08.20]
    NCDC Data Cleaning: Charlotte Velilla[28.08.20]
    ReadMe: Charlotte Velilla and Malon Kraaijvanger[26.08.20, 29.08.20]
    

## Organization

### General overview:

#### 26.08.20

Structuring and cleaning has started for all the CSV files from a timespan of 5 years from the World Happiness Report. Unifying all the data frames obtained from each CSV file in order to understand which countries are present throughout all dataframes and which of these countries have a high rank value. The documentation was read thoroughly on how to get data from the API in a JSON format from https://dev.meteostat.net and successfully managed to access the first step needed to retrieve the necessary data. Additionally, first function creation attempts were made to automate the process of retrieving the data on the second API call.


#### 27.08.20

The data obtained from the World Happiness Report was *cleaned*, filtered and prepared for final edits. In order to obtain the data from the Meteostat's API, requests were made efficiently through a series of *functions* attempts, *for loops*, *list comprehensions* and *functional strings*. As stated in the documentation, the latitude and longitude of the weather stations were obtained in order to send a second request for the data of each weather station. This process was needed for each of the countries obtained from the cleaning process of the WHR data set. The countries list was manipulated and matched through an automated conversion of Country:Capital in order to obtain the Capitals of the Countries evaluated by the WHR. By the end of this process and at the beginning of the second step for API data retrieval an obstacle was reached as the values obtained for latitude and longitude, for each weather station request, was different.


#### 28.08.20

Further changes and final edits were made to the dataframes of the World Happiness Report. The list of countries was updated, changes were made accordingly and had another look at the API to get historical weather information. A last minute turning point decision was made, the previous API extraction process was abandoned and documentation was extensively elaborated as for the process leading to it. In order to retrieve final weather information, CSV files were downloaded for the years 2015-2019 from another available source: https://www.ncdc.noaa.gov/cdo-web/datasets. This data was cleaned and partially prepared for further use and for the presentation on 28.09.20.  


## Links

https://www.kaggle.com/unsdsn/world-happiness

https://dev.meteostat.net/api/stations/daily

https://www.ncdc.noaa.gov/cdo-web/datasets

https://github.com/porimol/countryinfo (capital converter)


## File structure

The repository consists of the following files:

- main_happiness.ipynb: Data cleaning process of the World Happiness Report
- world_happiness_API_documented: Process of retrieving data through the API