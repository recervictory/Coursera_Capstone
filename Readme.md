<img src="https://i.ibb.co/NjSZDm5/kolkata-skyline-in-watercolor-background-pablo-romero.jpg" alt="kolkata"
	title="Kolkata" width = 1000/>

# Capstone Project - Kolkata - (The City of Joy) Restaurant Business Analysis
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

## Results and Discussion <a name="results"></a>
Using folium 144 pincodes used to map various location extracted from Zomato, Then the heatmap is created to view the crowded places in kolkata, after that I have used K-means Clustering algorithm from sklearn to cluster the places group by their location.

<img src="https://i.ibb.co/x79PqMR/Maps.png" alt="kolkata"
	title="Kolkata" width = 1000/>
    

The seven major areas are shown below:
<img src="https://i.ibb.co/kcSnCmY/kolkata-cluster-final.png" alt="kolkata"
	title="Kolkata" width = 1000/>


The result of Kolkata restaurants show most there are seven major clusters in the city with high popularity index. The following list are the most preferable location with high popularity index.

<table>
<thead>
<tr><th style="text-align: right;">  ClusterLabels</th><th style="text-align: right;">  popularity</th><th style="text-align: right;">  latitude</th><th style="text-align: right;">  longitude</th><th>top_areas                                                                                 </th></tr>
</thead>
<tbody>
<tr><td style="text-align: right;">              0</td><td style="text-align: right;">     4.986  </td><td style="text-align: right;">   22.5319</td><td style="text-align: right;">    88.3561</td><td>Ballygunge,Bhawanipur,Desapriya Park,Elgin,Park Circus Area                               </td></tr>
<tr><td style="text-align: right;">              1</td><td style="text-align: right;">     4.894  </td><td style="text-align: right;">   22.5932</td><td style="text-align: right;">    88.4134</td><td>Bangur,Lake Town,Sector 1, Salt Lake,Sector 3, Salt Lake,Sector 5, Salt Lake              </td></tr>
<tr><td style="text-align: right;">              2</td><td style="text-align: right;">     4.88286</td><td style="text-align: right;">   22.5628</td><td style="text-align: right;">    88.3558</td><td>Bow Bazar,Chowringhee,Dalhousie BBD Bagh,Entally,New Market Area,Park Street Area,Taltala </td></tr>
<tr><td style="text-align: right;">              3</td><td style="text-align: right;">     4.80714</td><td style="text-align: right;">   22.5012</td><td style="text-align: right;">    88.357 </td><td>Dhakuria,Golf Green,Jadavpur,New Alipore,Prince Anwar Shah Road,Southern Avenue,Tollygunge</td></tr>
<tr><td style="text-align: right;">              4</td><td style="text-align: right;">     4.596  </td><td style="text-align: right;">   22.5297</td><td style="text-align: right;">    88.3956</td><td>Kasba,Picnic Garden,Ruby Hospital Area,Tangra,Topsia                                      </td></tr>
<tr><td style="text-align: right;">              5</td><td style="text-align: right;">     4.615  </td><td style="text-align: right;">   22.6228</td><td style="text-align: right;">    88.4321</td><td>Baguihati,Kaikhali                                                                        </td></tr>
<tr><td style="text-align: right;">              6</td><td style="text-align: right;">     4.754  </td><td style="text-align: right;">   22.5869</td><td style="text-align: right;">    88.3755</td><td>College Street,Hatibagan,Kankurgachi,Maniktala,Shyam Bazar                                </td></tr>
</tbody>
</table>

Then location wise count used to find the numbers of restaurants each neighborhoods. The results show Behala has high numbers of restaurants 16. 
<img src="https://i.ibb.co/y6hKJMk/6.png" alt="kolkata"
	title="Kolkata" width = 1000/>
The results also show restaurants closer to kolkata's center points have higher rating than outskirts location, but also have exception like Barrackpore. 
<img src="https://i.ibb.co/Qjzy80F/78.png" alt="kolkata"
	title="Kolkata" width = 1000/>

Rating vs Average Cost for Two scatter plots show positive correlation between two. This indicates more expensive the restaurants are high rated. 


<img src="https://i.ibb.co/k3d43tr/7.png"  alt="kolkata"
	title="Kolkata" width = 1000/>

The Final results I provide customer a table of Location and Top 10 Service  and Cusine in that place are following:

<table>
<thead>
<tr><th style="text-align: right;">  </th><th style="text-align: right;">  ClusterLabels</th><th>subzone               </th><th style="text-align: right;">  latitude</th><th style="text-align: right;">  longitude</th><th style="text-align: right;">  popularity</th><th>1st Most Common Cusine  </th><th>2nd Most Common Cusine  </th><th>3rd Most Common Cusine  </th><th>4th Most Common Cusine  </th><th>5th Most Common Cusine  </th><th>6th Most Common Cusine  </th><th>7th Most Common Cusine  </th><th>8th Most Common Cusine  </th><th>9th Most Common Cusine  </th><th>10th Most Common Cusine  </th></tr>
</thead>
<tbody>
<tr><td style="text-align: right;"> 0</td><td style="text-align: right;">              5</td><td>Baguihati             </td><td style="text-align: right;">   22.6138</td><td style="text-align: right;">    88.4339</td><td style="text-align: right;">        4.57</td><td>Seafood                 </td><td>Chinese                 </td><td>North Indian            </td><td>Asian                   </td><td>Cantonese               </td><td>Cafe                    </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>Fast Food                </td></tr>
<tr><td style="text-align: right;"> 1</td><td style="text-align: right;">              0</td><td>Ballygunge            </td><td style="text-align: right;">   22.5313</td><td style="text-align: right;">    88.3661</td><td style="text-align: right;">        4.95</td><td>Chinese                 </td><td>North Indian            </td><td>Continental             </td><td>Bangladeshi             </td><td>Bengali                 </td><td>Mughlai                 </td><td>Momos                   </td><td>Fast Food               </td><td>Japanese                </td><td>Malaysian                </td></tr>
<tr><td style="text-align: right;"> 2</td><td style="text-align: right;">              1</td><td>Bangur                </td><td style="text-align: right;">   22.6111</td><td style="text-align: right;">    88.4091</td><td style="text-align: right;">        4.86</td><td>North Indian            </td><td>Biryani                 </td><td>Rolls                   </td><td>Mughlai                 </td><td>Cafe                    </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>Fast Food               </td><td>European                 </td></tr>
<tr><td style="text-align: right;"> 3</td><td style="text-align: right;">              0</td><td>Bhawanipur            </td><td style="text-align: right;">   22.5293</td><td style="text-align: right;">    88.3472</td><td style="text-align: right;">        4.98</td><td>Italian                 </td><td>Fast Food               </td><td>Beverages               </td><td>Continental             </td><td>Chinese                 </td><td>Cantonese               </td><td>Ice Cream               </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food              </td></tr>
<tr><td style="text-align: right;"> 4</td><td style="text-align: right;">              2</td><td>Dalhousie BBD Bagh    </td><td style="text-align: right;">   22.5736</td><td style="text-align: right;">    88.3483</td><td style="text-align: right;">        4.92</td><td>Bengali                 </td><td>Chinese                 </td><td>Vietnamese              </td><td>Cantonese               </td><td>Ice Cream               </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>Fast Food               </td><td>European                 </td></tr>
<tr><td style="text-align: right;"> 5</td><td style="text-align: right;">              3</td><td>Dhakuria              </td><td style="text-align: right;">   22.5075</td><td style="text-align: right;">    88.3727</td><td style="text-align: right;">        4.76</td><td>Cafe                    </td><td>Fast Food               </td><td>Cantonese               </td><td>Ice Cream               </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>European                </td><td>Desserts                </td><td>Continental              </td></tr>
<tr><td style="text-align: right;"> 6</td><td style="text-align: right;">              0</td><td>Elgin                 </td><td style="text-align: right;">   22.5378</td><td style="text-align: right;">    88.3515</td><td style="text-align: right;">        5   </td><td>Cafe                    </td><td>Desserts                </td><td>Italian                 </td><td>Awadhi                  </td><td>BBQ                     </td><td>Ice Cream               </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>Fast Food                </td></tr>
<tr><td style="text-align: right;"> 7</td><td style="text-align: right;">              2</td><td>Entally               </td><td style="text-align: right;">   22.5596</td><td style="text-align: right;">    88.3705</td><td style="text-align: right;">        4.5 </td><td>American                </td><td>Bengali                 </td><td>Fast Food               </td><td>Mughlai                 </td><td>Burger                  </td><td>Biryani                 </td><td>North Indian            </td><td>Bar Food                </td><td>Coffee                  </td><td>Healthy Food             </td></tr>
<tr><td style="text-align: right;"> 8</td><td style="text-align: right;">              6</td><td>Hatibagan             </td><td style="text-align: right;">   22.5891</td><td style="text-align: right;">    88.3688</td><td style="text-align: right;">        4.8 </td><td>Biryani                 </td><td>North Indian            </td><td>Fast Food               </td><td>Mughlai                 </td><td>Steak                   </td><td>Lebanese                </td><td>Rolls                   </td><td>Mishti                  </td><td>Burger                  </td><td>Cantonese                </td></tr>
<tr><td style="text-align: right;"> 9</td><td style="text-align: right;">              3</td><td>Jadavpur              </td><td style="text-align: right;">   22.4937</td><td style="text-align: right;">    88.3693</td><td style="text-align: right;">        4.84</td><td>Chinese                 </td><td>Tibetan                 </td><td>Momos                   </td><td>Thai                    </td><td>Asian                   </td><td>Bengali                 </td><td>Beverages               </td><td>Vietnamese              </td><td>Healthy Food            </td><td>Goan                     </td></tr>
<tr><td style="text-align: right;">10</td><td style="text-align: right;">              5</td><td>Kaikhali              </td><td style="text-align: right;">   22.6318</td><td style="text-align: right;">    88.4302</td><td style="text-align: right;">        4.66</td><td>North Indian            </td><td>Street Food             </td><td>Fast Food               </td><td>South Indian            </td><td>Desserts                </td><td>Mishti                  </td><td>Chinese                 </td><td>Cafe                    </td><td>Goan                    </td><td>Finger Food              </td></tr>
<tr><td style="text-align: right;">11</td><td style="text-align: right;">              6</td><td>Kankurgachi           </td><td style="text-align: right;">   22.5849</td><td style="text-align: right;">    88.3921</td><td style="text-align: right;">        4.87</td><td>Fast Food               </td><td>Chinese                 </td><td>North Indian            </td><td>Pizza                   </td><td>Mughlai                 </td><td>Beverages               </td><td>Mexican                 </td><td>Biryani                 </td><td>Italian                 </td><td>Bengali                  </td></tr>
<tr><td style="text-align: right;">12</td><td style="text-align: right;">              4</td><td>Kasba                 </td><td style="text-align: right;">   22.5132</td><td style="text-align: right;">    88.4018</td><td style="text-align: right;">        4.55</td><td>Bangladeshi             </td><td>Fast Food               </td><td>Bengali                 </td><td>Burger                  </td><td>Vietnamese              </td><td>Chinese                 </td><td>Ice Cream               </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food              </td></tr>
<tr><td style="text-align: right;">13</td><td style="text-align: right;">              1</td><td>Lake Town             </td><td style="text-align: right;">   22.6044</td><td style="text-align: right;">    88.4   </td><td style="text-align: right;">        4.92</td><td>Juices                  </td><td>South Indian            </td><td>Fast Food               </td><td>Desserts                </td><td>Chinese                 </td><td>Italian                 </td><td>Beverages               </td><td>North Indian            </td><td>Bar Food                </td><td>Bengali                  </td></tr>
<tr><td style="text-align: right;">14</td><td style="text-align: right;">              6</td><td>Maniktala             </td><td style="text-align: right;">   22.5775</td><td style="text-align: right;">    88.381 </td><td style="text-align: right;">        4.57</td><td>North Indian            </td><td>Chinese                 </td><td>Biryani                 </td><td>Cantonese               </td><td>Ice Cream               </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>Fast Food               </td><td>European                 </td></tr>
<tr><td style="text-align: right;">15</td><td style="text-align: right;">              3</td><td>New Alipore           </td><td style="text-align: right;">   22.5108</td><td style="text-align: right;">    88.3328</td><td style="text-align: right;">        4.58</td><td>Mughlai                 </td><td>Biryani                 </td><td>Mexican                 </td><td>Cafe                    </td><td>North Indian            </td><td>Rolls                   </td><td>Italian                 </td><td>Bakery                  </td><td>Bar Food                </td><td>Coffee                   </td></tr>
<tr><td style="text-align: right;">16</td><td style="text-align: right;">              2</td><td>New Market Area       </td><td style="text-align: right;">   22.5623</td><td style="text-align: right;">    88.3494</td><td style="text-align: right;">        5   </td><td>Mughlai                 </td><td>Salad                   </td><td>Biryani                 </td><td>Mexican                 </td><td>North Indian            </td><td>Beverages               </td><td>Rolls                   </td><td>Cafe                    </td><td>Spanish                 </td><td>Kebab                    </td></tr>
<tr><td style="text-align: right;">17</td><td style="text-align: right;">              0</td><td>Park Circus Area      </td><td style="text-align: right;">   22.5409</td><td style="text-align: right;">    88.3681</td><td style="text-align: right;">        5   </td><td>Biryani                 </td><td>North Indian            </td><td>Mughlai                 </td><td>Chinese                 </td><td>Bengali                 </td><td>Awadhi                  </td><td>Beverages               </td><td>Rolls                   </td><td>Healthy Food            </td><td>Goan                     </td></tr>
<tr><td style="text-align: right;">18</td><td style="text-align: right;">              2</td><td>Park Street Area      </td><td style="text-align: right;">   22.5535</td><td style="text-align: right;">    88.3566</td><td style="text-align: right;">        5   </td><td>North Indian            </td><td>Continental             </td><td>Chinese                 </td><td>Kebab                   </td><td>Mexican                 </td><td>American                </td><td>Biryani                 </td><td>Ice Cream               </td><td>Rolls                   </td><td>Mughlai                  </td></tr>
<tr><td style="text-align: right;">19</td><td style="text-align: right;">              4</td><td>Picnic Garden         </td><td style="text-align: right;">   22.528 </td><td style="text-align: right;">    88.3863</td><td style="text-align: right;">        4.77</td><td>North Indian            </td><td>Mughlai                 </td><td>Biryani                 </td><td>Chinese                 </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>Fast Food               </td><td>European                </td><td>Desserts                 </td></tr>
<tr><td style="text-align: right;">20</td><td style="text-align: right;">              3</td><td>Prince Anwar Shah Road</td><td style="text-align: right;">   22.5038</td><td style="text-align: right;">    88.3642</td><td style="text-align: right;">        5   </td><td>North Indian            </td><td>Continental             </td><td>Chinese                 </td><td>Biryani                 </td><td>Sandwich                </td><td>Fast Food               </td><td>Mughlai                 </td><td>Burger                  </td><td>American                </td><td>Bengali                  </td></tr>
<tr><td style="text-align: right;">21</td><td style="text-align: right;">              4</td><td>Ruby Hospital Area    </td><td style="text-align: right;">   22.5251</td><td style="text-align: right;">    88.4126</td><td style="text-align: right;">        4.58</td><td>Mughlai                 </td><td>North Indian            </td><td>Rolls                   </td><td>Biryani                 </td><td>Beverages               </td><td>Bengali                 </td><td>Fast Food               </td><td>Pizza                   </td><td>Italian                 </td><td>Bar Food                 </td></tr>
<tr><td style="text-align: right;">22</td><td style="text-align: right;">              1</td><td>Sector 1, Salt Lake   </td><td style="text-align: right;">   22.5925</td><td style="text-align: right;">    88.4127</td><td style="text-align: right;">        5   </td><td>Chinese                 </td><td>North Indian            </td><td>Continental             </td><td>Asian                   </td><td>Biryani                 </td><td>Beverages               </td><td>Mughlai                 </td><td>Tibetan                 </td><td>Kebab                   </td><td>Seafood                  </td></tr>
<tr><td style="text-align: right;">23</td><td style="text-align: right;">              1</td><td>Sector 3, Salt Lake   </td><td style="text-align: right;">   22.5761</td><td style="text-align: right;">    88.4148</td><td style="text-align: right;">        4.83</td><td>Healthy Food            </td><td>Fast Food               </td><td>Mexican                 </td><td>South Indian            </td><td>European                </td><td>Beverages               </td><td>Continental             </td><td>Italian                 </td><td>Vietnamese              </td><td>Chinese                  </td></tr>
<tr><td style="text-align: right;">24</td><td style="text-align: right;">              1</td><td>Sector 5, Salt Lake   </td><td style="text-align: right;">   22.5817</td><td style="text-align: right;">    88.4304</td><td style="text-align: right;">        4.86</td><td>North Indian            </td><td>Continental             </td><td>Chinese                 </td><td>Asian                   </td><td>American                </td><td>Bengali                 </td><td>Italian                 </td><td>Tibetan                 </td><td>Momos                   </td><td>Biryani                  </td></tr>
<tr><td style="text-align: right;">25</td><td style="text-align: right;">              6</td><td>Shyam Bazar           </td><td style="text-align: right;">   22.6004</td><td style="text-align: right;">    88.374 </td><td style="text-align: right;">        4.72</td><td>Mughlai                 </td><td>Kebab                   </td><td>Bengali                 </td><td>Mexican                 </td><td>Biryani                 </td><td>Rolls                   </td><td>North Indian            </td><td>Cafe                    </td><td>Chinese                 </td><td>Goan                     </td></tr>
<tr><td style="text-align: right;">26</td><td style="text-align: right;">              3</td><td>Southern Avenue       </td><td style="text-align: right;">   22.5107</td><td style="text-align: right;">    88.3495</td><td style="text-align: right;">        5   </td><td>Continental             </td><td>Chinese                 </td><td>Mughlai                 </td><td>Bengali                 </td><td>Italian                 </td><td>Tibetan                 </td><td>Kebab                   </td><td>Momos                   </td><td>Biryani                 </td><td>Goan                     </td></tr>
<tr><td style="text-align: right;">27</td><td style="text-align: right;">              2</td><td>Taltala               </td><td style="text-align: right;">   22.5641</td><td style="text-align: right;">    88.3584</td><td style="text-align: right;">        5   </td><td>Beverages               </td><td>Biryani                 </td><td>Rolls                   </td><td>Mughlai                 </td><td>Vietnamese              </td><td>Cantonese               </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>Fast Food                </td></tr>
<tr><td style="text-align: right;">28</td><td style="text-align: right;">              4</td><td>Tangra                </td><td style="text-align: right;">   22.5461</td><td style="text-align: right;">    88.3861</td><td style="text-align: right;">        4.52</td><td>Chinese                 </td><td>Vietnamese              </td><td>Cantonese               </td><td>Ice Cream               </td><td>Healthy Food            </td><td>Goan                    </td><td>Finger Food             </td><td>Fast Food               </td><td>European                </td><td>Desserts                 </td></tr>
<tr><td style="text-align: right;">29</td><td style="text-align: right;">              3</td><td>Tollygunge            </td><td style="text-align: right;">   22.4869</td><td style="text-align: right;">    88.3509</td><td style="text-align: right;">        4.65</td><td>Cafe                    </td><td>Beverages               </td><td>Fast Food               </td><td>Continental             </td><td>Chinese                 </td><td>Pizza                   </td><td>Biryani                 </td><td>Italian                 </td><td>Asian                   </td><td>Bengali                  </td></tr>
<tr><td style="text-align: right;">30</td><td style="text-align: right;">              4</td><td>Topsia                </td><td style="text-align: right;">   22.5359</td><td style="text-align: right;">    88.3914</td><td style="text-align: right;">        4.56</td><td>North Indian            </td><td>Italian                 </td><td>Chinese                 </td><td>Mughlai                 </td><td>Street Food             </td><td>Beverages               </td><td>Continental             </td><td>Biryani                 </td><td>Pizza                   </td><td>Rolls                    </td></tr>
</tbody>
</table>

The final figure show the rating and Location wise using scatter plot:
<img src="https://i.ibb.co/LJx3knw/8.png"  alt="kolkata"
	title="Kolkata" width = 1000/>

## Conclusion <a name="conclusion"></a>
Stakeholder happy to open a new restaurants in Ballygunge. They have chose to use top 10 service list from the above table. They also chose cusines from the table for the better services.
