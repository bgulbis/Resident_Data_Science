Data Analysis and Exploration
========================================================
author: Brian Gulbis
date: December 9, 2016
autosize: true
css: custom.css

Objectives
========================================================
type: mhtmc

* Need for exploring data
* Visualizing data as part of exploration

You finally have some data!!!
========================================================
type: mhtmc
incremental: true

* Now what?
* Perform an exploratory data analysis

Exploratory Data Analysis
========================================================
type: mhtmc

* Goal is to understand your data
* Identify possible patterns and relationships
* Two methods
    - Create summaries
    - Visualize

Summaries
========================================================
type: mhtmc

* Calculate summaries on your data
    - Discrete data
        + Counts
        + Proportions
    - Continuous data
        + Means
        + Medians

Visualization
========================================================
type: mhtmc

* Use rudimentary plots to examine the data
* Helps to identify patterns and areas of additional exploration
* Many researches skip this step... but you shouldn't!

Example
========================================================
type: mhtmc

* Anscombe dataset

```
  x1 x2 x3 x4   y1   y2    y3   y4
1 10 10 10  8 8.04 9.14  7.46 6.58
2  8  8  8  8 6.95 8.14  6.77 5.76
3 13 13 13  8 7.58 8.74 12.74 7.71
4  9  9  9  8 8.81 8.77  7.11 8.84
5 11 11 11  8 8.33 9.26  7.81 8.47
6 14 14 14  8 9.96 8.10  8.84 7.04
```

Summaries of Example Set
========================================================
type: mhtmc


|group | mean_x| sd_x| mean_y| sd_y|
|:-----|------:|----:|------:|----:|
|1     |      9| 3.32|    7.5| 2.03|
|2     |      9| 3.32|    7.5| 2.03|
|3     |      9| 3.32|    7.5| 2.03|
|4     |      9| 3.32|    7.5| 2.03|

Statistical Comparison
========================================================
type: mhtmc


```

	Pairwise comparisons using t tests with pooled SD 

data:  df$x and df$group 

  1 2 3
2 1 - -
3 1 1 -
4 1 1 1

P value adjustment method: holm 
```

Statistical Comparison - ANOVA
========================================================
type: mhtmc


```
Analysis of Variance Table

Response: x
          Df Sum Sq Mean Sq F value Pr(>F)
group      3      0       0       0      1
Residuals 40    440      11               
```

Assessment of the Data
========================================================
type: mhtmc
incremental: true

* How many think the groups are the same?
* Let's plot the data

Visualization of Example Set
========================================================
type: mhtmc
incremental: true

![plot of chunk unnamed-chunk-5](lecture_05-figure/unnamed-chunk-5-1.png)

Visualization
========================================================
type: mhtmc

* Without plotting the data, we would have assumed the groups were the same

Types of Plots
========================================================
type: mhtmc

* Scatterplots
* Box plots
* Bar plots
* Line plots
