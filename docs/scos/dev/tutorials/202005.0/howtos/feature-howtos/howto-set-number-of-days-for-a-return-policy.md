---
title: HowTo - Set Number of Days for a Return Policy
description: The article describes how to set a number of days for a Return Policy
originalLink: https://documentation.spryker.com/v5/docs/howto-set-number-of-days-for-a-return-policy
originalArticleId: ee3b765d-16b1-4108-9bfd-6545be4e91b0
redirect_from:
  - /v5/docs/howto-set-number-of-days-for-a-return-policy
  - /v5/docs/en/howto-set-number-of-days-for-a-return-policy
---

To define a period within which an item can be returned, redefine the Config in `Pyz\Zed\SalesReturn\SalesReturnConfig` by adding the following there:

`protected const GLOBAL_RETURNABLE_NUMBER_OF_DAYS = {% raw %}{{{% endraw %}Number of days{% raw %}}}{% endraw %};`

where *{% raw %}{{{% endraw %}Number of days{% raw %}}}{% endraw %}* is the time period in days after the item purchase, within which the item can be returned.

Example:
```php
namespace Pyz\Zed\SalesReturn;use Spryker\Zed\SalesReturn\SalesReturnConfig as SprykerSalesReturnConfig;class SalesReturnConfig extends SprykerSalesReturnConfig
{
    protected const GLOBAL_RETURNABLE_NUMBER_OF_DAYS = 30;
}
```

