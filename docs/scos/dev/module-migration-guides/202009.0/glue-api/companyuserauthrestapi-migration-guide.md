---
title: CompanyUserAuthRestApi Migration Guide
last_updated: Aug 27, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v6/docs/companyuserauthrestapi-migration-guide
originalArticleId: c74817d2-90b6-4964-8ea8-f6dc0ed6fbc5
redirect_from:
  - /v6/docs/companyuserauthrestapi-migration-guide
  - /v6/docs/en/companyuserauthrestapi-migration-guide
---

## Upgrading from Version 1.* to Version 2.*


CompanyUserAuthRestApi module version 2.0.0 brings the following major change:
Glue layer authentication has been moved from `OauthCompanyUser` to `CompanyUserAuthRestApi`.

To perform the upgrade:

1.     Update Composer: 
```php
composer require spryker/company-user-auth-rest-api: "^2.0.0" --update-with-dependencies
```

2.  Generate transfer objects:
```php
vendor/bin/console transfer:generate
```
3.  In `\Pyz\Glue\AuthRestApi\AuthRestApiDependencyProvider::getRestUserExpanderPlugins()` replace `Spryker\Glue\OauthCompanyUser\Plugin\AuthRestApi\CompanyUserRestUserMapperPlugin` with `Spryker\Glue\CompanyUserAuthRestApi\Plugin\AuthRestApi\CompanyUserRestUserMapperPlugin`:

   
```php
 - use Spryker\Glue\OauthCompanyUser\Plugin\AuthRestApi\CompanyUserRestUserMapperPlugin;
 + use Spryker\Glue\CompanyUserAuthRestApi\Plugin\AuthRestApi\CompanyUserRestUserMapperPlugin;
```
*Estimated migration time: ~5 minutes*

