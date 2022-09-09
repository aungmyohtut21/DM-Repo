githubrepo
================
Aung Myo Htut
2022-09-09

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.2 --
    ## v ggplot2 3.3.6     v purrr   0.3.4
    ## v tibble  3.1.7     v dplyr   1.0.9
    ## v tidyr   1.2.0     v stringr 1.4.0
    ## v readr   2.1.2     v forcats 0.5.1
    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
git <- read_csv("https://raw.githubusercontent.com/aungmyohtut21/DM-Repo/de8f6200dde87e535fd6a2d4a040c900bc9d6673/DiabetesAtlasData.csv")
```

    ## Rows: 3142 Columns: 6
    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr (3): Year, County, State
    ## dbl (3): County_FIPS, Diagnosed Diabetes Percentage, Overall SVI
    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
view(git)
```

``` r
nrow(git)
```

    ## [1] 3142

``` r
ncol(git)
```

    ## [1] 6

\#county with highest diabetes rate

``` r
new_data <- git%>% arrange(desc(git$`Diagnosed Diabetes Percentage`)) %>% group_by(git$County)
new_data
```

    ## # A tibble: 3,142 x 7
    ## # Groups:   git$County [1,877]
    ##    Year  County_FIPS County               State          Diagn~1 Overa~2 git$C~3
    ##    <chr>       <dbl> <chr>                <chr>            <dbl>   <dbl> <chr>  
    ##  1 2018        46102 Oglala Lakota County South Dakota      17.9   0.994 Autaug~
    ##  2 2018        45089 Williamsburg County  South Carolina    17.2   0.970 Baldwi~
    ##  3 2018        12039 Gadsden County       Florida           16.1   0.990 Barbou~
    ##  4 2018        35031 Mckinley County      New Mexico        15.9   0.989 Bibb C~
    ##  5 2018        46121 Todd County          South Dakota      15.9   0.956 Blount~
    ##  6 2018        46137 Ziebach County       South Dakota      15.9   0.954 Bulloc~
    ##  7 2018        28133 Sunflower County     Mississippi       15.7   0.949 Butler~
    ##  8 2018        54005 Boone County         West Virginia     15.7   0.704 Calhou~
    ##  9 2018        21133 Letcher County       Kentucky          15.4   0.876 Chambe~
    ## 10 2018        46041 Dewey County         South Dakota      15.3   0.883 Cherok~
    ## # ... with 3,132 more rows, and abbreviated variable names
    ## #   1: `Diagnosed Diabetes Percentage`, 2: `Overall SVI`, 3: `git$County`
    ## # i Use `print(n = ...)` to see more rows
