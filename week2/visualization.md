## Visualization

```library("tidyverse")```

[ggplot2 condensed](https://raw.githubusercontent.com/rstudio/cheatsheets/master/data-visualization-2.1.pdf)

### Scatter plot

```

ggplot(data = diamonds, aes(carat, price)) +
  geom_point()
  
ggplot(data = diamonds, aes(carat, price, color = cut))+
  geom_point()
  
ggplot(data = diamonds, aes(carat, price))+
  geom_point(color = "green")
  
ggplot(data = diamonds, aes(carat, price))+
  geom_point(aes(color = cut))
```

dplyr, ggplot2

```

diamonds %>%
  ggplot(aes(carat, price, shape = cut))+
  geom_point()

diamonds %>%
  ggplot(aes(carat, price, label = color))+
  geom_text()
  
diamonds %>%
  slice(1:100) %>% 
  ggplot(aes(carat, price, label = color))+
  geom_label()
  
diamonds %>%
  ggplot(aes(carat, price, color = cut))+
  geom_point() + 
  labs(x = "wt (carat)",
       y = "price ($)",
       title = "Price & weight relation",
       subtitle = "Data taken from diamonds dataset",
       caption = "plot is made with ggplot2 library")+
  theme(legend.position = "bottom") # theme() has huge functionality
  
diamonds %>%
  ggplot(aes(carat, price, color = cut))+
  geom_point()+
  annotate(geom = "rect", xmin = 4.8, xmax = 5.2,
           ymin = 17500, ymax = 18500, fill = "red", alpha = 0.2) + 
  annotate(geom = "text", x = 4.7, y = 16600,
           label = "help...\n I am in a red\nsquare")
```

### Bar plot

```
misspelling <- read_csv("misspelling_dataset.csv")
```
+ The variable spelling is aggregated: count represents the number of misspellings -- we can use ```geom_col()```
+ The variable correct is not aggregated: we see repeated values -- we can use ```geom_bar()```

```
misspelling %>% 
  slice(1:20) %>% 
  ggplot(aes(spelling, count))+
  geom_col()
```

Let's flip the axes:

```
misspelling %>% 
  slice(1:20) %>% 
  ggplot(aes(spelling, count))+
  geom_col()+
  coord_flip()
```
```
misspelling %>% 
  ggplot(aes(correct))+
  geom_bar()
```
  
Let's flip the axes:

```
misspelling %>% 
  ggplot(aes(correct))+
  geom_bar()+
  coord_flip()
```

We can aggregate non-aggregated values:

```
diamonds %>% 
  count(cut)
```

We can turn an aggregated variant into a non-aggregated:

```
diamonds %>% 
  count(cut) %>% 
  uncount(n)
```

### Factors

```
my_factor <- factor(misspelling$correct)
head(my_factor)

levels(my_factor)

levels(my_factor) <- rev(levels(my_factor))
head(my_factor)

misspelling %>% 
  mutate(correct = factor(correct, levels = c("deschanel",
                                              "galifianakis",
                                              "johansson",
                                              "kaepernick",
                                              "labeouf",
                                              "macaulay",
                                              "mcgwire",
                                              "mclachlan",
                                              "minaj",
                                              "morissette",
                                              "palahniuk",
                                              "picabo",
                                              "poehler",
                                              "shyamalan",
                                              "mcconaughey"))) %>% 
  ggplot(aes(correct))+
  geom_bar()+
  coord_flip()
  
#fct_reorder reorders factor levels by sorting along another variable
misspelling %>% 
  count(correct) %>% 
  ggplot(aes(fct_reorder(correct, n), n))+
  geom_col()+
  coord_flip()
  
diamonds %>% 
  mutate(cut = fct_reorder(cut, price, mean)) %>% 
  ggplot(aes(cut)) +
  geom_bar()

#multiple geom_
misspelling %>% 
  count(correct) %>% 
  ggplot(aes(fct_reorder(correct, n), n, label = n))+
  geom_col()+
  geom_text(nudge_y = 150)+
  coord_flip()
```
