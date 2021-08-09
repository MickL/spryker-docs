---
title: B2C API React Example
originalLink: https://documentation.spryker.com/v3/docs/b2c-api-react-example
redirect_from:
  - /v3/docs/b2c-api-react-example
  - /v3/docs/en/b2c-api-react-example
---

As a part of documentation related to Spryker Glue REST API, we have also developed a B2C API React Example. It is a [React](https://reactjs.org/) single page application based on a [webpack](https://webpack.js.org/) devserver, Typescript, [Redux](https://redux.js.org/), and Material UI.

The application has been developed for four primary purposes:

1. Provide a simple yet fully functional example of Glue REST API usage.
2. Illustrate a complete B2C Spryker experience using REST endpoints, starting from selecting the necessary product all the way through to placing an order. The shop also demonstrates the use of the API resources to create such features as the product catalog, search, auto-suggestions, customer registration, cart management, displaying order details etc.
3. Allow you to try Glue REST API without any coding.
4. Provide sample REST requests that can facilitate custom touchpoint development.

{% info_block errorBox %}
The shop is provided for display purposes only and should not under any circumstances be used as a starting point for any project.
{% endinfo_block %}

## API Resources
The Demo shop has been built using and demonstrates the use of the endpoints and resources provided by the following APIs:


| API | Reference Documents |
| --- | --- |
| Search API | [Catalog Search](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/catalog-search.html)<br>[Getting Suggestions for Auto-Completion and Search](https://documentation.spryker.com/v3/docs/retrieving-suggestions-for-auto-completion-and-search) |
| Category API | [Browsing a Category Tree](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/browsing-a-category-tree.html) |
| Product API | [Retrieving Product Information](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-products/retrieving-product-information.html) |
| Product Availability API | [Retrieving Product Information](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-products/retrieving-product-information.html) |
| Product Price API | [Retrieving Product Information](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-products/retrieving-product-information.html) |
| Product Tax Sets API | [Retrieving Product Information](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-products/retrieving-product-information.html) |
| Product Image Sets API | [Retrieving Product Information](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-products/retrieving-product-information.html) |
| Product Labels API | [Accessing Product Labels](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-products/accessing-product-labels.html) |
| Login API | [Authentication and Authorization](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/authentication-and-authorization.html) |
| Customer API | [Managing Customers](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-customers.html) |
| Cart API | [Managing Carts](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-carts/managing-carts.html) |
| Checkout API | [Checking Out Purchases and Getting Checkout Data](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/checking-out-purchases-and-getting-checkout-data.html) |
| Order History API | [Retrieving Customer's Order History](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/retrieving-customers-order-history.html) |
| Wishlist API | [Managing Wishlists](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/managing-wishlists.html) |
| Store API | [Retrieving Store Configuration](/docs/scos/dev/glue-api/201907.0/glue-api-storefront-guides/retrieving-store-configuration.html) |

## Running the Example Application
The app source code can be found in the following GitHub repository: [https://github.com/spryker-shop/b2c-api-react-example](https://github.com/spryker-shop/b2c-api-react-example). You can install it inside [Spryker Development Virtual Machine](/docs/scos/dev/features/201907.0/sdk/development-virtual-machine-docker-containers-and-console.html) or on a dedicated web server.

For detailed installation steps, see [B2C API React Example Installation](/docs/scos/dev/glue-api/201907.0/b2c-api-react-example/b2c-api-react-example-installation.html).

## Peeking Requests
After installing and running the example app, you can try its functionality. Depending on how you installed it, the shop will be available at:

* [http://glue.de.b2c-demo-shop.local/react/](http://glue.de.b2c-demo-shop.local/react/) - when installed it in the VM;
* [http://react.local](http://react.local) - when installed on a separate web server.

To get a list of Glue API requests that were used to build a page:

1. Open the F12 menu of your web browser.
2. Activate the **Console** section.
3. To get details of a specific request, expand it in the console.

![glue-requests-sample.png](https://cdn.document360.io/9fafa0d5-d76f-40c5-8b02-ab9515d3e879/Images/Documentation/glue-requests-sample.png){height="" width=""}