Lecture 2 - Data Storage
================

``` r
library(readr)
raw <- read_csv("lecture_02_data.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   `Reporting Area` = col_character(),
    ##   `MMWR YEAR` = col_integer(),
    ##   `MMWR WEEK` = col_integer(),
    ##   `All causes, by age (years), All Ages` = col_integer(),
    ##   `All causes, by age (years), All Ages, flag` = col_character(),
    ##   `All causes, by age (years), GE 65` = col_integer(),
    ##   `All causes, by age (years), GE 65, flag` = col_character(),
    ##   `All causes, by age (years), 45–64` = col_integer(),
    ##   `All causes, by age (years), 45–64, flag` = col_character(),
    ##   `All causes, by age (years), 25–44` = col_integer(),
    ##   `All causes, by age (years), 25–44, flag` = col_character(),
    ##   `All causes, by age (years), 1–24` = col_integer(),
    ##   `All causes, by age (years), 1–24, flag` = col_character(),
    ##   `All causes, by age (years), LT 1` = col_integer(),
    ##   `All causes, by age (years), LT 1, flag` = col_character(),
    ##   `P&I† Total` = col_integer(),
    ##   `P&I† Total, flag` = col_character(),
    ##   `Location 1` = col_character(),
    ##   `Location 2` = col_character()
    ## )

Problems with Dataset
---------------------

-   Zero encoded as a dash and is in Flag column
-   Flag column represents Unavailable
-   Data (age range) stored in variable names
-   Unusual characters in city and variable names
-   Mix of aggregate data with raw data (region totals and overall total)
-   Corresponding region not included with city
    -   New England: MA, CT, RI
    -   Mid. Atlantic: NY, PA, NJ
    -   E.N. Central: OH, IL, MI, IN, WI
    -   W.N. Central: IA, MN, KS, MO, NE; Lincoln, NC?
    -   S. Atlantic: GA, MD, NC, FL, VA, D.C., DE
    -   E.S. Central: AL, TN, KY
    -   W.S. Central: TX, LA, AR, OK
    -   Mountain: NM, ID, CO, NV, UT, AZ
    -   Pacific: CA, HI, OR, WA

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(tidyr)
library(stringr)

tidy <- raw %>%
    rename(city = `Reporting Area`, 
           year = `MMWR YEAR`, 
           week = `MMWR WEEK`, 
           coordinates = `Location 1`) %>%
    gather(age_range, mortalities, `All causes, by age (years), All Ages`:`P&I† Total, flag`) %>%
    mutate(city = iconv(city, "latin1", "ASCII", sub = ""),
           age_range = iconv(age_range, "latin1", "ASCII", sub = "-"),
           age_range = str_replace_all(age_range, "---", "-"),
           age_range = str_replace_all(age_range, "All causes, by age \\(years\\),", ""),
           age_range = str_replace_all(age_range, ", flag", ""),
           age_range = str_replace_all(age_range, "P&I- Total", "pna_inf"),
           age_range = str_trim(age_range, "both"),
           mortalities = str_replace_all(mortalities, "-", 0),
           city = str_replace_all(city, "Lincoln, NC", "Lincoln, NE")) %>%
    drop_na(mortalities) %>%
    mutate(mortalities = as.numeric(mortalities)) %>%
    arrange(city, year, week, age_range) %>%
    select(-`Location 2`) %>%
    filter(!city %in% c("New England", "Mid. Atlantic", "E.N. Central", "W.N Central", "S. Atlantic", "E.S. Central", "W.S. Central", "Mountain", "Pacific", "Total"))
```

    ## Warning in eval(substitute(expr), envir, enclos): NAs introduced by
    ## coercion

``` r
tidy$region <- case_when(str_detect(tidy$city, "MA|CT|RI") ~ "New England",
                         str_detect(tidy$city, "NY|PA|NJ") ~ "Mid. Atlantic",
                         str_detect(tidy$city, "OH|IL|MI|IN|WI") ~ "E.N. Central",
                         str_detect(tidy$city, "IA|MN|KS|MO|NE") ~ "W.N. Central",
                         str_detect(tidy$city, "GA|MD|NC|FL|VA|D.C.|DE") ~ "S. Atlantic",
                         str_detect(tidy$city, "AL|TN|KY") ~ "E.S. Central",
                         str_detect(tidy$city, "TX|LA|AR|OK") ~ "W.S. Central",
                         str_detect(tidy$city, "NM|ID|CO|NV|UT|AZ") ~ "Mountain",
                         str_detect(tidy$city, "CA|HI|OR|WA") ~ "Pacific")    

write_csv(tidy, "lecture_02_data_tidy.csv")
```

Questions
---------

1.  In which week in Houston were the largest number of mortalities reported among patients 45 years and older?
2.  What city in the US had the largest number of mortalities reported in a given week among patients 25 to 64 years old, and in what week did this occur?
3.  During which week was the largest average number of mortalities per city reported among patients 25 years and older for cities within the W.S. Central region, and what was the average?

### Week with largest number of mortalities in Houston, TX

``` r
q1 <- tidy %>%
    filter(city == "Houston, TX",
           age_range == "GE 65" | age_range == "45-64") %>%
    group_by(year, week) %>%
    summarize(mortalities = sum(mortalities, na.rm = TRUE)) %>%
    arrange(desc(mortalities))
```

``` r
q1[1, ]
```

    ## Source: local data frame [1 x 3]
    ## Groups: year [1]
    ## 
    ##    year  week mortalities
    ##   <int> <int>       <dbl>
    ## 1  2014    13         536

### City with the largest number of mortalities in US

``` r
q2 <- tidy %>%
    filter(age_range == "25-44" | age_range == "45-64") %>%
    group_by(city, year, week) %>%
    summarize(mortalities = sum(mortalities, na.rm = TRUE)) %>%
    arrange(desc(mortalities))
```

``` r
q2[1, ]
```

    ## Source: local data frame [1 x 4]
    ## Groups: city, year [1]
    ## 
    ##                city  year  week mortalities
    ##               <chr> <int> <int>       <dbl>
    ## 1 New York City, NY  2014     3         422

### Highest average number of mortalities per week in W.S. Central region

``` r
q3 <- tidy %>%
    filter(region == "W.S. Central",
           age_range == "GE 65" | age_range == "45-64" | age_range == "25-44") %>%
    group_by(city, year, week) %>%
    summarize(mortalities = sum(mortalities, na.rm = TRUE)) %>%
    group_by(year, week) %>%
    summarize(mortalities = mean(mortalities, na.rm = TRUE)) %>%
    arrange(desc(mortalities))
```

``` r
q3[1, ]
```

    ## Source: local data frame [1 x 3]
    ## Groups: year [1]
    ## 
    ##    year  week mortalities
    ##   <int> <int>       <dbl>
    ## 1  2014     2    164.3333
