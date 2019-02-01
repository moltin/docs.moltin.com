# Braintree Payments

{% hint style="info" %}
Brain integration supports the `purchase` payment method.
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
`purchase` is the only available method for Braintree
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
You will use `braintree` in this case
{% endapi-method-parameter %}

{% api-method-parameter name="options.custom\_fields" type="object" required=false %}
Available for preconfigured custom fields in Braintree
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
        "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "type": "transaction",
        "reference": "braintree",
        "gateway": "braintree",
        "amount": 100,
        "currency": "USD",
        "transaction-type": "purchase",
        "status": "complete",
        "relationships": {
            "order": {
                "data": {
                    "type": "order",
                    "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
                }
            }
        },
        "meta": {
            "display_price": {
                "amount": 100,
                "currency": "USD",
                "formatted": "$100.00"
            },
            "created_at": "2019-01-31T17:20:39.378Z"
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
curl -X POST https://api.moltin.com/v2/orders/:order_id/payments \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": {
        "gateway": "braintree",
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
  gateway: 'braintree',
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

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Pay by Customer ID
{% endapi-method-summary %}

{% api-method-description %}
This method allows you to bill a specific Braintree customer. Braintree will be the default billing method in the customer's account.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="order\_id" type="string" required=true %}
The UUID of the order you want to pay for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="options.custom\_fields" type="string" required=false %}
Available for preconfigured custom fields in Braintree
{% endapi-method-parameter %}

{% api-method-parameter name="payment" type="string" required=true %}
The Braintree Customer ID that you want to bill
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`purchase` is the only payment method for Braintree
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
You will use `braintree` in this case
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
        "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "type": "transaction",
        "reference": "braintree",
        "gateway": "braintree",
        "amount": 100,
        "currency": "USD",
        "transaction-type": "purchase",
        "status": "complete",
        "relationships": {
            "order": {
                "data": {
                    "type": "order",
                    "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
                }
            }
        },
        "meta": {
            "display_price": {
                "amount": 100,
                "currency": "USD",
                "formatted": "$100.00"
            },
            "created_at": "2019-01-31T17:20:39.378Z"
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
curl -X POST https://api.moltin.com/v2/orders/:order_id/payments \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": {
    "gateway": "braintree",
    "method": "purchase",
    "payment": BRAINTREE_CUSTOMER_ID
  }
}'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
Moltin.Orders.Payment('orderId', {
  gateway: "braintree",
  method: "purchase",
  payment: BRAINTREE_CUSTOMER_ID
}).then(() => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Pay by Token
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to pay for an order with a specific Braintree Payment Method Token. This is similar to the Customer ID payment type, but you can define a specific payment source to charge.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="order\_id" type="string" required=true %}
The UUID of the order you want to pay for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="gateway" type="string" required=true %}
You will use `braintree` in this case
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`purchase` is the only payment method for Braintree
{% endapi-method-parameter %}

{% api-method-parameter name="payment" type="string" required=true %}
The Braintree Customer ID you want to bill
{% endapi-method-parameter %}

{% api-method-parameter name="options.payment\_method\_token" type="string" required=true %}
The payment method token to charge
{% endapi-method-parameter %}

{% api-method-parameter name="options.custom\_fields" type="string" required=false %}
Available for preconfigured custom fields in Braintree
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

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
     -d $'{
  "data": {
    "gateway": "braintree",
    "method": "purchase",
    "payment": BRAINTREE_CUSTOMER_ID,
    "options": {
        "payment_method_token": BRAINTREE_PAYMENT_METHOD_TOKEN
    }
  }
}'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
Moltin.Orders.Payment('orderId', {
  gateway: "braintree",
  method: "purchase",
  payment: BRAINTREE_CUSTOMER_ID,
  options: {
      payment_method_token: BRAINTREE_PAYMENT_METHOD_TOKEN
  }
}).then(() => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Pay by Nonce
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to pay for an order with a previously created Braintree   
Payment Method Nonce. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="order\_id" type="string" required=true %}
The UUID of the order you want to pay for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
the Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="gateway" type="string" required=true %}
You will use `braintree` in this case
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`purchase` is the only payment method for Braintree
{% endapi-method-parameter %}

{% api-method-parameter name="payment" type="string" required=true %}
The Braintree Payment Nonce ID
{% endapi-method-parameter %}

{% api-method-parameter name="options.payment\_method\_nonce" type="boolean" required=true %}
Set this to `true`
{% endapi-method-parameter %}

{% api-method-parameter name="options.custom\_fields" type="string" required=false %}
Available for preconfigured custom fields in Braintree
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
        "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "type": "transaction",
        "reference": "braintree",
        "gateway": "braintree",
        "amount": 100,
        "currency": "USD",
        "transaction-type": "purchase",
        "status": "complete",
        "relationships": {
            "order": {
                "data": {
                    "type": "order",
                    "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
                }
            }
        },
        "meta": {
            "display_price": {
                "amount": 100,
                "currency": "USD",
                "formatted": "$100.00"
            },
            "created_at": "2019-01-31T17:20:39.378Z"
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
curl -X POST https://api.moltin.com/v2/orders/{ORDER_ID}/payments \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": {
    "gateway": "braintree",
    "method": "purchase",
    "payment": BRAINTREE_PAYMENT_NONCE,
    "options": {
        "payment_method_nonce": true
    }
  }
}'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
Moltin.Orders.Payment('orderId', {
  gateway: "braintree",
  method: "purchase",
  payment: BRAINTREE_PAYMENT_NONCE,
  options: {
      payment_method_nonce: true
  }
}).then(() => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

