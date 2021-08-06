---
title: File details- shipment.csv
originalLink: https://documentation.spryker.com/2021080/docs/file-details-shipmentcsv
redirect_from:
  - /2021080/docs/file-details-shipmentcsv
  - /2021080/docs/en/file-details-shipmentcsv
---

This article contains content of the **shipment.csv** file to configure [shipment](https://documentation.spryker.com/docs/shipment) information in your Spryker Demo Shop.

To import the file, run

```Bash
data:import:shipment
```

## Import file parameters 
The file should have the following parameters:

| Field Name | Mandatory | Type | Other Requirements/Comments | Description |
| --- | --- | --- | --- | --- |
| shipment_method_key| &check; | String | | Identifier of the shipment method. |
| name|  &check; | String | | Name of the shipment method. |
| carrier |  &check; | String |  | Name of the shipment carrier. |
| taxSetName |  &check; | String | | 	Name of the tax set. |
| avalara_tax_code |  | String | | [Avalara tax code](https://documentation.spryker.com/2021080/docs/tax-feature-overview#avalara-system-for-automated-tax-compliance) for automated tax calculation. |

## Dependencies
This file has no dependencies.

## Import template file and content example

Find the template and an example of the file below:

| FILE | DESCRIPTION |
| --- | --- |
| [template_shipment.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Commerce+Setup/202109.0/Template+shipment.csv) | Import file template with headers only. |
| [shipment.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Commerce+Setup/202109.0/shipment.csv) | Exemplary import file with the Demo Shop data. |
