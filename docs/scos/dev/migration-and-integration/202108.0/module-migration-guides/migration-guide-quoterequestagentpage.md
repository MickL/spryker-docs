---
title: Migration Guide - QuoteRequestAgentPage
originalLink: https://documentation.spryker.com/2021080/docs/mg-quoterequestagentpage
redirect_from:
  - /2021080/docs/mg-quoterequestagentpage
  - /2021080/docs/en/mg-quoterequestagentpage
---

## Upgrading from Version 1.x.x to Version 2.x.x

The only major change of the `QuoteRequestAgentPage` 2.x.x is the dependency update for `spryker/quote-request-agent:^2.0.0` and `spryker/quote-request:^2.0.0`

Also, transfer property `QuoteRequestTranser::isLatestVersionHidden` was replaced by `QuoteRequestTransfer:isLatestVersionVisible`.

**To migrate do the following:**
1. Update `spryker/quote-request-agent` to version ^2.0.0 by following the steps from [Migration Guide - QuoteRequest](/docs/scos/dev/migration-and-integration/202001.0/module-migration-guides/migration-guide-quoterequest.html).
2. Update `spryker/quote-request` to version ^2.0.0 by following the steps from [Migration Guide - Quote Request Agent](/docs/scos/dev/migration-and-integration/202001.0/module-migration-guides/migration-guide-quoterequestagent.html).
3. Update `spryker-shop/quote-request-agent-page:^2.0.0`

```bash
composer require spryker-shop/quote-request-agent-page: "^2.0.0" --update-with-dependencies
```

4. If you modified anything in the following files on the project level, ensure that the new module version changes do not conflict with yours:

```php
src/SprykerShop/Yves/QuoteRequestAgentPage/Form/QuoteRequestAgentForm.php
src/SprykerShop/Yves/QuoteRequestAgentPage/Theme/default/views/quote-request-details/quote-request-details.twig   
src/SprykerShop/Yves/QuoteRequestAgentPage/Theme/default/views/quote-request-edit/quote-request-edit.twig
```

5. To generate transfers, run the following command:

```bash
vendor/bin/console transfer:generate
```

*Estimated migration time: ~1h*
