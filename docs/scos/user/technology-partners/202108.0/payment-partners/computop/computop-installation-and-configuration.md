---
title: Computop - Installation and configuration
last_updated: Jun 16, 2021
template: concept-topic-template
originalLink: https://documentation.spryker.com/2021080/docs/computop-installation-and-configuration
originalArticleId: 7d6fd0b4-0e5e-41ac-9788-0361d3252a58
redirect_from:
  - /2021080/docs/computop-installation-and-configuration
  - /2021080/docs/en/computop-installation-and-configuration
  - /docs/computop-installation-and-configuration
  - /docs/en/computop-installation-and-configuration
---

This topic describes how to integrate Computop into a Spryker project by installing and configuring the Computop module.

## Installation

Install the Computop module:

```bash
composer require spryker-eco/computop
```

## Configuration

You can check all the necessary configurations in `vendor/spryker-eco/computop/config/config.dist.php`.

Find an example of the Computop module configuration below:

<details open>
<summary>config/Shared/config_default.php</summary>

```PHP
// Spryker security configuration
$config[KernelConstants::DOMAIN_WHITELIST] = [
	...
    'www.computop-paygate.com', // A trusted Computop domain, required for redirects to third-party services.
];
$config[SessionConstants::YVES_SESSION_COOKIE_SAMESITE] = 'none'; // Allows to redirect customers from Computop back to the shop via a `POST` request.

// Credantials
$config[ComputopApiConstants::MERCHANT_ID] = 'Computop merchant identifier';
$config[ComputopApiConstants::BLOWFISH_PASSWORD] = 'Password for blowfish hashing';
$config[ComputopApiConstants::HMAC_PASSWORD] = 'Password for hmac hashing';
$config[ComputopConstants::IDEAL_ISSUER_ID] = 'IDeal issuer identifier';
$config[ComputopConstants::PAYDIREKT_SHOP_KEY] = 'Paydirekt shop key';

// Init API call endpoints
$config[ComputopConstants::PAY_NOW_INIT_ACTION] = 'https://www.computop-paygate.com/paynow.aspx';
$config[ComputopConstants::CREDIT_CARD_INIT_ACTION] = 'https://www.computop-paygate.com/payssl.aspx';
$config[ComputopConstants::PAYPAL_INIT_ACTION] = 'https://www.computop-paygate.com/paypal.aspx';
$config[ComputopConstants::DIRECT_DEBIT_INIT_ACTION] = 'https://www.computop-paygate.com/paysdd.aspx';
$config[ComputopConstants::SOFORT_INIT_ACTION] = 'https://www.computop-paygate.com/sofort.aspx';
$config[ComputopConstants::PAYDIREKT_INIT_ACTION] = 'https://www.computop-paygate.com/paydirekt.aspx';
$config[ComputopConstants::IDEAL_INIT_ACTION] = 'https://www.computop-paygate.com/ideal.aspx';
$config[ComputopConstants::EASY_CREDIT_INIT_ACTION] = 'https://www.computop-paygate.com/easyCredit.aspx';
$config[ComputopConstants::PAYU_CEE_SINGLE_INIT_ACTION] = 'https://www.computop-paygate.com/payu.aspx';

// Post order place API calls endpoints
$config[ComputopApiConstants::PAYPAL_EXPRESS_PREPARE_ACTION] = 'https://www.computop-paygate.com/ExternalServices/paypalorders.aspx';
$config[ComputopApiConstants::PAYPAL_EXPRESS_COMPLETE_ACTION] = 'https://www.computop-paygate.com/paypalComplete.aspx';
$config[ComputopApiConstants::EASY_CREDIT_STATUS_ACTION] = 'https://www.computop-paygate.com/easyCreditDirect.aspx';
$config[ComputopApiConstants::EASY_CREDIT_AUTHORIZE_ACTION] = 'https://www.computop-paygate.com/easyCreditDirect.aspx';
$config[ComputopApiConstants::AUTHORIZE_ACTION] = 'https://www.computop-paygate.com/authorize.aspx';
$config[ComputopApiConstants::CAPTURE_ACTION] = 'https://www.computop-paygate.com/capture.aspx';
$config[ComputopApiConstants::REVERSE_ACTION] = 'https://www.computop-paygate.com/reverse.aspx';
$config[ComputopApiConstants::INQUIRE_ACTION] = 'https://www.computop-paygate.com/inquire.aspx';
$config[ComputopApiConstants::REFUND_ACTION] = 'https://www.computop-paygate.com/credit.aspx';

// Payment method specific configuration
$config[ComputopApiConstants::RESPONSE_MAC_REQUIRED] = [
    ComputopConfig::INIT_METHOD,
];
$config[ComputopConstants::CREDIT_CARD_TEMPLATE_ENABLED] = false;
$config[ComputopConstants::CREDIT_CARD_TX_TYPE] = '';
$config[ComputopConstants::PAY_NOW_TX_TYPE] = '';
$config[ComputopConstants::PAY_PAL_TX_TYPE] = ComputopConfig::TX_TYPE_AUTH;
$config[ComputopConstants::PAY_PAL_EXPRESS_PAYPAL_METHOD] = '';
$config[ComputopConstants::PAYMENT_METHODS_WITHOUT_ORDER_CALL] = [
    ComputopConfig::PAYMENT_METHOD_SOFORT,
    ComputopConfig::PAYMENT_METHOD_PAYDIREKT,
    ComputopConfig::PAYMENT_METHOD_IDEAL,
    ComputopConfig::PAYMENT_METHOD_CREDIT_CARD,
    ComputopConfig::PAYMENT_METHOD_PAY_NOW,
    ComputopConfig::PAYMENT_METHOD_PAY_PAL,
    ComputopConfig::PAYMENT_METHOD_PAY_PAL_EXPRESS,
    ComputopConfig::PAYMENT_METHOD_DIRECT_DEBIT,
    ComputopConfig::PAYMENT_METHOD_EASY_CREDIT,
    ComputopConfig::PAYMENT_METHOD_PAYU_CEE_SINGLE,
];
$config[ComputopApiConstants::PAYMENT_METHODS_CAPTURE_TYPES] = [
    ComputopApiConfig::PAYMENT_METHOD_PAYDIREKT => ComputopApiConfig::CAPTURE_TYPE_MANUAL,
    ComputopApiConfig::PAYMENT_METHOD_CREDIT_CARD => ComputopApiConfig::CAPTURE_TYPE_MANUAL,
    ComputopApiConfig::PAYMENT_METHOD_PAY_NOW => ComputopApiConfig::CAPTURE_TYPE_MANUAL,
    ComputopApiConfig::PAYMENT_METHOD_PAY_PAL => ComputopApiConfig::CAPTURE_TYPE_MANUAL,
    ComputopApiConfig::PAYMENT_METHOD_PAY_PAL_EXPRESS => ComputopApiConfig::CAPTURE_TYPE_MANUAL,
    ComputopApiConfig::PAYMENT_METHOD_DIRECT_DEBIT => ComputopApiConfig::CAPTURE_TYPE_MANUAL,
    ComputopApiConfig::PAYMENT_METHOD_PAYU_CEE_SINGLE => ComputopApiConfig::CAPTURE_TYPE_MANUAL,
];

// CRIF (formerly Deltavista) configuration
$config[ComputopConstants::CRIF_ENABLED] = true;
$config[ComputopApiConstants::CRIF_ACTION] = 'https://www.computop-paygate.com/deltavista.aspx';
$config[ComputopApiConstants::CRIF_PRODUCT_NAME] = ComputopConfig::CRIF_PRODUCT_NAME_QUICK_CHECK_CONSUMER;
$config[ComputopApiConstants::CRIF_LEGAL_FORM] = ComputopConfig::CRIF_LEGAL_FORM_PERSON;
$config[ComputopConstants::CRIF_GREEN_AVAILABLE_PAYMENT_METHODS] = [
    ComputopConfig::PAYMENT_METHOD_SOFORT,
    ComputopConfig::PAYMENT_METHOD_PAYDIREKT,
    ComputopConfig::PAYMENT_METHOD_IDEAL,
    ComputopConfig::PAYMENT_METHOD_CREDIT_CARD,
    ComputopConfig::PAYMENT_METHOD_PAY_NOW,
    ComputopConfig::PAYMENT_METHOD_PAY_PAL,
    ComputopConfig::PAYMENT_METHOD_PAY_PAL_EXPRESS,
    ComputopConfig::PAYMENT_METHOD_DIRECT_DEBIT,
    ComputopConfig::PAYMENT_METHOD_EASY_CREDIT,
    ComputopConfig::PAYMENT_METHOD_PAYU_CEE_SINGLE,
];
$config[ComputopConstants::CRIF_YELLOW_AVAILABLE_PAYMENT_METHODS] = [
    ComputopConfig::PAYMENT_METHOD_CREDIT_CARD,
    ComputopConfig::PAYMENT_METHOD_PAY_NOW,
    ComputopConfig::PAYMENT_METHOD_PAY_PAL,
    ComputopConfig::PAYMENT_METHOD_PAY_PAL_EXPRESS,
];
$config[ComputopConstants::CRIF_RED_AVAILABLE_PAYMENT_METHODS] = [
    ComputopConfig::PAYMENT_METHOD_CREDIT_CARD,
    ComputopConfig::PAYMENT_METHOD_EASY_CREDIT,
];
$config[ComputopShipmentConstants::PAYPAL_EXPRESS_DEFAULT_SHIPMENT_METHOD_KEY] = 'spryker_dummy_shipment-standard';
```

</details>

| Configuration Key | Type | Description |
| --- | --- | --- |
| `$config[ComputopApiConstants::MERCHANT_ID]` | string | Computop merchant identifier. |
| `$config[ComputopApiConstants::BLOWFISH_PASSWORD]` | string | Password for Blowfish hashing. |
| `$config[ComputopApiConstants::HMAC_PASSWORD]` | string | Password for HMAC hashing. |
| `$config[ComputopConstants::PAYDIREKT_SHOP_KEY]` | string | Shop key for the Paydirect payment method. |
| `$config[ComputopConstants::IDEAL_ISSUER_ID]`  | string  | Issuer ID for the Ideal payment method.  |
| `$config[ComputopConstants::PAY_NOW_INIT_ACTION]`  | string  | `init` API call endpoint for the PayNow payment method.  |
| `$config[ComputopConstants::CREDIT_CARD_INIT_ACTION]`  |string | `init` API call endpoint for the Credit Card payment method.  |
| `$config[ComputopConstants::PAYPAL_INIT_ACTION]`  | string  | `init` API call endpoint for the PayPal payment method.  |
| `$config[ComputopConstants::DIRECT_DEBIT_INIT_ACTION]`  | string  | `init` API call endpoint for the Direct Debit payment method.  |
| `$config[ComputopConstants::SOFORT_INIT_ACTION]`  | string  | `init` API call endpoint for the Sofort payment method.  |
| `$config[ComputopConstants::PAYDIREKT_INIT_ACTION]`  |string   | `init` API call endpoint for the Paydirect payment method.  |
| `$config[ComputopConstants::IDEAL_INIT_ACTION]`  | string  | `init` API call endpoint for the Ideal payment method.  |
| `$config[ComputopConstants::EASY_CREDIT_INIT_ACTION]`  | string  | `init` API call endpoint for the Easy Credit payment method.  |
| `$config[ComputopConstants::PAYU_CEE_SINGLE_INIT_ACTION]` | string | `init` API call endpoint for the PayU CEE Single payment method. |
| `$config[ComputopApiConstants::PAYPAL_EXPRESS_PREPARE_ACTION]` | string | `prepare` API call endpoint for the PayPal Express payment method. |
| `$config[ComputopApiConstants::PAYPAL_EXPRESS_COMPLETE_ACTION]` | string | `complete` API call endpoint for the PayPal Express payment method. |
| `$config[ComputopApiConstants::EASY_CREDIT_STATUS_ACTION]`  | string  | `status` API call endpoint for the Easy Credit payment method.  |
| `$config[ComputopApiConstants::EASY_CREDIT_AUTHORIZE_ACTION]` | string  | `authorize` API call endpoint for the Easy Credit payment method.  |
| `$config[ComputopApiConstants::AUTHORIZE_ACTION]`  | string  | `authorize` API call endpoint.  |
| `$config[ComputopApiConstants::CAPTURE_ACTION]`  | string  | `capture` API call endpoint.  |
| `$config[ComputopApiConstants::REVERSE_ACTION]`  | string  | `reserve` API call endpoint.  |
| `$config[ComputopApiConstants::INQUIRE_ACTION]`  | string  | `inquire` API call endpoint.  |
| `$config[ComputopApiConstants::REFUND_ACTION]`  | string  | `refund` API call endpoint.  |
| `$config[ComputopApiConstants::RESPONSE_MAC_REQUIRED]`  | array  | MAC is checked by methods on response.  |
| `$config[ComputopConstants::CREDIT_CARD_TEMPLATE_ENABLED]`  | bool  | Defines if a custom template is enabled for the Credit Card payment method.  |
| `$config[ComputopConstants::CREDIT_CARD_TX_TYPE]`  | string  | TX TYPE for the Credit Card payment method (empty string).  |
| `$config[ComputopConstants::PAY_NOW_TX_TYPE]`  | string  | TX TYPE for the PayNow payment method (empty string).  |
| `$config[ComputopConstants::PAY_PAL_TX_TYPE]`  | string  |  TX TYPE for the PayPal payment method (Auth). |
| `$config[ComputopConstants::PAY_PAL_EXPRESS_PAYPAL_METHOD]` | string | Using method for the PayPal Express payment method. |
| `$config[ComputopConstants::PAYMENT_METHODS_WITHOUT_ORDER_CALL]`  | array  | Payment methods without the order call.  |
| `$config[ComputopApiConstants::PAYMENT_METHODS_CAPTURE_TYPES]`  | array  | Mapping payment methods and their capture types: `MANUAL` or `AUTO`.  |
| `$config[ComputopConstants::CRIF_ENABLED]`  | bool  | Defines if CRIF risk check is enabled.  |
| `$config[ComputopApiConstants::CRIF_ACTION]`  | string  | CRIF API call endpoint.  |
| `$config[ComputopApiConstants::CRIF_PRODUCT_NAME]`  | string  | `QuickCheckConsumer` or <br> `CreditCheckConsumer` or <br> `QuickCheckBusiness`  or  <br>`CreditCheckBusiness`  or <br>`IdentCheckConsume`.  |
| `$config[ComputopApiConstants::CRIF_LEGAL_FORM]`  | string  | `PERSON`, `COMPANY`, or `UNKNOWN`.  |
| `$config[ComputopConstants::CRIF_GREEN_AVAILABLE_PAYMENT_METHODS]`  | array  | Payment methods available with a green response code.  |
| `$config[ComputopConstants::CRIF_YELLOW_AVAILABLE_PAYMENT_METHODS] ` | array  | Payment methods available with a yellow response code.  |
| `$config[ComputopConstants::CRIF_RED_AVAILABLE_PAYMENT_METHODS]`  | array  | Payment methods available with a red response code.  |
