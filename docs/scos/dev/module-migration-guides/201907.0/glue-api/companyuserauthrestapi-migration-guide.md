---
title: CompanyUserAuthRestApi Migration Guide
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/companyuserauthrestapi-migration-guide
originalArticleId: 6da475d7-e595-467f-a2e4-6f3fa5858dc4
redirect_from:
  - /v3/docs/companyuserauthrestapi-migration-guide
  - /v3/docs/en/companyuserauthrestapi-migration-guide
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

