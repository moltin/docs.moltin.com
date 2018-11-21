# Get all Gateways

{% api-method method="get" host="https://api.moltin.com" path="/v2/gateways" %}
{% api-method-summary %}
Get all Gateways
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "enabled": false,
      "merchant_account": "",
      "name": "Adyen",
      "password": "",
      "slug": "adyen",
      "test": false,
      "type": "gateway",
      "username": ""
    },
    {
      "enabled": false,
      "environment": "",
      "merchant_id": "",
      "name": "Braintree",
      "private_key": "",
      "public_key": "",
      "slug": "braintree",
      "type": "gateway"
    },
    {
      "enabled": true,
      "name": "Manual",
      "slug": "manual",
      "type": "gateway"
    },
    {
      "enabled": false,
      "login": "",
      "name": "Stripe",
      "slug": "stripe",
      "type": "gateway"
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
```bash
curl -X GET https://api.moltin.com/v2/gateways \
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

Moltin.Gateways.All().then(gateways => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

