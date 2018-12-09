**Final Project: A predictive map of Dissolved Oxygen Levels in the Chesapeake Bay**

**About:** For my final Project I want to make a predictive map of Dissolved Oxygen Levels in the Chesapeake Bay using past water quality data. I will use data from water quality monitoring stations upkept by the Chesapeake Bay Program for the years of 2000, 2006, 2012, and 2017 (2018 hasn’t been released yet) and from that I will generate a rate of change of DO for the total 4 years, putting more emphasis on the change from 2012-2017. I will then generate a map predicting DO for the year of 2022, the next in the four-year period

**Proposed Methods:** 
  -	1)   I will acquire water quality data for the years of 2000, 2006, 2012, and 2017. I will then create an IDW and clip it to a shapefile of the Chesapeake Bay
  -	2)   I will then create a hexagonal grid and use zonal statistics to take an average of the DO for each of the years according of the IDWs. 
  -	3)   Next, I will use SQL to determine an overall rate of change, and then a weighted rate of change, and then apply the weighted rate of change to the 2017 data, and finally use SQL to show the data.
  -	4)   My next step will be to use a 3D map to show the predicted DO in 2022 and the absolute rate of change of DO
  -	5)   If there is time, I plan to use the overall rate of change to determine spatial outliers in rate of change of DO using GeoDa and attempt to explain those patterns. 

**Questions to answer:**
-	What areas show the highest rates of change (urban, forest, high income, low income, up-stream, down-stream, agricultural areas, etc.)
-	Are any areas expected to stay or fall below 4 ppm DO (fatal for aquatic fish, but not for benthic species like aquatic worms). If so, are there reported outbreaks of deadzones or other records indicating awareness of a problem in those areas?
-	Are DO levels generally improving or worsening in the Chesapeake Bay? Have they been improving or worsening in the years before 2017, when Environmental regulations have been laxed?
-	Are areas of low DO or high DO clustered or separated? Do they happen more in tributaries or the main body of the bay?

**The Part where I explain why I get a B and an A**
I am using 3 non-superficial components of class elements to preform my analysis: 
-	Spatial Correlation with GeoDa to determine outliers
-	SQL to preform spatial joins, operations, and create new maps of DO
-	3D maps to show rate of change and expected DO levels

I believe this is a little more involved than the Labs because I will be using the data I create to predict the DO levels four years into the future, and I will be using a weighted rate of change to do that. I have never had the chance to do a predictive analysis, and so I am trying something new with this. I will also be attempting to determine patterns in the changes, such as local landcover, landuse up-stream, explain outliers, etc.
I choose this component because I used to work in environmental education. I would have to teach 4th graders about how the bay is changing and what they could do to help it. I never had access to predicted maps though. We would always tell the kids that the future of the bay is in their hands, and it is to some extent, but I plan to add this predictive map to the arsenal of teaching aids at my past work, so they can see whether the work they are doing is having an effect or not.
Additionally, I realize this is very similar to my Project 2. I did this on purpose due to lack of time; I already have the data needed and am familiar with the way the data is recorded. If this a problem, let me know.

**Data Sources:**
-	Information on harmful DO levels (#https://www.fondriest.com/environmental-measurements/parameters/water-quality/dissolved-oxygen/)
-	Water Quality Data (#https://www.chesapeakebay.net/what/data)

Author: Lexie Ferry
