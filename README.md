# QTL-analysis-arabidopsis
Four step complex analysis with plotting the results

###########################################################################
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
