# Get a Customer

{% api-method method="get" host="https://api.moltin.com" path="/v2/customers/:id" %}
{% api-method-summary %}
Get by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the requested Customer.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Customer-Token" type="string" required=false %}
A customer token used to access a customer implicitly.
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.  If there is no customer token the grant type must be `client_credentials`.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "type": "customer",
        "id": "a23cc59d-a6c2-4c14-89c7-80fd7e4fc6c0",
        "name": "Ron Swanson",
        "email": "ronwanson@example.com",
        "password": true,
        "phone_number": null,
        "promo_sent": "no",
        "username": null
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
curl -X GET https://api.moltin.com/v2/customers/:id \
     -H "Authorization: Bearer XXXX" \
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

Moltin.Customers.Get(id).then(customer => {
  // Do something
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.customer.get(forID: id) { result in
    switch result {
        case .success(let response):
            print(response)
        case .failure(let error):
            print(error)
    }
}
```
{% endtab %}
{% endtabs %}

## With customer token

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/customers/:id \
     -H "X-Moltin-Customer-Token: XXXX"
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const customerId = 'XXXX'
const addressId = 'XXXX'
const customerToken = 'XXXX'

Moltin.Addresses.All({
  customer: customerId,
  addresss: addressId,
  token: customerToken
}).then(address => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

## Without customer token

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/customers/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

