# Customer Tokens

We provide a basic `/tokens` endpoint that allows you authenticate customers by `email` and `password` so you can easily allow customers to manage their [addresses](../addresses/) or [get orders](../orders/get-all-orders.md) by `customer`.

## The customer token object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this otken |
| `type` | `string` | The type represents the object being returned |
| `customer_id` | `string` | The **ID** of the customer from which the token is generated |
| `token` | `string` | The JSON Web Token to be used for other endpoints |
| `expires` | `timestamp` | The epoch time that this token expires at |
{% endtab %}

{% tab title="Sample Response" %}
```javascript
{
  "data": {
    "type": "token",
    "id": "36f05940-0d38-411a-8909-3aea58bc1f09",
    "customer_id": "79cc0486-bbdf-491b-a0a2-722383b6288b",
    "token": "eyJhbGciOiAiSFMyNTYiLCAidHlwIjogIkpXVCJ9.eyJzdWIiOiI3OWNjMDQ4Ni1iYmRmLTQ5MWItYTBhMi03MjIzODNiNjI4OGIiLCJuYW1lIjoiUm9uIFN3YW5zb24iLCJleHAiOjE1MTA2ODQyMDAsImlhdCI6MTUxMDU5NzgwMCwianRpIjoiMzZmMDU5NDAtMGQzOC00MTFhLTg5MDktM2FlYTU4YmMxZjA5In0=.ea948e346d0683803aa4a2c09441bcbf7c79bd9234bed2ce8456ab3af257ea9f",
    "expires": 1510684200
  }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/customers/tokens" %}
{% api-method-summary %}
Generate a token
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

{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=true %}
The customer password
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}
The customer email
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
This must be `token`
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
    "type": "token",
    "id": "36f05940-0d38-411a-8909-3aea58bc1f09",
    "customer_id": "79cc0486-bbdf-491b-a0a2-722383b6288b",
    "token": "eyJhbGciOiAiSFMyNTYiLCAidHlwIjogIkpXVCJ9.eyJzdWIiOiI3OWNjMDQ4Ni1iYmRmLTQ5MWItYTBhMi03MjIzODNiNjI4OGIiLCJuYW1lIjoiUm9uIFN3YW5zb24iLCJleHAiOjE1MTA2ODQyMDAsImlhdCI6MTUxMDU5NzgwMCwianRpIjoiMzZmMDU5NDAtMGQzOC00MTFhLTg5MDktM2FlYTU4YmMxZjA5In0=.ea948e346d0683803aa4a2c09441bcbf7c79bd9234bed2ce8456ab3af257ea9f",
    "expires": 1510684200
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
curl -X POST https://api.moltin.com/v2/customers/tokens \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
        "data":{
          "type": "token",
          "email": "ron@swanson.com",
          "password": "mysecretpassword"
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

const email = 'ron@swanson.com';
const password = 'mysecretpassword';

Moltin.Customers.Token(email,password).then(data => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

### Using a token

You can use a `X-Moltin-Customer-Token` header with the following endpoints. They're available implicitly for you to read, create and update various resources.

{% page-ref page="get-a-customer.md" %}

{% page-ref page="update-a-customer.md" %}

{% page-ref page="../addresses/get-all-addresses.md" %}

{% page-ref page="../addresses/get-an-address.md" %}

{% page-ref page="../addresses/create-an-address.md" %}

{% page-ref page="../addresses/update-an-address.md" %}

{% page-ref page="../orders/get-all-orders.md" %}

{% page-ref page="../orders/get-an-order.md" %}

