Practical Guide for Using AgriPoliS
================
Mark Brady
2019-05-12

**NOTE: Can develop flowcharts with package diagrammeR**

Procedures for creating a region: ~/region
==========================================

The purpose of this paper is to document the steps for calibrating (creating) a new region in AgriPoliS, including the sources of data. The main steps are:

-   *upscaling*: representing the agricultural region
-   *investments*: collate investment data
-   *MIP\_data*: collate market and technical data on production activities
-   *MIP\_input*: develop static optimization model for each typical-farm type
-   *dynamic\_calibration*: validate the dynamic development of farmsin AgriPoliS

Represent the structure of agriculture: ~/upscaling
---------------------------------------------------

Select typical farms and upscale to reprent the structure of agriculture in the region. Refer to Niklas cluster analysis. Identifu farm structure data for the region

Collate investment data: ~/investments
--------------------------------------

Collate data on production activities: ~/MIP\_data
--------------------------------------------------

Identify relevant production activities. Main source of data AgriWise.

Develop static optimization models: ~/MIP\_input
------------------------------------------------

Develop static optimization model for each typical-farm type

Validate development of farms in AgriPoliS: ~/dynamic\_calibration
------------------------------------------------------------------

In this step we create the input files to run an AgriPoliS simulation and validate the reference scenario. The steps for creating these files are:

-   *text*: creates input files.
-   *policysettings*: create individual policy-settings files for simulating alternative policy scenarios.

### Creating input files: ~/text

The MS Excel workbook \*Text\_\[region\_name\_short\]\_\[YYYY-MM-DD\].xlsm\* is a macro-enabled workbook that contains a set of sheets for automaticall generating the input files in text format for simulating a region in AgriPoliS. The sheets are:

-   *History*: document edits to workbook
-   *globals*: global settings
-   *options*: simulation options for specific regions, e.g., number of periods
-   *translations*: for translating variable names that differ between inputfiles and AgriPoliS
-   *farmsdata*: data characterizing the typical farms, e.g., areable area
-   *market*: economic data for production activities, i.e., prices and variable costs
-   *environmental*: data for biodiversity modelling
-   *env\_market*: data for calculating linear environmnetal indicators based on production activity levels.
-   *yield*: coefficients of crop production functions for endogenous yields.
-   *investments*: catalogue of investment activities and underlying data.
-   *capacityLinks*: defines RHS of constraint rows in MIP matrix
-   *matrix*: the generic MIP matrix for optimization of farm-agents decisions
-   *matrixLinks*:values within the *matrix* can be influenced. Normally, used to calculate the share of bounded costs during a production period.
-   *objFuncLinks*: All activities that are in the *matrix*, but not in the *market* or *investments* sheets must be listed here.
-   *\[farmID\_0\_first\]...\[farmID\_last\]*: initial investment capacities of the typical farms. One sheet per farm.

### farmsdata

    #> Warning: package 'tidyverse' was built under R version 3.5.3
    #> -- Attaching packages --------------------------------------------- tidyverse 1.2.1 --
    #> v ggplot2 3.1.1       v purrr   0.3.0  
    #> v tibble  2.0.1       v dplyr   0.8.0.1
    #> v tidyr   0.8.3       v stringr 1.4.0  
    #> v readr   1.3.1       v forcats 0.4.0
    #> Warning: package 'ggplot2' was built under R version 3.5.3
    #> Warning: package 'tibble' was built under R version 3.5.2
    #> Warning: package 'tidyr' was built under R version 3.5.3
    #> Warning: package 'readr' was built under R version 3.5.2
    #> Warning: package 'purrr' was built under R version 3.5.2
    #> Warning: package 'dplyr' was built under R version 3.5.3
    #> Warning: package 'stringr' was built under R version 3.5.2
    #> Warning: package 'forcats' was built under R version 3.5.3
    #> -- Conflicts ------------------------------------------------ tidyverse_conflicts() --
    #> x dplyr::filter() masks stats::filter()
    #> x dplyr::lag()    masks stats::lag()
    #> Warning: package 'gridExtra' was built under R version 3.5.3
    #> 
    #> Attaching package: 'gridExtra'
    #> The following object is masked from 'package:dplyr':
    #> 
    #>     combine
    #> Warning: Missing column names filled in: 'X3' [3], 'X4' [4], 'X5' [5],
    #> 'X6' [6], 'X7' [7], 'X8' [8], 'X9' [9], 'X10' [10], 'X11' [11], 'X12' [12],
    #> 'X13' [13], 'X14' [14], 'X15' [15], 'X16' [16], 'X17' [17]
    #> Parsed with column specification:
    #> cols(
    #>   `#` = col_character(),
    #>   `generated from ===> J<f6>nk<f6>ping 2015.04.14.xlsm` = col_character(),
    #>   X3 = col_character(),
    #>   X4 = col_character(),
    #>   X5 = col_character(),
    #>   X6 = col_character(),
    #>   X7 = col_character(),
    #>   X8 = col_character(),
    #>   X9 = col_character(),
    #>   X10 = col_character(),
    #>   X11 = col_character(),
    #>   X12 = col_character(),
    #>   X13 = col_character(),
    #>   X14 = col_character(),
    #>   X15 = col_character(),
    #>   X16 = col_logical(),
    #>   X17 = col_double()
    #> )
    #> # A tibble: 34 x 17
    #>    `#`   `generated from~ X3    X4    X5    X6    X7    X8    X9    X10  
    #>    <chr> <chr>            <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr>
    #>  1 <NA>  <NA>             <NA>  <NA>  <NA>  <NA>  <NA>  <NA>  <NA>  <NA> 
    #>  2 #     Farm Data Colle~ <NA>  <NA>  <NA>  <NA>  <NA>  <NA>  <NA>  <NA> 
    #>  3 <NA>  <NA>             <NA>  <NA>  <NA>  <NA>  <NA>  <NA>  <NA>  <NA> 
    #>  4 <NA>  NumOfFarms       13    <NA>  <NA>  <NA>  <NA>  <NA>  <NA>  <NA> 
    #>  5 <NA>  Name             IF-D4 IF-D5 IF-D7 IF-D~ IF-D~ IF-D~ IF-D~ IF-G~
    #>  6 <NA>  Farm_Type        5     5     5     5     5     5     5     6    
    #>  7 <NA>  Form_of_Organis~ 1     1     1     1     1     1     1     1    
    #>  8 <NA>  Weighting_Factor 147   218   59    320   73    156   92    393  
    #>  9 #     Weighting        147   218   59    320   73    156   92    393  
    #> 10 #     Number_of_farms  15    22    6     32    7     16    9     39   
    #> # ... with 24 more rows, and 7 more variables: X11 <chr>, X12 <chr>,
    #> #   X13 <chr>, X14 <chr>, X15 <chr>, X16 <lgl>, X17 <dbl>

Procedures for simulating a region in AgriPoliS: ~/projects
===========================================================

To simulate a region in AgriPoliS requires an identical set of input files to those used in the dynamic calibration step. However, in adition to the reference policy scenario it is now necessary to define alternative policy scenarios.

Styles
------

The `html_vignette` template includes a basic CSS theme. To override this theme you can specify your own CSS in the document metadata as follows:

    output: 
      rmarkdown::html_vignette:
        css: mystyles.css

Figures
-------

The figure sizes have been customised so that you can easily put two images side-by-side.

``` r
plot(1:10)
plot(10:1)
```

![](calibration_procedures_files/figure-markdown_github/unnamed-chunk-3-1.png)![](calibration_procedures_files/figure-markdown_github/unnamed-chunk-3-2.png)

You can enable figure captions by `fig_caption: yes` in YAML:

    output:
      rmarkdown::html_vignette:
        fig_caption: yes

Then you can use the chunk option `fig.cap = "Your figure caption."` in **knitr**.

More Examples
-------------

You can write math expressions, e.g. *Y* = *X**β* + *ϵ*, footnotes[1], and tables, e.g. using `knitr::kable()`.

|                   |   mpg|  cyl|   disp|   hp|  drat|     wt|   qsec|   vs|   am|  gear|  carb|
|-------------------|-----:|----:|------:|----:|-----:|------:|------:|----:|----:|-----:|-----:|
| Mazda RX4         |  21.0|    6|  160.0|  110|  3.90|  2.620|  16.46|    0|    1|     4|     4|
| Mazda RX4 Wag     |  21.0|    6|  160.0|  110|  3.90|  2.875|  17.02|    0|    1|     4|     4|
| Datsun 710        |  22.8|    4|  108.0|   93|  3.85|  2.320|  18.61|    1|    1|     4|     1|
| Hornet 4 Drive    |  21.4|    6|  258.0|  110|  3.08|  3.215|  19.44|    1|    0|     3|     1|
| Hornet Sportabout |  18.7|    8|  360.0|  175|  3.15|  3.440|  17.02|    0|    0|     3|     2|
| Valiant           |  18.1|    6|  225.0|  105|  2.76|  3.460|  20.22|    1|    0|     3|     1|
| Duster 360        |  14.3|    8|  360.0|  245|  3.21|  3.570|  15.84|    0|    0|     3|     4|
| Merc 240D         |  24.4|    4|  146.7|   62|  3.69|  3.190|  20.00|    1|    0|     4|     2|
| Merc 230          |  22.8|    4|  140.8|   95|  3.92|  3.150|  22.90|    1|    0|     4|     2|
| Merc 280          |  19.2|    6|  167.6|  123|  3.92|  3.440|  18.30|    1|    0|     4|     4|

Also a quote using `>`:

> "He who gives up \[code\] safety for \[code\] speed deserves neither." ([via](https://twitter.com/hadleywickham/status/504368538874703872))

[1] A footnote here.
