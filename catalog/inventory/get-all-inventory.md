# Get All Inventory

{% api-method method="get" host="https://api.moltin.com" path="/v2/inventories" %}
{% api-method-summary %}
Get Stock for All Products
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="page\[limit\]" type="string" required=false %}
The number of items to return per page
{% endapi-method-parameter %}

{% api-method-parameter name="page\[offset\]" type="string" required=false %}
The number of pages to offset the results by
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "id": "95ff4acc-9d8e-4a8e-be3a-61b174b20c2b",
      "type": "stock",
      "total": 100,
      "available": 100,
      "allocated": 0
    },
    {
      "id": "db33dc42-6a08-4929-8e85-8e1ea619c832",
      "type": "stock",
      "total": 100,
      "available": 100,
      "allocated": 0
    },
    {
      "id": "721fcb79-37d9-4328-b69d-bab7b73d7770",
      "type": "stock",
      "total": 100,
      "available": 100,
      "allocated": 0
    }
  ],
  "links": {
    "current":
      "https://api.moltin.com/v2/inventories?page[offset]=0&page[limit]=50",
    "first":
      "https://api.moltin.com/v2/inventories?page[offset]=0&page[limit]=50",
    "last":
      "https://api.moltin.com/v2/inventories?page[offset]=0&page[limit]=50"
  },
  "meta": {
    "results": {
      "total": 3,
      "all": 3
    },
    "page": {
      "limit": 100,
      "offset": 0,
      "current": 1,
      "total": 1
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
curl -X GET https://api.moltin.com/v2/inventories \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Inventories.All().then(inventories => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { createClient } = require('@moltin/request')
​
const client = new createClient({
  client_id: 'X'
})
​
client
  .get('inventories')
  .then(inventories => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}
{% endtabs %}

