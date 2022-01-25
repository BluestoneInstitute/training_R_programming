# Training Module:  R Programming

![Data](https://d33wubrfki0l68.cloudfront.net/795c039ba2520455d833b4034befc8cf360a70ba/558a5/diagrams/data-science-explore.png)


## Import Data

### Videos

### Sample Code

### Exercises

## Tidy Data

## Explore Data

### Videos
* [Summary Statistics with One Variable](https://www.youtube.com/watch?v=l1lVtEyxnMs&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=8)
* [Summary Statistics with Two Variables](https://www.youtube.com/watch?v=L5WV8KiD8-A&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=10)

## Communicate Insights

## Important Functions
* head()
* subset()
* mean() - Average of a variable.
* sd() - Standard Deviation of a variable.
* median() - Median of a variable.
* summary() - Descriptive information of a variable.  By default, the function reports the minimum, 25th Percentile, Median, Mean, 75th Percentile, and maximum.
* table() - Listing of all the values contained in a variable.  Often useful for categorical variables (for example, years of education).  When used with multiple variables it will yield a cross-tab.  To add labels to the cross-tab, use "dnn=c()" option.
* cor() - Calculates a correlation between two variables.  Alt version can be done with cor.test().  The alternative will yield statistical tests.
* aggregate() - Calculates summary statistics by group [[Tutorial](https://www.datasciencemadesimple.com/aggregate-function-in-r/)]
* sapply() -
* lapply() -
* mapply() -
* tapply() -
* plot() - A simple (unformatted) scatterplot of data.  Can also be used to plot a density plot ("plot(density(dataset$variablename))").
* hist() - A simple (unformatted) histogram of data.
* barplot() - A simple (unformatted) bar chart.

## Important Packages
* Import
  * foreign - package that allows for the import of non-R, or "foreign", datasets.  For example, the package can be used to upload a Stata 13 datafile (".dta", via read.dta) or a SAS xport file (".xpt", via read.xport).
  * [haven](https://haven.tidyverse.org/) - Enables R to read and write various data formats ued by other statistical packages (SAS, SPSS, Stata).  Part of the tidyverse.  Output is a tibble.

* Tidying Data
  * tidyr ([Cheat Sheet]())
  * dplyr ([Cheat Sheet]())
  * lubridate ([Cheat Sheet]())

* Explore Data
  * stargazer ([]()) - Summary statistics (N, Mean, Std Dev., Min, Max by default) for a data frame.

* Communicate Insights
  * [ggplot2]() ([Cheat Sheet]())

