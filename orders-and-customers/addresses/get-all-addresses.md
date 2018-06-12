# Get all Addresses

{% api-method method="get" host="https://api.moltin.com" path="/v2/customers/:customerId/addresses" %}
{% api-method-summary %}
Get all
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="customerId" type="string" required=true %}
A customer **ID** that has addresses
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Customer-Token" type="string" required=false %}
A customer token used to access customer addresses implicitly
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "id": "5f8da740-6680-463e-b31c-190b2db4bf9d",
      "type": "address",
      "name": "Home",
      "first_name": "Ron",
      "last_name": "Swanson",
      "company_name": "",
      "phone_number": "(555) 555-1234",
      "line_1": "1 Sunny Street",
      "line_2": "Sunny Place",
      "city": "Sunny Town",
      "postcode": "SU33 1YY",
      "county": "Sunnyville",
      "country": "GB",
      "instructions": "Leave in the shed",
      "links": {
        "self":
          "https://api.moltin.com/v2/addresses/5f8da740-6680-463e-b31c-190b2db4bf9d"
      },
      "meta": {
        "timestamps": {
          "created_at": "2018-05-04T15:20:09.734Z",
          "updated_at": "2018-05-04T15:20:09.734Z"
        }
      }
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## With customer token

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/customers/:customer_id/addresses \
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
curl -X GET https://api.moltin.com/v2/customers/:customer_id/addresses \
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

const customerId = 'XXXX'
const addressId = 'XXXX'

Moltin.Addresses.All({
  customer: customerId,
  addresss: addressId
}).then(address => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

