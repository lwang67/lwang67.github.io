Fourth Blog Post
================
Li Wang
2022-07-20

``` r
rmarkdown::render("../_Rmd/2022-07-20-blog-post-Module11.Rmd", 
                  output_format ="github_document",
                  output_dir = "../_posts",output_options = list(html_preview= FALSE))
```

## Fourth Blog Post - Machine Learning

We just finished our section on machine learning and learned a lot of
machine learning methods. I think KNN is the most interesting\!

The abbreviation KNN stands for “K-Nearest Neighbour”. It is a
supervised machine learning algorithm. The algorithm can be used to
solve both classification and regression problem statements. The number
of nearest neighbours to a new unknown variable that has to be predicted
or classified is denoted by the symbol ‘K’.

## For an example:

### 1\. load the libraries

``` r
library(caret)
library(gbm)
library(foreach)
library(magrittr)
library(plyr)
```

### 2\. Load the ‘iris’ data

``` r
data(iris)
```

### 3\. Split the <data:70%> train,30% test.

``` r
set.seed(111)
split <- createDataPartition(y = iris$Species, p = 0.7, list = FALSE)
train <- iris[split, ]
test <- iris[-split, ]
```

### 4\. train the kNN model.Use repeated 10 fold cross-validation, with the number of repeats being 3, also preprocess the data by centering and scaling. Lastly, set the tuneGrid so that you are considering values of k of 1, 2, 3, . . . , 20.

``` r
kNNFit <- train(Species ~., data = train,
method = "knn",
trControl = trainControl(method = "repeatedcv", number = 10, repeats = 3),
preProcess = c("center", "scale"),
tuneGrid = data.frame(k = 1:20))
kNNFit
```

    ## k-Nearest Neighbors 
    ## 
    ## 105 samples
    ##   4 predictor
    ##   3 classes: 'setosa', 'versicolor', 'virginica' 
    ## 
    ## Pre-processing: centered (4), scaled (4) 
    ## Resampling: Cross-Validated (10 fold, repeated 3 times) 
    ## Summary of sample sizes: 93, 95, 95, 94, 95, 95, ... 
    ## Resampling results across tuning parameters:
    ## 
    ##   k   Accuracy   Kappa    
    ##    1  0.9581145  0.9368661
    ##    2  0.9496296  0.9237386
    ##    3  0.9456902  0.9178531
    ##    4  0.9550842  0.9320740
    ##    5  0.9712121  0.9562007
    ##    6  0.9614478  0.9414771
    ##    7  0.9715152  0.9567442
    ##    8  0.9671380  0.9502955
    ##    9  0.9748485  0.9618158
    ##   10  0.9684848  0.9522573
    ##   11  0.9687879  0.9527057
    ##   12  0.9654545  0.9477886
    ##   13  0.9718182  0.9573078
    ##   14  0.9654545  0.9479191
    ##   15  0.9650842  0.9474895
    ##   16  0.9590236  0.9383794
    ##   17  0.9556902  0.9332512
    ##   18  0.9526599  0.9288348
    ##   19  0.9432660  0.9148197
    ##   20  0.9317003  0.8975602
    ## 
    ## Accuracy was used to select the optimal model using the largest value.
    ## The final value used for the model was k = 9.

The model gives the highest accuracy for K = 9, therefore, the final
value used for the model was k = 9.

### 5\. Check how well the model does on the test set using the confusionMatrix() function.

``` r
confusionMatrix(kNNFit, newdata = test)
```

    ## Cross-Validated (10 fold, repeated 3 times) Confusion Matrix 
    ## 
    ## (entries are percentual average cell counts across resamples)
    ##  
    ##             Reference
    ## Prediction   setosa versicolor virginica
    ##   setosa       33.3        0.0       0.0
    ##   versicolor    0.0       31.7       1.0
    ##   virginica     0.0        1.6      32.4
    ##                             
    ##  Accuracy (average) : 0.9746

The Accuracy (average) is 0.9746.
