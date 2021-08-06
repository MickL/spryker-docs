---
title: File details- navigation_node.csv
originalLink: https://documentation.spryker.com/v5/docs/file-details-navigation-nodecsv
redirect_from:
  - /v5/docs/file-details-navigation-nodecsv
  - /v5/docs/en/file-details-navigation-nodecsv
---

This article contains content of the **navigation_node.csv** file to configure [Navigation Node](https://documentation.spryker.com/docs/en/navigation-node-types) information on your Spryker Demo Shop.

## Headers & Mandatory Fields 
These are the header fields to be included in the .csv file:

| Field Name | Mandatory | Type | Other Requirements/Comments | Description |
| --- | --- | --- | --- | --- |
| **navigation_key** | Yes | String |N/A* | Navigation entity key identifier. |
| **node_key** | Yes (*unique*) | String |N/A | Identifies a node. |
| **parent_node_key** | Yes | String |N/A | Identifies the parent node. Defines the hierarchy of the nodes. |
| **node_type** | Yes | String |Possible values are: category, link, cms_page, external_url, label, ….)  | Type of node. |
| **title.{ANY_LOCALE_NAME}** **<br>Example value: *title.en_US* | Yes | String |N/A | Tittle of the node (US locale for our example). |
| **url.{ANY_LOCALE_NAME}** **<br>Example value: *url.en_US* | Yes | String |N/A | URL of the node (US locale for our example). |
| **css_class.{ANY_LOCALE_NAME}** **<br>Example value: *css_class.en_US* | Yes | String |N/A | Class of the node (US locale for our example). |
| **valid_from** | Yes | Date |N/A |  Date from which the navigation node is valid.|
| **valid_to** | Yes | Date |N/A |  Date to which the navigation node is valid.|
*N/A: Not applicable.
** ANY_LOCALE_NAME: Locale date is dynamic in data importers. It means that ANY_LOCALE_NAME postifx can be changed, removed, and any number of columns with different locales can be added to the .csv files.

## Dependencies

This file has the following dependencies:

* [navigation.csv](https://documentation.spryker.com/docs/en/file-details-navigationcsv)
* [glossary.csv](https://documentation.spryker.com/docs/en/file-details-glossarycsv)

## Template File & Content Example
A template and an example of the *navigation_node.csv*  file can be downloaded here:

| File | Description |
| --- | --- |
| [navigation_node.csv template](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Navigation+Setup/Template+navigation_node.csv) | Navigation Node .csv template file (empty content, contains headers only). |
| [navigation_node.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Navigation+Setup/navigation_node.csv) | Navigation Node .csv file containing a Demo Shop data sample. |

