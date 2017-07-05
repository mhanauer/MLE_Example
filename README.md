---
title: "MLE_Example"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Create a fake dataset with missing values and then run with regular regression.  Could run with CFA and SEM.  
```{r}
set.seed(123)
data = data.frame(y = rnorm(100), x1 = rnorm(100), x2 = rnorm(100), x3 = rnorm(100))
is.na(data) = data < -1
sum(is.na(data))

head(data)

library(lavaan)
model = "
y ~ b1*x1 + b2*x2 + b3*x3
"
fit = sem(model, data = data, missing = "fiml")
summary(fit)
```

