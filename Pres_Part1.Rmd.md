KP R Intro Training Part I
========================================================
author: Nerissa Nance
date: 2/1/2019
autosize: true

Learning objectives
========================================================


Part 1 learning objectives:  
- Students will be able to structure and execute essential functions, including using Rmd files and utilizing read key documentation
- Students will be able to recognize and utilize different data types and data structures
- Students will be able to identify different types of missing data in R
- Students will feel comfortable accessing data from R


The basics: navigating RStudio and projects
========================================================

Currently, you have the "KP-R-Intro-Workshop" project open (as you can see in the upper right-hand corner of your screen). Projects are handy because a project's folder is automatically set as the working directory, which allows us to not worry about explicitly setting the working directory. This can be more convenient when working on the same code across different computers. 

We can see recent projects by selecting File -> Recent Projects in the upper left corner of RStudio, or by clicking the list of recent projects in the upper right corner. If we click the name of the project it will switch to that project, or if we click the button it will open in a new session.

Let's try creating a new project.

* Create a new project: File -> New Project
* Choose new directory or existing directory as preferred.
* Click "open in new session" to have multiple RStudio projects open.

Easy Challenge: close your project and then re-open it.


RStudio interface
========================================================

When we start RStudio we have no files open by default. Click File -> New File -> RScript to start a new R script (or program). This is a text file with all of the R commands you want to run for an analysis.

As an alternative to an R script we can use a **markdown file**. R Markdown files combine R scripts with simple text formatting, which makes reports  (PDFs or HTMLs) easy to generate with embedded R output. 

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

Challenge:

* Create a header line called "R Training Day 1", with size 1 (aka "header 1").
* Write this equation in the notes area: Area = pi * r^2
* In the first chunk of code, write an equation (eg. 2 + 2)
* Compile as a PDF (or html if you prefer).


Package installation
========================================================

Let's install some packages that we will use during the training. You can install packages by clicking the "Packages" tab in the bottom-right window, clicking install, and then searching for the package you wish to install.

Packages can also be installed through the command line using `install.packages()`. The package name must be wrapped in quotation marks so that R knows it is searching for that particular package named `"psych"`, rather than previously defined data named psych:

> It is generally good to keep RStudio and your packages up to date! Install the packages we will use in the workshop: 



```r
install.packages(c("ggplot2", "knitr", "psych", "rmarkdown", "reshape2", "swirl", "mlbench", "dplyr", "tidyr"))
```



- Recycling rule 
========================================================

![plot of chunk unnamed-chunk-2](Pres_Part1.Rmd-figure/unnamed-chunk-2-1.png)
