# Training Module:  R Programming

The figure below provides a reasonable visual representation of the data analyst's workflow.  The first step is **Importing** the data into the data analyst's preferred software package.  The second step is **Tidying** the data.  This step is sometimes referred to as "munging" or "wrangling" but they all generally mean the same thing:  preparing the data for analysis.  The remaining time is spent **Exploring** the data, often through summary statistics, regressions, or more advanced techniques like Machine Learning and Artificial Intelligence.  The final step is to **Communicate** insights through figures, charts, tables, and other visuals.

The true workflow is not as linear as the figure implies.  Nevertheless, it provides a useful framework for how to approach a project and for learning a new software package.  
#### **Data Analyst Workflow**

![Data](https://d33wubrfki0l68.cloudfront.net/795c039ba2520455d833b4034befc8cf360a70ba/558a5/diagrams/data-science-explore.png)

##### Notes:  Wickham, Hadley, and Garrett Grolemund. R for data science: import, tidy, transform, visualize, and model data. " O'Reilly Media, Inc.", 2016. (available at https://r4ds.had.co.nz/). #####

## Import Data

### Videos

* [Importing Data Into R (45:00)](https://www.rstudio.com/resources/webinars/importing-data-into-r/)
  * _Note:_ Focus on the discussion of Tabular Data (0:00 - 12:30).  The rest of the video is optional and covers Hierarchical, Relational, and Distributed data types.  These data types are not as common in economic research as Tabular Data.

### Additional Resources
* https://lgreski.github.io/dsdepot/2020/06/13/reading-Excel-files.html

### Sample Code
```R
# Import from Text
library(readr)
csv <- read_csv("data/Water_Right_Applications.csv")

# Import from Excel
library(readxl)
excel <- read_excel("data/Water_Right_Applications.xlsx")

# Import from SPSS
library(haven)
sav <- read_sav("data/Child_Data.sav")

# Import from SAS
sas <- read_sas("data/iris.sas7bdat")

# Import from Stata
stata <- read_dta("data/Milk_Production.dta")
```

### Exercises

## Tidy Data

The term "Tidy Data" comes from a [paper by Hadley Wickham](https://vita.had.co.nz/papers/tidy-data.pdf) (author of multiple R packages).  To understand what Tidy data are, it is helpful to understand what Tidy data are not.

Data are rarely, if ever, provided in a form that is analysis ready.  Often, one dataset will need to be combined with multiple other datasets before an analysis can begin.  Moreover, new variables will need to be created or formats will need to be changed prior to performing analyses.  Data may also be missing or wrong.  These all have severe implications for the results of an analysis.  As the old addage goes:  _Garbage In, Garbage Out_.  

By [some estimates](https://www.nytimes.com/2014/08/18/technology/for-big-data-scientists-hurdle-to-insights-is-janitor-work.html), data analysts spend between 50% and 80% of their time in the Import and Tidying phases.  

### Videos
* [Missing Data in R (12:51)](https://youtu.be/hLYAno2r9O4)

### Sample Code

### Exercises


## Explore Data

### Videos
* [Summary Statistics with One Variable](https://www.youtube.com/watch?v=l1lVtEyxnMs&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=8)
* [Summary Statistics with Two Variables](https://www.youtube.com/watch?v=L5WV8KiD8-A&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=10)
* [Simple Plots and Graphs](https://www.youtube.com/watch?v=pLh2gdHDUZc&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=11)

## Communicate Insights

## Important Functions
* head()
* str() - Get a summary of an object's structure.
* class() - Find the class an object belongs to.
* getwd() - Find the current working directory.
* setwd() - Change the current working direcotry.
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
  * readr ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-import.pdf))
  * readxl ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-import.pdf)) This package can read .xlsx files and legacy .xls files.

([Cheat Sheet]())

* Tidying Data
  * tidyr ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/tidyr.pdf))
  * dplyr ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-transformation.pdf))
  * lubridate ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/lubridate.pdf))
  * stringr ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/strings.pdf))
  * data.table()

* Explore Data
  * stargazer ([]()) - Summary statistics (N, Mean, Std Dev., Min, Max by default) for a data frame.

* Communicate Insights
  * [ggplot2]() ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-visualization.pdf))

