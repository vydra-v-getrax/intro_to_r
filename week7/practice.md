### Practice Problems

#### 1. Conditional statements

+ create a vector ```vec5 <- c(5, 20, 30, 0, 2, 9)```

+ create a string vector out of vec5 where numbers bigger than 10 will be replaced by 'big number', the rest of the numbers will be replaced by 'small number'

+ load [the file](https://raw.githubusercontent.com/dashapopova/Intro-to-R/main/week4/heroes_information.csv) into a variable ```heroes```

+ Create a new column hair in heroes, where characters with "No Hair" in Hair.color will have "Bold" in the new column, the rest of the cases will have "Hairy" in the new column.

+ Create a new column tall in heroes, where those superheroes that have a number bigger than 190 in the Height column will get "tall" in the new column, those superheroes that have a number smaller than 170 in the Height column will get "short" in the new column, and "middle" in all the other cases.

The first variant:

The second variant:

#### 2. Functions

+ Create a function ```plus_one()``` that takes a number and returns that number plus 1

+ Check the function ```plus_one()``` on 41

+ create a function ```circle_area()``` that computes the area of a circle

+ Compute the area of a circle with the radius 5

+ create a function ```cels2fahr()``` that will turn Celsius into Fahrenheit

+ Check on -100, -40 and 0 values that the function ```cels2fahr()``` works

+ Create a function ```highlight()``` that takes a string vector and returns the same vector with "***" at the beginning and the end of the vector 

+ Make the ```highlight()``` function more flexible: add a parameter ```wrapper =``` that will be set to the default value "***". Add the value of ```wrapper =``` at the beginning and at end of a vector.

+ Test the function

+ Create a function ```na_n()``` that will return the number of NAs in a vector

+ Test the function

+ Create a function ```factors()``` that returns all the delimiters of a number in a numeric vector

+ Test the function

+ Create a function ```is_prime()``` that checks if a number is a prime number

+ Test the function

+ Create a function ```monotonic()``` that returns TRUE, if the values in a vector increase or decrease monotonically.

A hint: ```diff()``` returns the difference between neighbours.

+ Create a function ```trim()``` that returns a vector without the first and the last element

+ Test the function ```trim()```

+ Now, add to the function ```trim()``` a parameter  ```n =``` with the default value of 1. This parameter signals how many values should be cut from the beginning and the end of a vector

+ Test the new version of the function

+ Modify the function so that it works correctly with n = 0, i.e. returns the initial vector without any modifications

+ now do a sanity check: trim() should give an error when n is a negative number or when n is too big and cuts off all the values of a vector

+ Test the new version of the function

+ Create a matrix M2:

```
M2 <- matrix(c(20:11, 11:20), nrow = 5)
M2
```

+ Compute the maximum for every row

+ Compute the maximum for every column

+ Compute the mean for every row

+ Compute the mean for every column

+ Create a list list3:

```
list3 <- list(
  a = 1:5,
  b = 0:20,
  c = 4:24,
  d = 6:3,
  e = 6:25
  )
```

+ Find the maximum value for each vector of list3


+ Compute the sum for each vector of list3



+ Compute the length of each vector of list3



+ Create a function ```max_item()``` that takes a list and returns the first most lengthy element

A hint: use ```which.max()``` which returns an index of the maximum value



+ Test the function ```max_item()``` on list3



+ Let's create list4:

```
list4 <- list(1:3, 3:40, list3)
```

+ Compute the length for every vector in ```list4```, including the embedded list. The result should be a list of the same structure as the initial ```list4```. Use ```rapply()```: recursive lapply



+ load the heroes dataset and count how many NAs are in each column. Use ```na_n()```



+ Using ```is_prime()```, create a function ```prime_numbers()``` that will return all the prime numbers up to a chosen number

