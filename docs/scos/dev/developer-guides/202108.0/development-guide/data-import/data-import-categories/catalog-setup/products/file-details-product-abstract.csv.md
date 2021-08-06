---
title: File details- product_abstract.csv
originalLink: https://documentation.spryker.com/2021080/docs/file-details-product-abstractcsv
redirect_from:
  - /2021080/docs/file-details-product-abstractcsv
  - /2021080/docs/en/file-details-product-abstractcsv
---

This article contains content of the **product_abstract.csv** file to configure [Abstract Product](https://documentation.spryker.com/docs/product-abstraction) information on your Spryker Demo Shop.

To import the file, run

```Bash
data:import:product-abstract
```

## Import file parameters
The file should have the following parameters:

| PARAMETER | REQUIRED | TYPE | REQUIREMENTS OR COMMENTS | DESCRIPTION |
| --- | --- | --- | --- | --- |
| category_key | &check; | String | | Identifier of category key name. |
| category_product_order |  | Integer | | Order of the product presentation inside a category. |
| abstract_sku | &check;  | String | | SKU identifier of the abstract product. |
| name.{ANY_LOCALE_NAME}<br>Example value: *name.en_US* | &check; | String |Locale data is dynamic in data importers. It means that ANY_LOCALE_NAME postifx can be changed, removed, and any number of columns with different locales can be added to the .csv files. | Name of the product in the specified location (US for our example). |
| url.{ANY_LOCALE_NAME}<br>Example value: *value_1.en_US* | &check; | String | | URL page of the product image in the specified location (US for our example). |
|is_featured |  | String |If it is empty, will be “False”. <br>False = 0<br>True = 1 | Indicates if it is a featured product. |
| attribute_key_{NUMBER}<br>Example value: *attribute_key_1*<br> | &check; (if this attribute is defined) | String | | Product attribute key for the attribute. |
| value_{NUMBER}<br>Example value: *value_1*<br>|&check; (if this attribute is defined) | String | | Product value for the attribute. |
| attribute_key_{NUMBER}.{ANY_LOCALE_NAME}<br>Example value: *attribute_key_1.en_US*<br> |  | String | | Product attribute key, for the first attribute, translated in the specified locale (US for our example). |
| value_{NUMBER}.{ANY_LOCALE_NAME}<br>Example value: *value_1.en_US*<br>| | String | | Product value for the attribute, translated in the specified locale (US for our example). |
| color_code |  | String | | Product colour code. |
| description.{ANY_LOCALE_NAME}<br>Example value: *description.en_US*  |  | String | | Product description, translated in the specified locale (US for our example). |
| icecat_pdp_url |  | String | | Icecat product catalogue URL service. |
| tax_set_name |  | String | | Name of the tax set. |
| meta_title.{ANY_LOCALE_NAME}<br>Example value: *meta_title.en_US* |  | String | | Meta title of the product in the specified locale (US for our example). |
| meta_keywords.{ANY_LOCALE_NAME}<br>Example value: *meta_keywords.en_US* |  | String | | Meta keywords of the product in the specified locale (US for our example). |
| meta_description.{ANY_LOCALE_NAME}<br>Example value: *meta_description.en_US* || String | | Meta description of the product in the specified locale (US for our example). |
| icecat_license |  | String | | Icecat product catalogue licence code. |
| new_from |  | Date | | To be considered a new product from this presented date. |
| new_to |  | String | | To be considered a new product until this presented date. |
| avalara_tax_code |  | String | | [Avalara tax code](https://documentation.spryker.com/2021080/docs/tax-feature-overview#avalara-system-for-automated-tax-compliance) for automated tax calculation. |


## Dependencies

This file has the following dependencies:

* [ category.csv](https://documentation.spryker.com/docs/file-details-categorycsv)
* [glossary.csv](https://documentation.spryker.com/docs/file-details-glossarycsv)
* [tax.csv](https://documentation.spryker.com/docs/file-details-taxcsv)

## Recommendations and other information
For each attribute, where N is a number starting in 1, it is mandatory to have both fields:

* `attribute_key_N`
* `value_N`

The amount of attributes is not limited. 

## Import template file and content example
Find the template and an example of the file below:

| FILE | DESCRIPTION |
| --- | --- |
| [template_product_abstract.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Catalog+Setup/Products/202109.0/Template+product_abstract.csv) | Import file template with headers only. |
| [product_abstract.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Catalog+Setup/Products/202109.0/product_abstract.csv) | Exemplary import file with the Demo Shop data. |
