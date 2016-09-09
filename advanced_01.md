Adavanced Data Tools Overview
================

R for Data Science
------------------

-   <http://r4ds.had.co.nz/> (blocked by MH firewall)
    -   [PDF Version](https://github.com/bgulbis/Resident_Data_Science/raw/master/R_for_Data_Science.pdf)

Why R?
------

1.  Purpose is to perform data analysis, statistics, and visualization
2.  Large community of support
3.  Large number of packages (over 7,000) available to extend base R functionality
    1.  Manipulating data (dplyr, tidry, purrr)
    2.  Visualization (ggplot2)
    3.  Modeling (caret)

4.  Open-source (free!)

How Much Programming Will I have to Learn?
------------------------------------------

1.  It depends...
    1.  You don't need a ton of programming experience to be able to do basic data manipulation and visualization (this is all you need to get started using R for QI and research projects).
    2.  You will need more programming knowledge if you want to do more difficult data manipulation, build your own packages, or develop interactive visualizations and dashboards.

Getting Started
---------------

**Will need to use a personal laptop**

1.  Download and install R from CRAN (<https://cloud.r-project.org>)
    1.  If you are using a 64-bit operating system, I would recommend installing 64-bit version of R

2.  Download and install RStudio (<http://www.rstudio.com/download>)
    1.  At some point, you may want to install the preview release of RStudio to utilize R Notebooks feature

3.  Install packages to follow examples in R for Data Science. To do this, open RStudio, and in the console (should be in the lower left-hand corner), copy and paste the following then hit Enter to run:

``` r
pkgs <- c("dplyr", "gapminder", "ggplot2", "jsonlite", 
          "Lahman", "lubridate", "modelr", "nycflights13", 
          "purrr", "readr", "stringr", "tibble", "tidyr")

install.packages(pkgs)
```

Resources
---------

1.  Google - adding "R" to the search query will usually find relevant results
2.  Ask for help!

Programming Resources
---------------------

1.  R-Specific
    1.  TryR (<http://tryr.codeschool.com/>)
    2.  DataCamp (<https://www.datacamp.com>)
    3.  Udemy (<https://www.udemy.com>)

2.  Non R-Specific
    1.  Codecademy (<https://www.codecademy.com>)

Other Resources
---------------

1.  Coursera
    1.  Data Science Specialization series by Johns Hopkins University

2.  edX
    1.  CS50x by Harvard University

3.  Twitter - use `#rstats`
4.  StackOverflow
5.  Khan Academy (math / statistics)
