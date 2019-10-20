# CME.assistant

<!-- badges: start -->
<!-- badges: end -->
__Under development__

The goal of CME.assistant is to share reuseable helper functions within the CME team.

## Installation

Please install from github:
``` {r}
devtools::install_github("UnicefDAPM/CME.assistant")
```

## UNICEF color scheme
```{r}
library(CME.assistant)
str(UNICEF_colors)
```

## Functions for data engineering
### Input
```{r}
# get CME mortality rate for certain years 
get.CME.data(year_range = c(2016:2018))[1:3]

# get CME death numbers for certain years
get.CME.data(year_range = c(2016:2018), "deaths")[1:3]

# get country info
get.country.info()[1:3, 1:5]
```

### Output
```{r}
# Write several dataset into one xlsx file:
xlsx.writeMultipleData("myworkbook.xlsx", mtcars, Titanic, sheet_name = c("dt1", "dt2"))
# to remove the file saved
file.remove("myworkbook.xlsx")
```

## Functions for making plots
```{r}
# use `ggsave.figs` to save ggplot into both pdf and png
# P.S. __SHAPforxgboost__ was my last package offering some simple ggplot visualization functions

ggplot_sample <- ggplot2::qplot(data = iris, x = Sepal.Length, y = Petal.Length)
ggsave.figs(ggplot_sample, file_name = "Iris_sample", folder_name = "figures")
# to remove the file saved
unlink(here::here("figures"), recursive = TRUE)


# Ads: if you wish to give a try, __SHAPforxgboost__ was my last package offering some simple ggplot visualization functions
install.packages("SHAPforxgboost")
SHAPforxgboost::scatter.plot.diagonal(data = iris, x = "Sepal.Length", y = "Petal.Length")


# a helpful function to revise labels, you can provide a __new_list__ to define the labels
get.label(c("2", "3"))
get.label(c("a","b", "c"), new_list = list("a" = "a new label"))

```

