## Development of National Lightning Detection Network 



1. **General statements**
	1. The first is it is well documented how the network is set up.This  
	2. The goal of this project would be to learn how to rank data quality for usability with just the data given 
3. **data sources**
	* NOAA's National Center for Environmental Information lightning catalog
		1. Count  per Year 
			1. 1986-2012
		2. Count by per month 
			1. January and July  for list years aboves
		2. count by hour per year 
			1. Hours 20 for year 1986 -2012

2. **Usefulness of this data**
	* The Catalog was highly useful to the project 
		* The variety of how the data was broken up in the catalog aloud for me to compare it in a handful of ways.
		* How they Divided it up
			1. Count by Hour per Month
			2. Count by Hour per Year
			3. Count per Day
			4. Count per month 
			5. Count per year
			
			**Note** each option also has positive polarity data as well 

1. **Looking at the data**
	 
	![Rendered photo of 1986 data](https://github.com/gbrandom/Geography-490/blob/master/1986.JPG)
	
	Looking at this first photo shows what looks like a lack of data  west of the missippi. Before one can conclude that there is not data there you have to compare several years. 
	
	 ![Rendered photo of 19887 data](https://github.com/gbrandom/Geography-490/blob/master/1987.JPG)
	
	![Rendered photo of 1996 data](https://github.com/gbrandom/Geography-490/blob/master/1996.JPG)

	![Rendered photo of 2000 data](https://github.com/gbrandom/Geography-490/blob/master/2000.JPG)

	![Rendered photo of 2008 data](https://github.com/gbrandom/Geography-490/blob/master/2008.JPG)
 
	![Rendered photo of 2012 data](https://github.com/gbrandom/Geography-490/blob/master/2012.JPG)

	This is where we can see that the first two data sets are missing something while the rest have data across the world. 

5. **Where is all this data still useful**
	The data clearly becomes completely useful over time so its important to know where it is useful and where for each of the 
This will give you the chart for the year 1986.
```{r}

light_path <- "C:/rcode/"
light_name <- "nldn-1986.nc"
light_file <- paste(light_path, light_name, sep="")
light <- raster(light_file) # open nldn-1986.nc
light

shape_path <- "c:/r/"
coast_shapefile <- paste(shape_path, "ne_50m_coastline.shp", sep="")
layer <- ogrListLayers(coast_shapefile)
ogrInfo(coast_shapefile, layer=layer)
coast_lines <- readOGR(coast_shapefile, layer=layer)
summary(coast_lines)
plot(coast_lines, col="purple")

mapTheme <- rasterTheme(region=brewer.pal(8,"Greens"))
plt <- levelplot(light, margin=F, par.settings=mapTheme)
plt + latticeExtra::layer(sp.lines(coast_lines, col="black", lwd=0.5))

```

All of the files needed  to see the rest of patern and growth of the system are included in the github depository.