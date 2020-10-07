---
title: "From Excel to R: Introduction"
---

## What is R and why?

R is a powerful tool to conduct complicated data analysis. In short, R is an open source programming environment, and RStudio is a common used user interface (IDE) that makes using R easier.

Many people would compare R with Python, to my understanding, both has pros and cons. I chose R simply because it fits my goal better, and I felt the language is easier to read thanks to R's packages.

I am a heavily Excel user, so this section will be focus on the basic functions that I used to perform in Excel.

## Installation and Setup R

Download R from [CRAN official website](https://cloud.r-project.org), then install RStudio from [RStudio website](https://rstudio.com/products/rstudio/).

R has many powerful packages and can be installed from RStudio directly. There're only two packages need to be installed for now: `tidyverse` and `openxlsx`. To do it, go to menu bar - `Tool` - `Install Packages`, put the name of the package and click Install.

## Import CSV and Excel Files

There's some prep needed to be done before any "actual" code. It is essential for every R script.

First is to import the packages that we just installed.

```r
# Import packages
library(tidyverse)
library(openxlsx)
```

Second step is to setup the working directory, which is the default folder to import/export documents.

```r
setwd("/Users/aster/myworkingdir")
```

Then we can import our raw data. Ideally, `csv` is preferred if it is available.

```r
prod <- read.csv('Sales.csv')
sale <- read.csv('Product.csv')
# prod/sale is the assigned name of the imported dataframe
```

If it's `xlsx` file:

```r
df <- read.xlsx('sample.xlsx',          # Name of the workbook
                sheet = 'Sheet 1',      # Name of the worksheet
                na.strings = ""         # Convert blank cell to NA in R
                )
```

## Filter Columns

Filtering in Excel is easy when there're only a few columns. What if there're more than 30+? Even finding the right column takes time. In such cases, R becomes a more handy tool.

```r
# filter Region = Asia
asiaonly <- sale %>% filter(Region == 'Asia')
```

Note that it should be `double equal` when relates to value.

If I want to apply multiple filters, simply add more conditions inside the bracket.


```r
# multiple filters:
# filter 1: Region = Asia
# filter 2: Sales Channel = Online
asiaonly <- sale %>% filter(Region == 'Asia',
                            Sales.Channel == 'Online')
```

## Hide Columns

For example, if we only need to review the first and second columns:

```r
# Show only column 1-2, and hide other columns
twocols <- sale %>% select(1:2)
```

Usually, it's easier to use column names (aka **variables** in R).
```r
# Show Regions and Channel, and hide other columns
anothertwocols <- sale %>% select(Region, Sales.Channel)
```
