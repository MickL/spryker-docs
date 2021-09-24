---
title: Shipment feature overview
description: With the feature, you can create and manage carrier companies and their delivery methods per specific store.
originalLink: https://documentation.spryker.com/v6/docs/shipment-feature-overview
originalArticleId: a23f790f-3a33-48b4-acd3-3f13e8440cea
redirect_from:
  - /v6/docs/shipment-feature-overview
  - /v6/docs/en/shipment-feature-overview
---

The *Shipment* feature allows you to create and manage carrier companies and assign multiple delivery methods associated with specific stores, which your customers can select during the checkout. With the feature in place, you can define delivery price and expected delivery time, tax sets, and availability of the delivery method per store.

The main concepts regarding shipping are as follows:

* **Carrier company**: A company that provides shipping services such as DHL, FedEx, Hermes, etc.
* **Delivery method**: Shipping services provided by a carrier company such as DHL Express, DHL Standard, Hermes Next Day, Hermes Standard, etc.

A sales order can have multiple delivery methods from different carrier companies.

In the Back Office, you can create a carrier company and configure multiple delivery methods. For each delivery method, you can set a price and an associated tax set, define a store in which the delivery method can be available, as well as activate or deactivate the delivery method. For more information on how to create and manage delivery methods in the Back Office, see [Creating and managing delivery methods](/docs/scos/user/user-guides/{{page.version}}/back-office-user-guide/administration/delivery-methods/creating-and-managing-delivery-methods.html).

{% info_block warningBox %}

If a Back Office user creates or edits a shipment of an order created by a customer, the grand total paid by the customer is not affected:

* If a new shipment method is added, its price is 0.
* If the shipment method is changed, the price of the previous shipment method is displayed.

{% endinfo_block %}

Additional behaviors can be attached to a delivery method from the Back Office by selecting specific plugins. For more information on method plugins types, see [Reference information: Shipment method plugins](/docs/scos/user/features/{{page.version}}/shipment/shipment/references/reference-information-shipment-method-plugins.html).

Each shipment method has a dedicated price and tax set in the various currencies you define. The price displayed to the customer is calculated based on the store they visit or their preferred currency selection.

{% info_block infoBox "Shipment calculation rules" %}

You can give shipment discounts based on the carrier, shipment method, or cart value. Intricate calculations enable you to freely define a set of rules to be applied to the various discount options.

{% endinfo_block %}