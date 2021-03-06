# Developing Data Products - Shiny App COurse Project

###Summary

For the Developing Data Products Course Project, I have developed a Shiny Application for use with the mtcars data package in R.

###Application Purpose

My Shiny application allows the user to choose a car manufacturer from the list, along with an associated feature of the car (please see below for a list of the available features). After doing to, the application will reactively display:

1. All records in the dataset associated with the chosen car manufacturer

2. An average value of the chosen car feature across all of the records associated with the chosen car manufacturer

###Development Approach

In order to develop this application, I first needed to extract the car manufacturer from the row names of the mtcars data. To do this I used the following codein the server.R file:


```r
library(datasets)
data(mtcars)

#Extract the row names as a column in the dataset
mtcars$makemodel <- rownames(mtcars)

#Extract the manufacturer/make from the rownames
mtcars$make <- gsub( " .*$", "", mtcars$makemodel)
```

For the chosen manufacturer and feature, the mean value was then derived in the way shown below. The variables "make" and "feature" in the code below represent the input values selected by the application user:


```r
make <- "Mazda"
feature <- "qsec"

data <- mtcars[mtcars$make==make,feature]
paste("The mean value of",feature,"for",make,"cars is",print(mean(data)))
```

```
## [1] 16.74
```

```
## [1] "The mean value of qsec for Mazda cars is 16.74"
```

###Viewing and Running the Shiny App

The shiny application I developed has been published to the Shiny server at the following [Link](https://elle248.shinyapps.io/Test)

Alternatively, to reproduce this application locally you will need to install all of the relevant packages (see the [Getting Started with Shiny Apps](http://shiny.rstudio.com/articles/shinyapps.html) documantation for details). Next, you can run the ui.R and server.R files located in the same repository as this document to run the application locally.

###Selecting a car feature
A number of car features can be selected in this Shiny Application. Each feature is defined below:

1. mpg - Miles/(US) gallon
2. cyl - Number of cylinders
3. disp	 - Displacement (cu.in.)
4. hp	 - Gross horsepower
5. drat	 - Rear axle ratio
6. wt	 - Weight (lb/1000)
7. qsec	 - 1/4 mile time
8. vs	 - V/S
9. am	 - Transmission (0 = automatic, 1 = manual)
10. gear - Number of forward gears
11. carb - Number of carburetors

###Supporting Resources

More information on the Developing Data Products course project can be found [here](https://class.coursera.org/devdataprod-015/human_grading/view/courses/973542/assessments/5/submissions)

More information on the mtcars data package can be found [here](https://stat.ethz.ch/R-manual/R-devel/library/datasets/html/mtcars.html)
