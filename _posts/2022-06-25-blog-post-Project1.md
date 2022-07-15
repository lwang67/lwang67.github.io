Project 1
================
Li Wang
2022-06-25

``` r
rmarkdown::render("_Rmd/2022-06-25-blog-post-Project1.Rmd", 
                  output_format = "github_document",
                  output_dir = "./_posts",
                  output_options = list(
                    html_preview= FALSE
                    )
)
```


## Project1

### Explaining what I did in the project and any interesting findings

In this project, I created a vignette about contacting the [COVID19 API](https://documenter.getpostman.com/view/10808728/SzS8rjbc) using functions I created to query, parse, and return some well-structured data. Then I used functions to obtain data from the API and do some exploratory data analysis. In the EDA section, I created some contingency tables, some numerical summaries, bar plots, one histogram, one box plot, and one scatter plot. 

It's my first time doing work with interacting API. There are some interesting findings, for example, how to contact the API using a function to query different data frames.



### Discuss things like:

+ what was the most difficult part of the logic and programming for me?

For me, the most difficult part is how to write codes to create the function to query a data frame. Sometimes, I made a function, and then the data frame could show the variable. However, when I used the variable to create plots the error said there was no this variable that confusing to me.



+ what would I do differently in approaching a similar project in the future?

In this project, I just did some fundamental exploratory data analysis. In the future, I hope I can do some high-level analysis.



• [link to the github pages repo](https://lwang67.github.io/ST558_project1/)

• [link the regular repo](https://github.com/lwang67/ST558_project1)
