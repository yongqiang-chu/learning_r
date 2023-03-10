--- 
title: "Data Science for Economists and Other Animals"
author: "Grant McDermott and Ed Rubin"
date: "2021-08-03"
site: bookdown::bookdown_site
url: 'https\://grantmcdermott/ds4e'
github-repo: grantmcdermott/ds4e
twitter-handle: grant_mcdermott
documentclass: book
bibliography: [book.bib, packages.bib]
biblio-style: apalike
link-citations: yes
description: "A compendium of tools and tricks that we wish we'd been taught in grad school."
---

# Welcome {.unnumbered}

This is the website for **Data Science for Economists and Other Animals**. The 
book is very much in the early development stages, but draws from lecture 
material that we have been refining over the last several years. We're not 
actively looking for feedback yet, but hope to once we've managed to build out
enough of the chapters and basic book structure.

If you're interested in the motivation for this book, here is some placeholder text from Grant's syllabus:

> This seminar (ED: book) is targeted at economics PhD students (ED: and other animals) and will introduce you to the modern data science toolkit. While some material will likely overlap with your other quantitative and empirical methods courses, this is not just another econometrics course. Rather, my goal is bring you up to speed on the practical tools and techniques that I feel will most benefit your dissertation work and future research career. This includes many of the seemingly forgotten skills --- like where to find interesting data sets in the "wild" and how to actually clean them --- that are crucial to any successful scientific project, but are typically excluded from core econometrics and statistics classes. We will cover topics like version control and effective project management; programming; data acquisition (e.g. web-scraping), cleaning and visualization; GIS and remote sensing products; and tools for big data analysis (e.g. relational databases, cloud computation and machine learning). In short, we will cover things that I wish someone had taught me when I was starting out in graduate school.

## Install necessary software packages {#sw-intro}

The primary programming language used throughout this book is R 
(https://www.r-project.org/). The book was built against R version 4.1.0.

Each chapter of the book begins with a description of the software --- e.g. R
packages and external libraries --- needed to complete that section. However, 
users may find it convenient to install all of the necessary packages (and 
versions thereof) in a single go. To that end, we have used **renv** 
([link](https://rstudio.github.io/renv)) to snapshot 
the project environment of the book. This means that you can install all of the 
R packages needed to run the code in this book, simply by cloning the 
companion GitHub repo (https://github.com/grantmcdermott/ds4e) and running:


```r
# renv::init() ## Only run this line if the next line returns an error
renv::restore(prompt = FALSE)
```

### Special requirements for Linux users

Linux users will likely need to install a few system requirements before running
the `renv::restore()` command above, mostly related to spatial libraries. (More 
information about individual distro requirements 
[here](https://github.com/r-spatial/sf#linux).) For Ubuntu users on 20.04 and 
above, the following commands should suffice:


```sh
sudo apt update && sudo apt upgrade -y
sudo apt install -y libudunits2-dev libgdal-dev gdal-bin \
  libgeos-dev libproj-dev libcairo2-dev
```

As an aside, our **renv** configuration is set up so that it will install
pre-compiled R package binaries across operating systems, including most Linux 
distros. This should make package installation much faster and less error prone.
If you are on a Linux system, but don't plan to use our recommended **renv** 
approach for simultaneously installing all of the needed packages, we would
still recommend configuring your system to install R package binaries from 
[RStudio Package Manager](https://packagemanager.rstudio.com/client/#/repos/1/overview).
(RSPM). Again, assuming a Linux user on Ubuntu 20.04, this would require adding 
the following line to your `~/.Rprofile` dotfile:

```
options(repos = c(RSPM = "https://packagemanager.rstudio.com/all/__linux__/focal/latest"))
```

An alternative approach for installing pre-compiled R package binaries on Linux
is available in the form of the **bspm** package 
([link](https://github.com/Enchufa2/bspm)). The benefit of this approach 
(compared to our recommended renv/RSPM approach) is that it will automatically 
handle system dependencies too. The downside is that there is no way to snapshot
packages and it will simply (and automatically) pull in the most recently 
available package versions. This may inadvertently introduce breaking changes 
with respect to the code presented here.

## Building the book locally

Finally, note that you might need a few extra packages if you want to build the 
book locally (unlikely):


```r
library(bookdown)
library(bslib)
library(downlit)
library(usethis)
```



