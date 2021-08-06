---
title: Retrieving the Return Reasons
originalLink: https://documentation.spryker.com/v5/docs/retrieving-the-return-reasons
redirect_from:
  - /v5/docs/retrieving-the-return-reasons
  - /v5/docs/en/retrieving-the-return-reasons
---

To retrieve a list of predefined return reasons, send the request:
***
`GET` **/return-reasons**
***
## Request
Sample request:  `GET https://glue.mysprykershop.com/return-reasons`

## Response
Sample response: 
```json
{
    "data": [
        {
            "type": "return-reasons",
            "id": null,
            "attributes": {
                "reason": "Damaged"
            },
            "links": {
                "self": "https://glue.mysprykershop.com/return-reasons"
            }
        },
        {
            "type": "return-reasons",
            "id": null,
            "attributes": {
                "reason": "Wrong Item"
            },
            "links": {
                "self": "https://glue.mysprykershop.com/return-reasons"
            }
        },
        {
            "type": "return-reasons",
            "id": null,
            "attributes": {
                "reason": "No longer needed"
            },
            "links": {
                "self": "https://glue.mysprykershop.com/return-reasons"
            }
        }
    ],
    "links": {
        "self": "https://glue.mysprykershop.com/return-reasons"
    }
}
```

| Attribute* | Type | Description |
| --- | --- | --- |
| reason | String | Predefined return reason. |
/* The fields mentioned are all attributes in the response. Type and ID are not mentioned.
