# Prerequisites

A number of different libraries are needed for the course. You can install these packages as below.


```r
cran.pkg <- c("devtools",
              "ape",
              "rentrez",
              "seqinr",
              "phangorn",
              "ips",
              "kdetrees",
              "bios2mds",
              "XML",
              "ggplot2",
              "magrittr")
bioc.pkg <- c("msa","annotate")
rforge.pkg <- c("rcolgem")
github.pkg <- c("GuangchuangYu/ggtree")
```

The following will install the missing packages on your system. You will first need to set repositories to install from CRAN, the Bioconductor repositories, and R-Forge.


```r
setRepositories()
```



```r
pkg <- c(cran.pkg,bioc.pkg,rforge.pkg)
pkg.new <- pkg[!(pkg %in% installed.packages()[,"Package"])]
if(length(pkg.new)) install.packages(pkg.new)
```

The ```ggtree``` library is on [GitHub](http://github.com) and so needs to be installed with a function from the ```devtools``` library.


```r
for(gp in github.pkg){
  gpname <- strsplit(gp,"/",)[[1]][2]
  if(!(gpname %in% installed.packages()[,"Package"])){
    devtools::install_github(gp)
  }
}
```
