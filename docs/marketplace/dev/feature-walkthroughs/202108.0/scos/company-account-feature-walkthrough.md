---
title: Company Account feature walkthrough
last_updated: Aug 13, 2021
description: The Company Account feature allows controlling user access to the system within an organization by configuring different permissions and roles for the company's entities (units) and users.
template: concept-topic-template
---

The _Company Account_ feature allows controlling user access to the system within an organization by configuring different permissions and roles for the company's entities (units) and users.

<!--
To learn more about the feature and to find out how end users use it, see [ feature overview]() for business users.
-->

## Entity diagram

The following schema illustrates relations between a company, business unit, company unit address and customer.

<div class="width-100">

![schema_1.png](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Company+Account+Management/Company+Account/Company+Account:+Module+Relations/schema_1.png)

</div>

The following schema illustrates relations between modules in of the business on behalf functionality:

<div class="width-100">

![business-on-behalf-module-relations.png](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Company+Account+Management/Business+on+Behalf/Business+on+Behalf+Feature+Overview/business-on-behalf-module-relations.png)

</div>

The BusinessOnBehalfGui` module provides the `BusinessOnBehalfGuiAttachToCompanyButtonCustomerTableActionExpanderPlugin` plugin for the `Customer` module, and `CompanyUserTableAttachToBusinessUnitActionLinksExpanderPlugin` as well as `ReplaceDeleteButtonCompanyUserTableActionLinksExpanderPlugin` plugins for the `CompanyUserG` module. Also, `BusinessOnBehalfGui` takes user information from the `CompanyUser` module.

## Related Developer articles

|INTEGRATION GUIDES  | MIGRATION GUIDES | GLUE API GUIDES  | DATA IMPORT | TUTORIALS AND HOWTOS |
|---------|---------|---------|---------|---------|
| Company Account feature integration  | CompanyUser migration guide  | Retrieving companies  |   | HowTo - Generate a Token for Login  |
| Glue API: Company Account feature integration | BusinessOnBehalfDataImport migration guide  | Retrieving business units  |   |   |
|   |   | Retrieving business unit addresses |   |   |
|   |   | Retrieving company users  |   |   |
|   |   | Retrieving company roles  |   |   |
|   |   | Authenticating as a company user  |   |   |
|   |   | Managing company user authentication tokens  |   |   |
|   |   |   |   |   |
