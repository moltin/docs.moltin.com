# Get all Orders

{% api-method method="get" host="https://api.moltin.com" path="/v2/orders" %}
{% api-method-summary %}
Get all Orders
{% endapi-method-summary %}

{% api-method-description %}
Getting all orders will return your orders with custom flow fields.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Customer-Token" type="string" required=false %}
A customer token to access specific customer orders
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="include" type="string" required=false %}
`items`
{% endapi-method-parameter %}

{% api-method-parameter name="filter" type="string" required=false %}
Filter attributes
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
      "type": "order",
      "id": "369ad4a4-ee67-48b0-x347-t50a6e61d83d",
      "status": "incomplete",
      "payment": "unpaid",
      "shipping": "unfulfilled",
      "customer": {
        "name": "Mr John Doe",
        "email": "johndoe@example.com"
      },
      "shipping_address": {
        "first_name": "John",
        "last_name": "Doe",
        "phone_number": "",
        "company_name": "",
        "line_1": "2nd Floor British India House",
        "line_2": "15 Carliol Square",
        "city": "Newcastle Upon Tyne",
        "postcode": "NE1 6UF",
        "county": "Tyne & Wear",
        "country": "United Kingdom",
        "instructions": ""
      },
      "billing_address": {
        "first_name": "John",
        "last_name": "Doe",
        "company_name": "",
        "line_1": "2nd Floor British India House",
        "line_2": "15 Carliol Square",
        "city": "Newcastle Upon Tyne",
        "postcode": "NE1 6UF",
        "county": "Tyne & Wear",
        "country": "United Kingdom"
      },
      "links": {},
      "meta": {
        "display_price": {
          "with_tax": {
            "amount": 217500,
            "currency": "USD",
            "formatted": "$2175.00"
          },
          "without_tax": {
            "amount": 217500,
            "currency": "USD",
            "formatted": "$2175.00"
          }
        },
        "timestamps": {
          "created_at": "2018-04-16T10:11:59.715Z",
          "updated_at": "2018-04-16T10:11:59.715Z"
        }
      },
      "relationships": {
        "items": {
          "data": [
            {
              "type": "item",
              "id": "de9fddf5-011b-4485-abf8-ebb8f53c39ff"
            }
          ]
        }
      }
    }
  ],
  "links": {
    "current":
      "https://api.moltin.com/v2/orders?page[offset]=0&page[limit]=50&filter=",
    "first":
      "https://api.moltin.com/v2/orders?page[offset]=0&page[limit]=50&filter=",
    "last":
      "https://api.moltin.com/v2/orders?page[offset]=600&page[limit]=50&filter=",
    "prev":
      "https://api.moltin.com/v2/orders?page[offset]=0&page[limit]=50&filter=",
    "next":
      "https://api.moltin.com/v2/orders?page[offset]=50&page[limit]=50&filter="
  },
  "meta": {
    "page": {
      "limit": 100,
      "offset": 0,
      "current": 1,
      "total": 1
    },
    "results": {
      "total": 100
    }
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
Pass the `X-Moltin-Customer-Token` header to limit orders to a specific customer. [Read more](../customers/customer-tokens.md).
{% endhint %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/orders \
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

Moltin.Orders.All().then(orders => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

