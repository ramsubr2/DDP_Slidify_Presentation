---
title       : Analyzing College Earnings Data 
subtitle    : Data analysis based on recently released White House report 
author      : Ramesh Subramanian
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

###Context for Data Analysis
The White House recently released a report on the state of College Education in the U.S.
Data collected from 7804 colleges offering a 4 year degree was analyzed along the following dimensions, 6, 8, and 10 years after completion of degree.  
1. Academics
2. cost of education
3. Earnings  
4. Debt

###Sources of Data and reports on findings 
1. Policy paper: www.whitehouse.gov/college/policy.html   
2. Technical paper: www.whitehouse.gov/college/technical.html  
3. Raw Data:  www.collegeboard.edu/collegeScoreCard (7804 rows, 109 variables)

###This report  
1.  Subset analyzing only 6 year data.  
2.  Only along dimensions of Earnings and Debt
3.  Processed raw data to extract fields of interest (7804 rows, 12 variables).  
4.  Imputed missing values with median value of column.  
5.  Data file for analysis (and on github): collegeEarningsData.csv


--- .class #id 

## Slide 2: Earnings of Top and Bottom 25 Colleges

###Top 25 Colleges

###Bottom 25 Colleges

## Shiny server code to display earnings data

```r
    output$school_table <- renderTable({ 
      var <- switch(input$var, 
                     "Top 20 colleges for earnings" = mean_earnings_display_top25,
                     "Bottom 20 Colleges for earnings" = mean_earnings_display_bottom25)
      })
```

--- .class #id

## Slide 3: Percent Graduates earning more than $25K

###Top 25 Colleges

##Some Code

###Bottom 25 Colleges

## Shiny server code to display data

```r
    output$school_table <- renderTable({ 
      var <- switch(input$var, 
                     "% students earning > $25K among top 25 Colleges" = gt_25k_earnings_display_top25,
                     "% students earning > $25K among bottom 25 Colleges" = gt_25k_earnings_display_bottom25)    })
```

--- .class #id

## Slide 4: Median Debt of Households by Income levels

###Income Level Classification  
1.  Low Income: Median Earnings per year of $0-$30,000
2.  Middle Income: Median Earnings per year of $30,001-$75,000
3.  High Income: Median Earnings per year greater than $75,000

## Shiny server code to display data

```r
    output$school_table <- renderTable({ 
      var <- switch(input$var, 
                     "Average Debt among Low, Medium and High Income families" = debt_data)
       })
```

--- .class #id

## Slide 5: Conclusions

### Professional Degree colleges pay higher  

1. 24 out of 25 top colleges had earnings higher than $75,000 per year
2. Range of earnings for bottom 25 colleges was $9000 - $13,000

### There are many who are making less than $25,000 6 years after graduation


### Average debt levels seem to be about the same regardles sof income levels

### Fatal flaw: Qualitative aspects of education ignored.
