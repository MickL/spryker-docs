---
title: Loggly
description: Read log messages from a queue and send the messages via https by integrating Loggly into the Spryker Commerce OS.
last_updated: Jun 16, 2021
template: concept-topic-template
originalLink: https://documentation.spryker.com/2021080/docs/loggly-queue
originalArticleId: 27b2bc47-2cf9-466c-b944-5a9768b601b3
redirect_from:
  - /2021080/docs/loggly-queue
  - /2021080/docs/en/loggly-queue
  - /docs/loggly-queue
  - /docs/en/loggly-queue
related:
  - title: Technology Partner Integration
    link: docs/scos/user/technology-partners/page.version/technology-partner-integration.html
---

The [Loggly](https://github.com/spryker-eco/loggly) module provides a plugin to read log messages from a queue and send the messages via https to [Loggly](https://www.loggly.com/).

To start using Loggly, you need to do some configuration, as described below.

## 1. Adjusting the config_default.php file

First of all, add necessary data to the *config_default.php* file:

```php
<?php
use SprykerEco\Shared\Loggly\LogglyConstants;
// ...

$config[LogglyConstants::TOKEN] = 'Token for your Loggly account';
$config[LogglyConstants::QUEUE_NAME] = 'Name of a log queue';

// Chunk size for messages to be processed from queue (default: 50)
$config[LogglyConstants::QUEUE_CHUNK_SIZE] = $chunkSize;

```

## 2. Setting up a log queue

Next, you have to set up a log queue. On project level, add the name of a log queue to an array returned by `\Pyz\Client\RabbitMq\RabbitMqConfig::getQueueConfiguration()` method:

**Pyz\Client\RabbitMqRabbitMqConfig**

```php
<?php

namespace Pyz\Client\RabbitMq;

use SprykerEco\Shared\Loggly\LogglyConstants
class RabbitMqConfig extends SprykerRabbitMqConfig
{
    /**
     * @return array
     */
    protected function getQueueConfiguration(): array
    {
        return [
            // ...
            $this->get(LogglyConstants::QUEUE_NAME),
        ];
    }
```

## 3. Configuring a queue consumer

Configure a queue consumer in `Pyz\Zed\Queue\QueueConfig`:

**Pyz\Zed\Queue\QueueConfig**

```php
<?php

namespace Pyz\Zed\Queue;

use Generated\Shared\Transfer\RabbitMqConsumerOptionTransfer;
use Spryker\Shared\Config\Config;
use Spryker\Zed\Queue\QueueConfig as SprykerQueueConfig;
use SprykerEco\Shared\Loggly\LogglyConstants;

class QueueConfig extends SprykerQueueConfig
{
    public const RABBITMQ = 'rabbitmq';

    /**
     * @return array
     */
    protected function getQueueReceiverOptions(): array
    {
        return [
            // ...
            Config::get(LogglyConstants::QUEUE_NAME) => [
                static::RABBITMQ => $this->getRabbitMqQueueConsumerOptions(),
            ],
        ];
    }

    /**
     * @return \Generated\Shared\Transfer\RabbitMqConsumerOptionTransfer
     */
    protected function getRabbitMqQueueConsumerOptions(): RabbitMqConsumerOptionTransfer
    {
        $queueOptionTransfer = new RabbitMqConsumerOptionTransfer();
        $queueOptionTransfer->setConsumerExclusive(false);
        $queueOptionTransfer->setNoWait(false);

        return $queueOptionTransfer;
    }

    // ...
}
```

## 4. Registering the Loggly plugin

Finally, register `\SprykerEco\Zed\Loggly\Communication\Plugin\LogglyLoggerQueueMessageProcessorPlugin` in  `\Pyz\Zed\Queue\QueueDependencyProvider::getProcessorMessagePlugins`:

**Pyz\Zed\Queue\QueueDependencyProvider**

```php
<?php

namespace Pyz\Zed\Queue;

use Spryker\Shared\Config\Config;
use Spryker\Zed\Kernel\Container;
use Spryker\Zed\Queue\QueueDependencyProvider as SprykerDependencyProvider;
use SprykerEco\Shared\Loggly\LogglyConstants;
use SprykerEco\Zed\Loggly\Communication\Plugin\LogglyLoggerQueueMessageProcessorPlugin;

class QueueDependencyProvider extends SprykerDependencyProvider
{
    /**
     * @param \Spryker\Zed\Kernel\Container $container
     *
     * @return \Spryker\Zed\Queue\Dependency\Plugin\QueueMessageProcessorPluginInterface[]
     */
    protected function getProcessorMessagePlugins(Container $container)
    {
        return [
            // ...
            Config::get(LogglyConstants::QUEUE_NAME) => new LogglyLoggerQueueMessageProcessorPlugin(),
        ];
    }

    // ...
}
```

For further information on this partner and integration into Spryker, please [contact us](https://spryker.force.com/support/s/).
