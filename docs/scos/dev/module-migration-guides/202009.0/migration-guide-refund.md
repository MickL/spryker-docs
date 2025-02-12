---
title: Migration Guide - Refund
description: Use the guide to learn how to update the Refund module to a newer version.
last_updated: Aug 27, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v6/docs/mg-refund
originalArticleId: 4830c0a9-46ea-4c08-98a5-90b2d05753db
redirect_from:
  - /v6/docs/mg-refund
  - /v6/docs/en/mg-refund
---

## Upgrading from Version 4.* to Version 5.*
Version 4 of the Refund module no longer uses `SalesAggregatorFacade` , it was replaced with `SalesFacade`.
The `RefundCalculator` business class must now replace `RefundToSalesAggregatorInterface` with the `RefundToSalesInterface` bridge.
To learn more see [Migration Guide - Calculation](https://docs.demo-spryker.com/v3/docs/mg-calculation). 

## Upgrading from Version 2.* to Version 3.*
To migrate the Refund module from version 2 to version 3, follow these steps:
Version 3 of the Refund module was completely rebuilt; the `SalesAggregator` is used to get a calculated `OrderTransfer` and plugins are used to change the refundable amount calculation behaviour.
The `RefundFacade` has completely changed and exposes only two methods. 
{% info_block warningBox %}
Check your code and where you make use of the `RefundFacade` change your implementation to use the new methods from the `RefundFacade`.
{% endinfo_block %}
These methods are:
* `RefundFacade::calculateRefund(array $salesOrderItems`, SpySalesOrder $salesOrderEntity)`
* `RefundFacade::saveRefund(RefundTransfer $refundTransfer)`
**You need to:**
1. Rename method `RefundFacade::calculateRefundableAmount()` to `RefundFacade::calculateRefund()` and pass needed arguments to it.
 `calculateRefund()` will return a `RefundTransfer` which holds the refundable amount.
2. When refund process of payment provider is done and accepted, pass the `RefundTransfer` to `RefundFacade::saveRefund()`.
3. Refund view in sales order detail page can be activated by adding `'refund' => '/refund/sales/list'` to `SalesConfig::getSalesDetailExternalBlocksUrls()`.
