# R-markdown-gun-deaths

---
title: "ANA 515 Assignment 1 - Zhiying Chen zc0102"
author: Zhiying Chen
date: 6/4/2022
output: html_document
---


```{r setup, include = FALSE}
#The include = FALSE function hides both the code and output in my output document

#You need to install these packages first to be able to use the functions within them. You can install them from the Tools tab or write a new code chunk: install.packages("package_name"). 
library(tidyverse)
library(knitr)
library(bslib)
```

```{r, include=FALSE}
url <- "https://raw.githubusercontent.com/fivethirtyeight/guns-data/master/full_data.csv"
gun_deaths <- read_csv(url)
```


```{r, include=FALSE}
youth <- gun_deaths %>% 
  filter(age <= 65)
```

`r nrow(gun_deaths) - nrow(youth)`

``` {r, echo = FALSE}
#This next code chunk will make a plot in our output doc
```

```{r youth-dist, echo = FALSE} 
youth %>% 
  ggplot(aes(age)) + 
  geom_freqpoly(binwidth = 1) 
```

# Gun deaths by race 
```{r race-dist, echo = FALSE} 
youth %>% 
  ggplot(aes(fct_infreq(race) %>% fct_rev())) + 
  geom_bar() + coord_flip() + 
  labs(x = "Victim race") 
```

```{r, echo = FALSE}
