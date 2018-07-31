# CardConnect Payments

{% hint style="info" %}
[CardConnect](https://cardconnect.com) integration supports the `purchase`, `authorize` and `capture` payment methods.
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Pay by card
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="orderId" type="string" required=true %}
The UUID of the order you want to pay for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="verification\_value" type="string" required=true %}
The CVV/CVC code from the back of the card
{% endapi-method-parameter %}

{% api-method-parameter name="year" type="string" required=true %}
The expiry year of the card
{% endapi-method-parameter %}

{% api-method-parameter name="month" type="string" required=true %}
The expiry month of the card
{% endapi-method-parameter %}

{% api-method-parameter name="number" type="string" required=true %}
The full card number
{% endapi-method-parameter %}

{% api-method-parameter name="last\_name" type="string" required=true %}
The last name of the card owner
{% endapi-method-parameter %}

{% api-method-parameter name="first\_name" type="string" required=true %}
The first name of the card owner
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`purchase`, `authorize` or `capture`
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
You will use `card_connect` in this case
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/orders/:order_id/payments \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": {
        "gateway": "card_connect",
        "method": "purchase",
        "first_name": "John",
        "last_name": "Smith",
        "number": "4242424242424242",
        "month": "10",
        "year": "2021",
        "verification_value": "123"
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

const orderId = 'XXXX'

Moltin.Orders.Payment(orderId, {
  gateway: 'card_connect',
  method: 'purchase',
  first_name: 'John',
  last_name: 'Smith',
  number: '4242424242424242',
  month: '10',
  year: '2021',
  verification_value: '123'
}).then(() => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

