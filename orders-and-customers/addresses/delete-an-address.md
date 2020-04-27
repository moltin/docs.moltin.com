# Delete an Address

{% api-method method="delete" host="https://api.moltin.com" path="/v2/customers/:customer\_id/addresses/:address\_id" %}
{% api-method-summary %}
Delete by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="address\_id" type="string" required=true %}
The **ID** for the Address to delete
{% endapi-method-parameter %}

{% api-method-parameter name="customer\_id" type="string" required=true %}
A customer **ID** that has addresses
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Customer-Token" type="string" required=false %}
A customer token used to access customer addresses for implicit calls
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## With customer token

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X DELETE https://api.moltin.com/v2/customers/:customer_id/addresses/:address_id \
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

Moltin.Addresses.Delete({
  customer: customerId,
  address: addressId,
  token: customerToken
}).then(response => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

## Without customer token

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X DELETE https://api.moltin.com/v2/custom
ers/:customer_id/addresses/:address_id \
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

Moltin.Addresses.Delete({
  customer: customerId,
  address: addressId
}).then(response => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

