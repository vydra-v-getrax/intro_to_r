## tidyverse

https://www.tidyverse.org/


   + ```ggplot2``` for visualization
   + ```tibble``` to work with tibbles, modern dataframes 
   + ```tidyr``` for the tidy data format
   + ```readr``` to read files
   + ```dplyr``` for data manipulation
   + ```stringr``` to work with string variables
   + ```forcats``` to work with factor variables

   + ```readxl``` to read .xls and .xlsx
   + ```jsonlite``` to work with JSON
   + ```tidytext``` to work with texts and corpora
 etc.
 
 ```
 library("tidyverse")
 ```
 
 To determine your workdirectory: ```getwd()``` and ```setwd(.../path/to/your/directory)```
 
 ```
 read_csv("...")
 
 read_csv("/home/user_name/work/data/my_file.csv")
 ```
 
 + ```read_tsv()``` – for files with tab separators
 + ```read_csv2()``` – for files with ; separator
 + ```read_delim(file = "...", delim = "...")``` – for files with a separator in the delim argument

 If there are no names for the columns, include ```col_names = FALSE```
 
 If you have problems with encoding, try to include this: ```locale(encoding = "UTF-8")```
 
 To read .xls (```read_xls```) and .xlsx (```read_xlsx```):
 
 ```
library("readxl")
xlsx_example <- read_xlsx("...")
 ```
 
 ```
 misspellings <- read_csv("misspelling_dataset.csv")
 
 diamonds
 ?diamonds
 ```
 
 #### tibble
 
 An alternative to the dataframe format
 
 ```
 month.name
 
 #we get an error since the variable was not created by us
 data.frame(id = 1:12,
           months = month.name,
           n_letters = nchar(months))
           
 data.frame(id = 1:12,
           months = month.name,
           n_letters = nchar(month.name))
           
 tibble(id = 1:12,
       months = month.name,
       n_letters = nchar(months))
       
df <- data.frame(id = 1:12,
                 months = month.name)

df

as_tibble(df)
 ```
 
 #### dplyr
 
 + ```dplyr::filter()```

To filter rows based on columns:

```
misspellings %>%
  filter(count < 10)
```

```%>%``` — pipe sends the result of the work of one function to the other function 

```
sort(sqrt(abs(sin(1:22))), decreasing = TRUE)

1:22 %>% 
  sin() %>% 
  abs() %>% 
  sqrt() %>% 
  sort(., decreasing = TRUE)
```

+ ```dplyr::slice()```

To filter rows based on their index

```
misspellings %>%
  slice(3:7)
```

+ ```dplyr::select()```

To select columns:

```
diamonds %>%
  select(8:10)
  
diamonds %>%
  select(color:price)
  
diamonds %>%
  select(-carat)
  
diamonds %>%
  select(-c(carat, cut, x, y, z))
  
diamonds %>%
  select(cut, depth, price)
```

#### dplyr::arrange()

For sorting:

```
misspellings %>%
  arrange(count)
  
diamonds %>%
  arrange(desc(carat), price)
```

#### dplyr::distinct()

Returns unique values in a column:

```
misspellings %>%
  distinct(correct)
  
misspellings %>%
  distinct(spelling)
  
diamonds %>%
  distinct(color, cut)
```

#### dplyr::mutate()

To create new variables:

```
misspellings %>%
  mutate(misspelling_length = nchar(spelling),
         id = 1:n())
```

#### dplyr::group_by(...) %>% summarise(...)

```
misspellings %>%
  summarise(min(count), mean(count))
  
misspellings %>%
  group_by(correct) %>% 
  summarise(mean(count))
  
misspellings %>%
  group_by(correct) %>% 
  summarise(my_mean = mean(count))
  
misspellings %>%
  group_by(correct) %>% 
  summarise(n = n())
  
misspellings %>%
  count(correct)
  
misspellings %>%
  count(correct, sort = TRUE)

#to create an additional column
misspellings %>%
  group_by(correct) %>% 
  mutate(my_mean = mean(count))
```

### Joining the dataframes

#### bind_...

To join different dataframes

```
my_tbl <- tibble(a  = c(1, 5, 2), 
                 b = c("e", "g", "s"))
                 
my_tbl %>% 
  bind_rows(my_tbl)
```

#### dplyr::..\_join()

```
languages <- data_frame(
  languages = c("Selkup", "French", "Chukchi", "Polish"),
  countries = c("Russia", "France", "Russia", "Poland"),
  iso = c("sel", "fra", "ckt", "pol")
  )
  
languages

country_population <- data_frame(
  countries = c("Russia", "Poland", "Finland"),
  population_mln = c(143, 38, 5))
country_population

inner_join(languages, country_population)

left_join(languages, country_population)

right_join(languages, country_population)

anti_join(languages, country_population)

anti_join(country_population, languages)

full_join(country_population, languages)
```

[Explanation](https://hollyemblem.medium.com/joining-data-with-dplyr-in-r-874698eb8898)

