# Get all Customers

{% api-method method="get" host=" https://api.moltin.com" path="/v2/customers" %}
{% api-method-summary %}
Get a list of customers
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}

{% api-method-parameter name="X-Moltin-Customer-Token" type="string" required=false %}
A customer token to access specific customer orders.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="filter" type="string" required=false %}
Filter the results.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
    "data": [
        {
            "type": "customer",
            "id": "2479c9b3-615d-4ebc-a99d-87ffc67d1955",
            "name": "Ron Swanson",
            "email": "ron@swanson.com",
            "password": true
        },
        {
            "type": "customer",
            "id": "7746d533-fd64-446f-ae8c-f8e07f3ed9fd",
            "name": "Ron Swanson_",
            "email": "ron_@swanson.com",
            "password": true
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
```javascript
curl -X GET https://api.moltin.com/v2/customers \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'XXXX'
})

Moltin.Customers.All().then((customer) => {
  // Do something
});

//Filter example
Moltin.Customers.Filter({eq: {email: 'jim@bob.com'}}).All().then(customers => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

