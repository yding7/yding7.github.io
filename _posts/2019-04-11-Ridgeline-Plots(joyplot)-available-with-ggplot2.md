---
published: true
layout: post
author: Yulun Ding
categories: journal
tags:
  - ggplot2
images: fg1.png
---
Today I am going to introduce an extension available for ggplot2 to create so-called ridgeline plots. I think the packages were created a long time ago by Claus O. Wilke (I will put related links for references…). I was surprised that I found this so late.

So what is a ridgeline plot? Basically, the plot tells the same story as a heatmap but looks much easier to interpret the trend within a group (y-axis) instead of between the group.

As introduced on Mr. Wilke GitHub, the package is already available on CRAN and should work perfectly fine with all the functions used on ggplot2. This is why I am so excited about these packages and would love to share.

Note:
- x: continuous 
- y: Discrete 
- fill: Discrete or Continous

Download package:
```
install.packages("ggridges")
```
 An example similar to the one on Github:

x: Continuous 
y: Discrete 
fill: Discrete
```
data("mtcars")
library(tidyverse)
library(ggridges)
Ridgelineplot<-
  ggplot(diamonds,
         aes(x = price,
             y = cut,
             fill = cut))
Ridgelineplot + geom_density_ridges()
```
![fg1.png]({{site.baseurl}}/assets/img/fg1.png)

Another example:
- x: Continuous 
- y: Discrete 
- fill: Continous

- With “geom_density_ridges_gradient()”, the fill aesthetic can vary along the x-axis.fill can be used for a continuous variable
```
ggplot(diamonds,
         aes(x = price,
             y = cut,
             fill = ..x..)) + 
    geom_density_ridges_gradient()
#The fill aesthetic can vary along the x axis.fill can be used for a continous variable
```
![fg2.png]({{site.baseurl}}//assets/img/fg2.png)
Other function available for you to explore:
```
# These are all easy to use if you are ggplot heavy user
geom_ridgeline()
stat__density_ridges()
```
## Advise to use in practice:
- You can use more scale related function to edit the plot,
- Add theme function to look more professional.
```
Ridgelineplot + 
  scale_y_discrete(expand = c(0.01, 0)) +
  scale_x_continuous(limits = c(-100,20000), expand = c(0.01, 0))
```
![fg3.png]({{site.baseurl}}//assets/img/fg3.png)
Here are the explanations from the R Documentation

`limits` A numeric vector of length two providing limits of the scale. Use NA to refer to the existing minimum or maximum.

`expand` Vector of range expansion constants used to add some padding around the data, to ensure that they are placed some distance away from the axes. Use the convenience function expand_scale() to generate the values for the expandargument. The defaults are to expand the scale by 5% on each side for continuous variables, and by 0.6 units on each side for discrete variables.



Mr Ding
