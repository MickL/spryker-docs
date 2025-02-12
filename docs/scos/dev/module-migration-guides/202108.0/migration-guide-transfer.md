---
title: Migration Guide - Transfer
description: Use the guide to learn how to update the Transfer module to a newer version.
last_updated: Jun 16, 2021
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/2021080/docs/mg-transfer
originalArticleId: 49dc6ee6-a3da-465f-96e7-281db0d4575a
redirect_from:
  - /2021080/docs/mg-transfer
  - /2021080/docs/en/mg-transfer
  - /docs/mg-transfer
  - /docs/en/mg-transfer
---

## Upgrading from Version 2.* to Version 3.*

When upgrading to the new major version of the `Transfer` module, it is necessary to make sure that everywhere the `$foo->fromArray($bar->toArray())` statement is used and the types are matching. 

From now on we are no longer silently ignoring when you try to set a string to an array field and an exception is getting thrown instead.

A concrete example is product attributes; they are stored as a `json` string and are expected to be an array in transfer objects. In this case, we need to make sure that the value of the attributes in the source array are converted to an array which is expected by the target transfer.
