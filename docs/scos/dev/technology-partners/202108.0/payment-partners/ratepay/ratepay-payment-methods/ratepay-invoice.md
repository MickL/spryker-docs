---
title: RatePay - Invoice
originalLink: https://documentation.spryker.com/2021080/docs/ratepay-invoice
redirect_from:
  - /2021080/docs/ratepay-invoice
  - /2021080/docs/en/ratepay-invoice
---

## Workflow Scenarios
### Payment Flow
![Click Me](https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Ratepay/ratepay-installment-payment-flow.png){height="" width=""}

### Cancellation Flow
![Click Me](https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Ratepay/ratepay-invoice-cancellation-flow.png){height="" width=""}

### Partial Cancellation Flow
![Click Me](https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Ratepay/ratepay-invoice-partial-cancellation-flow.png){height="" width=""}

### Refund Flow
![Click Me](https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Ratepay/ratepay-invoice-refund-flow.png){height="" width=""}


## Integrating RatePAY Invoice Payment
To integrate invoice payment, you need to: RatePAY invoice payment configuration and call the facade functions.

## Setting RatePAY Invoice Configuration
The configuration to integrate invoice payments using RatePAY is:
 
  * `PROFILE_ID`: merchant’s login (required).

  * `SECURITY_CODE`: merchant’s password (required).

  * `SHOP_ID`: shop identifier (required).

  * `SYSTEM_ID`: system identifier (required).

  * `CLIENT_VERSION`: client system version.

  * `CLIENT_NAME`: client name.

  * `RATEPAY_REQUEST_VERSION`: request version.

  * `RATEPAY_REQUEST_XMLNS_URN`: request XMLNS urn.

  * `MODE`: the mode of the transaction, either test or live (required).

  * `API_TEST_URL`: test mode API url.

  * `API_LIVE_URL`: live mode API url.

## Perform Requests
To perform the needed requests,  use the [RatePAY State Machine Commands and Conditions](/docs/scos/dev/technology-partners/202001.0/payment-partners/ratepay/ratepay-state-machine-commands-and-conditions.html) . You can also use the `facademethods`directly which, however, are invoked by the state machine.