# Installing METABOLIC 

## Background 

METabolic And BiogeOchemistry anaLyses In miCrobes (refer to https://github.com/AnantharamanLab/METABOLIC) <br> 
Current Version: 4.0 Tested on: Ubuntu 18.04.5 LTS (Linux 5.4.0-81-generic x86_64) (Sep 2021)

This software enables the prediction of metabolic and biogeochemical functional trait profiles to any given genome datasets. These genome datasets can either be metagenome-assembled genomes (MAGs), single-cell amplified genomes (SAGs) or isolated strain sequenced genomes. METABOLIC has two main implementations, which are METABOLIC-G and METABOLIC-C.

METABOLIC-G.pl allows for generation of metabolic profiles and biogeochemical cycling diagrams of input genomes and does not require input of sequencing reads. METABOLIC-C.pl generates the same output as METABOLIC-G.pl, but as it allows for the input of metagenomic read data, it will generate information pertaining to community metabolism. It can also calculate the genome coverage. The information is parsed and diagrams for elemental/biogeochemical cycling pathways (currently Nitrogen, Carbon, Sulfur and "other") are produced.

## Installation Instruction

I found conflicts appear when using the environment.yaml provided by the METABOLIC repository to install METABOLIC on REDHAT 
system. Therefore, I offer an installation instruction and I strongly suggest to **install R packages without conda**. 
Using conda in R package installing is highly unsustinable and easy to start multiple failures in many ways.

Step 1 Install All conda-depended packages

*Only for METABOLIC-G* <br> 
```
  mamba create -n METABOLIC -c conda-forge -c bioconda diamond hmmer r=3.6 perl prodigal icu
  source activate METABOLIC
  mamba install r=3.6 perl-data-dumper perl-bioperl perl-getopt-long perl-bio-procedural perl-statistics-descriptive perl-posix perl-file-spec perl-parallel-forkmanager
```  
Have to notice that, without `r=3.6` in mamba installation, the wrapper would ask you to automatically update R to the latest version. <br> 

Step 2 You are gonna run R for R dependencies. <br> 
```
  install.package("BiocManager")
  # to ensure correct installation of openxlsx or tidyverse or tidyr
  install.packages("stringi", configure.args="--disable-pkg-config") 
  BiocManager::install(c("diagram","forcats","digest","htmltools","rmarkdown","reprex","tidyverse",
    "ggthemes","ggalluvial","reshape2","ggraph","pdftools","igraph","tidygraph","stringr","plyr","dplyr",
    "openxlsx"))
```
Version of R packages do not matter.

Step 3 git clone the METABOLIC repository and start preparation for references under the instructions provided by METABOLIC. <br> 
