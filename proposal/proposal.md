Project proposal
================
zoomcoders

``` r
library(tidyverse)
library(broom)
```

## 1. Introduction

For our project, we want to investigate how the development of a country
can impact the health of its citizens. For the purposes of this project,
our research question will be “To what extent does economic development
lead to better quality of life?”

Through our project, we aim to see whether more developped countries
have better quality of life. While this would be expected, we will look
to see if there are any instances where development has a negative
correlation with certain elements of quality of life.

To analyse this, we will be using multiple datasets. As our dataset for
development, we will use the Human Development Index by country, as that
is a good indication of development in a country. For the other factors,
we will look at datasets such as infant mortality by country, current
health expenditure (% of GDP) by country, births attended by skilled
health personnel by country, healthy life expectancy at birth (HALE) by
country, maternity mortality ratio by country, leading causes of death
by country, suicide rates by country, and population living below income
poverty line, national poverty line (%) by country.

Throughout this project, we aim to test the hypothesis that “Higher
development leads to better quality of life”.

Our datasets will be coming from: -
<http://hdr.undp.org/en/indicators/137506> -
<http://hdr.undp.org/en/indicators/181806> -
<http://hdr.undp.org/en/indicators/39006> -
<https://www.who.int/data/gho/data/indicators/indicator-details/GHO/gho-ghe-hale-healthy-life-expectancy-at-birth>
-
<https://www.who.int/data/gho/data/indicators/indicator-details/GHO/maternal-mortality-ratio-(per-100-000-live-births)>
-
<https://www.who.int/data/gho/data/themes/mortality-and-global-health-estimates/ghe-leading-causes-of-death>
- <https://www.who.int/data/gho/data/themes/mental-health/suicide-rates>
-
<https://www.who.int/data/gho/data/indicators/indicator-details/GHO/births-attended-by-skilled-health-personnel-(-)>

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

``` r
human_development_index <- read_csv("/cloud/project/data/HumanDevelopmentIndex.csv")
```

    ## New names:
    ## * `` -> ...2
    ## * `` -> ...3
    ## * `` -> ...4
    ## * `` -> ...5
    ## * `` -> ...6
    ## * ...

    ## Rows: 211 Columns: 61

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (32): Human Development Index (HDI), ...2, ...3, ...5, ...7, ...9, ...11...
    ## lgl (29): ...4, ...6, ...8, ...10, ...12, ...14, ...16, ...18, ...20, ...22,...

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
healthy_life_expectancy_at_birth <- read_csv("/cloud/project/data/Healthy_life_expectancy_at_birth.csv")
```

    ## Rows: 4392 Columns: 34

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (14): IndicatorCode, Indicator, ValueType, ParentLocationCode, ParentLoc...
    ## dbl  (3): Period, FactValueNumeric, Value
    ## lgl (17): IsLatestYear, Dim2 type, Dim2, Dim2ValueCode, Dim3 type, Dim3, Dim...

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

We will plot “Quality of Life Index” on the Y axis and “Infant Mortality
Rate” on the X axis, not grouping the data, since we have only 1 entry
for both variables for each country. To prepare the data for what we
want to use we will select the Total Infant mortality rates for 2019 and
unite them with the Quality of Life data, so that we can have a new
modified data set that has a value for “Country” corresponding to
“Infant Mortality Rate” and “Quality of Life Index”. Then we will plot a
Jitter or Point graph with this new data set. To confirm or deny the
relation we will need to check to what extent the points seem to follow
a certain pattern. The stronger a pattern seems to be, the more sure we
can be that there is some sort of relation between our chosen variables.
