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
| `transaction-type` | `string` | The type of transaction \(`capture`, `authorize` or `refund`\) |
| `status` | `string` | The status provided by the gateway for this transaction. `complete` or `failed` |
| `relationships` | `object` | This will contain the order object this transaction relates to |
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
			"status": "complete",
			"relationships": {
				"order": {
					"data": {
						"type": "order",
						"id": "f6f63e5b-1e04-47aa-9213-993ead03d441"
					}
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
      "id": "150ce9ca-c3a8-4214-b4f9-509987054cf4",
      "type": "transaction",
      "reference": "manual",
      "gateway": "manual",
      "amount": 50000,
      "currency": "GBP",
      "transaction-type": "capture",
      "status": "complete",
      "relationships": {
        "order": {
          "data": {
            "type": "order",
            "id": "f7a70163-5878-48a8-97a3-1872178907aa"
          }
        }
      }
    },
    {
      "id": "1bcc324b-659c-40ba-81df-793f91298844",
      "type": "transaction",
      "reference": "",
      "gateway": "stripe",
      "amount": 50000,
      "currency": "GBP",
      "transaction-type": "purchase",
      "status": "failed",
      "relationships": {
        "order": {
          "data": {
            "type": "order",
            "id": "f7a70163-5878-48a8-97a3-1872178907aa"
          }
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
curl -X GET https://api.moltin.com/v2/inventories/:orderId/transactions \
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
Use this endpoint to capture a previously authorized payment. You will use this endpoint when you invoke the Manual Payments API.
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
        "transaction-type": "refund",
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

