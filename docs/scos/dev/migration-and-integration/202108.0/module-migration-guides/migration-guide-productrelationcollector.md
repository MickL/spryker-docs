---
title: Migration Guide - ProductRelationCollector
originalLink: https://documentation.spryker.com/2021080/docs/mg-product-relation-collector
redirect_from:
  - /2021080/docs/mg-product-relation-collector
  - /2021080/docs/en/mg-product-relation-collector
---

## Upgrading from Version 1.* to Version 2.*

From version 2 we added support for multi-currency. First of all, make sure that you [migrated the Price module](/docs/scos/dev/migration-and-integration/202001.0/module-migration-guides/migration-guide-price.html). We have changed collector dependency to use `PriceProduct` module instead of price, please update your code accordingly if you overwrote the core.

<!-- 
* [Learn more about Products in multi-store environment](https://documentation.spryker.com/v4/docs/product-store-relation-under-the-hood)-->

<!-- Last review date: Nov 23, 2017 by Aurimas Ličkus -->