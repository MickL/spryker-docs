---
title: Migration Guide - ProductRelation
description: Use the guide to learn how to update the ProductRelation module to a newer version.
last_updated: Sep 15, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/migration-guide-productrelation
originalArticleId: 003dc269-ed64-4e9f-a49f-2061c36a54f0
redirect_from:
  - /v5/docs/migration-guide-productrelation
  - /v5/docs/en/migration-guide-productrelation
---

## Upgrading from Version 1.* to Version 2.*
In version 2 we have added multi-currency support. First of all, make sure that you [migrated the Price module](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-price.html). We have changed Zed table to use `PriceProductFacade` for retrieving product prices. We have also changed `\Spryker\Client\ProductRelation\Storage\ProductRelationStorage` to resolve ProductRelation prices based on the selected currency, price mode combination. If you modified this class in project or extended it, you may want adapt to core version.



## Upgrading from version 2.* to 3.0.0

From version 2.* we have added the possibility to assign product relations to stores.

**To upgrade to the new version of the module, do the following:**
    
1. Upgrade the ProductRelation module to the new version:
```bash
composer require spryker/product-relation:"^3.0.0" --update-with-dependencies
```

2. Prepare a database entity schema for each store in the system:
```bash
APPLICATION_STORE=DE console propel:schema:copy
APPLICATION_STORE=US console propel:schema:copy
...
```


3. Run the database migration:
```bash
console propel:install
console transfer:generate
```

*Estimated migration time: 30 minutes.*


<!-- **See also:**
* [Learn more about Products in multi-store environment](https://documentation.spryker.com/v5/docs/en/product-store-relation-under-the-hood) -->

<!-- Last review date: Nov 23, 2017 by Aurimas Ličkus -->
