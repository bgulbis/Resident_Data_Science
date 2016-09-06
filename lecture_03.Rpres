Collecting Data Efficiently
========================================================
author: Brian Gulbis and Jennifer Gass
date: September 7, 2016
autosize: true

Objectives
========================================================

* Discuss common data collection mistakes
* Design a data collection form

Primary Goal of Data Collection
========================================================
incremental: true

* Gather all data needed for a project as __efficiently__ and __accurately__ as possible

Data Collection Exercise
========================================================
type: sub-section

* https://github.com/bgulbis/Resident_Data_Science/blob/master/lecture_03_example_data_collection.xlsx

Common Mistakes
========================================================

* Trying to collect and analyze everything in the same place
* Minimal preparation and testing
* Using tools which are not designed for efficient data collection
    - Poorly organized fields
    - Spreadsheets (without a data entry form)
* Recording aggregated data
    - Platelet decrease > 50% from baseline
    - Heparin dose in units/day

Separate Steps
========================================================
* Think of each step in process separately
    - Data collection
    - Data tidying
    - Data analysis
* Each should occur in own place (file) using tools designed for that step

Preparation - Form Design
========================================================

* Organize to facilitate efficient data collection
    - Data points should be grouped based on where they are in the medical record
    - May be different than how we group information to analyze
* Have choices to select from as much as possible
    - Faster than writing / typing
    - Ensures consistency in data entry

Why Make a Form if Pulling Data Electronically?
========================================================

* Helps to visualize all of the data points
    - Better able to determine if anything is missing
* Using a form (can be electronic) reduces data entry errors

Spreadsheets for Data Collection
========================================================

* If not properly designed
    - Easy to have inconsistent data entry
    - Easy to enter data in wrong place
    - Beware automatic type conversion
        + Ex: Dates
* Use a data entry form to get data into spreadsheet
* Use data validation to minimize entry errors

Data Entry Forms
========================================================

* Excel Data Form
    - Quick Access Toolbar -> More Commands
    - Choose commands from -> All Commands
    - Scroll to Form and click Add
* More customizable forms can be made for Excel using VBA and macros
* Google Forms
    - Links to Google Sheets
    - More customizable than basic Excel form

Aggregated Data
========================================================

* Often done for endpoints which must be calculated from multiple observations or data points
    - Think it will save time
    - Unsure how to store repeat observations (i.e., vital signs, infusion rates, etc.)
* Recommend collecting the raw data instead
    - Calculation errors at time of entry are hard to detect
    - Aggregate data may not allow for additional exploratory analysis

Recording Multiple Observations
========================================================

* Each group of repeat measures should be in a separate file
* Have an ID field which links to main table
    - patient_id
* Have a field which distinguishes each observation
    - date and time
    - obeservation number

Multiple Observations Example
========================================================

patient_id|date_time|heart_rate
----------|---------|----------
1|2016-05-01 08:05:00|74
1|2016-05-02 08:10:00|68
1|2016-05-03 09:23:00|81
2|2015-07-23 10:36:00|77
2|2015-07-25 11:12:00|93

Linking to Data in Another Spreadsheet
========================================================
type: sub-section

Design a Better Data Collection Form
========================================================
type: sub-section

Summary
========================================================

* Approach data collection, tidying, and analysis separately
    - Use tools specifically designed for each
* Develop a data collection form and test it for efficiency and accuracy
* Use a data entry form when using spreadsheet
* Collect raw data, not aggregated data
