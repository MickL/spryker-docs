---
title: Migration guide - SalesMerchantConnector
description: This guide contains instructions on migrating the deprecated SalesMerchantConnector to SalesOms modules provided by Spryker.
last_updated: Jan 28, 2021
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v6/docs/migration-guide-salesmerchantconnector
originalArticleId: 7d3cd59e-7b03-42fb-ba64-f614a631709b
redirect_from:
  - /v6/docs/migration-guide-salesmerchantconnector
  - /v6/docs/en/migration-guide-salesmerchantconnector
---

`SalesMerchantConnector` is deprecated. For a plugin expanding order items with the parameters, use the SalesOms module.

{% info_block infoBox "Info" %}

Keep in mind, if you use functionality from `SalesMerchantConnector`, you need to install `SalesOms` and `MerchantSalesOrder` modules.

{% endinfo_block %}

**To replace the deprecated functionality, do the following:**

1. Install the `SalesOms`, `MerchantSalesOrder` modules by running the following command:
```bash
composer require spryker/sales-oms spryker/merchant-sales-order
```
2. Update the transfer objects:
```bash
console transfer:generate
```
3. Generate translator cache by running the following command to get the latest Zed translations:
```bash
console propel:install
```
4. Update the transfer objects:
```bash
console transfer:generate
```
5. Replace the deprecated plugin from the `SalesMerchantConnector` and add the new one from `MerchantSalesOrder` modules in `src/Pyz/Zed/Sales/SalesDependencyProvider.php`.
6. Change namespace from:
```php
use Spryker\Zed\SalesMerchantConnector\Communication\Plugin\OrderItemReferenceExpanderPreSavePlugin;
```
to:
```bash
use Spryker\Zed\SalesOms\Communication\Plugin\OrderItemReferenceExpanderPreSavePlugin;
```
7. Add `MerchantReferencesOrderExpanderPlugin` to `src/Pyz/Zed/Sales/SalesDependencyProvider.php`.
```php
namespace Pyz\Zed\Sales;

use Spryker\Zed\Sales\SalesDependencyProvider as SprykerSalesDependencyProvider;
use Spryker\Zed\MerchantSalesOrder\Communication\Plugin\Sales\MerchantReferencesOrderExpanderPlugin;

class SalesDependencyProvider extends SprykerSalesDependencyProvider
{
  /**
    * @return \Spryker\Zed\SalesExtension\Dependency\Plugin\OrderExpanderPluginInterface[]
    */
  protected function getOrderHydrationPlugins(): array
  {
      return [
          new MerchantReferencesOrderExpanderPlugin(),
      ];
  }
}
```

*Estimated migration time: 1 hour.*
