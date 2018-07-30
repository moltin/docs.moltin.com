# Get a Product's Stock

{% api-method method="get" host="https://api.moltin.com" path="/v2/inventories/:productId" %}
{% api-method-summary %}
Get All Stock by Product ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** for the product you require stock
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
You will get the following response when you perform any of the
{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
    "type": "stock",
    "total": 20,
    "available": 20,
    "allocated": 0
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
curl -X GET https://api.moltin.com/v2/inventories/:productId \
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

Moltin.Inventories.Get(productId).then(inventories => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

