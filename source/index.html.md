---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

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
curl "http://example.com/api/kittens/2" \
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
curl "http://example.com/api/kittens/2" \
  -X DELETE \
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

# Bind Credit Card
Bind credit card (POST)
## End Point
https://

## Request Header

## Body

```json
[
  {
      "transaction": {
          "credit_card": {
              "card_exp_date": "",
              "card_number": "",
              "card_holder_name": "",
          },
      },
  },
]
```
#### OMSRequest
| Name | Type | Description |
| ------ | ------ | ------ |
| transaction | `object` | transaction object refer to OMSTransaction |

#### OMSTransaction
| Name | Type | Description |
| ------ | ------ | ------ |
| credit_card | `object` | credit_card object refer to OMSTransactionCreditCard |

#### OMSTransactionCreditCard
| Name | Type | Description |
| ------ | ------ | ------ |
| card_exp_date | `string` | Card expiry date |
| card_number | `string` | Card number |
| card_holder_name | `string` | Card holder name |


## Success Response - data
| Name | Type | Description |
| ------ | ------ | ------ |
| transaction | `object` | transaction object refer to OMSTransaction |

#### OMSTransaction
| Name | Type | Description |
| ------ | ------ | ------ |
| uuid | `string` | UUID |
| credit_card_token | `object` | credit_card_token object refer to CreditCardToken |
| transaction_state | `string` | "success" |
| acquirer_type | `string` | Card acquirer |

#### CreditCardToken
| Name | Type | Description |
| ------ | ------ | ------ |
| token | `string` |  |

```go
{
    "transaction": {
        "uuid": "",
        "credit_card_token": {
            "token": "",
        },
        "transaction_state": "success",
        "acquirer_type": "",
    },
}
```

## Error Response - data
| Name | Type | Description |
| ------ | ------ | ------ |
| transaction | `object` | OMSTransaction |

#### OMSTransaction
| Name | Type | Description |
| ------ | ------ | ------ |
| error_code | `string` |  |
| error_desc | `string` |  |

```go
{
    "transaction": {
        "error_code": "",
        "error_desc": "",
    },
}
```

#### Possible Error Response
| error_code | error_desc | Description |
| ------ | ------ | ------ |
| 100400 | request parameter error |  |
| 100400 | transaction can't not be empty | No Transaction |
| 100400 | creditCard can't not be empty | Credit Card Number Error |
| 100400 | uuid can't not be empty |  |
| 100400 | card expData invalid | Card Expiry Date Error |
| 100400 | bind card fail |  |
