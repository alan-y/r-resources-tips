# Getting Started

## Understanding R from the Perspective of Excel
This may be useful reading if you have never used R (or similar software for data analysis) before but are familiar with Microsoft Excel.  
[R for Excel users](http://rex-analytics.com/r-for-excel-users)  
[Where do things live in R? R for Excel Users](http://rex-analytics.com/things-live-r-r-excel-users)  
[What’s a variable in R?](http://rex-analytics.com/whats-variable-r)  

## Setting Up RStudio
When you first load RStudio, you should set up some options within it. First go to the **Tools** menu and then go into the **Global Options**. In the **General** tab, you should untick 'Restore .RData into workspace at startup' and change 'Save workspace to .RData on exit' to 'Never'. This is illustrated in [the Workflow: projects chapter in the R for Data Science book]((https://r4ds.had.co.nz/workflow-projects.html#what-is-real)). Doing this helps to ensure that R loads in a *fresh session* every time which also helps to ensure your work is fully reproducible.  
  
In addition to this, you should make sure R is set up to work with the [unicode character set](https://en.wikipedia.org/wiki/UTF-8) in case you ever need to use them. To do this, go to the **Code** tab (within Global Options) and then go to the **Saving** tab within there and make sure the 'default text encoding' is 'UTF-8'. 
  
Some optional settings:

* A lot of programmers like to use a dark theme for coding so if this is your preference, go to the **Appearance** tab and set the 'Editor theme' to something like 'Twilight'. 
* If you are working in the UK, go the **Spelling** tab, and set the 'Main dictionary language' to 'English (United Kingdom)'.


## Getting Help
To use R effectively, it is more or less essential to learn how to use the help facilities within R. This is because there are just so many functions available (especially when you consider the amount of packages that have been developed to extend the capabilities of R) and it is difficult to always remember exactly how to use them.  
  
Help pages for functions in R can be brought up by typing `?name-of-function` within R, e.g. to get the help for the `mean()` function, you can type `?mean`. Equally, `help(name-of-function)` also works, e.g. `help(mean)`. The help pages in R can be a little daunting at first so it is good to start by understanding the layout of a help page and what everything in it means.  
[How to read a help page in R](http://socviz.co/appendix.html#a-little-more-about-r)  
  
In addition to the help pages within R, there are also many other ways to get help.  
[Where to get help with your R question?](https://masalmon.eu/2018/07/22/wheretogethelp)
  
You can search online for help in your favourite search engine. Often typing something like 'joining data in R' will be good enough to return useful results. There is also a search page focussed on returning R-related results called [RSeek](https://rseek.org) if you want to try that.  
  
People are usually good at responding to questions if you post them online in a reproducible manner. Here is a good guide for doing this well using the [reprex](https://reprex.tidyverse.org) package in R.  
[So you’ve been asked to make a reprex](https://www.jessemaegan.com/post/so-you-ve-been-asked-to-make-a-reprex)  
  
You can post your question to the [Data Science Scotland Slack](https://datasciencescotland.slack.com) R Channel or to websites such as [StackOverflow](https://stackoverflow.com).

