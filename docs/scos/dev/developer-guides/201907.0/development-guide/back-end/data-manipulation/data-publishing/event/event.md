---
title: Event
originalLink: https://documentation.spryker.com/v3/docs/event
originalArticleId: f8ea487f-f881-4d0d-a6b8-c14081e287fb
redirect_from:
  - /v3/docs/event
  - /v3/docs/en/event
---

The Event module implements an Observer pattern where you can add hooks (events) to your code and allow other modules to listen and react to those events.

There are two methods:

1. Traditional Synchronous where listeners are handled at the same time as they are dispatched
2. Asynchronous (Queueable) where events are put into a queue and handled later by some queue service.