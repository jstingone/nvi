# Neighborhood Environmental Vulnerability Index 
***

**Citation:** We are in the process of preparing a manuscript describing the creation of this vulnerability index and will include a citation here when it is available. Our upcoming manuscript will include more information about the creation and potential applications of the index.

## 1. Overview
We developed a Neighborhood Environmental Vulnerability Index (NEVI) to measure vulnerability to environmental pollution using publicly available data. We applied the [Toxicological Prioritization Index (ToxPi)](https://toxpi.org/) to integrate data across different domains, characterize neighborhood vulnerability to environmental pollution in New York City (NYC), and determine if sources of vulnerability varied across neighborhoods.

## 2. Downloading the NEVI for NYC
The current version of the NEVI for NYC can be downloaded in the [`data/processed`](https://github.com/jstingone/nvi/tree/main/data/processed) folder. The data file is available in multiple formats at the following spatial scales:

*Census tract-level*
- CSV: [`nevi_tract_final.csv`](https://github.com/jstingone/nvi/blob/main/data/processed/nevi_tract_final.csv)
- R Data file: [`nevi_tract_final.rds`](https://github.com/jstingone/nvi/blob/main/data/processed/nevi_tract_final.rds)

*Zip code-level*
- CSV: [`nevi_zip_final.csv`](https://github.com/jstingone/nvi/blob/main/data/processed/nevi_zip_final.csv)
- R Data file: [`nevi_zip_final.rds`](https://github.com/jstingone/nvi/blob/main/data/processed/nevi_zip_final.rds)

![nevi plot](https://raw.githubusercontent.com/jstingone/nvi/main/figures%20and%20tables/figures/fig_nevi.png)

## 3. Folder Structure
We have organized relevant files for the calculation of the NEVI in the following folders:
- `code and instructions`: Code for the calculation of the index
- `data`: 
	- `data/raw`: data files downloaded before any data cleaning/processing
	- `data/processed`: data files after any data cleaning/processing or created manually
- `figures and tables`: figures and tables created from our code


## 4. Data Sources
We used two primary data sources for the following features used to calculate the NEVI:
- [U.S. American Community Survey, 2015-2019 5-year estimates](https://www.census.gov/data/developers/data-sets/acs-5year.2019.html): demographics, economic indicators, and residential characteristics
	- Request a U.S. Census API key [here](https://api.census.gov/data/key_signup.html)
- [U.S. Centers for Disease Control and Prevention PLACES, 2020](https://chronicdata.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-Place-Data-202/q8xq-ygsk): health status information (health behaviors, conditions, preventive practices, and insurance access)

Other data sources used to create zip code-level NEVI:
- [Modified Zip Code Tabulation Areas (MODZCTA) used by the New York City Department of Health & Mental Hygiene (NYC DOHMH)](https://data.cityofnewyork.us/Health/Modified-Zip-Code-Tabulation-Areas-MODZCTA-/pri4-ifjk)
- [U.S. Department of Housing and Urban Development - Zip Code and Tract Crosswalk](https://www.huduser.gov/portal/datasets/usps_crosswalk.html)


## 5. Requirements
You will need the following software, R packages, and data to calculate the NEVI.

### 5.1 Software and R Packages
1. Download the following software: 
- [R](https://cran.r-project.org/bin/windows/base/)
- [RStudio](https://www.rstudio.com/products/rstudio/download/#download) or another R graphical user interface
- [ToxPi Graphical User Interface](https://toxpi.org/)
2. Run the following code in R to install the following packages:
- These required packages are needed for the creation of the NEVI. 
	```installation_nevi	
	install.packages(c('tidyverse','tidycensus','rio'), dependencies = TRUE)
	```
- These optional packages are needed for the creation of clusters and figures and tables presented in the manuscript.
	```installation_figs_tabs
	install.packages(c('factoextra','cluster','skimr','janitor','factoextra','sf','ggpubr','ggsn','ggspatial','tigris','ggsflabel','ggpubr','colorBlindness','ggpattern','gplots'), dependencies = TRUE)
	devtools::install_github('yutannihilation/ggsflabel')
	```
3. We used the following versions of software and packages:
- **Software**:
	- *R:* 4.1.1 ("Kick Things")
	- *RStudio:* 2021.09.0+382 ("Ghost Orchid")
	- *ToxPi GUI:* version 2.3, August 2019 update
- **Packages**:
	- *`tidyverse`:* 1.3.1 
	- *`tidycensus`:* 1.1.2 
	- *`rio`:* 0.5.29 
- **Optional Packages**
	- *`cluster`:* 2.1.2 
	- *`factoextra`:* 1.0.7 
	- *`skimr`:* 2.1.3 
	- *`janitor`:* 2.1.0 
	- *`sf`:* 1.0.3 
	- *`ggpubr`:* 0.4.0 
	- *`ggsn`:* 0.5.0 
	- *`ggspatial`:* 1.1.5 
	- *`nycgeo`:* 0.1.0.9000 
	- *`tigris`:* 1.5 
	- *`devtools`:* 2.4.3
	- *`ggsflabel`:* 0.0.1 
	- *`ggpubr`:* 0.4.0 
	- *`colorBlindness`:* 0.1.9 
	- *`ggpattern`:* 0.2.0 
	- *`gplots`:* 3.1.1 


### 5.2 Data
- U.S. Centers for Disease Control and Prevention PLACES 2020
	- Download [here](https://chronicdata.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-Place-Data-202/q8xq-ygsk).
- U.S. American Community Survey, 5-year estimates from 2015-2019
	- To download the data, refer to our code: `code and instructions/A1-download-census-data.Rmd`
	- More information about the American Community 5-year estimates [here](https://www.census.gov/data/developers/data-sets/acs-5year.2019.html).


## 6. Code and Instructions
To calculate the NEVI, you will need to follow the instructions in these documents in the `code and instructions` folder. Click on the corresponding markdown (.md) files to view the code and instructions directly online.
- [`A1-download-census-data`](https://github.com/jstingone/nvi/blob/main/code%20and%20instructions/A1-download-census-data.md): Download features from the U.S. Census American Community Survey needed to calculate the index 
- [`A2-preprocess-nevi-features`](https://github.com/jstingone/nvi/blob/main/code%20and%20instructions/A2-preprocess-nevi-features.md): Prepare features to input into ToxPi.
- [`A3-calculate-nevi-toxpi-gui`](https://github.com/jstingone/nvi/blob/main/code%20and%20instructions/A3-calculate-nevi-toxpi-gui.docx): Calculate the NEVI and subdomain scores using Toxpi.
- [`A4-clean-nevi`](https://github.com/jstingone/nvi/blob/main/code%20and%20instructions/A4-clean-nevi.md): Clean the output from ToxPi and calculate domain scores.

There are also other code available to accomplish optional tasks:
- [`B1-create-nevi-clusters`](https://github.com/jstingone/nvi/blob/main/code%20and%20instructions/B1-create-nevi-clusters.md): Create clusters based on NEVI subdomain scores and their corresponding weights using hierarchical clustering
- [`B2-calculate-ndi-svi`](https://github.com/jstingone/nvi/blob/main/code%20and%20instructions/B3-calculate-ndi-svi.Rmd): Calculate a previously created index called the Neighborhood Deprivation Index (NDI).
- [`B3-create-figures-tables`](https://github.com/jstingone/nvi/blob/main/code%20and%20instructions/B4-create-figures-tables.Rmd): Create figures and tables presented in the manuscript.
- [`B4-calculate-nevi-zip`](https://github.com/jstingone/nvi/blob/main/code%20and%20instructions/B5-calculate-nevi-zip.md): Calculate zip code-level NEVI from Census tract-level NEVI using residential ratios.

## 7. Cloning this Repository with RStudio
Below are steps to clone this repository to your local device with RStudio. Please refer to this [link](https://resources.github.com/github-and-rstudio/) for more information about using git in RStudio.

1. On top this page, click on `Code` and copy the link to this git repository (starts with https://github.com/...).
2. Open RStudio.
3. In RStudio, click on `File` &rarr; `New Project...` &rarr; `Version Control` &rarr; `Git`.
4. Under "Repository URL", paste the link of the git repository.
5. Under "Project directory name", name your project directory.
6. Under "Create project as subdirectory of:", select the folder in which you would like your project directory to be located.
7. Click on `Create Project` when you are done to clone your repository! This should take a minute or two to complete.

## 8. Grant Information
The creation of this index was conducted under contract to the Health Effects Institute (HEI), an organization jointly funded by the United States Environmental Protection Agency (EPA) (Assistance Award No. CR-83998101) and certain motor vehicle and engine manufacturers (#4985-RFA20-1B/21-8). The contents of this repository do not necessarily reflect the views of HEI, or its sponsors, nor do they necessarily reflect the views and policies of the EPA or motor vehicle and engine manufacturers. Additional funding was received from the Robert Wood Johnson Foundation (Amos Medical Faculty Development Award) and National Institutes of Health National Institute of Environmental Health Sciences (T32ES007322, R00ES027022, P30ES023515, and R01ES030717), National Institute of Diabetes and Digestive and Kidney Diseases (P30DK111022), and National Heart, Lung, and Blood Institute (K01HL140216).
