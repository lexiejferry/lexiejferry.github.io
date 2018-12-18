**Predictive Map of Dissolved Oxygen Levels for the Chesapeake Bay**

**Description:** A predictive map of Dissolved Oxygen Levels of the Chesapeake Bay

**Project goal:** My project goal was to use past Chesapeake Bay water quality data to do a predicitve map of Dissolved Oxygen for the year of 2022, using a wheighted rate of change for the entirety of the Chesapeake Bay watershed.

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

**Results:** 

![alt text](https://github.com/lexiejferry/lexiejferry.github.io/blob/master/DOmap/DO_Prediction.png "Dissolved Oxygen Map")

This map shows the results of the 2022 dissolved oxygen prediction map. No area indicates a dissolved oxygen of less than one, indicating that no areas in the predicted map will have DO levels that completely kill all aquatic life. However, there are many areas that show DO levels that will cause the death of fish (but not benthic species like oysters), particularly in the Washington-Baltimore area, the mid-Potomac River, the western mouth of the Bay, and also in New York state and along the Susquehanna River near the Maryland-Pennslyvania border. Other areas of interest include the high DO levels around western Maryland and near Richmond Virginia. Additionally, most of the Chesapeake watershed falls into a grade of around 4.0 to 7.0 mg/L, indicating levels where fish are stressed but not harmed.

The healthy DO levels in western Maryland could be indicative of the spring fed small streams the run along the Appalachins. In the Richmond area, the DO rises somewhat anomalusly. This area would be indicative of the James River, alonge which many agricultural areas can be found. While this river has historically been polluted, this extreme postive DO may reflect recent changes that the city of Richmond and state of Vigrinia have made to improve water quality, but not enough information can be gathered from this map alone to know for sure.

The lower DO near the DC-Baltimore area is indicative of the effects of urbanization and city spaces. In the Susquehanna River, it could indicate an area downstream of farmland that experiences nutrient pollution, and therefore algeal blooms and lower DO levels. This patern is repeated again along the New York State and Pennsylvania border, an area rich in farmland.

![alt text](https://github.com/lexiejferry/lexiejferry.github.io/blob/master/DOmap/wheighted_change.png "Weighted Rate of Change Map")

This map shows the rate of change of dissolved oxygen for the selected years of analysis. This map shows that DO is changing most rapidly in western Maryland (in the postive direction) and in the southern Virginia area. This shows a clear distinction between state lines as Maryland is experiencing mostly small positve change while Virgina is experiencing negative change, especially along its southern watershed border.

This postive change in Maryland may be due to a number of factors; the involovement of educational outreach programs on children that are now coming into adulthood, an increased understanding about the Bay's health problems, the effect continued environmental regulations. The negative change in Virginia may be attributed to state wide environmental regulation changes in the wake of new administration, and near Richmond this could be a sign of nutrients collecting and travelling downstream as the change in DO increases from the western watershed border to the eastern mouth of the Chesapeake.

![alt text](https://github.com/lexiejferry/lexiejferry.github.io/blob/master/DOmap/cluster.JPG "GeoDa Cluster Map")

![alt text](https://github.com/lexiejferry/lexiejferry.github.io/blob/master/DOmap/significance.JPG "GeoDa Significance Map")

This map shows the results of the spatial coorelation mapping done in GeoDa. In this map, 'High' indicates an area that experiences positive change in DO, while 'Low' indicates a decrease in DO. GeoDa confirms that the area in western Maryland is a spatial outlier, and that the area in southern Pennsylvania is also an outlier. It also highlights the area near the mouth of the Bay that is experiencing positive change even though it is surrounded by negative change. Additionally, There is an area in mid- Pennsylvania that is experiencing a higher rate of change than the surrounding area. This area is covered in protected forests and farmlands and is around the border of the Appalachins. This could be because of an increase in riparian buffers, as farms in this area appear to have aa average of 1000 meters of riparian buffer before reaching the stream (according to satelite imagery from Google Maps), however more information would be needed to discern the true reason for this outlier.

---

**Software Used:** QGIS 3.3, GeoDa, ArcMap

**Tools, Plugins, and Packages Used:** Spatialite Databases, SQL Query, Zonal Statistics, IDW Interpolation, Hexagonal Grids, 2.5D Visualization

**Data Sources:**

- Water Quality Measurements: Chesapeake Bay Foundation (https://www.chesapeakebay.net/)

- Dissolved Oxygen Health Levels: Fondriest (https://www.fondriest.com/environmental-measurements/parameters/water-quality/dissolved-oxygen/)

Author: Lexie Ferry

Date Created:   2018-12

Email:  lexiejferry@gmail.com
