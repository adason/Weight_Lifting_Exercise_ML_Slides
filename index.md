---
title       : Introduction to Machine Learning Prediction App
subtitle    : on Weight Lifting Exercise Dataset
author      : You-Cyuan Jhang
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

- This app is build from the Weight Lifting Exercise Dataset collected by Groupware@LES. For more information about the dataset, see their [website](http://groupware.les.inf.puc-rio.br/har).

- The main description about my data preprocessing step is presented in my Practical Machine Learning Course Project [writeup](http://adason.github.io/Weight_Lifting_Exercise_ML/tree_based_prediction.html).

- This shiny app is very hepful in the visualization of preprocessed data. Meanwhile, the parameter tuning of machine learning predictions can also be demostred in this app. In particular, I am using comparing the performace of generalized linear model with `L1` (lasso) and `L2` (ridge) regularizations.

- Link to the [App](https://adason.shinyapps.io/wle_app/), [Documsntation](https://github.com/adason/Weight_Lifting_Exercise_ML_App/blob/master/README.md), and [Source](https://github.com/adason/Weight_Lifting_Exercise_ML_App)


--- .class #id 

## Interactive Plotting

- On the top left panel, you can choose changing the number of principle components that you want to use as features in machine leraning model. This gives the user some flexibility to choose the feature space size. Including more principle components might slow down the app since you have to perform machine learning on bigger feature space.

- To visualize multidimentional data, in most cases, you have to go into the code and change the part `aes(x = PC1, y = PC2)` manually to plot different principle components. This app allows you to print out the x and y axies for visualiazaion. 


--- .class #id

## Example
- Changeing code like this just to get plots of different axies is very tedius


```r
source("global.R", echo = FALSE)
df <- cbind(classe = wle_testing_y, wle_testing)
ggplot(df, aes(x = PC1, y = PC2)) + geom_point(aes(color = classe))
```

![plot of chunk plot_demo](assets/fig/plot_demo.png) 

--- .class #id

## Explore Parameters

- In the bottom panel of this app, you can control the type of regularizaions that you want to incluse in the taining model. You can choose to perform just L1 regularization (lasso) or L2 regularization (ridge), or you can include both.

- This is very flexable and the user doen't have to write lots of code to get some idea of the maching learning models. Besides, I can use presentation tab to hide some of the less interesting results. The use can consult these result anytime they want, without getting their hands dirty by changeing codes.
