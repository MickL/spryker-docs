---
title: Migration Guide - NavigationsRestApi
last_updated: Jan 30, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v2/docs/navigationsrestapi-migration-guide
originalArticleId: 641c11d7-e011-4648-8a42-f3735cb7f714
redirect_from:
  - /v2/docs/navigationsrestapi-migration-guide
  - /v2/docs/en/navigationsrestapi-migration-guide
---

## Upgrading from Version 1.* to Version 2.*

Version 2.0.0 of the `NavigationsRestApi` module introduces the resourceId field and a new dependency to the `spryker/url-storage` module.

**BC Breaks and Solutions:**

* Set up project configuration
* Migrate database

**To upgrade to the new version of the module, do the following:**
1. Update the NavigationsRestApi module with Composer:
`"spryker/navigations-rest-api": "^2.0.0" --update-with-dependencies`
2. Set up Project Configuration.
Configure mapping to specify source field from which the resourceId field should be filled depending on navigation node type.

<details open>
<summary markdown='span'>src/Pyz/Glue/NavigationsRestApi/NavigationsRestApiConfig.php</summary>

```php
<?php
 
namespace Pyz\Glue\NavigationsRestApi;
 
use Spryker\Glue\NavigationsRestApi\NavigationsRestApiConfig as SprykerNavigationsRestApiConfigi;
 
class NavigationsRestApiConfig extends SprykerNavigationsRestApiConfig
{
    /**
     * @return array
     */
    public function getNavigationTypeToUrlResourceIdFieldMapping(): array
    {
        return [
            'category' => 'fkResourceCategorynode',
            'cms_page' => 'fkResourcePage',
        ];
    }
}
```

<br>
</details>

3.  Perform database schema migration.
If you do not have the spryker/url-storage module in your project - you need to perform database schema migration to get the required tables.

On your local development environment you may run

```bash
console transfer:generate
console propel:install
console transfer:generate
```

When looking to generate a production migration, this command will help you find the SQL patches needed against your production schema:

```bash
vendor/bin/console propel:diff
```

{% info_block infoBox %}
Before migrating a production database, always review each SQL statement individually, even when there are many of them.
{% endinfo_block %}

_Estimated migration time: 30 minutes_

