# Update a Customer

{% api-method method="put" host="https://api.moltin.com" path="/v2/customers/:customerId" %}
{% api-method-summary %}
Update by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="customerId" type="string" required=true %}
The ID for the customer requested.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Customer-Token" type="string" required=false %}
The customer specific token.
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
The type of object being returned.
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The full name of the customer.
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}
The customer email.
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
The customers password.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X PUT https://api.moltin.com/v2/customers/:customerId \
    -H "Authorization: Bearer XXXX" \
    -d $'{
     "data": {
       "type": "customer",
       "email": "ron@swanson.com"
     }
}'
```
{% endtab %}

{% tab title="JavaScriptSDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

var customerId = 'xx'

var customer = {
    email: "ron@swanson.com"
}

Moltin.Customers.Update({customerId}, customer).then((response) => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

