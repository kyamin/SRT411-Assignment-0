---
title: "Assignment0 --- A (very) short introduction to R"
author: "Kashif Yamin"
date: '2016-01-31'
output: md_document
---


**Objective**   
This is Assigmnet0 for SRT411 course. The objective of this assigment is to demonetrate the basic syntax of R-Studio using various built-in functions. The code needs to be submitted on github. The usename I used for github and the resources to complete the assignment are following:

**Username for Github: kyamin**

<https://cran.r-project.org/doc/contrib/Torfs+Brauer-Short-R-Intro.pdf>
<http://kbroman.org/knitr_knutshell/pages/Rmarkdown.html>
<https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf>
<http://kbroman.org/knitr_knutshell/pages/markdown.html>
<http://nicercode.github.io/guides/reports/>
<http://rmarkdown.rstudio.com>

**ToDo # 1**

Compute the difference between 2014 and the year you started at this university and divide this by the di erence between 2014 and the year
you were born. Multiply this with 100 to get the percentage of your life you have spent at this university. Use brackets if you need them.

```{r}
((2016-2014)/(2016-1994)*100)
```



**ToDo # 2**

Repeat the previous ToDo, but with several steps in between. You can give the variables any name you want, but the name has to start
with a letter.

``` {r}
start = (2016 - 2014)
age = (2016-1994)
percent = 100
(start / age * 100)
```

**ToDo # 3**

Compute the sum of 4, 5, 8 and 11 by first com-bining them into a vector and then using the function sum.

```{r}
vector=c(4,5,8,11)
sum(vector)
```

**ToDo # 4**

Plot 100 normal random numbers.

```{r}
random=rnorm(100)
plot(random)
```

**ToDo # 5 **

Find help for the sqrt function.

```{r}
help(sqrt)
```

**ToDo # 6**

Make a file called firstscript.R containing R- code that generates 100 random numbers and plots them, and run this script several times.


```{r}
source("/home/kyamin/Desktop/firstscript.R")
```


**ToDo # 7**

Put the numbers 31 to 60 in a vector namedP and in a matrix with 6 rows and 5 columns namedQ.Tip: use the function seq. Look at the di erent ways scalars, vectors and matrices are denoted in the workspace window.

```{r}
P = seq(from=31, to=60, by=1)
Q = matrix(P, ncol=5, nrow = 6)
Q 
```

**ToDo # 8**

Make a script file which constructs three ran-dom normal vectors of length 100. Call these vectors x1,x2 and x3. Make a data frame called t with three columns (called a,b and c) con-taining respectively x1, x1+x2 and x1+x2+x3. Call the following functions for this data frame: plot(t) and sd(t). Can you understand the results? Rerun this script a few times.

```{r}
source("/home/kyamin/Desktop/source.R")
x1 = c(rnorm(100))
x2 = c(rnorm(100))
x3 = c(rnorm(100))
t = data.frame(a=x1, b=x1+x2, c=x1+x2+x3)
plot(t)
```

**ToDo # 9**

Add these lines to the script file of the previous section. Try to find out, either by experimenting or by using the help, what the meaning is of rgb, the last argument of rgb, lwd, pch, cex.

**Added the following lines in the previous script:**

```{r}
source("/home/kyamin/Desktop/source.R")
t = data.frame(a = x1,b = x1 + x2,c = x1 + x2 + x3)
plot(t$a, type="l", ylim=range(t),lwd=1, col=rgb(1,0,0,0.9))
lines(t$b, type="s", lwd=2,col=rgb(0.3,0.4,0.3,0.8))
points(t$c, pch=1, cex=2,col=rgb(0,0,1,0.9))
```


**ToDo # 10**

Make a file called tst1.txt in Notepad from the example in Figure 4 and store it in your working directory. Write a script to read it, to multiply the column called
g by 5 and to store it as tst2.txt

```{r}
variable = data.frame(a = c(3,4,5),b = c(12,43,54))
write.table(variable,file="tst1.txt",row.names=FALSE)
variable = read.table(file="tst1.txt",header=TRUE)
```

**ToDo # 11**

Compute the mean of the square root of a vec-tor of 100 random numbers. What happens?


```{r}
vec = c(sample.int(101,size=100,replace=TRUE))
mean(sqrt(vec))
```

**ToDo # 12**

Make a graph with on the x-axis: today, Sin-terklaas 2014 and your next birthday and on the y-axis the number of presents you expect on each of these days. Tip: make two vectors first.

```{r}
year=strptime( c("20160129000000",
"20141205000000", "20160118000000"),
format="%Y%m%d%H%M%S")
NumberPresents=c(1,5,10)
plot(year,NumberPresents)
```

**ToDo # 13**

Make a vector from 1 to 100.  Make a for-loop which runs through the whole vector.  Multiply the elements which are smaller than 5 and larger than 90 with 10 and the other elements with 0.1.

```{r}
vector = seq(from=1, to=100)
for(i in 1:100)
{
  if(vector[i] < 5 | vector[i] > 90)
    {
    vector[i] = vector[i] * 10
    }
  else
  {   vector[i] = vector[i] * 0.1
    }
}
```


**ToDo # 14**

Write a function for the previous ToDo, so that you can feed it any vector you like (as  argument).Use a for-loop  in the func-tion to do the computation with each ele-ment. Use the standard  R  function length in the specification of the counter

```{r}
myfunction = function(arg){
  for(i in 1:length(arg))
    {
    if(arg[i] < 5 | arg[i] > 90)
      {
      arg[i] = arg[i] * 10
      }
    else
      {   
        arg[i] = arg[i] * 0.1
      }
    }
  return(arg)
  }
```

```{r, echo=FALSE, results="hide"}
b = seq(from=1, to=100)
myfunction(arg=b)
```


**ToDo # 15**

```{r}
vector = (1:100)
vector = ifelse(vector < 5 | vector > 90, vector * 10, vector * 0.1)
```

```{r, echo=FALSE}
vector
```


