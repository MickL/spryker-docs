---
title: File details- warehouse.csv
originalLink: https://documentation.spryker.com/2021080/docs/file-details-warehousecsv
redirect_from:
  - /2021080/docs/file-details-warehousecsv
  - /2021080/docs/en/file-details-warehousecsv
---

This article contains content of the **warehouse.csv** file to configure [Warehouse](https://documentation.spryker.com/docs/inventory-management) information on your Spryker Demo Shop.

## Headers & Mandatory Fields 
These are the header fields to be included in the .csv file:

| Field Name | Mandatory | Type | Other Requirements/Comments | Description |
| --- | --- | --- | --- | --- |
| **name** | Yes | String | N/A*| Name of the warehouse. |
| **is_active** | No | Boolean | <ul><li>True = 1</li><li>False = 0</li>If empty, it will be assumed 0 (false)</li></ul>|Status of the warehouse, specified in a boolean value: 1 (true) or 0 (false), where 1 indicates that the warehouse is available and 0 indicates that the warehouse is unavailable. By default, the warehouse is not active.|
*N/A: Not applicable.

## Dependencies
This file has no dependencies.

## Recommendations & Other Information
Check the [HowTo - Import Warehouse Data](https://documentation.spryker.com/docs/ht-import-warehouse-data).
{% info_block infoBox "Note" %}

The *warehouse.csv* file replaces *stock.csv* previously used. 

{% endinfo_block %}
By default, *warehouse.csv* exists only in folder `…/vendor/spryker/stock-data-import/data/import/warehouse.csv`, but can be also be copied into `…/data/import` folder. 


## Template File & Content Example
A template and an example of the *warehouse.csv* file can be downloaded here:

| File | Description |
| --- | --- |
| [warehouse.csv template](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Commerce+Setup/Template+warehouse.csv) | Warehouse .csv template file (empty content, contains headers only). |
| [warehouse.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Commerce+Setup/warehouse.csv) | Warehouse .csv file containing a Demo Shop data sample. |
