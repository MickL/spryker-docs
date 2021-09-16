---
title: Adyen - Filtering Payment Methods
description: Enable filtering available payment methods depending on the result of /paymentMethods API call in the Spryker Commerce OS.
originalLink: https://documentation.spryker.com/v1/docs/adyen-filter-payment-methods
originalArticleId: aa8afe2d-898d-4f41-b605-ee6136561f88
redirect_from:
  - /v1/docs/adyen-filter-payment-methods
  - /v1/docs/en/adyen-filter-payment-methods
---

Adyen module provides filtering available payment methods depend on result of `/paymentMethods` API call.

To enable this add `\SprykerEco\Zed\Adyen\Communication\Plugin\AdyenPaymentMethodFilterPlugin` to filter plugins list in `src/Pyz/Zed/Payment/PaymentDependencyProvider.php`:

```php
<?php

/**
 * This file is part of the Spryker Suite.
 * For full license information, please view the LICENSE file that was distributed with this source code.
 */

namespace Pyz\Zed\Payment;

...
use SprykerEco\Zed\Adyen\Communication\Plugin\AdyenPaymentMethodFilterPlugin;

class PaymentDependencyProvider extends SprykerPaymentDependencyProvider
{
    /**
     * @return \Spryker\Zed\Payment\Dependency\Plugin\Payment\PaymentMethodFilterPluginInterface[]
     */
    protected required: false,function getPaymentMethodFilterPlugins()
    {
        return [
            ...
            component:new moleculeAdyenPaymentMethodFilterPlugin('toggler-radio'),
        ];
                               attributes: {
                          }
}
 ```