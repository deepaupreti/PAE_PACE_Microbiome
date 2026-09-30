# PAE_PACE_Microbiome
# Microbiome Analysis

This repository contains R code used for the microbiome analyses examining long-term gut microbial alterations following prenatal alcohol and/or cannabinoid exposure in mice.

The repository includes code for sequencing-depth quality control, alpha and beta diversity analyses, differential abundance testing, and associations between microbial taxa and adult behavioral outcomes.

## Study groups
Four prenatal exposure groups were included:

- CON – Control
- ALC – Prenatal alcohol exposure
- CB – Prenatal cannabinoid exposure
- ALC+CB – Combined prenatal alcohol and cannabinoid exposure

## Repository structure

### `QC_Alpha_Beta_RelativeAbundance.Rmd`

Performs microbiome quality control and community-level analyses, including:

- sequencing-depth quality control
- alpha diversity (Observed features, Chao1, Shannon, and Simpson)
- Bray-Curtis beta diversity and PCoA
- global PERMANOVA
- pairwise PERMANOVA with Benjamini-Hochberg correction
- assessment of multivariate dispersion
- generation of relative-abundance tables

One sample (`MICE.SEQ13`) was excluded from downstream analyses because of extreme sequencing depth and substantial library-size imbalance. The exclusion and associated QC are documented in the script.

### `Microbiome_MaAsLin2.Rmd`

Performs differential abundance analysis using the MaAsLin2 framework across multiple taxonomic levels.

Models include prenatal exposure group and sex as fixed effects and dam identity as a random effect to account for litter effects. Total sum scaling normalization and log transformation are performed within MaAsLin2.

### `MaAsLin2_species_barplot.R`

Generates species-level coefficient plots from the MaAsLin2 differential abundance results for visualization.

### `Microbiome_Behavior_Correlations.Rmd`

Examines associations between differentially abundant microbial taxa and behavioral outcomes using Spearman correlation analysis.

Behavioral measures include open-field locomotor activity, time spent in the center of the open field, and rotarod performance.

The script generates:
- correlation result tables
- volcano plots
- genus-level scatterplots
- species-level scatterplots
- CON versus pooled prenatal-exposure visualizations
- selected multipanel figures used for presentation of the results

The individual genus- and species-level scatterplots are provided as additional visualizations of the correlation analyses and are not all included in the manuscript.

## Input data

The analysis scripts require microbiome abundance/taxonomy tables and associated sample metadata.

Raw study data are not included in this GitHub repository. Data availability and repository accession information are provided in the associated manuscript.

Users wishing to reproduce the analyses should update the input file paths in the relevant scripts to point to their local copies of the required data files.

## Statistical analysis

Microbial community composition was evaluated using Bray-Curtis dissimilarity and PERMANOVA. Pairwise PERMANOVA p-values were adjusted for multiple comparisons using the Benjamini-Hochberg procedure.

Differential abundance was evaluated using MaAsLin2 with exposure group and sex as fixed effects and dam identity as a random effect.

Associations between microbial taxa and behavioral outcomes were evaluated using Spearman's rank correlations. Details of individual analyses and filtering criteria are documented within the corresponding scripts.

## Software

Analyses were performed primarily in R using packages including:

- phyloseq
- vegan
- MaAsLin2
- ggplot2
- dplyr
- ggpubr
- patchwork
- readxl
- openxlsx

Exact package and R versions used for the analyses are reported by `sessionInfo()` within the analysis scripts where applicable.

## Reproducibility

The scripts are provided to document the computational workflow used in the associated manuscript. Intermediate and figure output directories are created automatically by the scripts where specified.

To reproduce an analysis:

1. Download or clone this repository.
2. Obtain the corresponding input data described in the manuscript.
3. Place the input files in the appropriate local directory or update the file paths in the scripts.
4. Install the required R packages.
5. Run the relevant `.Rmd` or `.R` script from the beginning.

## Citation

Citation information for the associated manuscript will be added following publication.

## Contact

Questions regarding the analysis can be directed to the first and corresponding authors of the associated manuscript.
