---
title: Migration Guide - PriceProductScheduleGui
originalLink: https://documentation.spryker.com/v4/docs/mg-price-product-schedule-gui
redirect_from:
  - /v4/docs/mg-price-product-schedule-gui
  - /v4/docs/en/mg-price-product-schedule-gui
---

## Upgrading from Version 1.* to Version 2.0.0

1. Upgrade the **PriceProductScheduleGui** module to version 2.0.0:

```bash
composer require spryker/price-product-schedule-gui: "^2.0.0" --update-with-dependencies
```

2. Generate transfers:

```bash
console transfer:generate
```

*Estimated migration time: 5 minutes*