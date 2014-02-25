Problem-2--Wine
===============
> library(foreign)
> wine = read.csv("http://www.nd.edu/~mclark19/learn/data/goodwine.csv")
> summary(wine)
 fixed.acidity    volatile.acidity  citric.acid    
 Min.   : 3.800   Min.   :0.0800   Min.   :0.0000  
 1st Qu.: 6.400   1st Qu.:0.2300   1st Qu.:0.2500  
 Median : 7.000   Median :0.2900   Median :0.3100  
 Mean   : 7.215   Mean   :0.3397   Mean   :0.3186  
 3rd Qu.: 7.700   3rd Qu.:0.4000   3rd Qu.:0.3900  
 Max.   :15.900   Max.   :1.5800   Max.   :1.6600  
 residual.sugar     chlorides      
 Min.   : 0.600   Min.   :0.00900  
 1st Qu.: 1.800   1st Qu.:0.03800  
 Median : 3.000   Median :0.04700  
 Mean   : 5.443   Mean   :0.05603  
 3rd Qu.: 8.100   3rd Qu.:0.06500  
 Max.   :65.800   Max.   :0.61100  
 free.sulfur.dioxide total.sulfur.dioxide
 Min.   :  1.00      Min.   :  6.0       
 1st Qu.: 17.00      1st Qu.: 77.0       
 Median : 29.00      Median :118.0       
 Mean   : 30.53      Mean   :115.7       
 3rd Qu.: 41.00      3rd Qu.:156.0       
 Max.   :289.00      Max.   :440.0       
    density             pH          sulphates     
 Min.   :0.9871   Min.   :2.720   Min.   :0.2200  
 1st Qu.:0.9923   1st Qu.:3.110   1st Qu.:0.4300  
 Median :0.9949   Median :3.210   Median :0.5100  
 Mean   :0.9947   Mean   :3.219   Mean   :0.5313  
 3rd Qu.:0.9970   3rd Qu.:3.320   3rd Qu.:0.6000  
 Max.   :1.0390   Max.   :4.010   Max.   :2.0000  
    alcohol         quality        color     
 Min.   : 8.00   Min.   :3.000   red  :1599  
 1st Qu.: 9.50   1st Qu.:5.000   white:4898  
 Median :10.30   Median :6.000               
 Mean   :10.49   Mean   :5.818               
 3rd Qu.:11.30   3rd Qu.:6.000               
 Max.   :14.90   Max.   :9.000               
     white          good     
 Min.   :0.0000   Bad :2384  
 1st Qu.:1.0000   Good:4113  
 Median :1.0000              
 Mean   :0.7539              
 3rd Qu.:1.0000              
 Max.   :1.0000              
> install.packages("caret")
also installing the dependencies ‘iterators’, ‘foreach’

trying URL 'http://cran.rstudio.com/bin/windows/contrib/3.0/iterators_1.0.6.zip'
Content type 'application/zip' length 317868 bytes (310 Kb)
opened URL
downloaded 310 Kb

trying URL 'http://cran.rstudio.com/bin/windows/contrib/3.0/foreach_1.4.1.zip'
Content type 'application/zip' length 388546 bytes (379 Kb)
opened URL
downloaded 379 Kb

trying URL 'http://cran.rstudio.com/bin/windows/contrib/3.0/caret_6.0-24.zip'
Content type 'application/zip' length 3625007 bytes (3.5 Mb)
opened URL
downloaded 3.5 Mb

package ‘iterators’ successfully unpacked and MD5 sums checked
package ‘foreach’ successfully unpacked and MD5 sums checked
Warning in install.packages :
  unable to move temporary installation ‘C:\Program Files\R\R-3.0.2\library\file12b859264753\foreach’ to ‘C:\Program Files\R\R-3.0.2\library\foreach’
package ‘caret’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Documents and Settings\Russ Baker\Local Settings\Temp\RtmpMXXAu0\downloaded_packages

> library(corrplot)
Error in library(corrplot) : there is no package called ‘corrplot’
> install.packages("corrplot")
trying URL 'http://cran.rstudio.com/bin/windows/contrib/3.0/corrplot_0.73.zip'
Content type 'application/zip' length 2680428 bytes (2.6 Mb)
opened URL
downloaded 2.6 Mb

package ‘corrplot’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Documents and Settings\Russ Baker\Local Settings\Temp\RtmpMXXAu0\downloaded_packages
> library(corrplot)
> corrplot(cor(win[, -c(13, 15)]), method = "number", tl.cex = 0.5)
Error in is.data.frame(x) : object 'win' not found
> corrplot(cor(wine[, -c(13, 15)]), method = "number", tl.cex = 0.5)
> install.packages("lattice")
trying URL 'http://cran.rstudio.com/bin/windows/contrib/3.0/lattice_0.20-24.zip'
Content type 'application/zip' length 724822 bytes (707 Kb)
opened URL
downloaded 707 Kb

package ‘lattice’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Documents and Settings\Russ Baker\Local Settings\Temp\RtmpOqK2MG\downloaded_packages
> install.packages("ggplot2")
trying URL 'http://cran.rstudio.com/bin/windows/contrib/3.0/ggplot2_0.9.3.1.zip'
Content type 'application/zip' length 2656354 bytes (2.5 Mb)
opened URL
downloaded 2.5 Mb

package ‘ggplot2’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Documents and Settings\Russ Baker\Local Settings\Temp\RtmpOqK2MG\downloaded_packages
> install.packages("foreach")
trying URL 'http://cran.rstudio.com/bin/windows/contrib/3.0/foreach_1.4.1.zip'
Content type 'application/zip' length 388546 bytes (379 Kb)
opened URL
downloaded 379 Kb

package ‘foreach’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Documents and Settings\Russ Baker\Local Settings\Temp\RtmpOqK2MG\downloaded_packages
> library(caret)
Loading required package: lattice
Loading required package: ggplot2
> library(lattice)
> library(ggplot2)
> set.seed(1234)
> #so that the indices will be the same when re-run
> trainIndices = createDataPartition(wine$good, p =0.8, list =F)
> wanted = !colnames(wine) %in% c("free.sulfur.dioxide", "density", "quality", "color", "white")
> wine_train = wine[trainIndices, wanted] #remove quality and color, as well as density and others
> wine_test = wine[-trainIndices, wanted]
> wine_trainplot = predict(preProcess(wine_train[,-10], method="range"), wine_train[,-10])
> featurePlot(wine_trainplot, wine_train$good, "box")
