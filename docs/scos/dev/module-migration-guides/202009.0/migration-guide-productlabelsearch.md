---
title: Migration Guide - ProductLabelSearch
last_updated: Aug 31, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v6/docs/migration-guide-productlabelsearch
originalArticleId: e839271f-e4eb-4ddc-9024-84a7cf3b8038
redirect_from:
  - /v6/docs/migration-guide-productlabelsearch
  - /v6/docs/en/migration-guide-productlabelsearch
---

## Upgrading from Version 1.* to Version 2.*
Version 2.* of the ProductLabelSearch module changes the storage data structure to maintain relations of product labels to stores.

To upgrade to the new version of the module, do the following:
1. Upgrade the ProductLabelSearch module to the new version:
```bash
composer require spryker/product-label-search:"^2.0.0" --update-with-dependencies
```
2. Update the generated classes:
```bash
console transfer:generate
```
3. Remove the deprecated plugins from `Pyz\Zed\Event\EventDependencyProvider`
 ```php
Spryker\Zed\ProductLabelSearch\Communication\Plugin\Event\Subscriber\ProductLabelSearchEventSubscriber
```
4. Add the new plugins to `Pyz\Zed\Publisher\PublisherDependencyProvider`:
```php
<?php

namespace Pyz\Zed\Publisher;

...
use Spryker\Zed\ProductLabelSearch\Communication\Plugin\Publisher\ProductLabel\ProductLabelWritePublisherPlugin as ProductLabelSearchWritePublisherPlugin;
use Spryker\Zed\ProductLabelSearch\Communication\Plugin\Publisher\ProductLabelProductAbstract\ProductLabelProductAbstractWritePublisherPlugin as ProductLabelProductAbstractSearchWritePublisherPlugin;
use Spryker\Zed\ProductLabelSearch\Communication\Plugin\Publisher\ProductLabelStore\ProductLabelStoreWritePublisherPlugin as ProductLabelStoreSearchWritePublisherPlugin;
...
use Spryker\Zed\Publisher\PublisherDependencyProvider as SprykerPublisherDependencyProvider;

class PublisherDependencyProvider extends SprykerPublisherDependencyProvider
{
    /**
     * @return \Spryker\Zed\PublisherExtension\Dependency\Plugin\PublisherPluginInterface[]
     */
    protected function getPublisherPlugins(): array
    {
        return array_merge(
            $this->getProductLabelSearchPlugins(),
       );
    }

    /**
     * @return \Spryker\Zed\PublisherExtension\Dependency\Plugin\PublisherPluginInterface[]
     */
    protected function getProductLabelSearchPlugins(): array
    {
        return [
            new ProductLabelSearchWritePublisherPlugin(),
            new ProductLabelProductAbstractSearchWritePublisherPlugin(),
            new ProductLabelStoreSearchWritePublisherPlugin(),
        ];
    }
}
```

*Estimated migration time: 1 hour.*

## Upgrading from Version 1.2.* to Version 1.3.*

{% info_block errorBox "Prerequisites" %}

This migration guide is a part of the [Search migration effort](/docs/scos/dev/migration-concepts/search-migration-concept/search-migration-concept.html). Prior to upgarding this module, make sure you have completed all the steps from the [Search Migration Guide](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-search.html#upgrading-from-version-8-9---to-version-8-10--). 

{% endinfo_block %}
To upgrade the module, do the following:
1. Update the module with composer:
```bash
composer update spryker/product-label-search
```
2. Remove the usage of deprecated `Spryker\Zed\ProductLabelSearch\Communication\Plugin\PageMapExpander\ProductLabelMapExpanderPlugin` from `Pyz\Zed\ProductPageSearch\ProductPageSearchDependencyProvider`.
3. Enable the replacement plugin:
```php
<?php

namespace Pyz\Zed\ProductPageSearch;

...
use Spryker\Zed\ProductLabelSearch\Communication\Plugin\ProductPageSearch\Elasticsearch\ProductLabelMapExpanderPlugin;
use Spryker\Zed\ProductPageSearch\ProductPageSearchDependencyProvider as SprykerProductPageSearchDependencyProvider;

class ProductPageSearchDependencyProvider extends SprykerProductPageSearchDependencyProvider
{
    ...

    /**
     * @return \Spryker\Zed\ProductPageSearchExtension\Dependency\Plugin\ProductAbstractMapExpanderPluginInterface[]
     */
    protected function getProductAbstractMapExpanderPlugins(): array
    {
        return [
            ...
            new ProductLabelMapExpanderPlugin(),
        ];
    }
}
```
