Data Storage and Associated Implications
========================================================
author: Brian Gulbis and Jennifer Gass
date: August 31, 2016
autosize: true

Objectives
========================================================

* Data organization
* Tidy vs. messy data
* Data storage options
* Data types
* File naming

Data Organization
========================================================

* Good data organization will facilitate sharing and analysis
* Data typically organized in rows and columns
    - Rows: observations
    - Columns: variables
* Should follow the principles of "tidy data"

***

id | age | sex
---|-----|----
1 | 54 | male
2 | 72 | female
3 | 45 | female

Principles of Tidy Data
========================================================

* Each variable should be in one column
    - Data within the column should be of the same type
* Each observation of that variable should be in a different row
* Variable names should be stored in the first row
    - Names should be descriptive and readable
    - Use minimal abbreviations
    - Avoid having spaces in name
        + Good: med_name, sedativeRate
        + Bad: clnevnt, ce, clinical event

<small>Wickham, H. Tidy data. J Stat Software 2014; 59 (10)</small>

Principles of Tidy Data
========================================================

* Variables of different "kinds" should be stored in separate tables
    - Ex: Diagnostic data stored separately from vital sign data
* Each table should be stored in its **own file**
* Multiple tables should have a column which allows them to be linked

<small>Wickham, H. Tidy data. J Stat Software 2014; 59 (10)</small>

Common Problems with Messy Data
========================================================

* Column headers are values, not variable names
* Multiple variables are stored in one column
* Variables are stored in both rows and columns
* Multiple types of observational units are stored in the same table
* A single observational unit is stored in multiple tables

<small>Wickham, H. Tidy data. J Stat Software 2014; 59 (10)</small>

Headers are Values
========================================================

religion|<$10k|$10-20k|$20-30k|$30-40k|$40-50k|$50-75k
--------|-----|-------|-------|-------|-------|-------
Agnostic|27|34|60|81|76|137
Atheist|12|27|37|52|35|70
Buddhist|27|21|30|34|33|58
Catholic|418|617|732|670|638|1116
Don't know/refused|15|14|15|11|10|35
Evangelical Prot|575|869|1064|982|881|1486
Hindu|1|9|7|9|11|34
Historically Black Prot|228|244|236|238|197|223
Jehovah's Witness|20|27|24|24|21|30
Jewish|19|19|25|25|30|95

<small>Data from: [Pew Research Center](http://pewforum.org/Datasets/Dataset-Download.aspx)</small>

<small>Wickham, H. Tidy data. J Stat Software 2014; 59 (10)</small>

Tidy Version
========================================================

religion | income | freq
---------|--------|------
Agnostic|<$10k|27
Agnostic|$10-20k|34
Agnostic|$20-30k|60
Agnostic|$30-40k|81
Agnostic|$40-50k|76
Agnostic|$50-75k|137
Atheist|<$10k|12
Atheist|$10-20k|27

Multiple Variables in Each Column
========================================================

country|year|m014|m1524|m2534|m3544|m4554|m5564|m65|f014
-------|----|----|-----|-----|-----|-----|-----|---|----
AD|2000|0|0|1|0|0|0|0|-
AE|2000|2|4|4|6|5|12|10|3
AF|2000|52|228|183|149|129|94|80|93
AG|2000|0|0|0|0|0|0|1|1
AL|2000|2|19|21|14|24|19|16|3
AM|2000|2|152|130|131|63|26|21|1
AN|2000|0|0|1|2|0|0|0|0
AO|2000|186|999|1003|912|482|312|194|247
AR|2000|97|278|594|402|419|368|330|121
AS|2000|-|-|-|-|1|1|-|-

<small>Data from: World Health Organization</small>

<small>Wickham, H. Tidy data. J Stat Software 2014; 59 (10)</small>

Tidy Version
========================================================

country | year | sex | age | cases
--------|------|-----|-----|------
AD|2000|m|0-14|0
AD|2000|m|15-24|0
AD|2000|m|25-34|1
AD|2000|m|35-44|0
AD|2000|m|45-54|0
AD|2000|m|55-64|0
AD|2000|m|65+|0
AE|2000|m|0-14|2
AE|2000|m|15-24|4
AE|2000|m|25-34|4

Variables Stored in Rows and Columns
========================================================

id|year|month|element|d1|d2|d3|d4|d5|d6|d7|d8
---|----|-----|-------|---|---|---|---|---|---|---|---
MX17004|2010|1|tmax|-|-|-|-|-|-|-|-
MX17004|2010|1|tmin|-|-|-|-|-|-|-|-
MX17004|2010|2|tmax|-|27.3|24.1|-|-|-|-|-
MX17004|2010|2|tmin|-|14.4|14.4|-|-|-|-|-
MX17004|2010|3|tmax|-|-|-|-|32.1|-|-|-
MX17004|2010|3|tmin|-|-|-|-|14.2|-|-|-
MX17004|2010|4|tmax|-|-|-|-|-|-|-|-
MX17004|2010|4|tmin|-|-|-|-|-|-|-|-
MX17004|2010|5|tmax|-|-|-|-|-|-|-|-
MX17004|2010|5|tmin|-|-|-|-|-|-|-|-

<small>Data from: Global Historical Climatology Network</small>

<small>Wickham, H. Tidy data. J Stat Software 2014; 59 (10)</small>

Tidy Version
========================================================

id | date | tmax | tmin
---|------|------|-----
MX17004|2010-01-30|27.8|14.5
MX17004|2010-02-02|27.3|14.4
MX17004|2010-02-03|24.1|14.4
MX17004|2010-02-11|29.7|13.4
MX17004|2010-02-23|29.9|10.7
MX17004|2010-03-05|32.1|14.2

Data Storage
========================================================

* Spreadsheets (Excel, Google Sheets, etc.)
* Text files (delimited: csv, tab, etc.)
* Databases (Access, SQL Server, MySQL, PostgreSQL, etc.)

Spreadsheets
========================================================

* Commonly used by most people
* Usually works if organized appropriately
* Potential issues
    - Compatibility varies depending on file type
    - Calculated cells may not transfer correctly
    - Limits on number of rows that can be stored
    - No record of any transformations which were done

<small>https://github.com/jtleek/datasharing</small>

Reproducibility
========================================================

* Given your original data, someone else should be able to repeat your analysis and obtain the same results
* It is **essential** to keep track of step-by-step changes made to the data
    - Keep a code book which outlines how you got from messy data to tidy data
    - Your collaborators will greatly appreciate it
        + Especially "future you"

Data Analysis and Spreadsheets
========================================================
type: prompt

<small>Bryan J. jailbreakr: Get out of Excel, free. useR! Conference 2016</small>

Spreadsheet Do's and Don'ts
========================================================

* Do
    - Start in cell **A1**
        + Row 1 column names
    - Keep data in one sheet
    - Save tidy data in new file
    - Put analysis in separate file
        + Tables, charts, etc.

***

* Don't
    - Highlight, format, or merge cells
    - Use macros
    - Use spreadsheet as your data collection form
    - Manipulate data without recording what you did

Text Files
========================================================

* Highest degree of compatibility
* No limit on number of rows or columns
* Only the values are retained
    - No information about column types or cell formatting

<small>https://github.com/jtleek/datasharing</small>

Data Types
========================================================

* Continuous
* Ordinal and Categorical
    - In general, avoid coding as numbers
        + Sex should be "female" or "male"
        + Hypertension should be "true" or "false"
    - Will avoid coding errors when entering data
    - Will avoid confusion when interpreting data
    - Some programs may interpret numbers as continuous data

<small>https://github.com/jtleek/datasharing</small>

Missing Data
========================================================

* Missing data should be coded as NA
* Censored data
    - Know something about the missing data
        + Lab value outside detectable range
    - Still coded as NA, but add a new column which indicates the data is censored

<small>https://github.com/jtleek/datasharing</small>

File Naming
========================================================

* Bad
    - myabstract.docx
    - Joe's Filenames Use Spaces and Punctuation.xlsx
    - figure 1.png
    - fig 2.png
    - JW7d^(2sl@deletethisandyourcareerisoverWx2*.txt

<small>[Reproducible Science Curriculum](https://rawgit.com/Reproducible-Science-Curriculum/rr-organization1/master/organization-01-slides.html)</small>

File Naming
========================================================

* Good
    - 2014-06-08_abstract-for-sla.docx
    - joes-filenames-are-getting-better.xlsx
    - fig01_scatterplot-talk-length-vs-interest.png
    - fig02_histogram-talk-attendance.png
    - 1986-01-28_raw-data-from-challenger-o-rings.txt


File Naming Principles
========================================================

1. Machine readable
1. Human readable
1. Follows default ordering

<small>[Reproducible Science Curriculum](https://rawgit.com/Reproducible-Science-Curriculum/rr-organization1/master/organization-01-slides.html)</small>

Machine Readable
========================================================

* Avoid spaces, punctuation, case sensitivity
* Use delimiters to facilitate searching
    - "_" underscore to delimit sections
    - "-" hyphen to delimit words within sections
* Example
    - 2014-06-08_abstract-for-sla.docx

<small>[Reproducible Science Curriculum](https://rawgit.com/Reproducible-Science-Curriculum/rr-organization1/master/organization-01-slides.html)</small>

Human Readable
========================================================

* Name contains information on content
* Example
    - fig01_scatterplot-talk-length-vs-interest.png
    - fig02_histogram-talk-attendance.png

<small>[Reproducible Science Curriculum](https://rawgit.com/Reproducible-Science-Curriculum/rr-organization1/master/organization-01-slides.html)</small>

Follows Default Ordering
========================================================

* Put something numeric first
    - 01_raw-data.csv
    - 02_tidy-data.csv
* Use "YYYY-MM-DD" standard for dates
    - 2014-06-08_abstract-for-sla.docx
* Left pad with zeros (01, 02, etc.), or else you get
    - 10_final-figs-for-publication.r
    - 1_data-cleaning.r
    - 2_fit-model.r

<small>[Reproducible Science Curriculum](https://rawgit.com/Reproducible-Science-Curriculum/rr-organization1/master/organization-01-slides.html)</small>

Summary
========================================================

* Data organized in rows and columns
* Follow tidy data principles
* Store data in ways that will facilitate sharing and analysis
* Use standard data types and denote missing data
* Naming your files wisely and keeping a code book will be much appreciated by "future you"

Let's Work with Some Data
========================================================
type: section

Data Set
========================================================

1. Go to https://data.cdc.gov
1. Click on the dataset: TABLE III. Deaths in 122 U.S. cities
1. Click the Export button and save to your computer
1. Open the file and explore the data

* What problems can you identify with the way the data is stored and organized?

Questions
========================================================

1. In which week in Houston were the largest number of mortalities reported among patients 45 years and older?
1. What city in the US had the largest number of mortalities reported in a given week among patients 25 to 64 years old, and in what week did this occur?
1. During which week was the largest average number of mortalities per city reported among patients 25 years and older for cities within the W.S. Central region, and what was the average?

