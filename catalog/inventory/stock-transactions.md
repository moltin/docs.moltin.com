# Stock Transactions

Each product has its own Inventory and stock history. This is useful when auditing product movements across your project. Below is the Stock Transaction object, request and response examples for getting all stock transactions by Product ID.

## The Stock Transaction Object

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for the stock transaction |
| `type` | `string` | The type represents the object being returned |
| `action` | `string` | The type of [action](update-inventory.md#action-types) performed by this transaction |
| `product_id` | `string` | The product identifier that this stock transaction is for |
| `quantity` | `integer` | The amount of stock affected by the stock transaction |

{% api-method method="get" host="https://api.moltin.com" path="/v2/inventories/:productId/transactions" %}
{% api-method-summary %}
Get All Product Stock Transactions
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
You will see inside the response below you get all stock transactions, including the initial stock amount on product create.
{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "id": "0b0e5be3-b88b-4574-8316-f2871a803a8a",
      "type": "stock-transaction",
      "action": "create",
      "product_id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
      "quantity": 1,
      "timestamps": {
        "created_at": "2018-02-05 14:00:11 +0000 UTC"
      }
    },
    {
      "id": "4638fc99-faec-416c-94e0-c3e0d11af436",
      "type": "stock-transaction",
      "action": "increment",
      "product_id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
      "quantity": 1,
      "timestamps": {
        "created_at": "2018-03-07 14:34:32 +0000 UTC"
      }
    },
    {
      "id": "2edaa5f6-45fe-4272-96d4-3c745f80c26d",
      "type": "stock-transaction",
      "action": "decrement",
      "product_id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
      "quantity": 1,
      "timestamps": {
        "created_at": "2018-03-07 14:44:21 +0000 UTC"
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
curl -X GET https://api.moltin.com/v2/inventories/:productId/transactions \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const productId = 'XXXX'

Moltin.Inventories.GetTransactions(productId).then(transactions => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { MoltinClient } = require('@moltin/request')
​
const client = new MoltinClient({
  client_id: 'X'
})

const productId = 'XXXX'​

client
  .get(`inventories/${productId}/transactions`)
  .then(inventory => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}
{% endtabs %}

