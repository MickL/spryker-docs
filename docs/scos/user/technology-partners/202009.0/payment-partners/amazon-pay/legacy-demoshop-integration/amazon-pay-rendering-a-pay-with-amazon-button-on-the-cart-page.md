---
title: Amazon Pay - Rendering a “Pay with Amazon” Button on the Cart Page
description: This article describes the way how to render the "Pay with Amazon" button on the cart page.
originalLink: https://documentation.spryker.com/v6/docs/amazon-pay-rendering-pay-demoshop
originalArticleId: 9f93b75f-7e46-4903-84c0-9bc29ad4bcd9
redirect_from:
  - /v6/docs/amazon-pay-rendering-pay-demoshop
  - /v6/docs/en/amazon-pay-rendering-pay-demoshop
---

Usually the checkout page includes information for the buyer to review, items in the cart, prices, total price information and some other order related details.

From this page, the buyer can proceed to checkout by clicking a related GUI element (for example hyperlink or button).

Amazon Pay provides its own GUI element, a button which renders by Amazon Javascript code snippet and looks as follows:
![Click Me](https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Amazon+Pay/amazonpay_button.png)   

If the buyer is a registered Amazon customer, clicking the button prompts to enter their Amazon login and password.

If correct, Amazon creates an order reference and passes it to the shop.

Using this reference and Amazon Pay credentials it is possible to run Amazon Pay API queries.

**To insert the Amazon Pay button in your shop, add the following widget on your page:**:
```xml
{% raw %}{{{% endraw %} render(path('amazonpay_paybutton')) {% raw %}}}{% endraw %}
```

Configuration is used from your current settings profile.

**Results**:

If everything was done properly, the clickable button will be displayed and by clicking it, the user will see a popup window with Amazon prompt to login.

The Popup looks as follows:
![Click Me](https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Amazon+Pay/amazon_popup.png) 