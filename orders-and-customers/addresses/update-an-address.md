# Update an Address

{% api-method method="put" host="https://api.moltin.com" path="/v2/customers/:customerId/addresses/:addressId" %}
{% api-method-summary %}
Update by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="customerId" type="string" required=true %}
The **ID** for the customer you are adding an address for
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

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="first\_name" type="string" required=true %}
The first name of the recipient on this address
{% endapi-method-parameter %}

{% api-method-parameter name="last\_name" type="string" required=true %}
The last name of the recipient on this address
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The name under which this address is saved. You can display this name to the customer when you ask them to select from their saved addresses
{% endapi-method-parameter %}

{% api-method-parameter name="phone\_number" type="string" required=false %}
A phone number for this address
{% endapi-method-parameter %}

{% api-method-parameter name="instructions" type="string" required=false %}
Any delivery instructions for this address
{% endapi-method-parameter %}

{% api-method-parameter name="company\_name" type="string" required=false %}
The company name at this address
{% endapi-method-parameter %}

{% api-method-parameter name="line\_1" type="string" required=true %}
The first portion of the address, usually the street address
{% endapi-method-parameter %}

{% api-method-parameter name="line\_2" type="string" required=false %}
The second portion of the address, usually an apartment or unit number
{% endapi-method-parameter %}

{% api-method-parameter name="city" type="string" required=false %}
The city for this address
{% endapi-method-parameter %}

{% api-method-parameter name="county" type="string" required=true %}
The county for this address
{% endapi-method-parameter %}

{% api-method-parameter name="postcode" type="string" required=true %}
The ZIP Code, Postcode, or other postal reference string for this delivery address
{% endapi-method-parameter %}

{% api-method-parameter name="country" type="string" required=true %}
A two digit code for the country this address is in, expressed as per the ISO 3166-2 standard
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
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
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/customers/:customerId/addresses \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
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
         "instructions": "Leave in the shed"
       }
     }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X' // Required if customer token not present
})

const customer = 'XXXX'

const addressId = 'XXXX'

const address = {
  name: "Home sweet home",
}

const token = 'XXXX'

Moltin.Addresses.Update({
  customer,
  address: addressId,
  body: address,
  token // optional
}).then(address => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

