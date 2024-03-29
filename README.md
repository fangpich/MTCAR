---
title: "Motor Trend Car Road Tests"
author: "fangpich"
date: "2023-12-03"
output:
  html_document:
    df_print: paged
  pdf_document: default
  html_notebook: default
---
# Motor Trend Car Road Tests
he data was extracted from the 1974 Motor Trend US magazine, and comprises fuel consumption and 10 aspects of automobile design and performance for 32 automobiles (1973–74 models).

![cars](https://images.unsplash.com/photo-1667123057116-40cbf20e5a9d?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D.jpg)
```{r}
library(dplyr)
library(ggplot2)
library(ggthemes)
library(magrittr)
```

```{r}
mpg %>%
  count( manufacturer,class) %>%
  ggplot(aes(x = manufacturer, y = n, fill = class)) +
  geom_col() +
  theme_minimal() +
  scale_fill_brewer(palette = "Set3")

```

>This graph represents the manufacturers which manufacture various types of cars.

 -  Audi, Toyota, and Honda are the top three manufacturers with the most diverse car lineups. They produce cars across all car types except for pickup trucks.

 -  Chevrolet, Ford, and Nissan are the next three manufacturers with a wide range of car types, including all but 2-seaters.

- Subcompact and compact cars are the most popular categories, with the majority of manufacturers producing these types of vehicles.

- Only a few manufacturers, namely Audi, Toyota, Honda, GMC, and Lincoln, produce pickup trucks.

- SUVs are the least common car type, with only half of the manufacturers producing them.

>>Overall, the graph provides a comprehensive overview of the car types manufactured by different companies, highlighting the popularity of specific categories and the diversified product portfolios of top automakers.

```{r}
mpg %>%
  ggplot(aes(cty,fill = class))+
  geom_bar()+
  theme_minimal()+
  scale_fill_brewer(palette = "Accent")
  
```

>The graph shows the average city mileage (MPG) of different car classes. The data is presented in a bar graph, with each bar representing a different class of car. The height of each bar indicates the average city MPG for that class.
Here is a table summarizing the key takeaways from the graph:

Class	   |Average MPG
---------|------------
2-seater |     22.8
         |
Compact  |	   28.6
         |
Midsize	 |     29.8
         |
Minivan	 |    26.7
         |
Pickup	 |     20.5
         |
Subcompact|   31.7
          |
SUV	      |   25.4
 

As you can see, subcompact cars generally have the highest average city MPG, followed by compact cars. Midsize and minivans also have relatively good city MPG, while pickup trucks have the lowest average city MPG.

```{r}
mpg %>%
  ggplot(., aes(cty, hwy, fill = class, color = class)) +
  geom_point() +
  theme_minimal() +
  scale_fill_brewer(palette = "Accent") +
  facet_wrap(class~manufacturer)+
  facet_wrap(~manufacturer,ncol=3)
```
> This graph show relation between hwy (highway miles per gallon) and cty (city miles per gallon)
  compare by class of cars and manufacturer.City MPG refers to driving with occasional stopping and braking, simulating the conditions you're likely to run into while driving on city streets. Highway MPG is based on more continuous acceleration, which usually yields a higher figure because it's a more efficient use of the engine.
  
  - Overall, highway MPG is higher than city MPG. This is because highway driving typically involves less stopping and braking, which allows the engine to operate more efficiently.
  
  -  Subcompact and compact cars have the highest average city and highway MPG. This is likely due to their smaller size and weight, which makes them more aerodynamic and fuel-efficient.
   -  Pickup trucks have the lowest average city and highway MPG. This is likely due to their larger size and weight, as well as their powerful engines.
   
   -  There is a significant variation in city and highway MPG within each car class and manufacturer. This is likely due to factors such as the specific model of car, the engine and transmission type, and the features that are equipped.
   

```{r}
mpg %>%
  ggplot(aes(cty,hwy,fill = drv,color = drv))+
  geom_point()+
  theme_minimal() +
  scale_fill_brewer(palette = "Accent")
```
> This point graph shows city MPG and highway MPG grouped by drive train type (f = front-wheel drive, r = rear-wheel drive, 4 = 4-wheel drive). The highest point on the graph is for front-wheel drive vehicles, which indicates that front-wheel drive is generally the most fuel-efficient type of drive train.

>This is likely because front-wheel drive vehicles have less complex drivetrains than rear-wheel drive or 4-wheel drive vehicles. This means that there is less friction and energy loss in the drivetrain, which leads to better fuel economy.

>In addition, front-wheel drive vehicles are typically lighter than rear-wheel drive or 4-wheel drive vehicles. This is because they do not need the additional components that are required for rear-wheel drive or 4-wheel drive. Lighter vehicles also tend to be more fuel-efficient.

>Overall, the graph shows that front-wheel drive is the most fuel-efficient type of drive train. This is likely due to the fact that front-wheel drive vehicles have less complex and lighter drivetrains.
Here is a more concise description:
 Front-wheel drive vehicles have the highest city and highway MPG, making them the most fuel-efficient type of drive train.

```{r}
mpg %>%
  ggplot(aes(class,hwy,fill = fl))+
  geom_col() +
facet_wrap(~year,ncol=2)
```
>  the relationship between city MPG and highway MPG for different car classes and manufacturers. 
he data is presented in a point graph, with each point representing a different car model. The size of each point represents the sales volume of that model.

>- Overall, highway MPG is higher than city MPG. This is because highway driving typically involves less stopping and braking, which allows the engine to operate more efficiently.
- Subcompact and compact cars have the highest average city and highway MPG. This is likely due to their smaller size and weight, which makes them more aerodynamic and fuel-efficient.
- Pickup trucks have the lowest average city and highway MPG. This is likely due to their larger size and weight, as well as their powerful engines.
- There is a significant variation in city and highway MPG within each car class and manufacturer. This is likely due to factors such as the specific model of car, the engine and transmission type, and the features that are equipped model.
























