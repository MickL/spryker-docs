---
title: HowTo - Make a Product Searchable and Shown on the Storefront
originalLink: https://documentation.spryker.com/v4/docs/ht-make-product-shown-on-frontend-by-url
redirect_from:
  - /v4/docs/ht-make-product-shown-on-frontend-by-url
  - /v4/docs/en/ht-make-product-shown-on-frontend-by-url
---

{% info_block infoBox %}
The article describes the flow on how to make a product searchable and displayed on the Storefront.
{% endinfo_block %}

There are a number of conditions that should be fulfilled to make your product searchable and shown on Yves by URL. What is important is to make sure that your product meets the following conditions:

* It is assigned to categories. See the [Category](/docs/scos/user/user-guides/202001.0/back-office-user-guide/category/assigning-products-to-categories.html) section for details on how to assign products to categories.
* It is in stock in the warehouse for the current store. See the [Availability](/docs/scos/user/user-guides/202001.0/back-office-user-guide/products/availability/managing-products-availability.html) section to learn how to check products' availability.
* The product's status is **Active**. See the [Products](https://documentation.spryker.com/v4/docs/managing-products#activating-a-product) section to learn how to manage products, including status change.
* It has a price in the current locale. See the [Products](/docs/scos/user/user-guides/202001.0/back-office-user-guide/products/products/managing-products/managing-products.html) section for more details.
* It has been marked as searchable in the Back Office. See the [Products](/docs/scos/user/user-guides/202001.0/back-office-user-guide/products/products/references/concrete-product-reference-information.html) section for more details
* It has product variants - abstract product will not be displayed on Yves unless it has product variants. See [Products](/docs/scos/user/user-guides/202001.0/back-office-user-guide/products/products/concrete-products/creating-a-product-variant.html) to learn how to create product variants.