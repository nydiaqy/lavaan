---
editor_options: 
  markdown: 
    wrap: 72
---

# lavaan HIHI

lavaan is a free, open source R package for latent variable analysis.
You can use lavaan to estimate a large variety of multivariate
statistical models, including path analysis, confirmatory factor
analysis, structural equation modeling and growth curve models.

The lavaan package is developed to provide useRs, researchers and
teachers a free open-source, but commercial-quality package for latent
variable modeling. The long-term goal of lavaan is to implement all the
state-of-the-art capabilities that are currently available in commercial
packages. However, lavaan is still under development, and much work
still needs to be done.

## Installation

Install the stable version from CRAN:

``` r
install.packages("lavaan")
```

Or the development version from GitHub:

``` r
# install.packages("remotes")
remotes::install_github("yrosseel/lavaan")
```

## Usage

To get a first impression of how lavaan works in practice, consider the
following example of a SEM model (the Political Democracy Example from
Bollen's 1989 book):

```{r}
library(lavaan)

model <- '
   # latent variable definitions
     ind60 =~ x1 + x2 + x3
     dem60 =~ y1 + y2 + y3 + y4
     dem65 =~ y5 + y6 + y7 + y8
   # regressions
     dem60 ~ ind60
     dem65 ~ ind60 + dem60
   # residual covariances
     y1 ~~ y5
     y2 ~~ y4 + y6
     y3 ~~ y7
     y4 ~~ y8
     y6 ~~ y8
'
fit <- sem(model, data = PoliticalDemocracy)
summary(fit)
```

More information can be found on the website: <https://lavaan.org>
