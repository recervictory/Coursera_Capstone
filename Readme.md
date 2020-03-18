<img src="https://i.ibb.co/NjSZDm5/kolkata-skyline-in-watercolor-background-pablo-romero.jpg" alt="kolkata"
	title="Kolkata" width = 1000/>

# Capstone Project - Kolkata - (The City of Joy) Restaurant Business Analysis (Week 5)
### Applied Data Science Capstone by IBM/Coursera
### By Victor Banerjee


## Table of contents
* [Introduction: Business Problem](#introduction)
* [Data](#data)
* [Methodology](#methodology)
* [Analysis](#analysis)
* [Results and Discussion](#results)
* [Conclusion](#conclusion)


## Introduction: Business Problem <a name="introduction"></a>

In the project I tried to find an optimal location for a restaurant. The stakeholders is very new in the restaurant business so they are totally depends on my analysis to find a **optimal location**  to start new restaurant chain business.  

As **Kolkata,IN** is one of the four major cities in India the most part of the **Kolkata,IN** is crowded with multiple restaurants. As it is a 300 year old cities lots of types cuisine restaurant are predominant in Kolkata. My goal is to **provide few optimal options to the stakeholders to run a profitable business restaurant**.
I will try to find the optimal place with with following criteria :

    1. Less crowded with popular restaurants.
    2. Customer Rating Of the restaurant
    3. Possible cuisine for the restaurant
    4. Highly popular place in Kolkata 

In the final step I will try to find few promising areas in Kolkata meet the stakeholders criteria. Using **E**xploratory **D**ata **A**nalysis with provide summary of Kolkata restaurant business paradigm.

# Data <a name="data"></a>

By understanding our current business problem I have outline few factors that the decisions are:
* Popularity of the Place in Kolkata and distance from it
* Numbers of and distance to the Popular restaurant are in the neighborhood
* What types and kinds of cuisines available in the Kolkata restaurants
* Customers sentiments on restaurant business

To resolve the business problem following datasets are needed to extract/ generate data to summarize our prospective:
- Kolkata's pin codes Coordinates are extract from Google Search Page by BeutifulSoup Library
- FourSquare Api is used to generate neighborhood datasets
- Zomato Api is used to generate restaurants details datasets
- Zomato Api is used for generating Customers reviews datasets
- Kolkata Geojson File downloaded from GitHub Repo

~~~
#Python Library Used
from bs4 import BeautifulSoup #Web Scrapping
import numpy as np
from tabulate import tabulate
import json #library for Json file
from geopy.geocoders import Nominatim # Convert an address into latitude and longitude values
import folium # Map rendering library
~~~

## Methodology <a name="methodology"></a>
- I have used **BeautifulSoup** Kolkata's pincodes Coordinates scrap data from Google search page.
- There are no python codes available for extracting Zomato restaurants details, for I have created a **Object class for python to request Zomato Api**. 
- Data cleaning and EDA is done using Python Pandas and Numpy Library
- Folium Map used for displaying spatial location of the restaurants.
- NLP used for Review sentiment analysis