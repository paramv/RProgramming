# Visualizing Map data
* User read.csv to load a CSV data-set
* Plotting the longitude and lattitude of map data generates a scatter plot. Use the geom "polygon" to connect these dots and generate an actual map.
* Use `help(package="maps")` to display help for a specific package.
* tx <- qplot(long,lat,data=texas,geom="polygon") this saves the graph to the tx variable. Run tx to regenerate the graph


## Customizing Graphs
* tx+ggtitle('Population of Texas counties')
* `str` can be used to inspect the structure of any object

### Coordinate Systems
* Use `coord_<system>()` to add a coordinate system
* Example 
	cp = qplot(carat,price,data=diamonds)
	cp2 = cp + coord_polar()
* coord_flip can be used to switch x and y axes
* coord_fixed allows us to set an aspect-ratio for the graph
* coord_trans can transform an axis using an R function, example `coord_trans(ytrans=log10)`
* coord_cartesian can be used to set the range(y-axis) and domain(x-axis) for the graph, example `coord_cartesian(xlim=c(0,1),ylim=c(0,1000))`
* coord_map can be used to constrain the aspect-ratio and can also change the projection used (for example mercator projection) 
* _Note: A stacked bar chart with polar coordinates is a pie-chart_