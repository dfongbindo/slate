# Bind Credit Card
Bind credit card (POST)
## End Point
https://

## Request Header

## Body
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

```go
{
    "transaction": {
        "credit_card": {
            "card_exp_date": "",
            "card_number": "",
            "card_holder_name": "",
        },
    },
}
```

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
