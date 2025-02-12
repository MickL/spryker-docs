---
title: Shop Guide - Company Account
description: Use the procedures to create and manage a company from the company account in the storefront.
last_updated: Nov 22, 2019
template: howto-guide-template
originalLink: https://documentation.spryker.com/v4/docs/company-account-shop-guide
originalArticleId: 1cb30a5a-b0b2-40af-85a7-61e3035d6910
redirect_from:
  - /v4/docs/company-account-shop-guide
  - /v4/docs/en/company-account-shop-guide
---



Company Account Overview page allows your shop owner to manage the company in the shop application.

To open the Company Account page, go to the header of the shop application → Name of your company → Overview.

![Company account header](https://spryker.s3.eu-central-1.amazonaws.com/docs/User+Guides/Shop+User+Guides/Company+Account/company-account-header.png)


## Graphic User Interface

![Company Account GUI](https://spryker.s3.eu-central-1.amazonaws.com/docs/User+Guides/Shop+User+Guides/Company+Account/company-account-gui.png)

The *Company Overview* page consists of the following elements:

| # | Element | Description |
|---|---|---|
|  **1** |  **Company Account menu** | Use this menu to manage your Company: Overview, Users, Business Units, Roles. |
|  **2** |  **Company Name** | Displays the name of the company. |
|  **3** |  **Company Address** | Displays the address your company has. |

## Creating a New Company

To create a Company in the web-shop, go to `/company/register` and register a company.

![Register a company](https://spryker.s3.eu-central-1.amazonaws.com/docs/User+Guides/Shop+User+Guides/Company+Account/register-company.png)

Fill in the required (*) fields to complete the registration.

After the company has been registered, it should be approved in the [Back Office](/docs/scos/user/back-office-user-guides/{{page.version}}/customer/company-account/managing-companies.html#approving-and-activating-a-company) to continue building the hierarchy.

Once the company is approved, a Company Administrator can go to `/company/overview` page and create (and then also edit and delete) users, addresses, roles and business roles.

{% info_block infoBox %}
A Company Administrator needs to log out and then log in to refresh the changes.
{% endinfo_block %}
Don't forget to check out the video tutorial on setting up [Company](/docs/scos/user/features/{{page.version}}/company-account-feature-overview/company-accounts-overview.html) Structure in Spryker [B2B Demo Shop](/docs/scos/user/about-spryker/{{page.version}}/about-spryker.html#spryker-b2b-b2c-demo-shops):

{% wistia qkdgkeannb 960 720 %}