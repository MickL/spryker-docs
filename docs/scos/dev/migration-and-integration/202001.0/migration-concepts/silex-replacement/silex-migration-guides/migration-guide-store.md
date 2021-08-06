---
title: Migration Guide - Store
originalLink: https://documentation.spryker.com/v4/docs/migration-guide-store
redirect_from:
  - /v4/docs/migration-guide-store
  - /v4/docs/en/migration-guide-store
---

{% info_block errorBox %}

This migration guide is a part of the [Silex migration effort](/docs/scos/dev/migration-and-integration/202001.0/migration-concepts/silex-replacement/silex-replacement.html).

{% endinfo_block %}

To upgrade the module, do the following:

1. Update the module using composer:
```bash
composer update spryker/store
```
2. Add new plugins to dependency providers:


```php
<?php
 
namespace Pyz\Yves\ShopApplication;
 
use Spryker\Yves\ShopApplication\ShopApplicationDependencyProvider as SprykerShopApplicationDependencyProvider;
use Spryker\Yves\Store\Plugin\Application\StoreApplicationPlugin;
 
class ShopApplicationDependencyProvider extends SprykerShopApplicationDependencyProvider
{
    ...
 
    /**
     * @return \Spryker\Shared\ApplicationExtension\Dependency\Plugin\ApplicationPluginInterface[]
     */
    protected function getApplicationPlugins(): array
    {
        return [
            ...
            new StoreApplicationPlugin(),
            ...
        ];
    }
     ...
}
```

