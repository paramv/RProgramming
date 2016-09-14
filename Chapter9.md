# Introduction to ggplot2
* qplot - quick plot

## Key points
* Aesthetics
* Faceting
* Geoms

### Aesthetics
* _color_, _size_,_group_ and _shape_
* color and size will work for discrete and continuous values
* shape cannot be used for continuous values
* Example `qplot(x,y,data=diamonds,color=class)` where _class_ is a column

### Faceting
* `qplot(displ,hwy,data=mpg,color=cyl)+facet_grid(. ~ cyl)` - column wise faceting because the field name is after the ~
* `qplot(x,y,data=diamonds)+facet_grid(x ~ .)` - row wise faceting because the field name is before the ~
* `qplot(x,y,data=diamonds)+facet_grid(x ~ y)` - intersection faceting 
* `qplot(x,y,data=diamonds)+facet_wrap(~ class)` - renders the graph in 1D but wraps into 2D

## Geoms
*  `qplot(displ,hwy,data=mpg,geom="smooth")`; point is the default
*  `qplot(displ,hwy,data=mpg,geom=c("point","smooth"))`; point is the default
* The order of x axis values can be controlled using `reorder` - `qplot(reorder(class,hwy),hwy,data=mpg,geom="boxplot")`orders the values of x axis (class) according to values of hwy
* By default reorder works using the mean. But the property `FUN` can be used to change to median ex - `qplot(reorder(class,hwy,FUN="median"),hwy,data=mpg,geom="boxplot")`
* For bar graphs `color` aesthetic sets the border color whereas `fill` sets the fill color
* The `position` argument can set how the bar graph is arranged. allowed values are _stack, fill, dodge, identity, jitter_
* _`position` is not supported by qplot, use ggplot directly_
* _Note: Use a vector of geoms for plotting multiple geoms_
* `qplot(color,data=diamonds,fill=cut)` will create a stacked bar chart (color and cut are discrete)
* `position` argument can change how the above graph is rendered
* `stack`,`dodge`,`identity` and `fill` are supported values for `position`
* `qplot` does not support use of `position` arguments anymore. Must be done with `ggplot`
* `ggplot(diamonds,aes(x=color))+geom_bar(aes(fill=cut),position="dodge")`
* position=jitter adds noise to the data. This is done to eliminate false groupings which may be formed due to rounding off.

## Histograms
* Defaults
	* Two variables - scatter plot
	* One continuous variable - histogram
	* One discrete variable - bar
* Separate the horizontal axis into bins, distribute all data points across bins and draw bars in each bin
* Changing the _binwidth_ can alter the histogram
* `freqpoly` and `density` geoms are useful for creating area plots instead of histograms

## Visualizing Big Data
* Scatter plots are not very useful to view large datasets in more than 2 dimensions
* `bin2d` is a geom that will help create 2D bins where color is used to identify where the majority of the points are
* similarly `density2d` is a 2D projection of the density geom. This is equivalent to a contour plot
* `qplot(carat,price,data=diamonds,geom=c("point","density2d"))`
* for `smooth` geoms set se=FALSE to remove error bands around the plot
* method=LM (linear model) can fit a straight line to a distribution
* use geom=smooth and method=lm (linear model) to get straight lines
* __I__ (as-is/identity) lets you set an aesthetic to a string literal instead of a mapping. For example color=I("blue")

## Saving Graphs
* `ggsave("filename")`