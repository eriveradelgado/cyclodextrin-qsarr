# Cyclodextrin QSAR Comparison

This repository will detail the process of creating and comparing QSARs that predict binding affinity of small molecules to  α-, β-, and γ-cyclodextrin.

## Workflow

Overall, the workflow can be followed by running the R Markdown files in order. However, the "zeroth" file, `00-dwnld.Rmd`, can be skipped. This is the least important file for reproducibility and the data generated is already loaded in the repository. Additionally, loading the file is likely to be difficult without an academic VPN or academic credentials to download the data. 

## File descriptions

### 00-dwnld.Rmd

- Downloads data from Rekharsky and Inoue (1997), Suzuki (2001), and Singh et al (2015)
- Converted Singh data from constant of association to Gibbs free energy change
- Abbreviated as `ri`, `suzuki`, and `singh`
- Basic wrangling of data into data frames
- Cyclodextrin is categorized as "alpha", "beta", "gamma" rather than by Greek letter
- Raw data is stored in `data/raw`, derived data is stored in `data/derived`

### 01-clean.Rmd

- Removed special or unconventional characters
- Cleaned by solvent conditions
- Rekharsky and Inoue data required most cleaning as it comes from multiple compiled sources

## Acknowledgements

This research was performed at Horst von Recum's lab at Case Western Reserve University under the mentorship of Edgardo Rivera-Delgado. 