Organizing Data for Analysis
========================================================
author: Brian Gulbis and Jennifer Gass
date: October 5, 2016
autosize: true

Objectives
========================================================

* Actions for Data Manipulation
* Exploratory Analysis
* Data Validation
* Sharing Data

Reminder
========================================================
type: alert

* Do __NOT__ perform exploration or manipulation of the original data!

Data Manipulations Actions
========================================================

* Filtering
* Transforming
* Aggregating
* Sorting

<small>Wickham, H. Tidy data. J Stat Software 2014; 59 (10)</small>

Filtering
========================================================

* Selecting observations based on some condition
    - Patients who are > 18 years old
    - Patients admitted between January 1, 2015 and December 31, 2015

Transforming
========================================================

* Creating new variables from existing variables
    - Calculating CrCl and saving in a new column
* Modifying existing variables
    - Converting all weights to same units

Aggregating
========================================================

* Collapse multiple values into a single value
    - Mean of a group of observations
    - Total number of patients who experienced an adverse event

Sorting
========================================================

* Change the order of observations
    - From highest to lowest
    - From first to last

Data Organization
========================================================

* Wide Format
    - Variables are spread
* Long Format
    - Variables are stacked

Wide Format
========================================================

Patient|Date|SBP|DBP|HR
-------|----|---|---|---
1|2016-09-01|145|95|65
2|2016-09-02|156|89|76

Long Format
========================================================

Patient|Date|Measure|Reading
-------|----|-------|-------
1|2016-09-01|SBP|145
1|2016-09-01|DBP|95
1|2016-09-01|HR|65
2|2016-09-02|SBP|156
2|2016-09-02|DBP|89
2|2016-09-02|HR|76

Statistical Analysis
========================================================

* Most statistical programs (i.e., SPSS) need the data in the wide format
    - There should be only one observation per patient
* Data with repeated measures (i.e., BP, temp) is usually best stored in the long format
    - Data should be aggregated into a summary value(s) for analysis

Example
========================================================

* Set of multiple SBP readings for each patient
* Select a method to summarize the data for each patient
    - Min, Max, First, Last
    - Change from First to Last; Change from First to Min
    - AUC of SBP
* Use the summary value for each patient in statistical analysis

Exploratory Analysis
========================================================

* Looking at your data to better understand you have
* Use tables or graphs to visualize data
    - Look for trends
    - Look for outliers
* In Excel, use Pivot Tables and Pivot Charts

Data Validation
========================================================

* __Checking the data to make sure it is accurate is one of the most important steps__
* Almost every data set is going to have mistakes in it
    - Errors at the time data was recorded (charted)
    - Errors on collection
    - Errors when manipulating

Sharing Data
========================================================

* For faster analysis turnaround, include the following
    - Raw data
    - Tidy data
    - Code book
    - Instruction list

<small>https://github.com/jtleek/datasharing</small>

Code Book
========================================================

* Describes each variables in the data set
    - Units of measure
* Provides information about the summary choices made
* Includes information about the experimental study design used

<small>https://github.com/jtleek/datasharing</small>

Instruction List
========================================================

* Step-by-step instructions which describe how to
    - Process raw data into tidy data
    - Analyze tidy data and produce final results
* Results should be reproducible by others
    - Reviewers, readers, future self, etc.
    - Given your raw data, they should be able to replicate the analysis performed

<small>https://github.com/jtleek/datasharing</small>

Sharing Data Example
========================================================

![messy shared data](lecture_04-figure/data_sharing_messy.png)

Sharing Data Example Examined
========================================================



* Diagnosis
    - Number of distinct values: 172
* Alcohol Use


```
   0   NA   nk   Nk   NK   no   nO   No   NO Past  yes  Yes NA's 
   2    1   32    4   91  108    1  133    3    1   17   54    8 
```

* Number of packs/day
    - Contains numeric and non-numeric data
* Column P heading: "If yes"
    - Unclear what this data represents
