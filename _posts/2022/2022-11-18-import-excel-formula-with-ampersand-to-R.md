---
title: "Alternatives of openxlsx when importing Excel to R"
tags: [data, R]
toc: true
---

## The problem of openxlsx

At work, I rely on the R package `openxlsx` heavily and use `openxlsx::read.xlsx` to import excel spreadsheet, which is the most common format in business settings.

Now here is the issue I discovered recently. I have a spreadsheet that contains excel formula which generates value with special character `&`. However when importing the file using `openxlsx::read.xlsx`, all `&` become `&amp;`

Here is the sample of spreadsheet [sample_data.xlsx](https://github.com/ycphs/openxlsx/files/10032200/sample_data.xlsx). This is what it looks like in excel:

| colA                  | colB            |
|-----------------------|-----------------|
| colB is text          | US & Canada     |
| colB is formula (=B2) | US & Canada |

Note that the 2nd observation in colB is a formula "=B2". Therefore the expected result should be the same as the 1st observation.

```R
# Import spreadshet to R
df <- openxlsx::read.xlsx("sample_data.xlsx")
df
                   colA                      colB
1          colB is text               US & Canada
2 colB is formula (=B2)           US &amp; Canada
```

However, after importing to R, the value `&` becomes `&amp;` instead. This is what the result shows in R:

| colA                  | colB            |
|-----------------------|-----------------|
| colB is text          | `US & Canada`     |
| colB is formula (=B2) | `US &amp; Canada` |

## Solution 1: Resolve it in excel

The obvious solution is to get rid of the problem at the beginning. There are many ways can achieve the desired outcome - in the end, what we want is the value in R matches the value in the spreadsheet.

1. **Convert to csv**. Csv is my preferred format as it eliminates lots of format issues in xlsx. The problem is that this will creates multiple files , and people can get confused on which files to use. Besides, it might not be a good option if the file is meant to be a living dataset that need continuous edits.
2. **Paste as value**. Another way to do it is to transform the formula to plain text in excel by pasting as value. If the spreadsheet is okay to be edited and is not too big, it would be an easy solution. 

## Solution 2: Use other packages

Sometimes you probably don't want to touch the raw data. Also, if it's a large dataset, it might be unrealistic to perform such functionality in excel as the solution 1 suggested. Since this issue only occurs when using `openxlsx` package, we can choose other packages as a substitute.

`readxl` is one of the packages belong to tidyverse collections. It's designed to read data out of excel into R for both xls and xlsx, and does not have other dependencies. It's a dependent package outside of tidyverse library so we would need to specifically call it out in R.

`readxl::read_excel` is the substitute we're looking for and it does the job well. 

```R
library(readxl)

# Import
df <- read_excel("sample_data.xlsx")
df
# A tibble: 4 × 2
  colA                  colB                 
  <chr>                 <chr>                
1 colB is text          US & Canada          
2 colB is formula (=B2) US & Canada
```

However, `readxl` has its limitation. Comparing with `openxlsx`, `readxl::read_excel` has less arguments and therefore will possibly generates other format issue. For example, `detectDates` is the argument I use often that `readxl::read_excel` does not have, so I have to recognize dates and perform conversion later. Also, if I need to save the output to spreadsheet, I would need to call out another library `writexl` and it's just not as convenient as the all-in-one package `openxlsx`.

## Looking foward

I still prefer `openxlsx` to other as I like its arguments and it fits the business world well. There's an antecedent package `openxlsx2` on the way - Let's wait and see if it resolves the issue.
