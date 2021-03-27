# Visualizations
Working through some R tutorials and during that time, will be collating a lot of visuals here.
Most of the plots/graphics are built with the ggplot2 package (grammer of graphic package in R);
Some visuals will be just basic R plots.
..... ..pending.



library(tidyverse)
library(Amelia)


# Load Data
library(gapminder)

#check for missing values with missmap(missmap is from the Amelia package)
missmap(gapminder)

 ---- Exploratory data analysis -----

#step 1: convert gapminder to a data frame (need this to perform cluster and PCA analysis):

gp <- gapminder %>% filter(year == 2007) %>% 
  select(c(country, lifeExp, pop, gdpPercap)) %>%
  as.data.frame() %>% set_rownames(.[,1]) %>%
  .[,-1]

#step 2: scale data.frame (this is needed for PCA and clustering analysis):
gp1 <- scale(gp)

#step 3: Perform PCA:

gp2 <- prcomp(gp1, scale = T)

biplot(gp, cex = .7)

#comment: 
