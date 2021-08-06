---
title: File details- category_store.csv
originalLink: https://documentation.spryker.com/2021080/docs/file-details-category-storecsv
redirect_from:
  - /2021080/docs/file-details-category-storecsv
  - /2021080/docs/en/file-details-category-storecsv
---

This document describes the `category_store.csv`file to configure assignments of categories in your Spryker shop.

To import the file, run:
```bash
data:import category-store
```

## Import file parameters
The file should have the following parameters:

| PARAMETER | REQURIED | TYPE | DEFAULT VALUE | REQUIREMENTS OR COMMENTS | DESCRIPTION |
|-|-|-|-|-|-|
| category_key | &check; | String |   |   | Category key of the category. |
| included_store_names |   | String |   | To accept all stores, use the asterisk (*) symbol. | Holds store names to include separated by a comma. |
| excluded_store_names |   | String |   | To remove all stores, use the asterisk (*) symbol. | Holds store names to exclude separated by a comma. |

## Import file dependencies

The file has the following dependencies:

*stores.php* configuration file of the Demo Shop PHP project.

## Import template file and content example

Find the template and an example of the file below:

| FILE | DESCRIPTION |
|-|-|
| [template_category_store.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Commerce+Setup/template+category_store.csv) | Exemplary import file with headers only. |
| [category_store.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Commerce+Setup/category_store.csv) | Exemplary import file with Demo Shop data |

