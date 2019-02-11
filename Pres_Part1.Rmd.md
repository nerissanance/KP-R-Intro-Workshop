KP R Intro Training Part I
========================================================
author: Nerissa Nance
date: 2/1/2019
autosize: true

Learning objectives
========================================================


Part 1 learning objectives, students will:  
- be able to structure and execute essential functions, including using Rmd files and utilizing read key documentation
- be able to recognize and utilize different data types and data structures
- be able to identify different types of missing data in R
- feel comfortable accessing data from R


The basics: navigating RStudio and projects
========================================================

Currently, you have the "KP-R-Intro-Workshop" project open (as you can see in the upper right-hand corner of your screen). Projects are handy because a project's folder is automatically set as the working directory, which allows us to not worry about explicitly setting the working directory. This can be more convenient when working on the same code across different computers. 

We can see recent projects by selecting File -> Recent Projects in the upper left corner of RStudio, or by clicking the list of recent projects in the upper right corner. If we click the name of the project it will switch to that project, or if we click the button it will open in a new session.

The basics: navigating RStudio and projects
========================================================
Let's try creating a new project.

* Create a new project: File -> New Project
* Choose new directory or existing directory as preferred.
* Click "open in new session" to have multiple RStudio projects open.

Easy Challenge: close your project and then re-open it.


RStudio interface
========================================================

When we start RStudio we have no files open by default. Click File -> New File -> RScript to start a new R script (or program). This is a text file with all of the R commands you want to run for an analysis.

As an alternative to an R script we can use a **markdown file**. R Markdown files combine R scripts with simple text formatting, which makes reports  (PDFs or HTMLs) easy to generate with embedded R output. 


RStudio interface
========================================================

Try making a new R script and R markdown right now in your new project directory, and save the files. 

RStudio items to note:

* Files show up as tabs in the editor window, usually the upper left.
* The console is the R session where our commands are executed.
* Environment tab in the upper right, and history tab.
* Files tab in bottom right, plus plots, help, etc.
* We can click the "run" button to run the current R line in the editor.



Basic R markdown file
========================================================
File -> New -> R Markdown

To write R code we need to start an R block with three backticks followed by r in braces (squiggly brackets - { and }). We can write commands inside of those brackets to change settings.

Task: everyone google "RMarkdown cheat sheet" and save that PDF.

Challenge
========================================================

* Create a header line called "R Training Day 1", with size 1 (aka "header 1").
* Write this equation in the notes area: Area = pi * r^2
* In the first chunk of code, write an equation (eg. 2 + 2)
* Compile as a PDF (or html if you prefer).


Package installation
========================================================

Let's install some packages that we will use during the training. You can install packages by clicking the "Packages" tab in the bottom-right window, clicking install, and then searching for the package you wish to install.

Packages can also be installed through the command line using `install.packages()`. The package name must be wrapped in quotation marks so that R knows it is searching for that particular package named `"psych"`, rather than previously defined data named psych:


Package installation
========================================================

> It is generally good to keep RStudio and your packages up to date! Install the packages we will use in the workshop: 



```r
install.packages(c("ggplot2", "knitr", "psych", "rmarkdown", "reshape2", "swirl", "mlbench", "dplyr", "tidyr"))
```



The `library` function  
========================================================
Before using a previously installed package, you must retreive it with `library()` when you begin a new R session. You do not need to reinstall packages each time you quit and restart your R session. 


```r
library(ggplot2)
library(knitr)
library(psych)
library(rmarkdown)
library(reshape2)
library(swirl)
# these packages can now be used in our RStudio session!
```



Getting help 
========================================================
The `?` symbol can be used to bring up the help pages:  

```r
?update.packages
?read.csv
?summary
?describe
?plot
?ggplot
?geometric.mean
```

Variable assignment (`<-`)
========================================================
Variables are special data structures that allow you to enter data into R. Objects are stored in R's memory and can be retrieved ("called") when you need them.  

You define objects through `variable assignment` and they are stored in your `global environment`.  

You define objects through variable assignment using the **assignment operator** `<-`. This is a "less than" `<` symbol immediately followed by a hyphen `-`


Let's define an object named `numeric_oject` and define it as the number 4:

```r
numeric_object <- 4

# the ls() function will show us what is in our global environment
ls()
```

```
[1] "numeric_object"
```

```r
r <- 2

#back to our equation:

Area <- pi * r^2

Area
```

```
[1] 12.56637
```


The R global environment
========================================================

We now have an object defined in our global environment!


"Call" (retrieve) the data contained wihtin the object by typing its name into your script and running the line of code

```r
numeric_object 
```

```
[1] 4
```

```r
print(numeric_object)
```

```
[1] 4
```

```r
# 4 is returned
```

Let's try another example, this time using character data. Note that character data is **always** contained within quotation marks `" "` 

```r
welcome_object <- "Welcome"
ls()
```

```
[1] "Area"           "numeric_object" "r"              "welcome_object"
```

We now have four objects in our global environment. Call the data contained within the object by typing its name and running the line of code:

```r
welcome_object
```

```
[1] "Welcome"
```



Naming R variables  
========================================================
Object names can be anything, but are always case sensitive. However, they cannot begin with a number and generally do not begin with symbols. However you choose to name your objects, be consistent and use brief descriptions of their contents.  

Names must be __**unique**__. If you reuse an old name, the old definition will be overwritten.  

Let's overwrite the object `welcome_object` from above.

```r
welcome_object <- "Welcome to class" 
welcome_object
```

```
[1] "Welcome to class"
```

```r
welcome_object <- "Welcome to Part 1"
ls() 
```

```
[1] "Area"           "numeric_object" "r"              "welcome_object"
```
See how the definition of `welcome_object` changed in your global environment window? However, there are still only two objects in your global environment. 




Variable classes
========================================================
Each variable in R has a `class` that summarizes the type of the data stored within the object. We will talk more about data types below.

> NOTE! "numeric" is the default data type for numbers in R:


```r
# this is numeric (NOT integer) data type!
class(numeric_object) 
```

```
[1] "numeric"
```

```r
# character type
class(welcome_object) 
```

```
[1] "character"
```

Removing variables (`rm`)
========================================================
We remove individual variables from our environment with `rm()`. For example, to remove `numeric_object`, we type:

```r
rm(numeric_object)
ls()
```

```
[1] "Area"           "r"              "welcome_object"
```
See how `numeric_object` disappeared from our global environment?

We can also wipe the entire environment with `rm(list = ls())` (or, click the broom icon in the upper right "global environment" pane)

```r
rm(list = ls()) 
ls()
```

```
character(0)
```
Now, all objects are gone from our global environment.

Vignettes
========================================================
Double question marks ?? will lead you to coding walkthroughs called "vignettes". These usually come with preloaded data and examples:  

```r
??psych
```
You will often find that your questions are not answered by the help pages nor vignettes. In that case you should Google-search your question or error message along with the name of a free help website.  

For example, to get help making boxplots, I might Google search "R how to make boxplots stack overflow"


Atomic data types in R
========================================================
Numeric, character, and logical (aka "boolean") data types all exist at the `atomic level`. Normally this means that they cannot be broken down any further and are the raw inputs for functions in R. Other R variables are frequently built upon these atomic types.


Numeric data are numbers and integers. You may also hear numeric data referred to as `float` or `double` data types. By default, R stores everything as `doubles` (64 bit floating point numbers) which makes R very memory hungry. 

Define an object called `num` and then check its class

```r
num <- 2 * pi
num
```

```
[1] 6.283185
```

```r
class(num)
```

```
[1] "numeric"
```

Standard mathematical operators apply to the creation of numeric data:
`+`   `-`   `*`   `^`   `**`  `/`  `%*% (matrix multiplication)`  `%/% (integer division)`  `%% (modular division)`

```r
5 + 2  
```

```
[1] 7
```

```r
5 - 2  
```

```
[1] 3
```

```r
5 * 2  
```

```
[1] 10
```

```r
5 ^ 2  
```

```
[1] 25
```

```r
# same as ^ :
5 ** 2  
```

```
[1] 25
```

```r
5 / 2  
```

```
[1] 2.5
```

```r
5 %/% 2 
```

```
[1] 2
```

```r
5 %% 2  
```

```
[1] 1
```

```r
5 %*% 2  
```

```
     [,1]
[1,]   10
```

========================================================
Character (aka string or text) data are always contained within quotation marks `" "`. Character handling in R is fairly close to character handling in a Unix terminal.  

Let's create an object called `char` and define it with some character data. Then, check its class:

```r
char <- "This is character data"
char
```

```
[1] "This is character data"
```

```r
class(char)
```

```
[1] "character"
```



Function arguments
========================================================
Arguments go inside of the parentheses of R functions. Unnamed arguments are things like the number 4. `split = " "` is what is called a named argument. This argument goes inside the parentheses of another function such as `strsplit`. 

```r
char4 <- "This/is/slash/separated/text"
char4
```

```
[1] "This/is/slash/separated/text"
```

```r
split1 <- strsplit(char4, split = "/")
split1 # a list is returned. 
```

```
[[1]]
[1] "This"      "is"        "slash"     "separated" "text"     
```

Most functions require one or two arguments to be defined in order for it to properly run. You will find that functions are full of default, positional, and optional arguments that you can manipulate.  

Simple string subset example (`substr`)
========================================================
`substr` lets you extract text from certain character positions in character data. Refer back to `char2`

```r
char2 <- paste("Hey", "momma", "I'm", "a", "string")
char2
```

```
[1] "Hey momma I'm a string"
```

If we want to extract just the first four characters of the `char2` object we type:

```r
substr(char2, start = 1, stop = 4)
```

```
[1] "Hey "
```
"Hey " (Hey + blankspace) is returned.  

You can use `substr()` and the assignment operator `<-` to redefine the first four characters in `char2` with the word "Yes " followed by a blankspace

```r
substr(char2, 1, 4) <- "Yes "
char2 
```

```
[1] "Yes momma I'm a string"
```
What changed?  

Logical type  
========================================================
Logical (boolean) data are dichotomous TRUE/FALSE values. R internally stores `FALSE` as 0 and `TRUE` as 1. Define a logical object:

```r
bool_object <- TRUE
bool_object
```

```
[1] TRUE
```

```r
class(bool_object)
```

```
[1] "logical"
```
We recommend to always spell out `TRUE` and `FALSE` instead of abbreviating them `T` and `F` which might be mistaken for previously defined variables - therefore, you should not save anything as `T`, `F`, or `TRUE` or `FALSE`! Thus, there are certain words that do not make good variable names. R has many reserved words that you should avoid using. See `?reserved` for more information.

Note that logical data also take on numeric properties. Remember that `TRUE` is stored as the numeral 1 and `FALSE` is stored as 0. 

```r
bool_object + 1
```

```
[1] 2
```

```r
TRUE - TRUE
```

```
[1] 0
```

```r
TRUE + FALSE
```

```
[1] 1
```

```r
FALSE - TRUE
```

```
[1] -1
```

Logical tests  
========================================================
Logical tests are helpful in R if you want to check for equivalence. Logical tests compare two objects and return a logical output. This is useful for removing missing data and subsetting (you will learn more about this in Part 2). Note the use of the double equals `==` sign. 


```r
?"=="
?"&"
?"|"
?"!"
```

```r
TRUE == TRUE # is equivalent
```

```
[1] TRUE
```

```r
FALSE == FALSE
```

```
[1] TRUE
```

```r
TRUE == FALSE
```

```
[1] FALSE
```

```r
TRUE & TRUE   # and 
```

```
[1] TRUE
```

```r
TRUE | FALSE  # or
```

```
[1] TRUE
```

```r
TRUE != FALSE  # not
```

```
[1] TRUE
```

```r
TRUE > FALSE # greater than
```

```
[1] TRUE
```

```r
FALSE >= TRUE # greater than or equal to
```

```
[1] FALSE
```


Challenge 1
========================================================
1. What is the three-piece recipe for variable definition? What piece goes where?  
2. Define two numeric variables.  
3. Define two character variables.  
4. How do you check what types of data these variables are?  
5. What does the `ls()` function do? Where else do you see this information?  
6. Remove one of your numeric and one of your character variables.  
7. Try to subract your remaining character variable from your numeric one. What happens? What might this tell you about data of different types?  
8. Define a numeric object as 0 and check its class.  
9. Define a boolean object as "FALSE" and check its class.  
10. Use `==` to compare your numeric and boolean object. Are they equivalent? Why or why not?  
11. Define a character object that uses `paste()` to combine more than one word into a sentence.  
12. Use `substr` to extract the first word of your sentence.  
13. Wipe your environment clean.  
 



Data testing and type coercion (`as.type`)
========================================================
"Type coercion" refers to changing the data from one type to another. You can change data types with `as.` and then the data type to which you wish to convert.
 

Type        | Test          | Conversion
----------- | ------------- | ----------
character   | is.character  | as.character
complex     | is.complex    | as.complex
double      | is.double     | as.double
expression  | is.expression | as.expression
integer     | is.integer    | as.integer
list        | is.list       | as.list
logical     | is.logical    | as.logical
numeric     | is.numeric    | as.numeric
single      | is.single     | as.single
raw         | is.raw        | as.raw


 
Challenge 2
========================================================
1. Create a character object and check its type using `is.character` and `class`. What is the difference between these two methods?    
2. Try to change ("coerce") this object to another data type using `as.integer`, `as.numeric`, and `as.logical`.  
3. Create an object of class "integer". Remember, there are two ways to do this!  
4. Why is 1 == "1" true?   Why is -1 < FALSE true?   Why is "one" < 2 false?  



Data structures
========================================================
There are several kinds of data structures in R. Data structures are collections of data objects (e.g., numeric, character, and logical vectors, lists, and matrices) that work together. These four are the most common:  

1. vector  
2. list  
3. matrix  
4. dataframe  


Vector
========================================================
A **VECTOR** is an ordered group of the same kind of data. "Ordered" means that their position matters. Vectors are one-dimensional and homogenous, and are thus referred to by their type (e.g., character vector, numeric vector, logical vector).  

Create a numeric vector by combining/concatenating elements with `c()`  

```r
numeric_vector <- c(3, 5, 6, 5, 3)
numeric_vector
```

```
[1] 3 5 6 5 3
```
This numeric vector contains five elements.  

You can index a vector using square brackets (more on this in the subsetting section of Part 2). For example, to see what value lives in the third position of the object `numeric_vector`, you could type: 

```r
numeric_vector[3]
```

```
[1] 6
```

You can also add items to a vector using `c()` and a comma `,` (as long as it is the same data type)

```r
numeric_vector2 <- c(numeric_vector, 78)
numeric_vector2
```

```
[1]  3  5  6  5  3 78
```


Vector
========================================================

It doesn't matter what the datatype is for a vector, as long as it is all the same

```r
logical_vector <- c(TRUE, TRUE, FALSE, FALSE, TRUE)
logical_vector
```

```
[1]  TRUE  TRUE FALSE FALSE  TRUE
```

```r
logical_vector2 <- c(logical_vector, c(FALSE, FALSE, FALSE))
logical_vector2
```

```
[1]  TRUE  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE
```

You can also add and multiply vectors, but they need to be the same length

```r
logical_vector * logical_vector
```

```
[1] 1 1 0 0 1
```


Generating random vectors (`seq`)
========================================================
You might need to create vectors that are sequences of numbers. You can do this via `seq`. Here we specify a vector from zero to the `length` of our object `logical_vector2` (eight). The argument `by = 2` tells R that we want only the even numbers!

```r
?length
logical_vector2
length(logical_vector2)

seq(from=0,to=length(logical_vector2),by=2)
```

Sequence where `by = 1` (`:`)
========================================================
R also gives you a shorthand operator for creating sequences in whole number increments of 1. This is the colon symbol `:`

```r
0:8
```

```
[1] 0 1 2 3 4 5 6 7 8
```

```r
sequence_object <- 28:36
sequence_object 
```

```
[1] 28 29 30 31 32 33 34 35 36
```

```r
0:length(logical_vector2)
```

```
[1] 0 1 2 3 4 5 6 7 8
```

`set.seed`    
========================================================
You can also sample random groups of numbers. Use `set.seed()` to ensure that we all always get the same random draws from the parent universe, even on different machines
 
Set the seed, and then choose our values:

```r
set.seed(2346)
# 20 random samples from uniform distribution between the numbers 3 and 7
uniform <- runif(20, 3, 7) 
uniform
```

```
 [1] 4.544240 3.489348 6.068407 3.161751 6.461309 5.810518 3.404867
 [8] 5.238931 6.954126 6.328505 3.048943 6.305050 4.382296 4.475999
[15] 3.133005 3.390534 4.084209 4.689436 5.267931 4.996230
```

```r
# 20 random samples from the normal distribution with a mean of 0 and standard deviation of 1
normal <- rnorm(20, 0, 1) 
normal
```

```
 [1] -0.09149019  1.12753115 -1.61933145 -0.48718366 -1.06576577
 [6] -0.74445302 -2.35303871  0.15443995  0.35509938 -0.06067869
[11]  0.31884664  1.32218276  1.19400064 -0.23740576 -2.15278944
[16]  0.80304167 -0.31741855 -1.35466867  0.03503021 -0.81104751
```

```r
# 20 random samples from between the numbers 5 and 10. Note that `replace=TRUE` signifies that it is OK to reuse numbers already selected.
integer <- sample(5:10, 20, replace = TRUE) 
integer
```

```
 [1]  7 10  7  5  7 10  8  6  6  7  8  5  8  5  5  7  9  9 10  7
```

```r
character <- sample(c("Cat", "Dog", "Pig"), 20, replace = TRUE) # 20 random samples of character data
character
```

```
 [1] "Cat" "Cat" "Pig" "Pig" "Dog" "Pig" "Cat" "Dog" "Pig" "Dog" "Cat"
[12] "Pig" "Dog" "Pig" "Pig" "Cat" "Pig" "Cat" "Pig" "Cat"
```

List
========================================================
A **LIST** is an ordered group of data that are not of the same type. Lists are heterogenous. Instead of using `c()` like in vector creation, use `list()` to create a list:

```r
list1 <- list(TRUE, "one", 1) # include three kinds of data: logical, character, and integer
list1
class(list1)
```

Lists are simple containers and are not additive or multiplicative like vectors and matrices are:

```r
list1 * list(FALSE, "zero", 0) # Error
```

Matrix  
========================================================
**MATRICES** are homogenous like vectors. They are tables comprised of data all of the same type. Matrices are organized into rows and columns. 

Use `matrix()` to create a matrix

We can also specify how we want the matrix to be organized using the `nrow` and `ncol` arguments:

```r
matrix1 <- matrix(1:12, nrow = 4, ncol = 3) # this makes a 4 x 3 matrix
matrix1
```

```
     [,1] [,2] [,3]
[1,]    1    5    9
[2,]    2    6   10
[3,]    3    7   11
[4,]    4    8   12
```

```r
class(matrix1)
```

```
[1] "matrix"
```
We can also coerce a vector to a matrix, because a vector is comprised of homogenous data of the same kind, just like a matrix is:

```r
# Create a numeric vector from 1 to 20
vec1 <- c(1:20)
vec1
```

```
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

```r
class(vec1)
```

```
[1] "integer"
```

```r
# Coerce this vector to a matrix with 10 rows and 2 columns:
matrix2 <- matrix(vec1, ncol=2)
matrix2
```

```
      [,1] [,2]
 [1,]    1   11
 [2,]    2   12
 [3,]    3   13
 [4,]    4   14
 [5,]    5   15
 [6,]    6   16
 [7,]    7   17
 [8,]    8   18
 [9,]    9   19
[10,]   10   20
```

```r
class(matrix2)
```

```
[1] "matrix"
```



Data frame 
========================================================
_**It is worth emphasizing the importance of data frames in R!**_ Inside R, a **DATA FRAME** is a list of equal-length vectors. These vectors can be of different types. Data frames are thus heterogenous like lists.  

This is simply a spreadsheet!  

Let's create a dataframe called `animals` using the vectors we already created:

We do this using `data.frame()`


```r
animals <- data.frame(uniform, normal, integer, character, stringsAsFactors = FALSE)
# NOTE: `stringsAsFactors=FALSE` means that R will NOT try to interpret character data as factor type. More on this below. 
```

Take a peek at the `animals` data frame to see what it looks like:

```r
head(animals)
```

```
   uniform      normal integer character
1 4.544240 -0.09149019       7       Cat
2 3.489348  1.12753115      10       Cat
3 6.068407 -1.61933145       7       Pig
4 3.161751 -0.48718366       5       Pig
5 6.461309 -1.06576577       7       Dog
6 5.810518 -0.74445302      10       Pig
```

We can change the names of the columns by passing into it a vector with our desired names

```r
# Create a vector called `new_df_names` with the new column names and pass this vector into `colnames()`
colnames(animals) <- c("Weight", "Progress", "Height", "Type")
head(animals)
```

```
    Weight    Progress Height Type
1 4.544240 -0.09149019      7  Cat
2 3.489348  1.12753115     10  Cat
3 6.068407 -1.61933145      7  Pig
4 3.161751 -0.48718366      5  Pig
5 6.461309 -1.06576577      7  Dog
6 5.810518 -0.74445302     10  Pig
```

We can check the structure of our data frame via `str()`

```r
str(animals)
```
Here, we can see that a data frame is just a list of equal-length vectors! For readability purposes, `str()` displays columns from top to bottom, while the data are displayed left to right. 

Learning about your data frame 


```r
# View the dimensions (nrow x ncol) of the data frame:
dim(animals) 
```

```
[1] 20  4
```

```r
# View column names:
colnames(animals)
```

```
[1] "Weight"   "Progress" "Height"   "Type"    
```

```r
# View row names (we did not change these, so they default to character type)
rownames(animals)
```

```
 [1] "1"  "2"  "3"  "4"  "5"  "6"  "7"  "8"  "9"  "10" "11" "12" "13" "14"
[15] "15" "16" "17" "18" "19" "20"
```

```r
class(rownames(animals))
```

```
[1] "character"
```


Factor data type  
========================================================
Factor data are categorical types used to make comparisons between other data. Factors group the data by their "levels" (the different categorical groups within a factor).  

For example, in our `animals` dataframe, we can coerce "Type" from character to factor data type. Cat, Dog, and Pig are the factor levels. If we might want to compare heights and weights between Cat, Dog, and Pigs, we set the character "Type" vector to factor data type. We can do so with `factor()`.  

The dollar sign operator `$` is used to call a single vector from a data frame. This will be discussed more in Part 2 along with the rest of subsetting.

```r
# "Name" is character data type. See how each column name is preceded by `$`?
str(animals)   
```

```
'data.frame':	20 obs. of  4 variables:
 $ Weight  : num  4.54 3.49 6.07 3.16 6.46 ...
 $ Progress: num  -0.0915 1.1275 -1.6193 -0.4872 -1.0658 ...
 $ Height  : int  7 10 7 5 7 10 8 6 6 7 ...
 $ Type    : chr  "Cat" "Cat" "Pig" "Pig" ...
```

```r
 class(animals$Type)
```

```
[1] "character"
```

```r
animals$Type <- factor(animals$Type)
# "Name" is now factor data type!
str(animals)  
```

```
'data.frame':	20 obs. of  4 variables:
 $ Weight  : num  4.54 3.49 6.07 3.16 6.46 ...
 $ Progress: num  -0.0915 1.1275 -1.6193 -0.4872 -1.0658 ...
 $ Height  : int  7 10 7 5 7 10 8 6 6 7 ...
 $ Type    : Factor w/ 3 levels "Cat","Dog","Pig": 1 1 3 3 2 3 1 2 3 2 ...
```

Notice that R stores factors internally as integers and uses the character strings as labels. Also notice that by default R orders factors alphabetically and returns them when we call the "Type" vector.

```r
animals$Type
```

```
 [1] Cat Cat Pig Pig Dog Pig Cat Dog Pig Dog Cat Pig Dog Pig Pig Cat Pig
[18] Cat Pig Cat
Levels: Cat Dog Pig
```

```r
levels(animals$Type)
```

```
[1] "Cat" "Dog" "Pig"
```


Changing factor "levels"
========================================================
Each animal type (Cat, Dog, and Pig) within the factor `animals$Type` vector are the factor levels. 

If we want to change how R stores the factor levels, we can specify their levels using the `levels()` argument. For example:

```r
animals$Type  
```

```
 [1] Cat Cat Pig Pig Dog Pig Cat Dog Pig Dog Cat Pig Dog Pig Pig Cat Pig
[18] Cat Pig Cat
Levels: Cat Dog Pig
```

```r
# What if we want to change the factor level sort to Levels: Dog Pig Cat?
animals$Type <- factor(animals$Type, levels = c("Dog", "Pig", "Cat"))

# Now when we call animals$Name, we can see that the levels have changed
animals$Type 
```

```
 [1] Cat Cat Pig Pig Dog Pig Cat Dog Pig Dog Cat Pig Dog Pig Pig Cat Pig
[18] Cat Pig Cat
Levels: Dog Pig Cat
```




Importing and exporting with the Rio package
========================================================

The Rio package simplifies importing/exporting by putting all data-specific import tools under one umbrella (popularly known as the "swiss army knife" of data importing and exporting)
 See [this helpful rio documentation as well](https://cran.r-project.org/web/packages/rio/vignettes/rio.html). 
 


```r
library(rio)

df.who <- import("./data/whostats_suicide.sas7bdat")
 dim(df.who)
```

```
[1] 43776     6
```
 

Challenge 3
========================================================

1. Save the "animals" data frame as a .csv file named "animals.csv". How many basic arguments should you use to save using the `write.csv` function? 
2. Import the "animals" data frame using the rio package. 
3. Compare the two data frames. Are they the same? Why or why not?
 

Visualize data 
========================================================

We'll use this more in parts 2 and 3, but take a moment to look at the data you imported. You can use the `hist()` command to do a histogram and the `summary()` command to look at summary statistics. For example:


```r
names(df.who)
```

```
[1] "country"     "year"        "sex"         "age"         "suicides_no"
[6] "population" 
```

```r
class(df.who$suicides_no)
```

```
[1] "character"
```

```r
df.who$suic_no_num <- as.numeric(df.who$suicides_no)

hist(df.who$suic_no_num)
```

![plot of chunk plotting](Pres_Part1.Rmd-figure/plotting-1.png)

```r
summary(df.who$suic_no_num)
```

```
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
    0.0     1.0    14.0   193.3    91.0 22338.0    2256 
```

Challenge 4 Homework (optional)
========================================================

swirl is a package that helps you learn R by using R. Visit the [swirl](http://swirlstats.com/) homepage to learn more

```r
library(swirl)
swirl()
# follow the instructions until you can select number 1 "R Programming: The basics of programming in R"
```

> NOTE: type `bye()` to exist swirl. 


