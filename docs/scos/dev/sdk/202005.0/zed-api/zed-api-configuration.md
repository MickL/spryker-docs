---
title: Zed API Configuration
description: The article describes how you can configure API for Zed.
last_updated: Apr 3, 2020
template: concept-topic-template
originalLink: https://documentation.spryker.com/v5/docs/zed-api-config
originalArticleId: 3ab7826c-b6b8-4bb9-95dd-ff75f24d110b
redirect_from:
  - /v5/docs/zed-api-config
  - /v5/docs/en/zed-api-config
---

First of all we need to decide on the resources being exposed. Those will be mapped inside the `ApiDependencyProvider`:

```php
<?php
use Spryker\Zed\CustomerApi\Communication\Plugin\Api\CustomerApiResourcePlugin;
use Spryker\Zed\ProductApi\Communication\Plugin\Api\ProductApiResourcePlugin;

    /**
     * @return \Spryker\Zed\Api\Dependency\Plugin\ApiResourcePluginInterface[]
     */
    protected function getApiResourcePluginCollection()
    {
        return [
            new CustomerApiResourcePlugin(),
            new ProductApiResourcePlugin(),
            ...
        ];
    }

```

Each resource plugin contains a `getResourceName()` which will map to the resource name of the URL. Those can also be versioned or customized if necessary.

Example: If you create a `CustomerApiResourcePlugin` containing `customer-groups` as a resource name, the API resource URL is then API prefix (/api/rest/) + resource name, in this case `/api/rest/customer-groups`.
