# MA \[46\]15 Homework 5
**`[==[`**Your Name**`]==]`**

## Question 1

In this work I’ll analyze the titles of the most recent 10,000 papers in
the [Criminal Justice category](https://www.ssrn.com/index.cfm/en/cjrn/)
of the [Social Science Research
Network](https://www.ssrn.com/index.cfm/en/) preprint repository. The
data in file `data/ssrn_cjn.rds` is loaded into the table `papers`. As
an initial check, I’m plotting the distribution of number of words in
title for each year.

**`[==[`** Modify the `q1` chunk below to load `ssrn_cjn.rds` into the
dataset `papers`. Create a new variable `word_count` with the number of
words in each title and then make boxplots of number of words per title
for each year. Write a short assessment about the variability of title
sizes over the years. How many papers have exactly one word in the
title? **`]==]`**

``` r
suppressPackageStartupMessages(library(tidyverse))
```

## Question 2

**`[==[`** Modify chunk `q2` below to “cross” each title in `papers`
with each keyword in `keywords` and then check if each title contains
each keyword. Before checking, however, convert the words in the title
to lower case since the keywords are all in lower case. Store the
outcome of the check, `FALSE` if keyword is absent, `TRUE` if present in
title, in a new variable called `keyword_in_title`. Then, for each year
and keyword, count the total number of times papers with each keyword
were downloaded; stored in variable `n`. Finally, using `pivot_wider`,
cross-tabulate these counts for the last ten years by indexing rows by
year and columns by keyword. Your final table should like the output of
this chunk but with different numbers.

    # A tibble: 6 × 8
       year crimin eviden international justice polic right violen
      <dbl>  <int>  <int>         <int>   <int> <int> <int>  <int>
    1  2018   1461    747           198    1240  1656   171    371
    2  2019   1573   1061          1708     936   820   929   2032
    3  2020   1812   2071           200     295   165  1626   1724
    4  2021    718   1506           687     609   439   776   1323
    5  2022   2054   2057           652     812  1071  1952   1804
    6  2023   1034   1861          1349     145   255  1413   1706

**`]==]`**

``` r
keywords <- tibble(keyword = 
                     c("crimin", "justice", "polic", 
                       "eviden", "violen", "right", "international")
                   )
# example of crossing between two tables:
crossing(tibble(x = 1:3), tibble(y = letters[1:3]))
```

    # A tibble: 9 × 2
          x y    
      <int> <chr>
    1     1 a    
    2     1 b    
    3     1 c    
    4     2 a    
    5     2 b    
    6     2 c    
    7     3 a    
    8     3 b    
    9     3 c    

## Question 3

**`[==[`** It’s hard to assess counts in a table, so, in a chunk labeled
`q3`, make a line plot of the counts you computed in Question 2, one
line per keyword (color each line by keyword). Comment on any specific
patterns; for instance, what seems to be the most commonly downloaded
keyword? Any keywords declining or increasing in interest? **`]==]`**

## Question 4

**`[==[`** The counts for some keyword can be changing simply because
the number of overall downloads is changing with the years. Thus,
instead of plotting counts, make line plots of the **proportion** of
total downloads in each year that had each keyword in their titles. To
this end, in a `q4` chunk, first create a new dataset called
`papers_year` with the counts of the total downloads per year and then
**join** this with the title-keyword crossed dataset in Question 2. Then
compute a new variable called `prop` with the proportion of titles
containing each keyword by year. Finally, create the plot. Do your
conclusions change when compared to the plot in Question 3? Comment.
**`]==]`**
