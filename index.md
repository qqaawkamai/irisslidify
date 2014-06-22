---
title       : Iris Prediction App
subtitle    : Predict the type of Iris
author      : qqaawkamai
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## What does the app do?

- Iris is a genus of flowering plants.
- Iris means rainbow in Greek.
- Pretty much the coolest looking flowers out there.
- 3 species of Iris that are predicted in this model are:
    - Iris setosa
    - Iris versicolor
    - Iris virgincia
- Model takes the Petal and Sepal dimensions (length and width) and accurately
predicts the species of Iris.

--- .class #id 

## The Data

The Edgar Anderson Iris dataset (provided in R) is used in the app.


```r
data(iris)
summary(iris)
```

```
##   Sepal.Length   Sepal.Width    Petal.Length   Petal.Width 
##  Min.   :4.30   Min.   :2.00   Min.   :1.00   Min.   :0.1  
##  1st Qu.:5.10   1st Qu.:2.80   1st Qu.:1.60   1st Qu.:0.3  
##  Median :5.80   Median :3.00   Median :4.35   Median :1.3  
##  Mean   :5.84   Mean   :3.06   Mean   :3.76   Mean   :1.2  
##  3rd Qu.:6.40   3rd Qu.:3.30   3rd Qu.:5.10   3rd Qu.:1.8  
##  Max.   :7.90   Max.   :4.40   Max.   :6.90   Max.   :2.5  
##        Species  
##  setosa    :50  
##  versicolor:50  
##  virginica :50  
##                 
##                 
## 
```

--- .class #id

## The Model

Random Forest library is used to build a fairly accurate prediction model based on Sepal and Petal dimensions.


```r
library(randomForest)
```


```r
modFit <- randomForest(Species ~., data=iris)
modFit$err.rate[500,1]
```

```
##     OOB 
## 0.04667
```

```r
modFit$confusion
```

```
##            setosa versicolor virginica class.error
## setosa         50          0         0        0.00
## versicolor      0         47         3        0.06
## virginica       0          4        46        0.08
```

--- .class #id

## The Model - continued

- The model has a very low error rate (~5%).
- From the confusion matrix, we see that very few are misclassified.
- Thus, putting in the Petal and Sepal dimensions in the app, will accurately
predict the species of iris.
- [Link to Shiny App](https://qqaawkamai.shinyapps.io/iris/)
