---
title: Migration Guide - Messenger
originalLink: https://documentation.spryker.com/v6/docs/migration-guide-messenger
redirect_from:
  - /v6/docs/migration-guide-messenger
  - /v6/docs/en/migration-guide-messenger
---

{% info_block errorBox %}

This migration guide is a part of the [Silex migration effort](https://documentation.spryker.com/docs/silex-replacement).

{% endinfo_block %}

To upgrade the module, do the following:

1. Update the module using composer:
```bash
composer update spryker/messenger
```

2. Remove old service providers, if you have them in the project:
```php
\Spryker\Yves\Messenger\Plugin\Provider\FlashMessengerServiceProvider
\Spryker\Zed\Messenger\Communication\Plugin\ServiceProvider\MessengerServiceProviderx
```
3. Add  new plugins to  dependency providers:

**Zed Integration**

```php
<?php
 
namespace Pyz\Zed\Application;
 
use Spryker\Zed\Application\ApplicationDependencyProvider as SprykerApplicationDependencyProvider;
use Spryker\Zed\Messenger\Communication\Plugin\Application\MessengerApplicationPlugin;
 
class ApplicationDependencyProvider extends SprykerApplicationDependencyProvider
{
    ...
 
    /**
     * @return \Spryker\Shared\ApplicationExtension\Dependency\Plugin\ApplicationPluginInterface[]
     */
    protected function getApplicationPlugins(): array
    {
        return [
            ...
            new MessengerApplicationPlugin(),
            ...
        ];
    }
 
    ...
}
```

**Yves Integration**

```php
<?php
 
namespace Pyz\Yves\ShopApplication;
 
use Spryker\Yves\ShopApplication\ShopApplicationDependencyProvider as SprykerShopApplicationDependencyProvider;
use Spryker\Yves\Messenger\Plugin\Application\MessengerApplicationPlugin;
 
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
            new MessengerApplicationPlugin(),
            ...
        ];
    }
 
    ...
}
```
