# IMQF Master’s Thesis — Spanish Portfolio Dataset

This repository provides a downloadable snapshot of the dataset used for my master’s thesis in the International Master in Quantitative Finance programme at the University of Belgrade.

**Student:** Dea Peni Larasati

## Download the dataset

The dataset is available as **spanish_portfolio.csv** in this repository.

Open the file and select **Download raw file** to download it. No BigQuery account or access to my Google Cloud project is required.

## Dataset source and attribution

This thesis uses secondary data published by Priscila Espinosa, Josep Lledó, and David Atance.

**Dataset citation:**

Espinosa, P., Lledó, J., & Atance, D. (2026). *A detailed dataset of motor insurance policies with coverage-specific financial information* [Dataset]. Mendeley Data, Version 1. https://doi.org/10.17632/sw4jmdb2sm.1

**Related article:** [Read the accompanying article in Data in Brief](https://www.sciencedirect.com/science/article/pii/S235234092600435X).

### Original dataset

The source contains anonymised motor insurance records covering January 2022–December 2024, with 354,140 records and 47 variables. These figures describe the original dataset, rather than a separately verified count of this repository’s working copy.

[Download the original dataset from Mendeley Data](https://data.mendeley.com/datasets/sw4jmdb2sm/1).

### Licence

The source dataset is distributed under the [Creative Commons Attribution 4.0 International licence](https://creativecommons.org/licenses/by/4.0/).

Credit for the original dataset belongs to its authors. My contribution concerns the preparation and analysis undertaken for my master’s thesis; the original authors do not endorse this work.

### Changes to the source data

[Before uploading, describe any format conversion, column renaming, filtering, cleaning, or additional variables. If no changes were made, state this explicitly.]


## BigQuery working table

The working copy is maintained in:

`personal-imqf.thesis_imqf.spanish_portfolio`
https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1spersonal-imqf!2sthesis_imqf!3sspanish_portfolio

The CSV is a static export and does not automatically update when the BigQuery table changes.
