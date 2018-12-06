**Chesapeake Bay Nitrate Levels, 2017**

- **Description:** A map showing changes in Total Dissolved Nitrate from years 2000-2017 in the chesapeake bay

- **Project Goal:** My project goal was to see how water quality measurements for plant nutrients how changed over the years between 2000 and 2017.

- **About:** For this project, Four maps were made, showing the level of Total Nitrates measured at water quality monitoring stations for four different years: 2000, 2006, 2012, and 2017. Time periods were chosen to be in intervals of four to show the passage of time, without adding too much data. Data was first retrieved from Chesapeakebay.net, then extracted into a point shapefile. The shapefiles were then filtered to only show Total Nitrates, and the ranges were derived automatcially to create an equal interval symbology. The maps were then put into a gif to showcase the change over the years in the Bay.

**MAP**

![Project 2 GIF](https://github.com/lexiejferry/lexiejferry.github.io/blob/master/Chesapeake_Nitrates_Map/Nitrates.gif "Project1mapT2")


- **Python Code Description:** The python code used was specifically designed to be able to switch between different variables for the years in the [wq2000.selectByExpression('"Parameter"=\'TN\'', QgsVectorLayer.SetSelection)] line, by simply switching out TN with a different prefered variable. The code creates a range for the variable selected and automatically assigns and Equal Interval Classification Scheme.
Python Code Used

**Python Code Used**
``` python
from PyQt5 import *
from qgis import *
import qgis.analysis
import gdal

"Loads all the oringinal vector layers for the water quality point data."
wq2000 = QgsVectorLayer('//gis-server2/lev2/Project2/shapefiles/wq_2000_r.shp', 'wq2000import', 'ogr')
wq2006 = QgsVectorLayer('//gis-server2/lev2/Project2/shapefiles/wq_2006_r.shp', 'wq2006import', 'ogr')
wq2012 = QgsVectorLayer('//gis-server2/lev2/Project2/shapefiles/wq_2012_r.shp', 'wq2012import', 'ogr')
wq2017 = QgsVectorLayer('//gis-server2/lev2/Project2/shapefiles/wq_2017_r.shp', 'wq2017import', 'ogr')

"Selects the Parameter chosen from the points, and writes the file"

"wq200selection"
wq2000.selectByExpression('"Parameter"=\'TN\'', QgsVectorLayer.SetSelection)
QgsVectorFileWriter.writeAsVectorFormat(wq2000, r'//gis-server2/lev2/Project2/shapefiles/selection/wq2000selection.gpkg', 'utf-8', wq2000.crs(), 'GPKG', True)
wq2000_selection = QgsVectorLayer('//gis-server2/lev2/Project2/shapefiles/selection/wq2000selection.gpkg', 'wq2000_selection', 'ogr')
wq2000_max = wq2000_selection.maximumValue(30)
wq2000_min = wq2000_selection.minimumValue(30)
wq2000_count = (wq2000_max - wq2000_min)/5
wq2000_ranges = [(wq2000_min),(wq2000_min+wq2000_count),(wq2000_min+(wq2000_count*2)),(wq2000_min+(wq2000_count*3)),(wq2000_min+(wq2000_count*4)),(wq2000_max)]

"wq2006 selection"
wq2006.selectByExpression('"Parameter"=\'TN\'', QgsVectorLayer.SetSelection)
QgsVectorFileWriter.writeAsVectorFormat(wq2006, r'//gis-server2/lev2/Project2/shapefiles/selection/wq2006selection.gpkg', 'utf-8', wq2006.crs(), 'GPKG', True)
wq2006_selection = QgsVectorLayer('//gis-server2/lev2/Project2/shapefiles/selection/wq2006selection.gpkg', 'wq2006_selection', 'ogr')
wq2006_max = wq2006_selection.maximumValue(30)
wq2006_min = wq2006_selection.minimumValue(30)
wq2006_count = (wq2006_max - wq2006_min)/5
wq2006_ranges = [(wq2006_min),(wq2006_min+wq2006_count),(wq2006_min+(wq2006_count*2)),(wq2006_min+(wq2006_count*3)),(wq2006_min+(wq2006_count*4)),(wq2006_max)]

"wq2012 selection"
wq2012.selectByExpression('"Parameter"=\'TN\'', QgsVectorLayer.SetSelection)
QgsVectorFileWriter.writeAsVectorFormat(wq2012, r'//gis-server2/lev2/Project2/shapefiles/selection/wq2012selection.gpkg', 'utf-8', wq2006.crs(), 'GPKG', True)
wq2012_selection = QgsVectorLayer('//gis-server2/lev2/Project2/shapefiles/selection/wq2012selection.gpkg', 'wq2012_selection', 'ogr')
wq2012_max = wq2012_selection.maximumValue(30)
wq2012_min = wq2012_selection.minimumValue(30)
wq2012_count = (wq2012_max - wq2012_min)/5
wq2012_ranges = [(wq2012_min),(wq2012_min+wq2012_count),(wq2012_min+(wq2012_count*2)),(wq2012_min+(wq2012_count*3)),(wq2012_min+(wq2012_count*4)),(wq2012_max)]

"wq2017 selection"
wq2017.selectByExpression('"Parameter"=\'TN\'', QgsVectorLayer.SetSelection)
QgsVectorFileWriter.writeAsVectorFormat(wq2017, r'//gis-server2/lev2/Project2/shapefiles/selection/wq2017selection.gpkg', 'utf-8', wq2012.crs(), 'GPKG', True)
wq2017_selection = QgsVectorLayer('//gis-server2/lev2/Project2/shapefiles/selection/wq2017selection.gpkg', 'wq2017_selection', 'ogr')
wq2017_max = wq2017_selection.maximumValue(30)
wq2017_min = wq2017_selection.minimumValue(30)
wq2017_count = (wq2017_max - wq2017_min)/5
wq2017_ranges = [(wq2017_min),(wq2017_min+wq2017_count),(wq2017_min+(wq2017_count*2)),(wq2017_min+(wq2017_count*3)),(wq2017_min+(wq2017_count*4)),(wq2017_max)]

'Classify the data by its range and separte into 5 classes, then add the map'

"Setting up some values for the symbology layer"
myTargetField = 'Value'
myRangeList2000 = []
myRangeList2006 = []
myRangeList2012 = []
myRangeList2017 = []
myOpacity = 1
myColour = QtGui.QColor('#fff5f0')
myColour2 = QtGui.QColor('#fdcab5')
myColour3 = QtGui.QColor('#fc8a6a')
myColour4 = QtGui.QColor('#f96245')
myColour5 = QtGui.QColor('#d42020')
mySymbol1 = QgsSymbol.defaultSymbol(wq2000_selection.geometryType())
mySymbol1.setColor(myColour)
mySymbol1.setOpacity(myOpacity)
mySymbol2 = QgsSymbol.defaultSymbol(wq2000_selection.geometryType())
mySymbol2.setColor(myColour)
mySymbol2.setOpacity(myOpacity)
mySymbol3 = QgsSymbol.defaultSymbol(wq2000_selection.geometryType())
mySymbol3.setColor(myColour3)
mySymbol3.setOpacity(myOpacity)
mySymbol4 = QgsSymbol.defaultSymbol(wq2000_selection.geometryType())
mySymbol4.setColor(myColour4)
mySymbol4.setOpacity(myOpacity)
mySymbol5 = QgsSymbol.defaultSymbol(wq2000_selection.geometryType())
mySymbol5.setColor(myColour5)
mySymbol5.setOpacity(myOpacity)
# First Range 2000
myRangeList2000.append(QgsRendererRange(wq2000_ranges[0], wq2000_ranges[1], mySymbol1, 'Lowest'))
# Second Range 2000
myRangeList2000.append(QgsRendererRange(wq2000_ranges[1], wq2000_ranges[2], mySymbol2, 'Low'))
# Third Range 2000
myRangeList2000.append(QgsRendererRange(wq2000_ranges[2], wq2000_ranges[3], mySymbol3, 'Medium'))
# Fourth Range 2000
myRangeList2000.append(QgsRendererRange(wq2000_ranges[3], wq2000_ranges[4], mySymbol4, 'High'))
# Fifth Range 2000
myRangeList2000.append(QgsRendererRange(wq2000_ranges[4], wq2000_ranges[5], mySymbol5, 'Highest'))
#Putting wq 2000 togethere
myRenderer2000 = QgsGraduatedSymbolRenderer('', myRangeList2000)
myRenderer2000.setMode(QgsGraduatedSymbolRenderer.EqualInterval)
myRenderer2000.setClassAttribute(myTargetField)
wq2000_selection.setRenderer(myRenderer2000)
QgsProject.instance().addMapLayer(wq2000_selection)

# First Range 2006
myRangeList2006.append(QgsRendererRange(wq2006_ranges[0], wq2006_ranges[1], mySymbol1, 'Lowest'))
# Second Range 2006
myRangeList2006.append(QgsRendererRange(wq2006_ranges[1], wq2006_ranges[2], mySymbol2, 'Low'))
# Third Range 2006
myRangeList2006.append(QgsRendererRange(wq2006_ranges[2], wq2006_ranges[3], mySymbol3, 'Medium'))
# Fourth Range 2006
myRangeList2006.append(QgsRendererRange(wq2006_ranges[3], wq2006_ranges[4], mySymbol4, 'High'))
# Fifth Range 2006
myRangeList2006.append(QgsRendererRange(wq2006_ranges[4], wq2006_ranges[5], mySymbol5, 'Highest'))
#Putting wq 2006 together
myRenderer2006 = QgsGraduatedSymbolRenderer('', myRangeList2006)
myRenderer2006.setMode(QgsGraduatedSymbolRenderer.EqualInterval)
myRenderer2006.setClassAttribute(myTargetField)
wq2006_selection.setRenderer(myRenderer2006)
QgsProject.instance().addMapLayer(wq2006_selection)

# First Range 2012
myRangeList2012.append(QgsRendererRange(wq2012_ranges[0], wq2012_ranges[1], mySymbol1, 'Lowest'))
# Second Range 2012
myRangeList2012.append(QgsRendererRange(wq2012_ranges[1], wq2012_ranges[2], mySymbol2, 'Low'))
# Third Range 2012
myRangeList2012.append(QgsRendererRange(wq2012_ranges[2], wq2012_ranges[3], mySymbol3, 'Medium'))
# Fourth Range 2012
myRangeList2012.append(QgsRendererRange(wq2012_ranges[3], wq2012_ranges[4], mySymbol4, 'High'))
# Fifth Range 2012
myRangeList2012.append(QgsRendererRange(wq2012_ranges[4], wq2012_ranges[5], mySymbol5, 'Highest'))
#Putting wq 2012 togethere
myRenderer2012 = QgsGraduatedSymbolRenderer('', myRangeList2012)
myRenderer2012.setMode(QgsGraduatedSymbolRenderer.EqualInterval)
myRenderer2012.setClassAttribute(myTargetField)
wq2012_selection.setRenderer(myRenderer2012)
QgsProject.instance().addMapLayer(wq2012_selection)

# First Range 2017
myRangeList2017.append(QgsRendererRange(wq2017_ranges[0], wq2017_ranges[1], mySymbol1, 'Lowest'))
# Second Range 2017
myRangeList2017.append(QgsRendererRange(wq2017_ranges[1], wq2017_ranges[2], mySymbol2, 'Low'))
# Third Range 2017
myRangeList2017.append(QgsRendererRange(wq2017_ranges[2], wq2017_ranges[3], mySymbol3, 'Medium'))
# Fourth Range 2017
myRangeList2017.append(QgsRendererRange(wq2017_ranges[3], wq2017_ranges[4], mySymbol4, 'High'))
# Fifth Range 2017
myRangeList2017.append(QgsRendererRange(wq2017_ranges[4], wq2017_ranges[5], mySymbol5, 'Highest'))
#Putting wq 2017 together
myRenderer2017 = QgsGraduatedSymbolRenderer('', myRangeList2017)
myRenderer2017.setMode(QgsGraduatedSymbolRenderer.EqualInterval)
myRenderer2017.setClassAttribute(myTargetField)
wq2017_selection.setRenderer(myRenderer2017)
QgsProject.instance().addMapLayer(wq2017_selection)

```

- **Results:** This data was not well represented by the equal interval classification scheme, and as a result the data is not easily interpretable. Using a classification scheme that equally weighs all maps on the same range would have been a better choice, but due to time constrainsts this was not possible.

- **Software Used:** QGIS 3.2, #https://giphy.com

- **Data Sources:** Chesapeake Bay Program (#http://data.chesapeakebay.net), PyQGISDeveloper Cookbook (#https://docs.qgis.org/testing/pdf/en/QGIS-testing-PyQGISDeveloperCookbook-en.pdf), GIS Stack Exchange (#https://gis.stackexchange.com/questions/100188/how-to-compute-an-interpolation-raster-from-the-python-console-in-qgis/233322)

**Author:** Lexie Ferry

**Date Created:** 2018-11-08

**Email:** lexiejferry@gmail.com
