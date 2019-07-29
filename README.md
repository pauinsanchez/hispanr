# hispanr package (v 0.1.0)
This is a personal package I created to simplify the process of creating simple choropleth maps for Spanish provinces. 

## Installation
In order to install this package, just call the development version from GitHub:
``` r
install.packages("devtools")
devtools::install_github("pauinsanchez/hispanr")
```

## How to use
The structure of the function `provmap` is the following
```r
provmap(data, a, color)
```
The user only needs to provide a file containing the variable values for each province to be represented in the choropleth map. This has to be done using the national standard code for each of the provinces, as in file  `base.csv` that can be found in the `data-raw` folder. Once this information has been imported as a dataframe, it can be included in the function as the `data` argument. `a` is a vector with the interval breakpoints for the variable, which will represent the different colors of the map. `color` corresponds to any of the color palettes of the `ColorBrewer` package, which you can see [here](http://colorbrewer2.org/).
