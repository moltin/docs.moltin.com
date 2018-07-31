# Update Inventory

## Action types

| **Type** | **Description** |
| --- | --- |
| `increment` | You'll use this when you receive stock from a supplier, making products available for purchase |
| `decrement` | You'll use this when you want to remove stock from product inventory |
| `allocate` | You'll use this when you want to allocate stock, normally to a reseller who will sell on the stock |
| `deallocate` | You'll use this when you want to deallocate any previously allocated stock |

{% api-method method="post" host="https://api.moltin.com" path="/v2/inventories/:productId/transactions" %}
{% api-method-summary %}
Create a Stock Transaction for a Product
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** for the product you're performing this action on
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="quantity" type="integer" required=true %}
The amount of stock affected by this transaction
{% endapi-method-parameter %}

{% api-method-parameter name="action" type="string" required=true %}
`increment`, `decrement`, `allocate`, `deallocate`
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Always  `stock-transaction`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
You will get the response below for any of the `action` types.
{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "da9a0008-d2c4-4a17-bbc6-5e0b2f9430aa",
    "type": "stock-transaction",
    "action": "increment",
    "product_id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
    "quantity": 10,
    "timestamps": {
      "created_at": "2018-05-01 10:10:57 +0000 UTC"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
You will get an error if you try to perform an action with incorrect amounts
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "status": 422,
      "title": "Cannot complete request",
      "detail":
        "Your request could not be completed due to insufficient stock levels"
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
curl -X POST https://api.moltin.com/v2/inventories/{PRODUCT_ID}/transactions \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
         "type": "stock-transaction",
         "action": "increment",
         "quantity": 3
       }
     }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const productId = 'XXXX'
const quantity = 10

Moltin.Inventories.IncrementStock(productId, quantity).then(transaction => {
  // Do something
})

Moltin.Inventories.DecrementStock(productId, quantity).then(transaction => {
  // Do something
})

Moltin.Inventories.AllocateStock(productId, quantity).then(transaction => {
  // Do something
})

Moltin.Inventories.DeallocateStock(productId, quantity).then(transaction => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

