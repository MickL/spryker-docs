---
title: Migration Guide - Cart
description: Use the guide to update versions to the newer ones of the Cart module.
last_updated: Aug 27, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v6/docs/mg-cart
originalArticleId: bad263f7-55d0-435e-9bde-03413d91da3b
redirect_from:
  - /v6/docs/mg-cart
  - /v6/docs/en/mg-cart
related:
  - title: Migration Guide - Quote
    link: docs/scos/dev/module-migration-guides/page.version/migration-guide-quote.html
---

## Upgrading from Version 5.* to Version 7.0.0

{% info_block infoBox %}
In order to dismantle the Horizontal Barrier and enable partial module updates on projects, Technical Release took place. Public API of source and target major versions are equal. No migration efforts are required. Please [contact us](https://spryker.com/en/support/) if you have any questions.
{% endinfo_block %}

## Upgrading from Version 4.* to Version 5.*

With the implementation of the quote storage strategies, the new version of the Cart module allows to use different behaviors for different strategies.
Since `QuoteClient::getStorageStrategy` method is used now, the Quote module's version must be 2.0.0 or higher.
`CartClientInterface::storeQuote` method is deprecated, remove it from your code and use `QuoteClientInterface::setQuote()`  instead.
`CartClientInterface::getZedStub` method is deprecated, remove it from your code and use `\Spryker\Client\ZedRequest\ZedRequestClient::addFlashMessagesFromLastZedRequest` to push stack of ZED request messages to flash messages.

All logic from CartClient has been moved to `\Spryker\Client\Cart\Plugin\SessionQuoteStorageStrategyPlugin`.
Make sure that all your local overwrites of those methods have been moved there.

<!-- Last review date: Apr 10, 2018- by Dmitriy Krainiy -->
