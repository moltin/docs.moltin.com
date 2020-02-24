# Transactions

### The transaction object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The ID of the transaction |
| `type` | `string` | Always transaction |
| `reference` | `string` | The payment gateway reference |
| `gateway` | `string` | The name of the payment gateway used |
| `amount` | `integer` | The amount for this transaction |
| `currency` | `string` | The transaction currency |
| `transaction_type` | string | The type of transaction \(`purchase`,`capture`, `authorize` or `refund`\) |
| `status` | string | The status provided by the gateway for this transaction. `complete` or `failed` |
| `relationships` | object | This will contain the order object this transaction relates to |
| `timestamps` | object | Contains the `created_at` and `updated_at` properties |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
	"data": [
		{
			"id": "03f634c3-9c70-4aa1-8178-f7d41a45d92z",
			"type": "transaction",
			"reference": "ch_1CVFEDCTrBHFHIc3NNG6EaFU",
			"gateway": "stripe",
			"amount": 40000,
			"currency": "USD",
			"transaction-type": "purchase",
			"transaction_type": "purchase",
			"status": "complete",
			"relationships": {
				"order": {
					"data": {
						"type": "order",
						"id": "f6f63e5b-1e04-47aa-9213-993ead03d441"
					}
				}
			},
			"meta": {
				"display_price": {
		        	"amount": 40000,
			        "currency": "USD",
			        "formatted": "$400.00"
				},
				"created_at": "2019-06-24T13:14:21.913Z",
				"timestamps": {
					"created_at": "2019-06-24T13:14:21.913Z",
					"updated_at": "2019-06-24T13:14:21.913Z"
				}
			}
		}
	]
}
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/orders/:orderId/transactions" %}
{% api-method-summary %}
Get all transactions
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="orderId" type="string" required=true %}
The UUID of the order you require transactions for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": [
        {
            "id": "015a3452-29a2-45b4-8b0d-0d697b224d45",
            "type": "transaction",
            "reference": "manual",
            "gateway": "manual",
            "amount": 19000,
            "currency": "USD",
            "transaction_type": "capture",
            "status": "complete",
            "relationships": {
                "order": {
                    "data": {
                        "type": "order",
                        "id": "24f17926-af4b-439c-ae3c-13aa371bce77"
                    }
                }
            },
            "meta": {
                "display_price": {
                    "amount": 19000,
                    "currency": "USD",
                    "formatted": "$190.00"
                },
				"timestamps": {
					"created_at": "2018-12-17T16:19:53.379Z",
					"updated_at": "2018-12-17T16:19:53.379Z"
				}
            }
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/orders/:orderId/transactions \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const id = 'XXXX'

Moltin.Orders.Transactions(id).then(transactions => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Authorize payment
{% endapi-method-summary %}

{% api-method-description %}
This endpoint is for those who wish to authorize payments using the manual gateway.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="orderId" type="string" required=true %}
The UUID of the order you wish to authorize payment for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="method" type="string" required=true %}
Payment method to use
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
The type of gateway to use
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/orders/:orderId/payments \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
         "gateway": "manual",
         "method": "authorize"
       }
     }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const orderId = 'XXXX'

Moltin.Orders.Payment(orderId, {
  gateway: 'manual',
  method: 'authorize'
}).then(() => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/transactions/:transactionId/capture" %}
{% api-method-summary %}
Capture payment
{% endapi-method-summary %}

{% api-method-description %}
Use this endpoint to capture a previously authorized payment. You will use this endpoint when you invoke the Manual Payments API. In this step you can also pass in a custom reference, such as the payment reference from your chosen gateway.  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="transactionId" type="string" required=true %}
The UUID of the transaction to capture
{% endapi-method-parameter %}

{% api-method-parameter name="orderId" type="string" required=true %}
The UUID of the order
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="custom\_reference" type="string" required=false %}
A custom reference you can use to identify this transaction
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "data": {
        "id": "bcafac29-c8ca-4293-822c-d1213e085c7c",
        "type": "transaction",
        "reference": "manual",
        "custom_reference": "my_custom_reference",
        "gateway": "manual",
        "amount": 60000,
        "currency": "GBP",
        "transaction_type": "capture",
        "status": "complete",
        "relationships": {
            "order": {
                "data": {
                    "type": "order",
                    "id": "239f104c-0b56-433c-a5f8-b73349196269"
                }
            }
        },
        "meta": {
            "display_price": {
                "amount": 60000,
                "currency": "GBP",
                "formatted": "£600.00"
            },
            "timestamps": {
                "created_at": "2020-02-17T13:24:42Z",
                "updated_at": "2020-02-17T13:24:45Z"
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/orders/:orderId/transactions/:transaction_id/capture \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/transactions/:transactionId/refund" %}
{% api-method-summary %}
Refund payment
{% endapi-method-summary %}

{% api-method-description %}
You can mark a transaction as refunded. You will need to handle the actual refund on your side with your payment provider.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="transactionId" type="string" required=true %}
The UUID of the transaction you wish to refund
{% endapi-method-parameter %}

{% api-method-parameter name="orderId" type="string" required=true %}
The UUID of the order
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```bash
{
    "data": {
        "id": "78cf43c3-b8fa-4b84-9444-d2adf81ed8bd",
        "type": "transaction",
        "reference": "manual",
        "gateway": "manual",
        "amount": 59992,
        "currency": "USD",
        "transaction_type": "refund",
        "status": "complete",
        "relationships": {
            "order": {
                "data": {
                    "type": "order",
                    "id": "a15894b0-7e6c-49e8-aad0-85b92e6501d4"
                }
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="warning" %}
You will need to handle the actual refund with your payment provider
{% endhint %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/orders/:orderId/transactions/:transactionId/refund \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/transactions/:transactionId/confirm" %}
{% api-method-summary %}
Confirm payment intent
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="transactionId" type="string" required=true %}
ID of the transaction you want to confirm
{% endapi-method-parameter %}

{% api-method-parameter name="orderId" type="string" required=true %}
ID of the order
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="payment" type="string" required=true %}
Payment method or source
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
`purchase`
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`stripe_payment_intents`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "b07c45c7-cd6d-466b-9ed9-bf44dd80696f",
        "type": "transaction",
        "reference": "pi_1FCnB5CTrBHFHKc35eHmhqnF",
        "gateway": "stripe_payment_intents",
        "amount": 5499,
        "currency": "USD",
        "transaction_type": "purchase",
        "status": "complete",
        "payment_intent": {
            "client_secret": "pi_1FCnB5CTrBHFHKc35eHmhqnF_secret_netgkKN9Cs9U4P98BG1T6esPa",
            "status": "requires_action"
        },
        "relationships": {
            "order": {
                "data": {
                    "type": "order",
                    "id": "a37e7229-3539-4acb-95b9-9705da42d20e"
                }
            }
        },
        "meta": {
            "display_price": {
                "amount": 5499,
                "currency": "USD",
                "formatted": "$54.99"
            },
            "timestamps": {
                "created_at": "2019-08-29T12:56:39Z",
                "updated_at": "2019-08-29T12:56:43Z"
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/orders/:orderId/transactions/:transactionId/confirm \
     -H "Authorization: Bearer XXXX" \
     -d $'{
        "data": {
          "gateway": "stripe_payment_intents",
          "method": "purchase",
          "payment": "pm_card_threeDSecureRequired"
        }
      }'
```
{% endtab %}
{% endtabs %}

