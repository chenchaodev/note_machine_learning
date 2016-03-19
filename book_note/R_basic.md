##Bacsic Objects
###R Objects and Attributes
- atomic classes 
    - character
    - numeric (real numbers)
    - integer
    - complex
    - logical (True/False)
- most basic object is a vecter
    - only contain objects of the same class
    - **exception** list can contain different classes
    - `vector()` can create empty vectors
- Numbers
    - numeric objects
    - want an integer, use L suffix
    - Inf = 1/0
    - NaN
- Attributes, R objects can have attributs
    - names, dimnames
    - dimensions
    - class
    - length
    - other
    - use `attributes()` to access the attributes

###Vectors and Lists
- creating vectors
        x <- c(0.5, 0.6)
        x <- c("numeric", length = 10)
- mixing object
        y <- c(1,7, "a") ##character
- explicit coercion
        as.numeric(y)
        ##Nonsensical coercion results in NA
- Matrices
        m <- matrix(nrow = 2, ncol = 3)
        dim(m) ##[1] 2 3
        m <- matrix1:6, nrow = 2, ncol =3)
        m <- 1:10
        dim(m) <- c(2, 5)
- cbind an rbind
        x <- 1:3 
        y <- 10:12
        cbind(x, y)
            x y
         [1] 1 10
            ,,,
            rbind(x, y)
- lists
        x <- list(1, "a", TRUE, 1+4i)

###factors
    - label
            x <- factor(c("yes", "no", "yes"), levels = c("yes", "no"))
            unclas(x) ## 2 1 2

### Missing Values
        is.na(x) ##test NA
        is.nan(x) ## test nan

### data Frames
    - a special type of list where every element has the same length
    - can store different classes of objects
    - `row.name()`
    - created by `read.table()` or `read.csv()`
    - `data.matrix()` converted to matrix

### Names        
        names(x) = ("a,", "b", "c") 
        x <- list(a=1, b=2, c=3)
        x$a
        dimnames(m) <- list(c("a", "b"), c("c", "d"))

## data
### reading data
- ` read.table()`     `read.csv()` tabular
- `readLine()`  text
- `source()` R code file (inverse of dump)
- `dget` R code file (inverse of dput)
- `load` reading workspaces
- `unserialize` reading single R object in binary form

 ###writing data
        write.table
        writeLine
        dump
        dput
        save
        serialized

###read.table
        data <- read.table("foo.txt")
        clip <- read.table("clipboard")

###Large Dataset
- memory required MUST small than the amount of RAM
- set `comment.char = ""` if there are no commented lines in your file
- use read.table
        initial <- read.table("datatable.txt", nrows = 100)
        classes <- sapply(initial, class)
        tabAll <- read.table("datatable.txt", colClasses =classes)
- a data frame with 1,500,000 rows and 120 columns, all are numeric
        1,5000,000 x 12- x 8 bytes = 1.44 x 10 ^9 bytes ~1GB
###textual data formats


    y <- data.frame(a=1, b="a")
    dput(y)
    dput(y, file = "y.R")
    new.y <- dget("y.R")

    x <- "foo"
    y <- data.frame(a=1, b="a")
    dump(c("x", "y"), file = "data.R")
    rm(x, y)
    source("data.R")

###Interface to outside
- file
        con <- file("foo.txt", "r")
        data <- read.csv(con)
        close(con)
        ## is the same as  data<- read.csv("foo.txt")
- gzfile
        con <- gzfile("words.gz")
        x <- readLines(con, 10)
- bzfile
- url
        con <- url("http://www.jhsph.edu", "r")
        x <- readLines(con)
        head(x)

##Subsettings
- [] returns an object of the same class as the originnal
- [[]] used to extract elements of a list or a data frame, 
- $ used to extract element of a list or data frame by name
        x <- c("a", "b", "c", "c", "d", "a")
        x[1] ##"a"
        x[1:2] ## "a" "b"
        x[x > "a"]
        u <- x >"a"

### subsetting lists
    > x <- list(foo = 1:4, bar = 0.6)
    > x[1]
    $foo
    [1] 1 2 3 4
    > x[[1]
    [1] 1 2 3 4
    > x$bar
    [1] 0.6
    > x[["bar"]]
    [1] 0.6
    > x["bar"]
    $bar
    [1] 0.6
    > x[c(1, 2)]
    > x <- list(a = list(1, 3, 5), b = c(2, 4, 6))
    > x[[c(1, 3)]]
    [1] 5
    > x[[1][3]]
    [1] 5

### subsetting a matrix
    x <- matrix(1:6, 2, 3)
    x[1, 2] ##3
    x[2, 1] ##2
    x[1,] ## 1 3 4
    x[,2] ## 3 4
    x[1, 2, drop =FALSE]  ##return a matrix
    ##        [,1]
    ##[1,]     3

### partial matching
    x <- list(aardvark = 1:5)
    s$a ## 1 2 3 4 5
    x[["a", exact = FALSE]]

###remove missing value
    x <- c(1, NA, 4)
    bad <- is.na(x)
    x[!bad]

    x <- c(1, NA)
    y <- c("a", NA)
    good <- complete.cases(x, y)
    x[good]

    ##airquality is a matrix
    good <- complete.cases(airquality)
    airquality[good,][1:6,] ##remove NA values

### vectorized operations
    x <- 1:4 
    y <- 6:9
    x + y

    x <- matrix(1:4, 2, 2)
    y <- matrix(rep(10,4), 2, 2)
    x * y

## control
- if else
        y <- if(x>3) {
            10
        } else {
            0
        }
- for
        for (i in 1:10) {
            ## dosth
        }
        x <- c("a", "b", "c", "d")
        for( i in seq_along(x)) {}
        for( letter in x) {}
- while
        count <- 0
        while(count < 10) {
            count <- count +1
        }
- repeat
        count <-0
        repeat {
            if(count >1) {
                break
            } else {
                count <- count +1
            }
        }
- next and return
        for( i in 1:100) {
            if (i <= 20) {
                next
            }
            if(i == 90) {
                return
            }
        }

##functions
    f <- function(a, b = 1, c = 2, d= = NULL) {    
    }

    f <- function(a, b) {
        a^2
    }
    f(2)

    mplot <- function(x, y, type = "1", ...) {
        plot(x, y, type = type, ...)
    }

    function(..., sep = "", collapse= NULL)

###scoping
    make.power <- function(n) {
        pow <- function(x) {
            x^n
        }
        pow
    }

    cube <- make.power(2)
    ls(environment(cube))

    y <- 10
    f <- function(x) {
        y <- 2
        y^2 + g(x)
    }

    g <- fuction(x) {
        x*y
     }

## code standard

## date and time
    x <- as.Date("1879-01-01")
    unclass(x) ## 0
    weekdays
    months
    quarters
    x <- Sys.time()

    p <- as.POSIXlt(x)
    p$sec
    
    x <-as.Date("2012-01-01")
    y <- strptime("9 Jan 2011 11:34:21", "%d %b %Y %H:%M:%S")

    x <- as.POSIXlt(x)
    x - y
##loop in the command line
- lapply: loop over a list and evaluate a function on each element
        x <- list(a = 1:5, b = rnorm(10))
        lapply(x, mean)
        lapply(x, runif, min = 1, max = 3)
        lapply(x, function(elt) elt[,1])
- sapply: same as lapply bu simplify the result
    - result is a list which every on  length 1, return  a vector
    - is a list which same  length, return a matrix
    - else, return a list
- apply: apply a function over the margins of an array
        x <- matrix(rnorm(200), 20, 10)
        apply(x, 2, mean) ## return a list of 10
        apply(x, 1, mean) ## return a list of 20
        rowSums = apply(x, 1, sum)
        apply(x, 1, quantile, probs = c(0.25, 0.75))
        a <- array(rnorm(2*2*10), c(2,2,10))
        apply(a, c(1,2), mean)
        rowMeans(a, dims -2)
- tapply: apply afunction over subsets of a vector
        x <- c(rnorm(10), runif(10), rnorm(10, 1))
        f <- gl(3, 10)
        tapply(x, f, mean, simplify = FALSE)
- mapply: multivariate version on lapply
        mapply(rep, 1:4, 4:1)
        list(rep(1, 4), rep(2, 3), rep(3, 2), rep(4,1)
        noise <- function(n, mean, sd) {
            rnorm(n, mean, sd)
        }
        mapply(noise, 1: 5, 1: 5, 2)
- split
        x <- c(rnorm(10), runif(10), rnorm(10))
        f <- gl(3, 10)
        split(x, f)
        lapply(split(x, f), mean)

        s <- split(airquality, airquality$Month)
        lapply(s, mean, function(x) colMeans(x[, c("Ozone", "Solar.R", "Wind")]))

        split(x, list(f1, f2), drop= TRUE)

##debugging
- traceback
        lm(y-x)
        traceback()
- debug
        debug(lm)
        lm(y-x)
        ...
        Browse[2]> n
- browser
- trace
- recover
        option(error=recover)

## str funcgion
        str(lm)

## Simulation
### generation random number
- `rnorm` Normal variates with a given mean and standard deviation
- `dnorm` evaluate the Normal probability density at a point
-  `pnorm` evaluate the cumulative distribution function for a Normal distribution
- `rpois` Poisson variates with a given rate

d for density
r for random
p for cumulative distribution
q for quantile function

    dnorm(x, mean=0, sd=1, log= FALSE)
    pnorm(q, mean=0, sd=1, lower.tail = TRUE, log.p = FALSE)
    qnorm(p, mean=0, sd=1, lower.tail = TRUE, log.p = FALSE)
    rnorm(n, mean-0, sd=1)

    x <- rnorm(10)
    x <- rnorm(10, 20, 2)

    rpois(10, 1)
    ppois(2,2)

    set.seed(20)
    x <- rnorm(100)
    e <- rnorm(100, 0, 2)
    y <- 0.5 + 2 * x + e


##R Profiler
- `systerm.time(readLine("http://www.baidu.com/"))`
- `Rprof()` function starts the profiler in R
- `summaryRprof()`

##RMarkdown
- `install.packages("rmarkdown")`
- Rstudio 菜单新建RMarkdown文档
- 书写内容
- 按钮 `Knit HTML`，并选择 `View in Pane`
- 预览
   
    \```{r}
    summary(cars)
    \```

    \```{r, echo=FALSE}
    plot(cars)
    \```








    


 





        







    

