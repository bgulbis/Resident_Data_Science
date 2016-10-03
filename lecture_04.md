Organizing Data for Analysis
========================================================
author: Brian Gulbis and Jennifer Gass
date: October 5, 2016
autosize: true

Objectives
========================================================

* Verbs for Data Tidying

Data Tidying Actions
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

Wide vs. Long
========================================================



Sharing Data
========================================================

* For faster analysis turnaround, include the following
    - Raw data
    - Tidy data
    - Code book
    - Instruction list

<small>https://github.com/jtleek/datasharing</small>

Components of Tidy Data
========================================================

* Video - Leek J., Coursera - Getting and Cleaning Data

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
