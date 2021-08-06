---
title: Company account- module relations
originalLink: https://documentation.spryker.com/2021080/docs/company-account-module-relations
redirect_from:
  - /2021080/docs/company-account-module-relations
  - /2021080/docs/en/company-account-module-relations
---

The schema below illustrates relations between company, business unit, company unit address and company user (customer).

![schema_1.png](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Company+Account+Management/Company+Account/Company+Account:+Module+Relations/schema_1.png){height="" width=""}


The schema below illustrates relations between modules in of the business on behalf functionality:

![business-on-behalf-module-relations.png](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Company+Account+Management/Business+on+Behalf/Business+on+Behalf+Feature+Overview/business-on-behalf-module-relations.png){height="" width=""}

`BusinessOnBehalfGui` module provides plugin `BusinessOnBehalfGuiAttachToCompanyButtonCustomerTableActionExpanderPlugin` for Customer module, and `CompanyUserTableAttachToBusinessUnitActionLinksExpanderPlugin` as well as `ReplaceDeleteButtonCompanyUserTableActionLinksExpanderPlugin` plugins for `CompanyUserG` module. Also, `BusinessOnBehalfGui` takes user information from `CompanyUser` module.
