---
title: Public Folder
description: To publish means to place the built assets in a place where they can be accessed and loaded by the browser. In the whole project, the only place with such access rights is the @project/public folder.
originalLink: https://documentation.spryker.com/v3/docs/public-folder
originalArticleId: add70c03-3265-4294-99a3-834c650d459b
redirect_from:
  - /v3/docs/public-folder
  - /v3/docs/en/public-folder
---

To publish means to place the built assets in a place where they can be accessed and loaded by the browser.

In the whole project, the only place with such access rights is the `@project/public` folder.

## Application Folders

* `@project/public/Yves`
* `@project/public/Zed`

These folders contain only application-related public files.

Each file is directly accessible from the browser by using the `/<filename>.<ext> path`.

{% info_block errorBox %}
Do not add any files here as they will not be accessible.
{% endinfo_block %}

Due to strict nginx configuration, only the content that already exists is public.

## Assets Dedicated Folders

* `@project/public/Yves/assets`
* `@project/public/Zed/assets`

These folders can contain any file that needs to be accessed and loaded by the browser. Contents can be addressed by using the `/assets/<path>/<filename>.<ext>` path. Assets must be placed here.

{% info_block infoBox "Yves Themes Folders" %}
To avoid conflicts and incorrect behaviour in Yves UI, create a subfolder (`@project/public/Yves/assets/<theme>`
{% endinfo_block %} for each theme you have in your project, and place the related files there.)