---
title: Migration Guide - Transfer
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v2/docs/mg-transfer
originalArticleId: 2961be56-93b9-4f91-b7c6-690e85498edf
redirect_from:
  - /v2/docs/mg-transfer
  - /v2/docs/en/mg-transfer
---

## Upgrading from Version 2.* to Version 3.*

When upgrading to the new major version of the `Transfer` module, it is necessary to make sure that everywhere the `$foo->fromArray($bar->toArray())` statement is used and the types are matching. 

From now on we are no longer silently ignoring when you try to set a string to an array field and an exception is getting thrown instead.

A concrete example is product attributes; they are stored as a `json` string and are expected to be an array in transfer objects. In this case, we need to make sure that the value of the attributes in the source array are converted to an array which is expected by the target transfer.
