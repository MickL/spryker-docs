---
title: Quotation process + approval process feature integration
originalLink: https://documentation.spryker.com/2021080/docs/quotation-process-approval-process-feature-integration
redirect_from:
  - /2021080/docs/quotation-process-approval-process-feature-integration
  - /2021080/docs/en/quotation-process-approval-process-feature-integration
---

## Install Feature Core
### Prerequisites
To start feature integration, overview and install the necessary features:

| Name | Version |
| --- | --- |
| Quotation Process | 202009.0 |
| Approval Process | 202009.0 |

### 1) Set up Behavior
Register the following plugins:

| Plugin | Specification | Prerequisites | Namespace |
| --- | --- | --- | --- |
| `QuoteApprovalQuoteRequestQuoteCheckPlugin` | Checks if the "Request For Quote" button should be shown on the cart page or not. | None | `Spryker\Client\QuoteApproval\Plugin\QuoteRequest` |
| `QuoteRequestQuoteApprovalUnlockPreCheckPlugin` | Prevents quote unlock  by approval process when it is in quotation process. | None | `Spryker\Zed\QuoteRequest\Communication\Plugin\QuoteApproval` |

**src/Pyz/Client/QuoteRequest/QuoteRequestDependencyProvider.php**

```php
<?php
 
namespace Pyz\Client\QuoteRequest;
 
use Spryker\Client\QuoteApproval\Plugin\QuoteRequest\QuoteApprovalQuoteRequestQuoteCheckPlugin;
use Spryker\Client\QuoteRequest\QuoteRequestDependencyProvider as SprykerQuoteRequestDependencyProvider;
 
class QuoteRequestDependencyProvider extends SprykerQuoteRequestDependencyProvider
{
    /**
     * @return \Spryker\Client\QuoteRequestExtension\Dependency\Plugin\QuoteRequestQuoteCheckPluginInterface[]
     */
    protected function getQuoteRequestQuoteCheckPlugins(): array
    {
        return [
            new QuoteApprovalQuoteRequestQuoteCheckPlugin(),
        ];
    }
}
```

**src/Pyz/Client/QuoteApproval/QuoteApprovalDependencyProvider.php**

```php
<?php
 
namespace Pyz\Zed\QuoteApproval;
 
use Spryker\Zed\QuoteApproval\QuoteApprovalDependencyProvider as SprykerQuoteApprovalDependencyProvider;
use Spryker\Zed\QuoteRequest\Communication\Plugin\QuoteApproval\QuoteRequestQuoteApprovalUnlockPreCheckPlugin;
 
class QuoteApprovalDependencyProvider extends SprykerQuoteApprovalDependencyProvider
{
    /**
     * @return \Spryker\Zed\QuoteApprovalExtension\Dependency\Plugin\QuoteApprovalUnlockPreCheckPluginInterface[]
     */
    protected function getQuoteApprovalUnlockPreCheckPlugins(): array
    {
        return [
            new QuoteRequestQuoteApprovalUnlockPreCheckPlugin(),
        ];
    }
}
```

{% info_block warningBox "Verification" %}
Make sure that the **Request For Quote** button is not available on the cart page when the quote is in status "Waiting".
{% endinfo_block %}

{% info_block warningBox "Verification" %}
Make sure that when you have locked cart after quotation process and request approval for this cart, the cart should stay locked even if approver declined it.
{% endinfo_block %}