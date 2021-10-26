Project proposal
================
zoomcoders

``` r
library(tidyverse)
library(broom)
```

*For instructions on what each section should include, please see the
[project page](https://idsed.digital/assessments/project/#proposal) on
the course website. Remove this text when completing your proposal*.

## 1. Introduction

For our project, we want to investigate the correlation between infant
mortality rate and overall quality of life. We will do so by joining two
datasets from the kaggle database; one on infant mortality rate trends
by country, and the other being the quality of life index trends by
country over the past ten years. Both these datasets are .csv files.

Each dataset contains values of their respective variable for each
country for a given number of years. Given that the infant mortality
rate dataset has missing data for a lot of countries for most of the
years, we will filter the dataset so that the time frame for both
datasets shows only one year (2019), as this was the year where the most
data was collected for infant mortality rate.

For the purposes of this project, our research question will be “To what
extent does infant mortality rate impact quality of life?”

Through our research question, we aim to see whether there is a strong
positive relationship between the two variables as one would expect, or
if it plays a smaller role in other scenarios.

## 2. Data

``` r
countries_quality_of_life_index <- read_csv("/cloud/project/data/countries_quality_of_life_index.18-10-2021.csv") 
```

    ## Rows: 115 Columns: 3

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Name, NativeName
    ## dbl (1): QualityOfLifeIndex

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
infant_mortality_rate <- read_csv("/cloud/project/data/InfantMortalityRate.csv")
```

    ## Rows: 7625 Columns: 4

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Country, Gender
    ## dbl (2): Infant Mortality Rate, Year

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

> glimpse(countries\_quality\_of\_life\_index) Rows: 115 Columns: 3 $
> Name <chr> “Canada”, “Japan”, “Norway”, “Ireland”, “Hungary”, … $
> NativeName <chr> “Canada”, “日本”, “Kongeriket Norge”, “Eire”, "Magy…
> $ QualityOfLifeIndex <dbl> 159.51190, 165.32691, 173.15817, 153.18219,
> 135.343…

> glimpse(infant\_mortality\_rate) Rows: 7,625 Columns: 4 $ Country
> <chr> “Afghanistan”, “Angola”, “Albania”, “Andorra”,… $
> `Infant Mortality Rate` <dbl> 43.050731, 44.851045, 7.659442,
> 2.555451, 5.71… $ Gender <chr> “Female”, “Female”, “Female”, “Female”,
> "Femal… $ Year <dbl> 2019, 2019, 2019, 2019, 2019, 2019, 2019, 2019…

## 3. Data analysis plan
