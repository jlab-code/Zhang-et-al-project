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

Required input datasets
mp_traits_dir - directory to csv comma divided file with quantitative traits for each line and phenotype
(column names: phenotype/epiRILs; row names: lines)

gc_genotype_dir - directory to csv comma divided file with epigenotype profile (M/U) for each epimarker and line
(column names: epimarkers; row names: lines)
first row: chromosome for a given marker

marker_dir - directory to csv comma divided file with marker chromosome and start-end positions
(column names: marker, chr, start, end)

positions_dir - directory to csv comma divided file with phenotype (epiRIL positions)
(column names: name, chr, start, end)

###########################################################################

Functions overview
mapping_qtl function (required datasets: mp_traits_dir, gc_genotype_dir, marker_dir)
mapping_qtl - perform preprocessing of the data (based on the log transformation and preparing datasets for QTL analysis)
            - perform a mappinh and permutations (QTL analysis)
            - calculate genotype probabilites and map
            - calculate effect direction (phenotype ~ epigenotype)
            
getQTLpeaks_new function (required datasets: directory with outputs after performing mapping_qtl function)
getQTLpeaks_new - select a significant peaks with a given alpha level          

qtlpeaks.plot function (required datasets: directory with outputs after performing mapping_qtl function, marker_dir)
qtlpeaks.plot - plot a LOD score thresholds for the peaks selected in getQTLpeaks_new

transcis.plot function (required datasets: directory with outputs after performing mapping_qtl function, marker_dir, positions_dir)
transcis.plot - plot a LOD score thresholds for the peaks selected in getQTLpeaks_new
