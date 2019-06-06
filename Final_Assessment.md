---
title: "Advanced Bioinformatics 2019 Assessment"
author: '9513'
date: "06/06/2019"
output: 
  html_document:
   keep_md: yes  
---



## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


```r
summary(cars)
```

```
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
```

## Including Plots

You can also embed plots, for example:

![](Final_Assessment_files/figure-html/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.


```r
"Task 1"
```

```
## [1] "Task 1"
```

```r
sum(5:55)
```

```
## [1] 1530
```

```r
"Task 2"
```

```
## [1] "Task 2"
```

```r
sumfun<-function(n){
  sum(5:n)
}
sumfun(10)
```

```
## [1] 45
```

```r
sumfun(20)
```

```
## [1] 200
```

```r
sumfun(100)
```

```
## [1] 5040
```


```r
"Task 3"
```

```
## [1] "Task 3"
```

```r
a=1
b=1

print(a)
```

```
## [1] 1
```

```r
print(b)
```

```
## [1] 1
```

```r
for(i in 1:12) {
  c=a+b
  print(c)
  a=b
  b=c
}
```

```
## [1] 2
## [1] 3
## [1] 5
## [1] 8
## [1] 13
## [1] 21
## [1] 34
## [1] 55
## [1] 89
## [1] 144
## [1] 233
## [1] 377
```

```r
"Task 4"
```

```
## [1] "Task 4"
```

```r
#Import ggplot2
library(ggplot2)
#Load the data
data(mtcars)
#Convert miles per gallon into a factor from numeric 
mtcars$gear<-as.factor(mtcars$gear)
#Generate a box plot of gear against mpg and color by gear 
ggplot(mtcars, aes(x=gear,y=mpg,fill=gear)) + geom_boxplot()
```

![](Final_Assessment_files/figure-html/unnamed-chunk-4-1.png)<!-- -->


```r
"Task 5"
```

```
## [1] "Task 5"
```

```r
#Fit a linear model with lm, with cars data (speed and breaking distance)
model<-lm(dist~speed,data=cars)
summary(model)
```

```
## 
## Call:
## lm(formula = dist ~ speed, data = cars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -29.069  -9.525  -2.272   9.215  43.201 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept) -17.5791     6.7584  -2.601   0.0123 *  
## speed         3.9324     0.4155   9.464 1.49e-12 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 15.38 on 48 degrees of freedom
## Multiple R-squared:  0.6511,	Adjusted R-squared:  0.6438 
## F-statistic: 89.57 on 1 and 48 DF,  p-value: 1.49e-12
```

```r
"Task 6"
```

```
## [1] "Task 6"
```

```r
plot(data=cars, dist~speed)
abline(model)
```

![](Final_Assessment_files/figure-html/unnamed-chunk-6-1.png)<!-- -->


```r
"Task 7 - part 1"
```

```
## [1] "Task 7 - part 1"
```

```r
library(ggplot2)
data("cars")
additional_speed <- cars$speed * (5280/3600)
lm_2 <- lm(dist ~ 0 + additional_speed + I(additional_speed^2), cars)
summary(lm_2)
```

```
## 
## Call:
## lm(formula = dist ~ 0 + additional_speed + I(additional_speed^2), 
##     data = cars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -28.836  -9.071  -3.152   4.570  44.986 
## 
## Coefficients:
##                       Estimate Std. Error t value Pr(>|t|)   
## additional_speed       0.84479    0.38180   2.213  0.03171 * 
## I(additional_speed^2)  0.04190    0.01366   3.067  0.00355 **
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 15.02 on 48 degrees of freedom
## Multiple R-squared:  0.9133,	Adjusted R-squared:  0.9097 
## F-statistic: 252.8 on 2 and 48 DF,  p-value: < 2.2e-16
```

```r
"Task 7 - part 2"
```

```
## [1] "Task 7 - part 2"
```

```r
y <- cars$dist
x <- cars$additional_speed
ggplot(cars, aes(additional_speed, dist)) + geom_point() + geom_smooth(method='lm', formula="y~0+x+I(x^2)") + labs(title ="Average reaction time", x="Additional Speed (seconds)", y="Distance (feet)")
```

![](Final_Assessment_files/figure-html/unnamed-chunk-8-1.png)<!-- -->


