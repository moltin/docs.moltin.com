# Create a Customer

{% api-method method="post" host="https://api.moltin.com" path="/v2/customers" %}
{% api-method-summary %}
Create a customer
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being returned.
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The full name of the customer.
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}
The customer email.
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
The customer password.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "type": "customer",
        "id": "fc4679bf-f8a8-4029-bc67-945f74b756a0",
        "name": "Ron Swanson+6",
        "email": "ron+6@swanson.com",
        "password": true
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X POST https://api.moltin.com/v2/customers \
    -H "Authorization: Bearer XXXX" \
    -d $'{
     "data": {
     "type": "customer",
     "name": "Ron Swanson",
     "email": "ron@swanson.com",
     "password": "mysecretpassword",
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

const customer = {
    name: "Ron Swanson",
    email: "ron@swanson.com",
    password: "mysecretpassword",
}

Moltin.Customers.Create(customer).then(customer => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

