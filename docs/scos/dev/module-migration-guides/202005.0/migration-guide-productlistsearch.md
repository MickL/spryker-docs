---
title: Migration Guide - ProductListSearch
description: Use the guide to learn how to update the ProductListSearch module to a newer version.
last_updated: Apr 3, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/mg-product-list-search
originalArticleId: aececb0d-69c7-419f-a6e6-b5a05ee58c23
redirect_from:
  - /v5/docs/mg-product-list-search
  - /v5/docs/en/mg-product-list-search
---

## Upgrading from Version 1.* to Version 2.*

The main goal of `ProductListSearch` 2.x.x is to add support of Concrete Products search introduced in `ProductPageSearch` 3.x.x.
To complete the migration, follow the steps below:

1. Update `spryker/product-page-search` ^3.2.0
2. Follow the steps from Migration guide - ProductPageSearch.
3. Update `spryker/product-list-search` to ^2.0.0
4. Generate transfers:
`vendor/bin/console transfer:generate`
5. Enable plugins in `\Pyz\Zed\ProductPageSearch\ProductPageSearchDependencyProvider`.

```php
<?php
/**
 * @return \Spryker\Zed\ProductPageSearchExtension\Dependency\Plugin\ProductConcretePageMapExpanderPluginInterface[]
 */
protected function getConcreteProductPageMapExpanderPlugins(): array
{
	return [
		new ProductConcreteProductListPageMapExpanderPlugin(),
	];
}
 
/**
 * @return \Spryker\Zed\ProductPageSearchExtension\Dependency\Plugin\ProductConcretePageDataExpanderPluginInterface[]
 */
protected function getProductConcretePageDataExpanderPlugins(): array
{
	return [
		new ProductConcreteProductListPageDataExpanderPlugin(),
	];
}
```

_Estimated migration time: ~1h_

<!-- Last review date: Mar 13, 2019 by Stanislav Matveyev, Oksana Karasyova -->
