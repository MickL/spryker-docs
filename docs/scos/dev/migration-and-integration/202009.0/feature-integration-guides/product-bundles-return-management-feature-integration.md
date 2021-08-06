---
title: Product bundles + return management feature integration
originalLink: https://documentation.spryker.com/v6/docs/product-bundles-return-management-feature-integration
redirect_from:
  - /v6/docs/product-bundles-return-management-feature-integration
  - /v6/docs/en/product-bundles-return-management-feature-integration
---

## Install Feature Core

### Prerequisites
To start feature integration, overview and install the necessary features:

| Name | Version |
| --- | --- |
| Product Bundles | 202009.0 |
| Return Management | 202009.0 |
| Spryker Core | 202009.0 |

### 1) Set up Behavior
| Plugin | Specification | Prerequisites | Namespace |
| --- | --- | --- | --- |
| `ProductBundleReturnCreateFormHandlerPlugin` | Expands `ReturnCreateForm` data with product bundles subforms. Handles form submit. | None | `Spryker\Zed\ProductBundle\Communication\Plugin\SalesReturnGui` |

**src/Pyz/Zed/SalesReturnGui/SalesReturnGuiDependencyProvider.php**
```php
<?php

namespace Pyz\Zed\SalesReturnGui;

use Spryker\Zed\ProductBundle\Communication\Plugin\SalesReturnGui\ProductBundleReturnCreateFormHandlerPlugin;
use Spryker\Zed\SalesReturnGui\SalesReturnGuiDependencyProvider as SprykerSalesReturnGuiDependencyProvider;

class SalesReturnGuiDependencyProvider extends SprykerSalesReturnGuiDependencyProvider
{
    /**
     * @return \Spryker\Zed\SalesReturnGuiExtension\Dependency\Plugin\ReturnCreateFormHandlerPluginInterface[]
     */
    protected function getReturnCreateFormHandlerPlugins(): array
    {
        return [
            new ProductBundleReturnCreateFormHandlerPlugin(),
        ];
    }
}
```

{% info_block warningBox "Verification" %}

Make sure that on return creation page in the Back Office UI, you are able to create returns for orders which have product bundles.

{% endinfo_block %}

