---
title: Migration Guide - Product Relation
originalLink: https://documentation.spryker.com/v1/docs/mg-product-relation
redirect_from:
  - /v1/docs/mg-product-relation
  - /v1/docs/en/mg-product-relation
---

## Upgrading from Version 1.* to Version 2.*
In version 2 we have added multi-currency support. First of all, make sure that you [migrated the Price module](/docs/scos/dev/migration-and-integration/201811.0/module-migration-guides/migration-guide-price.html). We have changed Zed table to use `PriceProductFacade` for retrieving product prices. We have also changed `\Spryker\Client\ProductRelation\Storage\ProductRelationStorage` to resolve ProductRelation prices based on the selected currency, price mode combination. If you modified this class in project or extended it, you may want adapt to core version.

<!-- **See also:**
* [Learn more about Products in multi-store environment](https://documentation.spryker.com/v1/docs/product-store-relation-under-the-hood) -->

<!-- Last review date: Nov 23, 2017 by Aurimas Ličkus -->
