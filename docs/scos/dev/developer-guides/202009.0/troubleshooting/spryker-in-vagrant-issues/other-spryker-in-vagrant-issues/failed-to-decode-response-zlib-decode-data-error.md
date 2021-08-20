---
title: Failed to decode response- zlib_decode()- data error
description: Learn how to fix the issue Failed to decode response- zlib_decode()- data error
originalLink: https://documentation.spryker.com/v6/docs/failed-to-decode-response-zlib-decode-data-error
originalArticleId: b9190c93-0453-42c7-bbcb-d3068d063ce1
redirect_from:
  - /v6/docs/failed-to-decode-response-zlib-decode-data-error
  - /v6/docs/en/failed-to-decode-response-zlib-decode-data-error
---

## Description
When running `composer install` or `composer update`, you might get the issue *Failed to decode response: zlib_decode(): data error* .

## Solution
Change the composer configuration by running `composer config -ge` in the terminal and replacing the configuration with the following one

```php
{
    "repositories": {
        "packagist": { "url": "https://packagist.org", "type": "composer" }
    }
}
```