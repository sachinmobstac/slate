---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

The Beaconstac API is organized around [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Our API has predictable resource-oriented URLs, accepts [form-encoded](https://en.wikipedia.org/wiki/POST_(HTTP)#Use_for_submitting_web_forms) request bodies, returns [JSON-encoded](http://www.json.org/) responses, and uses standard HTTP response codes, authentication, and verbs.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://beaconstac.mobstac.com/api/2.0/"
  -H "Authorization: Token YOUR_TOKEN"
```

> Make sure to replace `YOUR_TOKEN` with your API key.

The Beaconstac API uses API key to authenticate requests.

Your API key carry many privileges, so be sure to keep them secure! Do not share your secret API keys in publicly accessible areas such as GitHub, client-side code, and so forth.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.

You can find your developer token by using the following steps.

1. Login to the [Beaconstac dashboard](https://dashboard.beaconstac.com/).
2. Go to your 'Account' section using the drop-down on the top-right.
3. In the 'Account Details' section, copy the 'Developer Token' value.

![Account Page](https://github.com/Beaconstac/api/blob/master/images/account_page.png)

Beaconstac expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token YOUR_TOKEN`

<aside class="notice">
You must replace <code>YOUR_TOKEN</code> with your personal API key.
</aside>

# Beaconstac

## Beacons

### Get all beacons

```shell
curl "https://beaconstac.mobstac.com/api/2.0/beacons/"
  -H "Authorization: Token YOUR_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "count": 2,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": 8072,
      "meta": {
        "hardware_type": 1
      },
      "deployment_meta": {},
      "kit_type": {
        "types": [
          "AK",
          "SK"
        ]
      },
      "place_data": {
        "id": 8361,
        "name": "KIA Bengaluru"
      },
      "tag_data": [],
      "campaign": {
        "id": 3335,
        "name": "Ola - Scooter taxi",
        "custom_url": "https://www.tiny.cc/gmymry",
        "content_type": 2,
        "campaign_active": true,
        "created": "2017-09-01T05:22:20.318082Z",
        "updated": "2019-05-28T08:43:13.826580Z",
        "organization": 1697,
        "markdown_card": 9572,
        "form": 12406,
        "schedule": 28
      },
      "proximity_status": 0,
      "eddystone_url": "https://eddy.pro/vLkeTm",
      "name": "0117C5978008",
      "url": "https://eddy.pro/vLkeTm",
      "state": "A",
      "heartbeat": "2019-06-24T06:19:24.245871Z",
      "created": "2017-09-01T05:22:19.967161Z",
      "updated": "2019-06-24T06:19:24.246013Z",
      "UUID": "F94DBB23-2266-7822-3782-57BEAC0952AC",
      "major": 58460,
      "minor": 21851,
      "latitude": 12.9818683,
      "longitude": 77.6404922,
      "temperature": 19,
      "battery": 99,
      "advertising_interval": 211,
      "tx_power": 4,
      "mode": "IL",
      "serial_number": "0117C5978008",
      "eddystone_nid": "5DC33487F02E477D4058",
      "eddystone_bid": "0117C5978008",
      "closeby_id": 731031,
      "nearby_id": "beacons/3!5dc33487f02e477d40580117c5978008",
      "organization": 1697,
      "place": 8361,
      "tags": []
    },
    {
      "id": 20017,
      "meta": {
        "hardware_type": 4
      },
      "deployment_meta": {},
      "kit_type": {
        "types": [
          "AK",
          "SK"
        ]
      },
      "place_data": {
        "id": 2888,
        "name": "Times Square"
      },
      "tag_data": [
        {
          "id": 1076,
          "name": "Footwear"
        }
      ],
      "campaign": {
        "id": 14395,
        "name": "Vipin Schedule Test",
        "custom_url": "https://www.google.com",
        "content_type": 4,
        "campaign_active": true,
        "created": "2018-09-17T07:29:28.674926Z",
        "updated": "2019-04-18T09:49:37.916926Z",
        "organization": 1697,
        "markdown_card": 10790,
        "form": 11805,
        "schedule": 4586
      },
      "proximity_status": 0,
      "eddystone_url": "https://eddy.pro/uREvlU",
      "name": "AC233F25A31B",
      "url": "https://eddy.pro/uREvlU",
      "state": "A",
      "heartbeat": "2019-06-24T06:11:59.475411Z",
      "created": "2018-09-17T07:29:28.649751Z",
      "updated": "2019-06-24T06:11:59.475541Z",
      "UUID": "F94DBB23-2266-7822-3782-57BEAC0952AC",
      "major": 46468,
      "minor": 13497,
      "latitude": 40.758895,
      "longitude": -73.985131,
      "temperature": 22,
      "battery": 100,
      "advertising_interval": 200,
      "tx_power": -8,
      "mode": "IL",
      "serial_number": "AC233F25A31B",
      "eddystone_nid": "5DC33487F02E477D4058",
      "eddystone_bid": "AC233F25A31B",
      "closeby_id": 16278664,
      "nearby_id": "beacons/3!5dc33487f02e477d4058ac233f25a31b",
      "organization": 1697,
      "place": 2888,
      "tags": [
        1076
      ]
    }
  ]
}
```

Returns a list of your beacons. The beacons are returned sorted by beacon heartbeat, with the most recent detected beacons appearing first.

Filter arguments:

1. `name`: `exact`, `icontains`
2. `serial_number`:  `exact`, `icontains`
3. `place__name`: `exact`, `icontains`
4. `tags__name`: `exact`, `icontains`
5. `url`: `exact`
6. `heartbeat`: `lt`, `lte`, `gt`, `gte`
7. `campaign__content_type`: `exact` 
8. `state`: `exact`

Search Fields:

1. `name`
2. `serial_number`
3. `place__name`
4. `tags__name`
5. `url`
6. `campaign__content_type`

Ordering fields:

1. `name`
2. `serial_number`
3. `battery`
4. `heartbeat`: default
5. `place__name`
6. `created`
7. `updated`
8. `campaign__content_type`
9. `state`

### Retrieve a beacon

`GET https://beaconstac.mobstac.com/api/2.0/beacons/{beacon_id}`

```shell
curl "https://beaconstac.mobstac.com/api/2.0/beacons/{beacon_id}"
  -H "Authorization: Token YOUR_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "id": 15646,
  "meta": {
    "hardware_type": 3
  },
  "place_data": {
    "id": 7466,
    "name": "Times Square"
  },
  "tag_data": [],
  "campaign": {
    "id": 10130,
    "name": "Half Price, Happy Hour",
    "custom_url": "https://www.google.com",
    "content_type": 2,
    "campaign_active": true,
    "created": "2018-06-01T10:47:21.785384Z",
    "updated": "2019-06-05T20:39:35.266185Z",
    "organization": 3935,
    "markdown_card": 11653,
    "form": 12422,
    "schedule": 4399
  },
  "deployment_meta": {},
  "kit_type": {
    "types": [
      "AK",
      "SK"
    ]
  },
  "rules": [],
  "rule_data": [],
  "notifications": [
    {
      "id": 1323950,
      "meta": {
        "closeby": {},
        "nearby": {}
      },
      "title": "轉數快：隨時隨地，跨行即時過數！",
      "description": null,
      "icon_url": "https://d1bqobzsowu5wu.cloudfront.net/3568/a7fbe7d8f0d84595ac0dfa75c31f9a08",
      "banner_type": 1,
      "banner_image_url": null,
      "app_intent": null,
      "is_default": false,
      "slug": "轉數快隨時隨地跨行即時過數",
      "created": "2018-09-17T10:15:33.082052Z",
      "updated": "2019-05-02T11:48:55.626906Z",
      "language_code": "en"
    },
    {
      "id": 1383027,
      "meta": {
        "closeby": {},
        "nearby": {}
      },
      "title": "轉數快：隨時隨地，跨行即時過數！",
      "description": "",
      "icon_url": "https://d1bqobzsowu5wu.cloudfront.net/3568/a7fbe7d8f0d84595ac0dfa75c31f9a08",
      "banner_type": 1,
      "banner_image_url": null,
      "app_intent": null,
      "is_default": true,
      "slug": "轉數快隨時隨地跨行即時過數",
      "created": "2018-10-30T08:12:21.938128Z",
      "updated": "2019-05-02T11:48:55.640839Z",
      "language_code": "zh"
    }
  ],
  "proximity_status": 0,
  "eddystone_url": "https://eddy.pro/CKEc5X",
  "name": "The Coffeeshop",
  "url": "https://eddy.pro/CKEc5X",
  "state": "A",
  "heartbeat": "2018-09-17T10:15:59.184415Z",
  "created": "2018-06-01T10:47:21.744035Z",
  "updated": "2019-06-05T20:39:35.299706Z",
  "UUID": "F94DBB23-2266-7822-3782-57BEAC0952AC",
  "major": 54222,
  "minor": 60051,
  "latitude": null,
  "longitude": null,
  "temperature": 0,
  "battery": 0,
  "advertising_interval": 200,
  "tx_power": -8,
  "mode": "IL",
  "serial_number": "AC233F251546",
  "eddystone_nid": "5DC33487F02E477D4058",
  "eddystone_bid": "AC233F251546",
  "closeby_id": 11348073,
  "nearby_id": "beacons/3!5dc33487f02e477d4058ac233f251546",
  "organization": 3935,
  "place": 7466,
  "tags": []
}
```

Retrieves the details of an existing beacon. You need only supply the unique beacon identifier that was returned upon beacon listing

### Update Beacon

`PUT https://beaconstac.mobstac.com/api/2.0/beacons/{beacon_id}`

```shell
curl "https://beaconstac.mobstac.com/api/2.0/beacons/{beacon_id}"
  -X PUT
  -H "Authorization: Token YOUR_TOKEN"
  -d "{"id":beacon_id, "campaign":{"id":10130}}"
```

> The above command returns JSON structured like this:

```json
{
  "id": 15646,
  "meta": {
    "hardware_type": 3
  },
  "place_data": {
    "id": 7466,
    "name": "Times Square"
  },
  "tag_data": [],
  "campaign": {
    "id": 10130,
    "name": "Customer satisfaction survey",
    "custom_url": "https://www.google.com",
    "content_type": 3,
    "campaign_active": true,
    "created": "2018-06-01T10:47:21.785384Z",
    "updated": "2019-06-24T08:47:29.158541Z",
    "organization": 3935,
    "markdown_card": 11653,
    "form": 12422,
    "schedule": 4399
  },
  "deployment_meta": {},
  "kit_type": {
    "types": [
      "AK",
      "SK"
    ]
  },
  "rules": [],
  "rule_data": [],
  "notifications": [
    {
      "id": 1323950,
      "meta": {
        "closeby": {},
        "nearby": {}
      },
      "title": "轉數快：隨時隨地，跨行即時過數！",
      "description": null,
      "icon_url": "https://d1bqobzsowu5wu.cloudfront.net/3568/a7fbe7d8f0d84595ac0dfa75c31f9a08",
      "banner_type": 1,
      "banner_image_url": null,
      "app_intent": null,
      "is_default": false,
      "slug": "轉數快隨時隨地跨行即時過數",
      "created": "2018-09-17T10:15:33.082052Z",
      "updated": "2019-06-24T08:47:29.139565Z",
      "language_code": "en"
    },
    {
      "id": 1383027,
      "meta": {
        "closeby": {},
        "nearby": {}
      },
      "title": "轉數快：隨時隨地，跨行即時過數！",
      "description": "",
      "icon_url": "https://d1bqobzsowu5wu.cloudfront.net/3568/a7fbe7d8f0d84595ac0dfa75c31f9a08",
      "banner_type": 1,
      "banner_image_url": null,
      "app_intent": null,
      "is_default": true,
      "slug": "轉數快隨時隨地跨行即時過數",
      "created": "2018-10-30T08:12:21.938128Z",
      "updated": "2019-06-24T08:47:29.152753Z",
      "language_code": "zh"
    }
  ],
  "proximity_status": 0,
  "eddystone_url": "https://eddy.pro/CKEc5X",
  "name": "The Coffeeshop",
  "url": "https://eddy.pro/CKEc5X",
  "state": "A",
  "heartbeat": "2018-09-17T10:15:59.184415Z",
  "created": "2018-06-01T10:47:21.744035Z",
  "updated": "2019-06-24T08:47:29.095082Z",
  "UUID": "F94DBB23-2266-7822-3782-57BEAC0952AC",
  "major": 54222,
  "minor": 60051,
  "latitude": null,
  "longitude": null,
  "temperature": 0,
  "battery": 0,
  "advertising_interval": 200,
  "tx_power": -8,
  "mode": "IL",
  "serial_number": "AC233F251546",
  "eddystone_nid": "5DC33487F02E477D4058",
  "eddystone_bid": "AC233F251546",
  "closeby_id": 11348073,
  "nearby_id": "beacons/3!5dc33487f02e477d4058ac233f251546",
  "organization": 3935,
  "place": 7466,
  "tags": []
}
```


Updates the specified beacon by setting the values of the parameters passed. Any parameters not provided will be left unchanged. However, the request should contain the required fields. Please refer to the Beacon object.

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

