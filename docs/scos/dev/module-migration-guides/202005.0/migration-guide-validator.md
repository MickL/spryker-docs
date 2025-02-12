---
title: Migration Guide - Validator
description: Use the guide to perform the Validator part of the Silex Migration Effort.
last_updated: Sep 14, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/migration-guide-validator
originalArticleId: a420bdae-d2c0-49c4-9b4b-3d65ad6da9a7
redirect_from:
  - /v5/docs/migration-guide-validator
  - /v5/docs/en/migration-guide-validator
---

{% info_block errorBox %}

This migration guide is a part of the [Silex migration effort](/docs/scos/dev/migration-concepts/silex-replacement/silex-replacement.html).

{% endinfo_block %}

To upgrade the module, do the following:

1. Update the module using composer:
```bash
composer require spryker/validator
```

2. Remove old service providers, if you have them in the project:
```php
\Silex\Provider\ValidatorServiceProvider
```

3. Enable new plugins in the corresponding files:

**Zed Integration (when usable in ZED)**

```php
<?php

namespace Pyz\Zed\Application;

use Spryker\Zed\Application\ApplicationDependencyProvider as SprykerApplicationDependencyProvider;
use Spryker\Yves\Validator\Plugin\Application\ValidatorApplicationPlugin;

class ApplicationDependencyProvider extends SprykerApplicationDependencyProvider
{
	...

	/**
     * @return \Spryker\Shared\ApplicationExtension\Dependency\Plugin\ApplicationPluginInterface[]
     */
    protected function getApplicationPlugins(): array
	{
		return [
			...
			new ValidatorApplicationPlugin(),
   			...
		];
	}
	...
}
```

**Yves Integration (when usable in Yves)**

```php
<?php

namespace Pyz\Yves\ShopApplication;

use Spryker\Yves\ShopApplication\ShopApplicationDependencyProvider as SprykerShopApplicationDependencyProvider;
use Spryker\Zed\Validator\Communication\Plugin\Application\ValidatorApplicationPlugin;

class ShopApplicationDependencyProvider extends SprykerShopApplicationDependencyProvider
{
	...

	/**
     * @return \Spryker\Shared\ApplicationExtension\Dependency\Plugin\ApplicationPluginInterface[]
     */
    protected function getApplicationPlugins(): array
	{
		return [
			...
			new ValidatorApplicationPlugin(),
   			...
		];
	}
	...
}
```

4. Enable additional plugins:

**Zed Integration (when usable in ZED)**

```php
<?php

namespace Pyz\Zed\Validator;

use Spryker\Zed\Security\Communication\Plugin\Validator\UserPasswordValidatorConstraintPlugin;
use Spryker\Zed\Translator\Communication\Plugin\Validator\TranslatorValidatorPlugin;
use Spryker\Zed\Validator\Communication\Plugin\Validator\ConstraintFactoryValidatorPlugin;
use Spryker\Zed\Validator\Communication\Plugin\Validator\MetadataFactoryValidatorPlugin;
use Spryker\Zed\Validator\ValidatorDependencyProvider as SprykerValidatorDependencyProvider;

class ValidatorDependencyProvider extends SprykerValidatorDependencyProvider
{
    /**
     * @return \Spryker\Shared\ValidatorExtension\Dependency\Plugin\ValidatorPluginInterface[]
     */
    protected function getValidatorPlugins(): array
    {
        return [
            new MetadataFactoryValidatorPlugin(),
            new ConstraintFactoryValidatorPlugin(),
            new TranslatorValidatorPlugin(),
        ];
    }
    /**
     * @return \Spryker\Shared\ValidatorExtension\Dependency\Plugin\ConstraintPluginInterface[]
     */
    protected function getConstraintPlugins(): array
    {
        return [
            new UserPasswordValidatorConstraintPlugin(),
        ];
    }
}
```

**Yves Integration (when usable in Yves)**

```php
<?php

namespace Pyz\Yves\Validator;

use Spryker\Yves\Security\Plugin\Validator\UserPasswordValidatorConstraintPlugin;
use Spryker\Yves\Translator\Plugin\Validator\TranslatorValidatorPlugin;
use Spryker\Yves\Validator\Plugin\Validator\ConstraintValidatorFactoryValidatorPlugin;
use Spryker\Yves\Validator\Plugin\Validator\MetadataFactoryValidatorPlugin;
use Spryker\Yves\Validator\ValidatorDependencyProvider as SprykerValidatorDependencyProvider;

class ValidatorDependencyProvider extends SprykerValidatorDependencyProvider
{
    /**
     * @return \Spryker\Shared\ValidatorExtension\Dependency\Plugin\ValidatorPluginInterface[]
     */
    protected function getValidatorPlugins(): array
    {
        return [
            new MetadataFactoryValidatorPlugin(),
            new ConstraintValidatorFactoryValidatorPlugin(),
            new TranslatorValidatorPlugin(),
        ];
    }
    /**
     * @return \Spryker\Shared\ValidatorExtension\Dependency\Plugin\ConstraintPluginInterface[]
     */
    protected function getConstraintPlugins(): array
    {
        return [
            new UserPasswordValidatorConstraintPlugin(),
        ];
    }
}
```
