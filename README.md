# BIOC0023

This repository includes the scripts submitted to Cirrus to analyse the genomic DNA from the microbial community of 13 paper pound notes, 13 polymer GBP banknotes, a control (i.e. swab from the inside of the plastic bag used for banknotes transport), a blank (i.e. unused swab) and a set of 12 hand microbiome samples. A full description of the bioinformatic procedure, the interpretation of the obtained results and the theoretical background to understand the aims and hypothesis of the study are provided in the report “Polymer Pound Notes: A Change in the Microbiome of British Currency”.

The attached files were written following the Portable Batch System (PBS) format. Therefore, the scripts include the walltime, the cores, the commands and cluster resources needed for each job. 

The files are presented following the order in which they were executed. Scripts were named according to the job they performed. The bioinformatic analysis procedure can be divided into four main components: raw sequence processing, taxonomic composition characterisation, diversity analysis and profiling of metagenome functional predictions. An outline of the purpose served by each script within the context of one of these components is provided below:


## Raw Sequence Processing

1.	Mapping file validation: 1_validate_mapping_file_combo.script
2.	Paired-end reads joining: 2_join_paired_ends.script
3.	Reads demultiplex and quality filtering: 3_demultiplex_joined_combo.script
4.	Chimeras detection: 4_identify_chimeras_joined_combo.script
5.	Chimeras exclusion: 5_filter_chimeras.script
6.	Closed-reference OTU picking against the UCHIME reference 'Gold' database using USEARCH (v6.1.5.44): 6_pick_closed_otus_joined_combo.script
7.	Singletons removal: 7_filter_singletons_joined_combo.script
8.	Outliers removal: 8_filter_outliers_joined_combo.script
9.	Summarisation of OTU table after exclusion of singletons and outliers: 9_summarise_sing+outliers_out_OTU_table_joined_combo.script


## Taxonomic Composition Characterisation

10.	Core diversity analysis: 10_analyse_core_diversity_joined_combo.script


## Diversity Analysis

11.	Selection of representative sequences: 11_pick_rep_joined_combo.script
12.	Alignment of representative sequences: 12_align_rep_OTUs_joined_combo.script 
13.	Exclusion of highly variable regions from the alignment: 13_filter_alignment_joined_combo.script
14.	Building of phylogenetic tree: 14_make_philogeny_joined_combo.script

### I. Alpha Diversity Analysis

15.	Rarefaction of OTU tables at multiple sequencing depths: 15_multi_rarefactions_joined_combo.script
16.	Calculation of alpha diversity at each rarefaction depth: 16_alpha_diversity_joined_combo.script
17.	Collation of alpha diversity tables: 17_collate_alpha_diversity_joined_combo.script
18.	Rarefaction curves plotting: 18_make_rarefaction_plots_joined_combo.script

### II. Beta Diversity Analysis

19.	Generation of unweighted UniFrac distance matrices on previously rarefied OTU tables: 19_beta_diversity_unweighted_unifrac_joined_combo.script
20.	Generation of weighted UniFrac distance matrices on previously rarefied OTU tables: 20_beta_diversity_weighted_unifrac_joined_combo.script
21.	Transformation of unweighted UniFrac distance matrices to principal coordinate axes: 21_principal_coordinates_unweighted_unifrac_joined_combo.script
22.	Transformation of weighted UniFrac distance matrices to principal coordinate axes: 22_principal_coordinates_weighted_unifrac_joined_combo.script
23.	PCoA of unweighted UniFrac distances: 23_make_emperor_unweighted_unifrac_joined_combo.script
24.	PCoA of weighted UniFrac distances: 24_make_emperor_weighted_unifrac_joined_combo.script
25.	ANOSIM of unweighted UniFrac distances: 25_anosim_beta_diversity_unweighted_unifrac_joined_combo.script
26.	ANOSIM of weighted UniFrac distances: 26_anosim_beta_diversity_weighted_unifrac_joined_combo.script


## Profiling of Metagenome Functional Predictions

27.	Closed-reference OTU picking against the GreenGenes (v13.5) database: 27_pick_picrust_OTUs_joined_combo.script

The output of step 27 was used as an input for the workflow outlined in the Langille Lab PICRUSt Galaxy server (http://galaxy.morganlangille.com/). Having performed the “Normalize by Copy Number”, “Predict Metagenome” and “Categorize by Function” steps, a BIOM file with the PICRUst predictions for the specified level (i.e. L3) was generated, downloaded from the site and uploaded to Cirrus. Subsequently, it was used as an input for step 28.

28.	Graphical summarisation of the biom file resulting from the PICRUSt pipeline: 28_functional_summary_through_plots_joined_combo.script 


