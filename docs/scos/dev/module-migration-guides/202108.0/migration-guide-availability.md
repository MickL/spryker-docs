---
title: Migration Guide - Availability
description: Use the guide to migrate to the new version of the Availability module.
last_updated: Jun 16, 2021
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/2021080/docs/mg-availability
originalArticleId: 53009fca-6f6b-4583-8946-eb521e6f8235
redirect_from:
  - /2021080/docs/mg-availability
  - /2021080/docs/en/mg-availability
  - /docs/mg-availability
  - /docs/en/mg-availability
---

## Upgrading from Version 8.* to Version 9.0.0

In this new version of the **Availability** module, we have added support of decimal stock. You can find more details about the changes on the [Availability release](https://github.com/spryker/availability/releases) page.

{% info_block errorBox %}

This release is a part of the **Decimal Stock** concept migration. When you upgrade this module version, you should also update all other installed modules in your project to use the same concept as well as to avoid inconsistent behavior. For more information, see [Decimal Stock Migration Concept](/docs/scos/dev/migration-concepts/decimal-stock-migration-concept.html).

{% endinfo_block %}

**To upgrade to the new version of the module, do the following:**

1. Upgrade the **Availability** module to the new version:

```bash
composer require spryker/availability: "^9.0.0" --update-with-dependencies
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
4. Add the following plugin to the project dependency provider, if applicable:

src/Pyz/Zed/Cart/CartDependencyProvider.php

```php
<?php

namespace Pyz\Zed\Cart;

use Spryker\Zed\AvailabilityCartConnector\Communication\Plugin\CheckAvailabilityPlugin;
use Spryker\Zed\Cart\CartDependencyProvider as SprykerCartDependencyProvider;
use Spryker\Zed\Kernel\Container;

class CartDependencyProvider extends SprykerCartDependencyProvider
{

    /**
     * @param \Spryker\Zed\Kernel\Container $container
     *
     * @return \Spryker\Zed\CartExtension\Dependency\Plugin\CartPreCheckPluginInterface[]
     */
    protected function getCartPreCheckPlugins(Container $container)
    {
        return [
            new CheckAvailabilityPlugin(),
        ];
    }
}
```
*Estimated migration time: 5 min*

## Upgrading from Version 6.* to Version 8.0.0

{% info_block infoBox %}

In order to dismantle the Horizontal Barrier and enable partial module updates on projects, Technical Release took place. Public API of source and target major versions are equal. No migration efforts are required. Please [contact us](https://spryker.com/en/support/) if you have any questions.

{% endinfo_block %}

## Upgrading from Version 5.* to Version 6.*

In **Availability** module version 6 we have added support for multi-store. The Back Office has undergone some changes to allow selecting stores and update database tables to store relations to store.

To upgrade, first you need to run database migrations:

```php
           ALTER TABLE "spy_availability"
               ADD "fk_store" INTEGER;

           ALTER TABLE "spy_availability" ADD CONSTRAINT "spy_availability-fk_store"
              FOREIGN KEY ("fk_store")
              REFERENCES "spy_store" ("id_store");

           ALTER TABLE "spy_availability_abstract"
              ADD "fk_store" INTEGER;

           ALTER TABLE "spy_availability_abstract" ADD CONSTRAINT "spy_availability_abstract-fk_store"
             FOREIGN KEY ("fk_store")
             REFERENCES "spy_store" ("id_store");
 ```

Then:

* Run `vendor/bin/console propel:model:build` - this will update models.
* Run  `vendor/bin/console transfer:generate` - this will create new transfer objects.

We have changed public API for methods in: `\Spryker\Zed\Availability\Business\AvailabilityFacade::findProductAbstractAvailability` received a third argument for `idStore`.

We have also changed the way data is collected by collector, now it has to filter data by current store.

Change: `\Pyz\Zed\Collector\Business\Storage\AvailabilityCollector`:

```php
$productConcreteAvailability = SpyAvailabilityQuery::create()
            ->filterByFkStore($this->getCurrentStore()->getIdStore()) //note the new filter by method.
            ->findByFkAvailabilityAbstract($idAvailabilityAbstract);
```

Change: `\Pyz\Zed\Collector\Persistence\Storage\Propel\AvailabilityCollectorQuery` to collect only current store availability:

```php
$this->touchQuery->addJoin(
            [
                SpyAvailabilityAbstractTableMap::COL_ABSTRACT_SKU,
                SpyAvailabilityAbstractTableMap::COL_FK_STORE,
            ],
            [
                SpyProductAbstractTableMap::COL_SKU,
                $this->getStoreTransfer()->getIdStore(),
            ],
            Criteria::INNER_JOIN
        );
```

## Upgrading from Version 3.* to Version 4.*

All `Availability` UI has been moved to `AvailabilitGui` module, mostly Communication or Persistence were changed. If you have overwritten any of moved classes from those layers please change base class namespace from `Availability` to `AvailabilityGui` root.

## Upgrading from Version 2.* to Version 3.*

With Availability version 3, we have changed the way availability is calculated.
Two new tables have been added:

```php
CREATE TABLE "spy_availability_abstract"
(
    "id_availability_abstract" INTEGER NOT NULL,
    "abstract_sku" VARCHAR(255) NOT NULL,
    "quantity" INTEGER DEFAULT 0 NOT NULL,
    PRIMARY KEY ("id_availability_abstract"),
    CONSTRAINT "spy_availability_abstract-sku" UNIQUE ("abstract_sku")
);

CREATE SEQUENCE "spy_availability_pk_seq";

CREATE TABLE "spy_availability"
(
    "id_availability" INTEGER NOT NULL,
    "fk_availability_abstract" INTEGER NOT NULL,
    "sku" VARCHAR(255) NOT NULL,
    "quantity" INTEGER NOT NULL,
    "is_never_out_of_stock" BOOLEAN DEFAULT \'f\',
    PRIMARY KEY ("id_availability"),
    CONSTRAINT "spy_availability-sku" UNIQUE ("sku")
);

ALTER TABLE "spy_availability" ADD CONSTRAINT "spy_availability-fk_spy_availability_abstract"
    FOREIGN KEY ("fk_availability_abstract")
    REFERENCES "spy_availability_abstract" ("id_availability_abstract");
',
```

As this involves more than the Availability module, to start using it some configuration needed per module basis.

**Oms version >= 4** is required. See the [Migration Guide - OMS](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-oms.html) to version 4 step by step guide how to migrate OMS to have the new Availability module integrated.

**Cart > 2.1** and **AvailabilityCartConnector > 2.0**. To have cart availability per check, add a new plugin `Spryker\Zed\AvailabilityCartConnector\Communication\Plugin\CheckAvailabilityPlugin` to the Cart project dependency provider. `Pyz\Zed\Cart\CartDependencyProvider::getCartPreCheckPlugins()` which is a core implementation of the cart availability check.
A new availability collector is required. Take it from demoshop, `Pyz\Zed\Collector\Business\Storage\AvailabilityCollector`, this has to be added to the `Pyz\Zed\Collector\CollectorDependencyProvider` storage plugin stack.
