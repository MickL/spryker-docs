---
title: Glue API- Product Bundles feature integration
originalLink: https://documentation.spryker.com/2021080/docs/glue-api-product-bundles-feature-integration
redirect_from:
  - /2021080/docs/glue-api-product-bundles-feature-integration
  - /2021080/docs/en/glue-api-product-bundles-feature-integration
---

Follow the steps below to integrate the Glue API: Product Bundles feature.

## Prerequisites

To start the feature integration, overview and install the necessary features:


| Name | Version | Integration guide |
| --- | --- | --- |
| Spryker Core | master | [Glue API: Spryker Core feature integration](https://documentation.spryker.com/docs/glue-api-spryker-core-feature-integration) |
| Product Bundles| master| [Product Bundles feature integration](https://documentation.spryker.com/upcoming-release/docs/product-bundles-feature-integration)|
| Order Management| master| [Glue API: Order Management feature integration](https://documentation.spryker.com/docs/glue-api-order-management-feature-integration)|

## 1) Install the required modules using Composer

Run the following command to install the required modules:
```bash
composer require spryker/product-bundles-rest-api:"^1.0.0" --update-with-dependencies
```
{% info_block warningBox "Verification" %}

 Make sure that the following module has been installed:

| Module |  Expected Directory  |
| --- | --- |
| ProductBundlesRestApi | vendor/spryker/product-bundles-rest-api |
 
 

{% endinfo_block %}  

## 2) Set up transfer objects
Set up transfer objects:
```bash
console transfer:generate
``` 
{% info_block warningBox "Verification" %}

Make sure that the following changes have been applied in the transfer objects:

| Transfer | Type | Event | Path |
| --- | --- | --- | --- |
| RestBundledProductsAttributesTransfer | class | created | src/Generated/Shared/Transfer/RestBundledProductsAttributesTransfer |
| RestErrorMessageTransfer| class |created |src/Generated/Shared/Transfer/RestErrorMessageTransfer|
| ProductBundleStorageTransfer| class| created| src/Generated/Shared/Transfer/ProductBundleStorageTransfer|
| ProductForProductBundleStorageTransfer| class| created |src/Generated/Shared/Transfer/ProductForProductBundleStorageTransfer|
| OrderTransfer| class |created |src/Generated/Shared/Transfer/OrderTransfer|
| ItemTransfer| class| created| src/Generated/Shared/Transfer/ItemTransfer|
| RestOrderDetailsAttributesTransfer| class| created |src/Generated/Shared/Transfer/RestOrderDetailsAttributesTransfer|
| RestOrderItemsAttributesTransfer| class| created| src/Generated/Shared/Transfer/RestOrderItemsAttributesTransfer|
| RestOrderItemMetadataTransfer| class |created| src/Generated/Shared/Transfer/RestOrderItemMetadataTransfer|
| ProductBundleStorageCriteriaTransfer |class |created |src/Generated/Shared/Transfer/ProductBundleStorageCriteriaTransfer|

{% endinfo_block %}
## 3) Set up behavior

Activate the following plugins:

| Plugin | Specification | Prerequisites | Namespace |
| --- | --- | --- | --- |
| BundledProductByProductConcreteSkuResourceRelationshipPlugin | Adds the `bundled-products` resource as a relationship to the `concrete-products` resource by product concrete `sku`. | None | Spryker\Glue\ProductBundlesRestApi\Plugin\GlueApplication |
|ConcreteProductsBundledProductsResourceRoutePlugin| Provides the `bundled-products` resource route with `concrete-products` as a parent resource. |None |Spryker\Glue\ProductBundlesRestApi\Plugin\GlueApplication|
| BundleItemRestOrderDetailsAttributesMapperPlugin |Maps the additional information from`OrderTransfer` to `RestOrderDetailsAttributesTransfer`. |None |Spryker\Glue\ProductBundlesRestApi\Plugin\OrdersRestApi|



 <details open>
    <summary>src/Pyz/Glue/GlueApplication/GlueApplicationDependencyProvider.php</summary>

```php
<?php

namespace Pyz\Glue\GlueApplication;

use Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRelationshipCollectionInterface;
use Spryker\Glue\ProductBundlesRestApi\Plugin\GlueApplication\BundledProductByProductConcreteSkuResourceRelationshipPlugin;
use Spryker\Glue\ProductBundlesRestApi\Plugin\GlueApplication\ConcreteProductsBundledProductsResourceRoutePlugin;
use Spryker\Glue\GlueApplication\GlueApplicationDependencyProvider as SprykerGlueApplicationDependencyProvider;
use Spryker\Glue\ProductBundlesRestApi\ProductBundlesRestApiConfig;
use Spryker\Glue\ProductsRestApi\Plugin\GlueApplication\ConcreteProductBySkuResourceRelationshipPlugin;
use Spryker\Glue\ProductsRestApi\ProductsRestApiConfig;

class GlueApplicationDependencyProvider extends SprykerGlueApplicationDependencyProvider
{
    /**
     * @return \Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRoutePluginInterface[]
     */
    protected function getResourceRoutePlugins(): array
    {
        return [
            new ConcreteProductsBundledProductsResourceRoutePlugin(),
        ];
    }

    /**
     * @param \Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRelationshipCollectionInterface $resourceRelationshipCollection
     *
     * @return \Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRelationshipCollectionInterface
     */
    protected function getResourceRelationshipPlugins(
        ResourceRelationshipCollectionInterface $resourceRelationshipCollection
    ): ResourceRelationshipCollectionInterface {
        $resourceRelationshipCollection->addRelationship(
            ProductBundlesRestApiConfig::RESOURCE_BUNDLED_PRODUCTS,
            new ConcreteProductBySkuResourceRelationshipPlugin()
        );
        $resourceRelationshipCollection->addRelationship(
            ProductsRestApiConfig::RESOURCE_CONCRETE_PRODUCTS,
            new BundledProductByProductConcreteSkuResourceRelationshipPlugin()
        );

        return $resourceRelationshipCollection;
    }
}
```

</details>

{% info_block warningBox "Verification" %}

Ensure that you have activated the plugins:

| Request | Test |
| --- | --- |
| `GET https://glue.mysprykershop.com/bundled-products` | Returns the list of bundled products. |
| `GET https://glue.mysprykershop.com/concrete-products/{% raw %}{{{% endraw %}sku{% raw %}}}{% endraw %}/bundled-products?include=concrete-products` |In the response body, the `bundled-products` resource has a relationship to the `concrete-products` resource.|
|`GET https://glue.mysprykershop.com/concrete-products/{% raw %}{{{% endraw %}sku{% raw %}}}{% endraw %}?include=bundled-products`  |In the response body, the `concrete-products` resource has a relationship to its `bundled-products` resource.|

{% endinfo_block %}

**src/Pyz/Glue/OrdersRestApi/OrdersRestApiDependencyProvider.php**
```php
<?php

namespace Pyz\Glue\OrdersRestApi;

use Spryker\Glue\ProductBundlesRestApi\Plugin\OrdersRestApi\BundleItemRestOrderDetailsAttributesMapperPlugin;
use Spryker\Glue\AuthRestApi\AuthRestApiDependencyProvider as SprykerAuthRestApiDependencyProvider;

class OrdersRestApiDependencyProvider extends SprykerOrdersRestApiDependencyProvider
{
    /**
     * @return \Spryker\Glue\OrdersRestApiExtension\Dependency\Plugin\RestOrderDetailsAttributesMapperPluginInterface[]
     */
    protected function getRestOrderDetailsAttributesMapperPlugins(): array
    {
        return [
            new BundleItemRestOrderDetailsAttributesMapperPlugin(),
        ];
    }
}
```

{% info_block warningBox "Verification" %}

Ensure that you have activated the plugins:

1.  Place an order with product bundles.
    
2.  Send the request: `GET https://glue.mysprykershop.com/orders/{% raw %}{{{% endraw %}orderReference{% raw %}}}{% endraw %}`.
    
3.  Check that, in the response:
    
    *   There is a `data.attributes.bundleItems` section.
        
    *   The `data.attributes.items.relatedBundleItemIdentifier` attribute value of a bundled item is the same as the `data.attributes.bundleItems.bundleItemIdentifier` attribute value of the product bundle item it belongs to.


{% endinfo_block %}
        

## Related features

  
Integrate the following related features:

| Feature | Required for the current feature | Integration guide |
| --- | --- | --- |
| Products  | ✓ | [Glue API: Products feature integration - ongoing](https://documentation.spryker.com/upcoming-release/docs/glue-api-products-feature-integration) |



