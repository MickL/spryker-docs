---
title: File details- cms_slot.csv
last_updated: Aug 27, 2020
template: data-import-template
originalLink: https://documentation.spryker.com/v6/docs/file-details-cms-slotcsv
originalArticleId: 0c358180-23d7-418d-b229-d2d62d303c7c
redirect_from:
  - /v6/docs/file-details-cms-slotcsv
  - /v6/docs/en/file-details-cms-slotcsv
---

This article contains content of the **cms_slot.csv** file to configure [CMS Slot](https://documentation.spryker.com/v6/docs/templates-and-slots-overview) information on your Spryker Demo Shop.

## Headers & Mandatory Fields 
These are the header fields to be included in the .csv file:

| Field Name | Mandatory | Type | Other Requirements/Comments | Description |
| --- | --- | --- | --- | --- |
| **template_path** | Yes | String |Must be a valid path to a twig template. | Path to the Twig file template. |
| **slot_key** | Yes (*unique*) | String |N/A | Identifier of the slot that is used by slot widget when rendering the content of this slot |
| **content_provider** | Yes | String |Must be a valid type of content provider. | Defines the source of content of this slot. |
| **name** | Yes | String |N/A | Alphabetical identifier of the slot. It will be shown in the Back Office. |
| **description** | Yes | String |N/A | Description of the slot. It will be shown in the Back Office. |
| **is_active** | No | Boolean |<ul><li>Inactive = 0</li><li>Active = 1</li><li>If empty during the import, the slots will be imported as inactive.</li> | Indicates if the slot is active or inactive.<br>If the slot is inactive, it is not rendered in the Storefront by the slot widget. |

*N/A: Not applicable.

## Dependencies

This file has no dependencies.

## Template File & Content Example
A template and an example of the *cms_slot.csv*  file can be downloaded here:

| File | Description |
| --- | --- |
| [cms_slot.csv template](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Content+Management/Template+cms_slot.csv) | CMS Slot .csv template file (empty content, contains headers only). |
| [cms_slot.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Content+Management/cms_slot.csv) | CMS Slot file containing a Demo Shop data sample. |
