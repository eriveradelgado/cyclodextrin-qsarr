# Cyclodextrin QSAR Comparison

This repository will detail the process of creating and comparing QSARs that predict binding affinity of small molecules to  α-, β-, and γ-cyclodextrin.

## Workflow

Overall, the workflow can be followed by running the R Markdown files in order. However, the "zeroth" file, `00-dwnld.Rmd`, can be skipped. This is the least important file for reproducibility and the data generated is already loaded in the repository. Additionally, loading the file is likely to be difficult without an academic VPN or academic credentials to download the data. 

## Steps

### 00. Downloading experimental observations

File: `00-dwnld.Rmd`

- Downloads data from Rekharsky and Inoue (1997), Suzuki (2001), and Singh et al (2015)
- Converted Singh data from constant of association to Gibbs free energy change
- Abbreviated as `ri`, `suzuki`, and `singh`
- Basic wrangling of data into data frames
- Cyclodextrin is categorized as "alpha", "beta", "gamma" rather than by Greek letter
- Raw data is stored in `data/raw`, derived data is stored in `data/derived`

### 01. Cleaning experimental observations

File: `01-clean.Rmd`

- Removed special or unconventional characters
- Cleaned by solvent conditions
- Rekharsky and Inoue data required most cleaning as it comes from multiple compiled sources
  - Additional cleaning is necessary in order to pass the data to `02-sdf.Rmd`
  - Typos in chemical names corrected

### 02. Downloading ligand structures as SDFs

File: `02-sdf.Rmd`

- Structure data files (SDFs) downloaded into `sdf/`
  - Subdirectories for each data source
  - Additional subdirectory for compiled data from each source
- Queried Chemical Identifier Resolver from NCI https://cactus.nci.nih.gov/chemical/structure
- All observations successfully downloaded
- Observations compiled into single SDFs
- The directories of individual SDFs is not uploaded onto GitHub for convenience
  - Combined SDF file is backed up in GitHub

### 03. Calculating chemical descriptors using CDK for R

File: `03-cdk.Rmd`

- Using package `rcdk` to obtain chemical descriptors
  - https://cran.r-project.org/web/packages/rcdk/vignettes/using-rcdk.html
- Calculates 281 descriptors for each molecule
- Does not calculate 3D descriptors
  - 3D descriptors may not be reliable due to lack of optimization

### 04. Other sources for chemical descriptors

File: `04-desc_external.Rmd

- Incorporation of descriptors from other sources
- PaDEL-Descriptor
  - http://yapcwsoft.com/dd/padeldescriptor/
- Online chemical database with modeling environment
  - https://ochem.eu
- Mordred
  - https://github.com/mordred-descriptor/mordred

## Acknowledgements

This research was performed at Horst von Recum's lab at Case Western Reserve University under the mentorship of Edgardo Rivera-Delgado. 