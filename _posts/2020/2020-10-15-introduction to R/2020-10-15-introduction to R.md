---
title: "From Excel to R: Beginner's Guide on Data Manipulation"
tags: [R, data]
---

## What is R and why?

R is a powerful tool to conduct complicated data analysis. In short, R is an open source programming environment, and RStudio is a common used user interface (IDE) that makes using R easier.

Many people would compare R with Python, to my understanding, both has pros and cons. I chose R simply because it fits my goal better, and I felt the language is easier to read thanks to R's packages.

I am a heavily Excel user, so this section will be focus on the basic functions that I used to perform in Excel.

## Installation and Setup R

Download R from [CRAN official website](https://cloud.r-project.org), then install RStudio from [RStudio website](https://rstudio.com/products/rstudio/).

R has many powerful packages and can be installed from RStudio directly. There're only two packages need to be installed for now: `tidyverse` and `openxlsx`. To do it, go to menu bar - `Tool` - `Install Packages`, put the name of the package and click Install.

## Import csv/xlsx Files

There's some prep needed to be done before any "actual" code. It is essential for every R script.

First is to import the packages that we just installed.

```r
# Import packages
library(tidyverse)
library(openxlsx)
```

Second step is to setup the working directory, which is the default folder to import/export documents. R only recognizes forward slash, which is contrary to Windows' backslash, so you would need to make changes if you are on Windows system.

```r
setwd("/Users/aster/myworkingdir")
```

Then we can import our raw data. Ideally, `csv` is preferred if it is available.

```r
sale <- read.csv('Sales.csv')
# prod/sale is the assigned name of the imported dataframe
```

If the file is `xlsx`, the function would be `read.xlsx` instead, and we need to specify the name of worksheet when importing.

```r
df <- read.xlsx('sample.xlsx',          # Name of the workbook
                sheet = 'Sheet 1',      # Name of the worksheet
                na.strings = ""         # Convert blank cell to NA in R
                )
```

Let's take a glimpse on the imported dataframe.

<!-- ![](/assets/sale.head.png) -->
![](sale.head.png)

## Filter Columns

Filtering in Excel is not difficult when there're only a few columns. What if there're more than 30? Even finding the right column takes time. In such cases, R becomes a handy tool. We put names in the script instead of searching through endless columns, and R has the autocomplete feature when typing the name, making the process even smoother.

```r
# filter Region = Asia
asiaonly <- sale %>% filter(Region == 'Asia')
```

Note that it should be `double equal` if it relates to specific value (e.g. strings, integer).

To apply multiple filters, simply add more conditions inside the bracket.

```r
# multiple filters:
# filter 1: Region = Asia
# filter 2: Sales Channel = Online
asiaonly <- sale %>% filter(Region == 'Asia',
                            Sales.Channel == 'Online')
```

## Remove Unwanted Columns

For example, if we only need to review the first and second columns:

```r
# Show only first two clumns, and remove other columns
regioncountry <- sale %>% select(1:2)
```

Usually, it's easier to use column names (aka **variables** in R) when dealing with non-consecutive columns.

```r
# Show Regions and Channel only, and remove other columns
regionchannel <- sale %>% select(Region, Sales.Channel)
```

If we want to remove a certain column while keep everything else, apply a minus sign in front of variables.

```r
# Remove Channel column
nochannel <- sale %>% select(-Sales.Channel)
```

Those are basic functions that I've been used all the time. Next post I'll introduce more advanced functions that Excel normally cannot handle.
