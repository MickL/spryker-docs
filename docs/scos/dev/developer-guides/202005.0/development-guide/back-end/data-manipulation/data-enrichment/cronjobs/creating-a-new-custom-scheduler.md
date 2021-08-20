---
title: Creating a New Custom Scheduler
description: This tutorial describes how to create a new custom scheduler.
originalLink: https://documentation.spryker.com/v5/docs/ht-create-a-new-custom-scheduler
originalArticleId: 28caa06f-fdd6-4150-8d03-5324f8e5c6f9
redirect_from:
  - /v5/docs/ht-create-a-new-custom-scheduler
  - /v5/docs/en/ht-create-a-new-custom-scheduler
---

To create a new custom scheduler:

1. Create a reader plugin that reads configuration of jobs from the specific source.
2. Create an adapter plugin that covers the basic scheduler functionality.
3. Enable plugins in `\Pyz\Zed\Scheduler\SchedulerDependencyProvider` and adjust configuration settings according to your changes.


<!--*Last review date: Oct 29, 2019* by Oleksandr Myrnyi, Andrii Tserkovnyi-->

