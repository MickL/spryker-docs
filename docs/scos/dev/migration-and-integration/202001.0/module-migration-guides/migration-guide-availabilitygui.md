---
title: Migration Guide - AvailabilityGui
originalLink: https://documentation.spryker.com/v4/docs/mg-availability-gui
redirect_from:
  - /v4/docs/mg-availability-gui
  - /v4/docs/en/mg-availability-gui
---

## Upgrading from Version 5.* to Version 6.0.0

In this new version of the **AvailabilityGui** module, we have added support of decimal stock. You can find more details about the changes on the [AvailabilityGui module](https://github.com/spryker/availability-gui/releases) release page.

{% info_block errorBox %}
This release is a part of the **Decimal Stock** concept migration. When you upgrade this module version, you should also update all other installed modules in your project to use the same concept as well as to avoid inconsistent behavior. For more information, see [Decimal Stock Migration Concept](/docs/scos/dev/migration-and-integration/202001.0/migration-concepts/decimal-stock-migration-concept.html
{% endinfo_block %}.)

**To upgrade to the new version of the module, do the following:**

1. Upgrade the **AvailabilityGui** module to the new version:

```bash
composer require spryker/availability-gui: "^6.0.0" --update-with-dependencies
```
2. Update the database entity schema for each store in the system:

```bash
APPLICATION_STORE=DE console propel:schema:copy
APPLICATION_STORE=US console propel:schema:copy
...
```
3. Run the database migration:

```bash
console propel:install
console transfer:generate
```

*Estimated migration time: 5 min*

## Upgrading from Version 3.* to Version 5.0.0

{% info_block infoBox %}
In order to dismantle the Horizontal Barrier and enable partial module updates on projects, Technical Release took place. Public API of source and target major versions are equal. No migration efforts are required. Please [contact us](https://support.spryker.com/hc/en-us
{% endinfo_block %} if you have any questions.)