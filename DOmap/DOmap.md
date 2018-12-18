**Predictive Map of Dissolved Oxygen Levels for the Chesapeake Bay**

- **Description:** A predictive map of Dissolved Oxygen Levels of the Chesapeake Bay

- **Project goal:** My project goal was to use past Chesapeake Bay water quality data to do a predicitve map of Dissolved Oxygen for the year of 2022, using a wheighted rate of change for the entirety of the Chesapeake Bay watershed.
---

**About:** 

At the time of this map making, there has been a cut of environmental restrictions and a de-funding of environmental regulatory bodies. This project was done to show the how the most recent water quality measurements in the Chesapeake Bay have affected the rate of change of dissolved oxygen. Dissolved oxygen was chosen as the measurement because it is a derivitive of many environmental inputs, such as thermal pollution and nutrient pollution, but other environmental measurements were debated as using for the basis of this analysis, such as total dissolved nitrate, total dissolved phosphate, turbidity.

An additional goal of this analysis was to map out areas that had a high rate of change and to look for patterns in change, such as an increase or decrease down stream of farmland, near high-income or low-income neighborhoods, across state borders, etc.

---

**Methodology** 

This analysis was created based on previous years of water quality data that came from The Chesapeake Bay Programs's (https://www.chesapeakebay.net/) water quality monitoring stations for the years of 2006, 2012, and 2017. The years of 2000 and 2018 were desired for a more true analysis, however the data for year 2000 does not cover a wide enough range to be acurate for the analysis, and the 2018 was not out at the time this analysis was made.

Data was selected for the 3 years by taking all dissolved oxygen measurements between the months of August and July for each year. Data was selected at this time to showcase the seasonal drop in dissolved oxygen levels due to an increase in temperature, so data is only accurate for the averaged change in those three months of for each year.

Dissolved oxygen values originally came in overlapping points for each measurement during the three months time span. Data was first converted to a *Albers North American Equal Area Conic* projection to utilize meters. Instead of taking an average between the months for each year, an IDW was created for each year. Then a hexagonal grid was created to take an average of the DO measurements within each year. The hexagonal grid was made 20,000 meters in diameter, to show a big enough area at the scale of the entire Chesapeake Bay watershed while still being able to differentiate areas of differing tributaries and cities.

Using *zonal statistics* an average of the DO measurement was taken from the IDWs for each year for each hexagon. After this the hexagonal grid was converted to a SpaiaLite Datbase in order to do a SQL query. The specific SQL query used is below.

![alt text](https://github.com/lexiejferry/lexiejferry.github.io/blob/master/DOmap/SQL.JPG "SQL")

This analysis was done using a rated rate of change for the three years, with a higher wheight on the 2012 and 2017 change. To do this, the entire rate of change was taken for 2006 and 2017, and then combined with the the rate of change between the years of 2012 and 2017, and then divided by two. This wheighted rate of change was then simply added to the 2017 data to create the prediction for 2022.A map for the wheighted rate of change was also created to show the rate of change in dissolved oxygen across the watershed

GeoDa was used to preform the spatial analysis. A Moran's I for the hexagonal wheighted rate of change map was used to look for spatial outliers. Both a significance and a cluster map were created. These maps acted to show the sharp transitions between areas

---

- **Results:** 

![alt text](https://github.com/lexiejferry/lexiejferry.github.io/blob/master/DOmap/DO_prediction.png "Dissolved Oxygen Map")

- **Software Used:** QGIS 3.2, Mircrosoft Excel (for the graphing and Correlation Equation)

- **Tools, Plugins, and Packages:** Spatialite Databases, SQL Query, Zonal Statistics, Clip, Extract/clip by extent, Raster Calculator, Join attributes by location, 2.5D Visualization

- **Data Sources:** Chesapeake Bay Foundation (https://www.chesapeakebay.net/)

Author: Lexie Ferry

Date Created:   2018-09-24T09:45:11-04:00

Email:  lexiejferry@gmail.com
