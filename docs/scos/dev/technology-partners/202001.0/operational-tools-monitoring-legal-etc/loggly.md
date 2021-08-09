---
title: Loggly
originalLink: https://documentation.spryker.com/v4/docs/loggly-queue
redirect_from:
  - /v4/docs/loggly-queue
  - /v4/docs/en/loggly-queue
---

The Loggly module provides a plugin to read log messages from a queue and send the messages via https to [Loggly](https://www.loggly.com/).

To integrate this plugin you need to have the `QueueHandler` enabled in your Logger configuration. <!-- as described [here](https://documentation.spryker.com/v4/docs/logger.htm).-->

In addition you need to properly configure the queue setup for Loggly to work.

## RabbitMqDependencyProvider

```php
<?php

namespace Pyz\Client\RabbitMq;

use ArrayObject;
use Generated\Shared\Transfer\RabbitMqOptionTransfer;
use Spryker\Client\RabbitMq\RabbitMqDependencyProvider as RabbitMqRabbitMqDependencyProvider;
use Spryker\Shared\Config\Config;
use SprykerEco\Shared\Loggly\LogglyConstants;

class RabbitMqDependencyProvider extends RabbitMqRabbitMqDependencyProvider
{

 /**
 * @return \ArrayObject
 */
 protected function getQueueOptions()
 {
 $queueOptionCollection = new ArrayObject();
 $queueOptionCollection->append($this->getLoggerQueueOption());

 return $queueOptionCollection;
 }

 /**
 * @return \Generated\Shared\Transfer\RabbitMqOptionTransfer
 */
 protected function getLoggerQueueOption()
 {
 $queueOption = new RabbitMqOptionTransfer();
 $queueOption->setQueueName(Config::get(LogglyConstants::QUEUE_NAME));
 $queueOption->setDurable(true);
 $queueOption->setType('direct');
 $queueOption->setDeclarationType(Connection::RABBIT_MQ_EXCHANGE);
 $queueOption->setBindingQueue($this->getLoggerQueueBinding());

 return $queueOption;
 }

 /**
 * @return \Generated\Shared\Transfer\RabbitMqOptionTransfer
 */
 protected function getLoggerQueueBinding()
 {
 $queueOption = new RabbitMqOptionTransfer();
 $queueOption->setQueueName(Config::get(LogglyConstants::QUEUE_NAME));
 $queueOption->setDurable(true);

 return $queueOption;
 }

}
```

## QueueConfig

```php
<?php

namespace Pyz\Zed\Queue;

use Generated\Shared\Transfer\RabbitMqConsumerOptionTransfer;
use Spryker\Shared\Config\Config;
use Spryker\Shared\Event\EventConstants;
use Spryker\Zed\Queue\QueueConfig as SprykerQueueConfig;
use SprykerEco\Shared\Loggly\LogglyConstants;

class QueueConfig extends SprykerQueueConfig
{

 /**
 * @return array
 */
 protected function getQueueReceiverOptions()
 {
 return [
 Config::get(LogglyConstants::QUEUE_NAME) => [
 'rabbitmq' => $this->getRabbitMqQueueConsumerOptions(),
 ],
 ];
 }

 /**
 * @return \Generated\Shared\Transfer\RabbitMqConsumerOptionTransfer
 */
 protected function getRabbitMqQueueConsumerOptions()
 {
 $queueOptionTransfer = new RabbitMqConsumerOptionTransfer();
 $queueOptionTransfer->setConsumerExclusive(false);
 $queueOptionTransfer->setNoWait(false);

 return $queueOptionTransfer;
 }

}
```

## QueueDependencyProvider

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
 Config::get(LogglyConstants::QUEUE_NAME) => new LogglyLoggerQueueMessageProcessorPlugin(),
 ];
 }

}
```

For further information on this partner and integration into Spryker, please contact us.

<div class="hubspot-form js-hubspot-form" data-portal-id="2770802" data-form-id="163e11fb-e833-4638-86ae-a2ca4b929a41" id="hubspot-1"></div>
