# Training Module:  R Programming

The figure below provides a reasonable visual representation of the data analyst's workflow.  The first step is **Importing** the data into the data analyst's preferred software package.  The second step is **Tidying** the data.  This step is sometimes referred to as "munging" or "wrangling" but they all generally mean the same thing:  preparing the data for analysis.  The remaining time is spent **Exploring** the data, often through summary statistics, regressions, or more advanced techniques like Machine Learning and Artificial Intelligence.  The final step is to **Communicate** insights through figures, charts, tables, and other visuals.

The true workflow is not as linear as the figure implies.  Nevertheless, it provides a useful framework for how to approach a project and for learning a new software package.  

#### **Data Analyst Workflow**

![Data](https://d33wubrfki0l68.cloudfront.net/795c039ba2520455d833b4034befc8cf360a70ba/558a5/diagrams/data-science-explore.png)

##### Notes:  Wickham, Hadley, and Garrett Grolemund. R for data science: import, tidy, transform, visualize, and model data. " O'Reilly Media, Inc.", 2016. (available at https://r4ds.had.co.nz/). #####

Programming often follows the Pareto Principle:  80% of the work can be done by 20% (or less) of the available features.  This module is designed to introduce the fewest number of concepts necessary to be proficient on the vast majority of tasks.

## Import Data
There are lots of ways to import data into R.  For example, the base version of R has several data import functions like **read.table**, **read.csv**, and **read.delim** (note the "." after "read").  However, other packages provide slightly better functionality and speed than what is available in base R.  

The **readR** package includes functions like **read_csv**, **read_tsv**, and **read_fwf** (note the "\_" after "read").  The **readXL** package includes functions like **read_excel** (again, note the "\_" after "read").  Both readR and readXL are part of the Tidyverse.  The Tidyverse is a collection of R packages that share underlying design philosophy, grammer and datas structures.  **haven** is another Tidyverse package that imports datasets from other statistical packages (SAS, Stata, and SPSS) into R.

> **BEST PRACTICE NOTE:**  
> Learn the packages readR, readXL, and haven before branching out into other data import packages.  

Cheat sheets for [readr](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-import.pdf), [readXL](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-import.pdf), and [haven](https://haven.tidyverse.org/) are available.

### Videos

* [Introduction to readR (5:04)](https://www.youtube.com/watch?v=URJNKVBMCAY) - This video provides a very quick and high-level overview of the **readR** package.  It covers Hierarchical data types that are commonly found in social science research.  More detail on the readR package or other data types can be found in the optional videos below.

  * _(Optional)_ [The readr Package for Importing Delimited Data (25:02)](https://www.youtube.com/watch?v=qxbfVEDfi0o)
  * _(Optional)_ [Importing Excel Data, SAS Data, and More (14:44)](https://www.youtube.com/watch?v=qxbfVEDfi0o)
  * _(Optional)_ [Importing Data Into R (45:00)](https://www.rstudio.com/resources/webinars/importing-data-into-r/)

> **BEST PRACTICE NOTE:**  
> Import data using code saved to a program **NOT** through drop-down menus included in the software.

* [Importing/Reading Excel data into R using RStudio (8:11)](https://www.youtube.com/watch?v=JYVWufSQ4OI) - A brief introduction to the **readXL** package.  It begins by introducing how to import data using the drop-down menus in RStudio.  This is a great way to learn the syntax of readXL **however**, it is best practice to save the code into the program you are writing.  That way work can be replicated by others.
  * _(Optional)_ There are a lot of other packages that can read in Excel files. An overview of these packages and their pros and cons can be found here:  https://lgreski.github.io/dsdepot/2020/06/13/reading-Excel-files.html.

### Sample Code
```r
# Import from Text using readR
library(readr)
csv <- read_csv("data/Water_Right_Applications.csv")

# Import from Excel using readXL
library(readxl)
excel <- read_excel("data/Water_Right_Applications.xlsx")

# Import from SPSS using haven
library(haven)
sav <- read_sav("data/Child_Data.sav")

# Import from SAS using haven
sas <- read_sas("data/iris.sas7bdat")

# Import from Stata using haven
stata <- read_dta("data/Milk_Production.dta")
```
readR can also save objects to different formats.  This is done via the functions write_csv, write_delim, and write_rds.

> **BEST PRACTICE NOTE:**  
> .RData (sometimes abbreviated as .Rda) is a valid data type.  .RData files can store multiple objects under the same name.  It is preferred to use .Rds rather than .Rda.

```r
# Save excel to an R dataset
write_rds(excel, "imported_from_excel.rds")

# Save excel to a csv file
write_csv(excel, "imported_from_excel.csv")

# Save excel to a bar delimited txt
write_delim(excel, "imported_from_excel.txt", delim = "|")
```

> **BEST PRACTICE NOTE:**  
> Most datasets should be imported once and then saved to a permanent dataset. This saves you from having to re-import data multiple times.


## Tidy Data
Data must be structured to facilitate analysis to be useful.  Unfortunately, data are rarely, if ever, provided in a form that is analysis ready.  By [some estimates](https://www.nytimes.com/2014/08/18/technology/for-big-data-scientists-hurdle-to-insights-is-janitor-work.html), data analysts spend between 50% and 80% of their time in the Import and Tidying phases.  The term "Tidy Data" comes from a [paper by Hadley Wickham](https://vita.had.co.nz/papers/tidy-data.pdf) (author of multiple R packages and creator of the [Tidyverse](https://www.tidyverse.org/packages/)).  According to Wickham, there are generally four types of transformations needed to convert messy data to Tidy data:
* Filter:  subsetting or removing observations based on some condition.
* Transform:  adding or modifying variables
* Aggregate:  collapsing multiple values into a single value (e.g., by summing or taking means).
* Sort:  changing the order of observations.

The Tidyverse is a collection of R packages intended to make the task of Tidying simple.  The main packages used are **tidyr**, **dplyr**, **stringr**, **lubridate**, and **magrittr**.  Included below are a collection of short videos that introduce the tidyr and dplyr packages.  

Cheatsheets for [tidyr](https://raw.githubusercontent.com/rstudio/cheatsheets/main/tidyr.pdf), [dplyr](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-transformation.pdf), [stringr](https://raw.githubusercontent.com/rstudio/cheatsheets/main/strings.pdf), and [lubridate](https://raw.githubusercontent.com/rstudio/cheatsheets/main/lubridate.pdf) can be used as a quick reference.

* _Optional_ [Materials from an R workshop covering tidyr and dplyr](https://bobaekang.github.io/icjia-r-workshop/modules.html)
* _Optional_ [Data Wrangling with R and the Tidyverse (2:56:24)](https://www.youtube.com/watch?v=CnY5Y5ANnjE&t=3416s) on the tidyverse is also available.

### Videos

* [Missing Data in R (12:51)](https://youtu.be/hLYAno2r9O4)

* **tidyr** Package
  * [Reshaping Data with tidyr (19:10)](https://www.youtube.com/watch?v=JKM4Xu7FAF8) - This video focuses on the functions **pivot_longer()**, **pivot_wider()**, **unite()**, and  **separate()**  pivot_longer() and pivot_wider are used to transpose data.  Previous versions of Tidyr used the functions gather() and spread() to transpose data.  You may run across gather() and spread() functions online even though they have been replaced.
* **dplyr** Package
  * [Join Data with dplyr (9:07)](https://www.youtube.com/watch?v=Yg-pNqzDuN4) - Joining datasets is another aspect of the dplyr package.  A Venn diagram may be more intuitive than the tables used in the video (conceptually the diagram and tabular represenations are the same):
<p align="center">
  <img src="https://tavareshugo.github.io/r-intro-tidyverse-gapminder/fig/07-dplyr_joins.svg" alt="Venn Diagram of Joins" width = "300" height="auto">
</p>
* Mastering 6 dplyr verbs should allow you to accomplish most tasks:  filter, mutate, group, summarize, and join.

##### Notes:  Introduction to R/tidyverse for Exploratory Data Analysis. available at https://tavareshugo.github.io/r-intro-tidyverse-gapminder/index.html. #####

  * [dplyr (9:11)](https://www.youtube.com/watch?v=bUM3wX4YZDc) - Focuses on the functions **mutate()**, **filter()**, **select()**, **arrange()**, and **rename()** functions in dplyr.
  * [Piping in dplyr (6:50)](https://www.youtube.com/watch?v=e_SQnJpS5fA) - Introduces the pipe operator (**%>%**) used in the tidyverse.  The pipe operator chains together multiple operations at once.
  * [Grouping in dplyr (9:48)](https://www.youtube.com/watch?v=zEhlgY2l3gE) - Covers the **group_by()** function in dplyr.

### Sample Code

```r
# Forthcoming
```

## Explore Data

**stargazer** is a package commonly used by academics to generate tables used in their research.  The popularity is because most **style** options are typically designed to resemble academic journals.  While mostly geared to regression output, stargazer's features are also useful for summary tables.  stargazer includes more summary statistics by default (N, Mean, Std. Dev., Min, Max) than does Base R's table() function.

* _Optional_ Unlike other packages, [stargazer's vignette](https://cran.r-project.org/web/packages/stargazer/vignettes/stargazer.pdf) is readable and intuitive.

### Videos
* [Summary Statistics with One Variable](https://www.youtube.com/watch?v=l1lVtEyxnMs&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=8)
* [Summary Statistics with Two Variables](https://www.youtube.com/watch?v=L5WV8KiD8-A&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=10)
* [Simple Plots and Graphs](https://www.youtube.com/watch?v=pLh2gdHDUZc&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=11)

### Sample Code


```r
# Forthcoming
```

## Communicate Insights

Figures generated in R are typically better than most other statistical packages (Stata and SAS, for example).  The main package for generating figures is **ggplot2** [(Cheat Sheet)](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-visualization.pdf).  The options available for ggplot2 are so vast that multiple books have been written on the subject (See online versions written by [Hadley Wickham](https://ggplot2-book.org/index.html) or [Winston Chang](https://r-graphics.org/)).

Before reviewing code, it is helpful to be familiar with the "grammar of graphics" concept on which ggplot2 is based.  A grammar of graphics is intended to define a set of rules that help to define and establish components of a language.  The key ideas behind the grammar of graphics is:
* Graphics are built from layers of grammatical elements
* Variables are mapped onto asthetics
* Seven *Layers* in total (Data, Aesthetics (Scales), Geometries, Facets, Statistical transformations, Coordinate Systems, and Themes)
* Every plot must include the first three layers:
  * Data:  The dataset being plotted
  * Aesthetics:  Scales onto which we map our data (characteristics like x-axis, y-axis, color, fill, size, etc.)
  * Geometries:  Visual elements used for our data (essentially points for scatterplots, bars for barchart, lines for line graph, etc.)

This means a figure is comprised of multiple layers and that each layer is comprised of multiple options.  By specifiying the details of each layer you can assemble a figure, for example:
<p align="center">
 <img src=http://r.qcbs.ca/workshop03/book-en/images/Layers_ggplot.png alt="Example of Layers Creating a Figure" width = "700" height="auto">
</p>

##### Notes:  "Quebec Centre for Biodiversity Science" (available at http://r.qcbs.ca/workshop03/book-en/). #####

### Videos
* [Intro to ggplot2 (10:47)](https://www.youtube.com/watch?v=XPaB-gj-7Ts) - This video covers the grammar of graphics and then combines those concepts with code that generates some basic figures.
* [ggplot (5:58)](https://www.youtube.com/watch?v=SWJh_rt25mo) - Another introduction to the ggplot function but without the detail on grammar of graphics.
* [ggplot Geometries (10:14)](https://www.youtube.com/watch?v=4djbRljsoyk) - Introduction to the geometries layer 
* [Overlaid and Grouped ggplots (10:39)](https://www.youtube.com/watch?v=Wxq1ln92v5g) - Horizontal lines, vertical lines, and other attributes commonly used in social science research.
* [ggplot Titles and Labels (6:55)](https://www.youtube.com/watch?v=yW9fswgGDBE) - Adding in **ggtitle**, **xlab**, **ylab**, and other parts to a simple ggplot figure.


**BEST PRACTICE NOTE:**  
The "grammar of graphics" concept is also useful for creating footnotes that help the reader to understand a figure.  For example, a figure's footnote should include the source data and any filters applied (Data Layer) and identify any calculations done on those data (Statistical Transformation Layer).

**BEST PRACTICE NOTE:**  
Frequently you will want to see a side-by-side comparision of graphs, [like this one](https://community.rstudio.com/uploads/default/original/3X/8/f/8fcfe3fef075847058e9de576a2dd0e3a2bdefa1.png).  This can be accomplished using facet_wrap() function in **ggplot2**.

* _Optional_ ["A Comprehensive Guide to the Grammar of Graphics for Effective Visualization of Multi-Dimensional Data"](https://towardsdatascience.com/a-comprehensive-guide-to-the-grammar-of-graphics-for-effective-visualization-of-multi-dimensional-1f92b4ed4149)
* _Optional_ ["R Workshop: Module 4 (1)"](https://bobaekang.github.io/icjia-r-workshop/notes/module4_notes1.html)

### Sample Code

```r
# Forthcoming
```
Sometimes it is easier to export raw data into excel for formatting there.  This may be true if it is a one-off analysis and the time to format the output in R would be greater than the time to format in Excel.  It may also be easier if you are working with people that do not know R.  Fortunately, the **openxlsx** package exists for this purpose.  It is straightforward to use for the purposes of exporting raw data.  That said, the package is capable of much more than just exporting data.  As your knowledge of R expands you may want to learn some of these other features.

### Sample Code
```r
install.packages("openxlsx") 
library(openxlsx)

#Write a single worksheet to a single excel file
write.xlsx(df, file = "output.xlsx", sheetName = "Data Frame", asTAble = FALSE)

#Write multiple worksheets to the same file

#create a list of 'worksheet' names and dataframes
dataset_names <- list('df1' = df1, 'df2' = df2
                      , 'df3' = df3, 'df4' = df4)
#export all dataframes                   
write.xlsx(dataset_names, file = 'output.xlsx', asTable = TRUE)
```
> **BEST PRACTICE NOTE:**  
> It is best to ignore people who claim "you should never use" another tool like Excel.  These people often prefer a single tool (e.g., R, Python, etc.) to do all jobs and don't often work on teams with a diverse skillset.  As the saying goes, "When all you have is a hammer...."  That said, when moving across tools you do break the chain between raw data and final tables.  Be very cautious about that as it could lead to a replicatability problem.  
> 
> Use the right tool for the right job but be mindful of the costs and benefits to time, replicatability, checking efficiency, risk of data corruption, learning new skills, etc.

## Important Functions (Optional)
* head() - Returns the first or last parts of a vector, matrix, table, data frame or function.  The opposite of tail().
* str() - Get a summary of an object's structure.
* class() - Find the class an object belongs to.
* getwd() - Find the current working directory.
* setwd() - Change the current working direcotry.
* subset() - An easy way to select variables and observations without using the Tidyverse
* mean() - Average of a variable.
* sd() - Standard Deviation of a variable.
* median() - Median of a variable.
* summary() - Descriptive information of a variable.  By default, the function reports the minimum, 25th Percentile, Median, Mean, 75th Percentile, and maximum.
* table() - Listing of all the values contained in a variable.  Often useful for categorical variables (for example, years of education).  When used with multiple variables it will yield a cross-tab.  To add labels to the cross-tab, use "dnn=c()" option.
* cor() - Calculates a correlation between two variables.  Alt version can be done with cor.test().  The alternative will yield statistical tests.
* aggregate() - Calculates summary statistics by group [[Tutorial](https://www.datasciencemadesimple.com/aggregate-function-in-r/)]
* plot() - A simple (unformatted) scatterplot of data.  Can also be used to plot a density plot ("plot(density(dataset$variablename))").
* hist() - A simple (unformatted) histogram of data.
* barplot() - A simple (unformatted) bar chart.

## Important Packages (Optional)
One you have mastered the packages mentioned above you are ready to branch out.  Some other packages that might be useful are:
* [boot](https://cran.r-project.org/web/packages/boot/boot.pdf)
* [purrr](https://purrr.tidyverse.org/)
* [furrr](https://furrr.futureverse.org/)
* [zoo](https://cran.r-project.org/web/packages/zoo/zoo.pdf)
* [scales](https://cran.r-project.org/web/packages/scales/scales.pdf)
* [modelr](https://www.tidymodels.org/)
* [RQuantLib](https://cran.r-project.org/web/packages/RQuantLib/RQuantLib.pdf)
* [rvest](https://cran.r-project.org/web/packages/rvest/rvest.pdf)
* [broom](https://cran.r-project.org/web/packages/broom/broom.pdf)
* [gt](https://cran.r-project.org/web/packages/gt/gt.pdf)
* [here](https://cran.r-project.org/web/packages/here/here.pdf) and a good rant about the benefits of here [here](https://malco.io/2018/11/05/why-should-i-use-the-here-package-when-i-m-already-using-projects/)
* data.table()
