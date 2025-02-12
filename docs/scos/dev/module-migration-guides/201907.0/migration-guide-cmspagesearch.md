---
title: Migration Guide - CmsPageSearch
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/mg-cmspagesearch
originalArticleId: c63eeace-aabe-4dfe-8039-0e7b5d0a3cbf
redirect_from:
  - /v3/docs/mg-cmspagesearch
  - /v3/docs/en/mg-cmspagesearch
---

## Upgrading from Version 1.* to Version 2.*
Version 2.0.0 of the CmsPageSearch module introduces the [multi-store functionality](https://documentation.spryker.com/v3/docs/cms-pages-overview). The multi-store CMS page feature enables management of CMS page display per store via a store toggle control in the Back Office.

To avoid the BC break, a synchronization behavior must be removed.

**To upgrade to the new version of the module, do the following:**
1. Update `cms-page-search` to `^2.0.0` with the command: `composer update spryker/cms-page-search:^2.0.0`
2. Remove `queue_pool=synchronizationPool` behavior from the `spy_cms_page_search` table.
`src/Pyz/Zed/CmsPageSearch/Persistence/Propel/Schema/spy_cms_page_search.schema.xml<behavior name="synchronization"><parameter name="queue_pool" value="synchronizationPool" /></behavior>`
{% info_block infoBox %}
When completed, the above synchronization parameter should not be in the file.
{% endinfo_block %}
3. Apply the database changes:
`$ console propel:install`
4. Generate new transfers:
`$ console transfer:generate`
_Estimated migration time: 30 minutes_

<!-- Last review date: Mar 12, 2019- by Alexander Veselov, Yuliia Boiko -->
