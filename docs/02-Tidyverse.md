# Tidyverse

This statement from the [official tidyverse website](https://www.tidyverse.org) describes what the tidyverse is

>The tidyverse is an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures. 

Further background information on what the tidyverse is can be found in the R Views blog: [What is the tidyverse?](https://rviews.rstudio.com/2017/06/08/what-is-the-tidyverse). In addition, Hadley Wickham has laid out his principles for tidyverse packages within his [tidy tools manifesto](https://cran.r-project.org/web/packages/tidyverse/vignettes/manifesto.html).  
  
At this point, you should watch this video to get an introduction to data wrangling with the tidyverse.  
[What is data wrangling? Intro, Motivation, Outline, Setup -- Pt. 1 Data Wrangling Introduction](https://www.youtube.com/watch?v=jOd65mR1zfw&list=PL9HYL-VRX0oQOWAFoKHFQAsWAI3ImbNPk&index=1)
  
## Installation
The package can be installed and loaded with

```r
install.packages("tidyverse")
library(tidyverse)
```

This loads the core set of tidyverse packages – see [here](https://www.tidyverse.org/packages) for more details.

## Getting Data into R
The tidyverse installs a number of packages that help with getting your data into R. However, only the [readr](https://readr.tidyverse.org) package is loaded as part of the core set of packages so the other data import packages, ([readxl](https://readxl.tidyverse.org) and [haven](https://haven.tidyverse.org) have to be loaded with their own `library()` calls).

* readr: for reading in data formats such as csv, tsv and fwf.
* readxl: for reading in Excel data formats (.xls and .xlsx).
* haven: for reading in SPSS, Stata and SAS data formats.

RStudio also provides an 'Import Dataset' button to help with this. The RStudio support pages describe how to [import data with RStudio](https://support.rstudio.com/hc/en-us/articles/218611977-Importing-Data-with-RStudio). If you decide to use this to help you import data into R, my recommendation is to copy over the code generated in the 'Code Preview' box into your R script. This helps you to keep a record of the data import step in your script.  
  
Besides these data types, you should familiarise yourself with R's own data formats: .rds and .RData – .rds format can be used when saving a single object or dataset while .RData should only be used when you want to save multiple objects or datasets from your R session. These formats load fast into R and an important advantage is that they keep data exactly as they were when they were created in R (i.e. all information about variable types and metadata will be retained after saving).

* .rds: read in data with `readRDS()`; save data with `saveRDS()`
* .RData: read in data with `load()`; save data with `save()`

## Data Manipulation with dplyr
[dplyr](https://dplyr.tidyverse.org) provides a set of functions (often described as *verbs*) to help with data manipulation. Most common tasks can be done using only a handful of functions: `select()`, `filter()`, `mutate()`, `rename()`, `arrange()`, `summarise()` and `group_by()` – note that `rename()` is not usually included in this list but I have included it as renaming variables comes up a lot during data cleaning/processing. Out of these functions, `group_by()` is the most complex and should probably be tackled after understanding the others; in particular, it is often used together with `summarise()`. Furthermore, two functions that often come in handy when used together with `mutate()` are `ifelse()` (or the stricter dplyr equivalent [`if_else()`](https://dplyr.tidyverse.org/reference/if_else.html)) and [`case_when()`](https://dplyr.tidyverse.org/reference/case_when.html) – these help to create new variables depending on certain conditions being met.  
  
It is a good idea to understand what each of these functions does on their own first before thinking about how to *combine* multiple manipulation steps together using [pipes (`%>%`)](https://r4ds.had.co.nz/pipes.html). Once you are comfortable with each of these functions, it should be a relatively small step to learn how to combine them together with the pipe operator; the ability to do this in a way that is relatively intuitive is one of the most powerful design features of the tidyverse. This is more or less the learning order used in the [dplyr chapter of the R Programming for Data Science book](https://bookdown.org/rdpeng/rprogdatascience/managing-data-frames-with-the-dplyr-package.html) which is worth a read through (there is also an accompanying video for that chapter which may also help). I would definitely recommend spending a good amount of time learning dplyr as you will want to reach the point where you can use these functions without requiring much thinking.

A good place to get started on learning about these functions are these videos.  
[Data Manipulation Tools: dplyr -- Pt 3 Intro to the Grammar of Data Manipulation with R](https://www.youtube.com/watch?v=Zc_ufg4uW4U&list=PL9HYL-VRX0oQOWAFoKHFQAsWAI3ImbNPk&index=3)  
[Hands-on dplyr tutorial for faster data manipulation in R](https://www.youtube.com/watch?v=jWjqLW-u3hc) – note that this tutorial is a little old (2014) so some parts of it are out-of-date but I think it is still useful. Only minor changes will be needed to make this current and the old dplyr functions mentioned should still be useable anyway. For example, they use `tbl_df()` which can now be replaced by `tibble()` instead. You should try running the R commands yourself while watching this video to aid the learning process.
  
Once you have watched these videos, you can work through all the tutorials in the [Work with Data section on RStudio Cloud](https://rstudio.cloud/learn/primers/2). Then you can further consolidate this knowledge by reading through [data transformation chapter of the R for Data Science book](https://r4ds.had.co.nz/transform.html) and working through the exercises at the end. After this, a set of four tutorials by Suzan Baert provides much more depth on what some of the basic dplyr functions can do. Again, trying to run the R codes while following along with the tutorials will be very beneficial.  
[Data Wrangling Part 1: Basic to Advanced Ways to Select Columns](https://suzanbaert.netlify.com/2018/01/dplyr-tutorial-1)  
[Data Wrangling Part 2: Transforming your columns into the right shape](https://suzan.rbind.io/2018/02/dplyr-tutorial-2)  
[Data Wrangling Part 3: Basic and more advanced ways to filter rows](https://suzan.rbind.io/2018/02/dplyr-tutorial-3)  
[Data Wrangling Part 4: Summarizing and slicing your data](https://suzan.rbind.io/2018/04/dplyr-tutorial-4)


### Working with Multiple Datasets
It is very likely that you will need to perform data linkage at some point so this makes it more or less essential to learn how to work with the various *joining* functions within dplyr. To get a quick overview on this, you can watch this short video.  
[Working with Two Datasets: Binds, Set Operations, and Joins -- Pt 4 Intro to Data Manipulation](https://www.youtube.com/watch?v=AuBgYDCg1Cg&list=PL9HYL-VRX0oQOWAFoKHFQAsWAI3ImbNPk&index=4)  
  
After this short introduction, I recommend reading three short sections of the relational data chapter in the R for Data Science book: [Understanding joins](https://r4ds.had.co.nz/relational-data.html#understanding-joins), [Inner join](https://r4ds.had.co.nz/relational-data.html#inner-join), [Outer joins](https://r4ds.had.co.nz/relational-data.html#outer-join).

Then you can follow this video tutorial – the parts about joins start from around 25 minutes into the video but if you want to further solidify your dplyr knowledge, you can watch it from the beginning. Again, note that this video is a little old (2015) so some aspects may be out-of-date but it is still useful nevertheless.  
[Going deeper with dplyr: New features in 0.3 and 0.4 (tutorial)](https://www.youtube.com/watch?v=2mh1PqfsXVI)  
  
There is also a [Join Data Sets tutorial on RStudio Cloud](https://rstudio.cloud/learn/primers/4.3) that you can try. Finally, you will want to read and work through all of [relational data chapter in the R for Data Science book](https://r4ds.had.co.nz/relational-data.html) to understand how to work with multiple related datasets more thoroughly. By the end, you should be familiar with just about everything on this [Data Transformation Cheat Sheet](https://github.com/rstudio/cheatsheets/raw/master/data-transformation.pdf).


## Reshaping Data with tidyr
Sometimes you will need to format your data into a specific *shape* to make it work for a certain purpose – [tidyr](https://tidyr.tidyverse.org) is a package that has functions that help with this. For example, for output tables, you may want to have data on different years in separate columns while for analytical operations within R, it may be easier to work with 'year' stored in only one column (or variable); the latter format here can be considered as [*tidy data*](https://cran.r-project.org/web/packages/tidyr/vignettes/tidy-data.html). In particular, the [ggplot2](https://ggplot2.tidyverse.org) package often requires data to be in the *long* or *tidy* format. To get a better idea on this, watch this video.  
[Tidy Data and tidyr -- Pt 2 Intro to Data Wrangling with R and the Tidyverse](https://www.youtube.com/watch?v=1ELALQlO-yM&list=PL9HYL-VRX0oQOWAFoKHFQAsWAI3ImbNPk&index=2) – however please note that the `gather()` and `spread()` functions mentioned will be replaced by [pivoting functions](https://tidyr.tidyverse.org/dev/articles/pivot.html) so you should mainly be concerned with the concepts here rather than learning about these functions specifically.  
  
Then you can try the [Reshape Data tutorial on RStudio Cloud](https://rstudio.cloud/learn/primers/4.1). The main thing you need to be able to do with tidyr is to be confident in knowing how to transform your data from *wide-to-long* format or from *long-to-wide* format. However, if you want to know more about what tidyr can do or find out more about tidy data in general, please refer to the [tidy data chapter in the R for Data Science book](https://r4ds.had.co.nz/tidy-data.html) (keeping in mind the caveat made previously about the change to using pivoting functions).


## Other Data Manipulation Tips
As you progress further along with learning to manipulate data using the tidyverse, you will inevitably encounter situations where you need to know more about how to deal with specific types of data such as dates/times and string variables. In addition, there will also be times when you wish there was a convenient and quick way to process data – luckily there usually is in R. Please note that some of the material mentioned in this section is probably optional until you specifically have a need for it but I recommend that you go through some of it anyway to build an awareness of where to look for solutions when you need it.


### Dates/Times
The main package within the tidyverse for dealing with dates and times is the [lubridate](https://lubridate.tidyverse.org/reference/lubridate-package.html) package. This is not loaded with the core set of tidyverse packages so has to be loaded separately by typing `library(lubridate)`. The main reference text for learning about how to work with dates/times using lubridate is the [dates and times chapter in R for Data Science](https://r4ds.had.co.nz/dates-and-times.html). Dates/times can sometimes be very complex (e.g. when thinking about time calculations across timezones) but it is likely that you will usually only need to perform fairly simple data processing operations involving dates. In this case, you will only really need to know a small number of functions from lubridate:

* `dmy()`, `mdy()`, `ymd()` to convert text to a Date format in R, e.g. `ymd("2001/05/20")` would convert the text "2001/05/20" so that R can recognise this as 20 May 2001.
* `year()`, `month()`, `day()` to extract the year, month, day from a date object, e.g. `year(ymd("2001/05/20"))` would extract 2001.


### Strings

The [stringr package](https://stringr.tidyverse.org) package is loaded within the core set of tidyverse packages and provides a set of consistent functions for working with string (or text) data. Again, the main reference is the [strings chapter in R for Data Science](https://r4ds.had.co.nz/strings.html). You will likely not need to know everything contained in that chapter but I would recommend learning some basics of using [regular expressions](https://www.regular-expressions.info). These can help to, for instance, filter data or create new variables according to some text pattern found in a string variable. This can sometimes be much quicker than filtering using a list of keywords, particularly if your data may contain variations on a common item (e.g. 'Male', 'M', 'Man') or mispellings (e.g. 'Mal').  
  
A useful place to practice and learn how to use regular expressions is [regexr](https://regexr.com). There is also an RStudio addin that may help called [regexplain](https://www.garrickadenbuie.com/project/regexplain) which was inspired by regexr but may help with your learning as it can be used within RStudio. Once you gain some familiarity on how to use regular expressions, many of the stringr functions should be relatively easy to understand and use. In particular, `str_detect()` is useful for filtering and creating variables.  
  
If you are already familiar with regular expressions using base R functions and want to find out about their stringr equivalents to take advantage of the consistencies in their design, the [from base R to stringr vignette](https://stringr.tidyverse.org/articles/from-base.html) is a handy resource. Furthermore, this blog post on [Demystifying Regular Expressions in R](https://blog.rsquaredacademy.com/regular-expression-in-r) gives a very clear and descriptive guide to how the different base R regular expression functions work.


### janitor

* `clean_names()`
* `tabyl()`

## Further Resources
[R for Data Science by Garrett Grolemund and Hadley Wickham](https://r4ds.had.co.nz)  
[R for Data Science: Exercise Solutions by Jeffrey B. Arnold](https://jrnold.github.io/r4ds-exercise-solutions)
