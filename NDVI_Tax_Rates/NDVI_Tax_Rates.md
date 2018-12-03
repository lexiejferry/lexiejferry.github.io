# NDVI Tax Rates

**A Comarision of Vegetation Presence to State Tax rates in Baltimore City**

- **Project goal:** My project goal was to see if there is a correlation between vegetation intensity and average state tax rates in Baltimore City.

- **About:** For this project, I made an NDVI from freely availible Landsat 8 images. I gathered Baltimore City census data for the year of 2017 and made a hexagonal grid of 350m by 350m (approximately the size of 3 city blocks) to cover the entirety of the census data. I then extracted the average NDVI and State Tax information using a combination of SQL query and Zonal Statistics. Data was then reclassified for viewing and displayed on a 2.5D Map. All data was converted to a North American Albers Equal Area Conic projection before processing, as this allowed the final product to be consistent in projections and have a visualy appealing tilt. Landsat Data used was taken in June of 2017 to maximize vegetation intensity and to allow consistency between census data and vegetation levels

![alt text](https://github.com/lexiejferry/Project-1/blob/master/Project1mapT2.png "Project1mapT2")

![alt text](https://github.com/lexiejferry/Project-1/blob/master/Chart_P2.PNG "Chart_P2")

- **Results:** There was determined to be a slightly negative correlation between NDVI and State Tax values with a correlation of -0.1434. This is most likely due to the distribution of residential property being located near forests in suburbs, versus commercial property being located more in the city center where there is less vegetation. For a better result, a differentiation between residential and commercial property would be needed.

**Software Used:** QGIS 3.2, Mircrosoft Excel (for the graphing and Correlation Equation)

- **Tools, Plugins, and Packages:** Spatialite Databases, SQL Query, Zonal Statistics, Clip, Extract/clip by extent, Raster Calculator, Join attributes by location, 2.5D Visualization

**Data Sources:** USGS Landsat 8 satellites, Baltimore City Services (https://cityservices.baltimorecity.gov/realproperty)

Author: Lexie Ferry

Date Created:   2018-09-24T09:45:11-04:00

Email:  lexiejferry@gmail.com
