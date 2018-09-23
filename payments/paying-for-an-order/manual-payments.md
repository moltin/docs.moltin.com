# Manual Payments

Out of the box we are able to support an unlimited amount of payment gateways using the Manual Payments API.

{% hint style="warning" %}
The manual gateway currently supports the `authorize` and `capture` methods only.
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Authorize payment
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="orderId" type="string" required=true %}
The UUID of the order you want to authorize payment for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="method" type="string" required=true %}
The payment method, in this example it is `authorize`
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
This will always be `manual` for the manual payment gateway
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
```bash
curl -X POST https://api.moltin.com/v2/orders/:orderId/payments \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
         "gateway": "manual",
         "method": "authorize",
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

const payment = {
  gateway: 'manual',
  method: 'authorize'
}

Moltin.Orders.Payment(orderId, payment).then(() => {
  // Do something
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")
let id = "XXXX"

let paymentMethod = ManuallyAuthorizePayment()

moltin.cart.pay(forOrderID: order.id, withPaymentMethod: paymentMethod) { (result) in
    switch result {
        case .success:
            print("Success")
        case .failure(let error):
            print(error)
    }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/transactions/:transactionId/capture" %}
{% api-method-summary %}
Capture transaction
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="transactionId" type="string" required=true %}
The UUID of the previously authorized transaction
{% endapi-method-parameter %}

{% api-method-parameter name="orderId" type="string" required=true %}
The UUID of the order you want to capture for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="method" type="string" required=true %}
The payment method, in this example it is `capture`
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
This will always be manual for the manual payment gateway
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

{% hint style="warning" %}
The `capture` method requires [client\_credentials](../../basics/authentication/client-credential-token.md#create-a-client-credential-token) authentication.
{% endhint %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/orders/:orderId/transactions/transactionId/capture \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
         "gateway": "manual",
         "method": "capture"
       }
     }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const orderId = 'XXXX'
const transactionId = 'XXXX'

Moltin.Transactions.Capture({
  order: orderId,
  transaction: transactionId
}).then(() => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

