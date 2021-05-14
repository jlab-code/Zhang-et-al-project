# Zhang-et-al-project
Mapping meQTL-epi in ddm1-derived epiRILs in four-step QTL analysis 

## System requirements
• R version 4.0.2 with the following installed packages: data.table, qtl, dplyr, xlsx, stringr, ggplot2, reshape2

• Sufficient amount of RAM memory to run the QTL analysis (recommended minimum is 8 GB)

• The administrative privileges are required to install and run R‑Studio utilities.

• A network connection for data recovering over network.

## Installation
To install the required packages type the following command in the R console.
```
install.packages(c('data.table', 'qtl', 'dplyr', 'xlsx', 'stringr', 'ggplot2', 'reshape2'))
```
To load the provided functions use load command in the R console.
```
source('functions/qtl-functions.R')
```

## Demo
examplary_run.R file presents the demo of running the pipeline for toy datasets located in toy_dataset directory (containing phenotype.csv, genotype.csv, positions.csv and marker.csv files).

The expected output is located in toy_outputs and it consists of the following files:

• PERM-all-traits_log_nm.Rdata - Rbinary dataset with the results from permutation test performed by rqtl package;

• QTL-direction-data-all-traits_log_nm.Rdata - Rbinary dataset with the effect direction for a given association (epimarker and phenotype);

• QTL-mapping-all-traits_log_nm.Rdata - Rbinary dataset with the results from the mapping procedure performed by rqtl package;

• REF-data-all-traits_log_nm.Rdata - Rbinary dataset with the crossing file used as the input for mapping procedure by rqtl package;

• SCANPOSINFO-all-traits_log_nm.Rdata - Rbinary dataset with positions of the markers after mapping procedure;

• gc_genotype_log_nm.csv - comma-separated csv file with the genotype data after preprocessing used for running the mapping procedure by rqtl package;

• mp_traits_log_nm.csv - comma-separated csv file with the phenotype data after preprocessing used for running the mapping procedure by rqtl package;

• info_peaks_log_nm.csv - comma-separated csv file with the positions of the peaks from mapping outputs.


## Instructions for use
• Required input datasets:
### phenotype dataset - csv comma divided file with quantitative traits for each line and phenotype
### genotype dataset - csv comma divided file with epigenotype profile (M/U) for each epimarker and line
### marker information dataset - directory to csv comma divided file with marker chromosome and start-end positions
### positions_dir - directory to csv comma divided file with phenotype (epiRIL positions)

## Functions overview
### mapping_qtl function (required datasets: mp_traits_dir, gc_genotype_dir, marker_dir)
mapping_qtl - perform preprocessing of the data (based on the log transformation and preparing datasets for QTL analysis)
            - perform a mappinh and permutations (QTL analysis)
            - calculate genotype probabilites and map
            - calculate effect direction (phenotype ~ epigenotype)         

#### getQTLpeaks_new function (required datasets: directory with outputs after performing mapping_qtl function)
getQTLpeaks_new - select a significant peaks with a given alpha level          

### qtlpeaks.plot function (required datasets: directory with outputs after performing mapping_qtl function, marker_dir)
qtlpeaks.plot - plot a LOD score thresholds for the peaks selected in getQTLpeaks_new

### transcis.plot function (required datasets: directory with outputs after performing mapping_qtl function, marker_dir, positions_dir)
transcis.plot - plot a LOD score thresholds for the peaks selected in getQTLpeaks_new
