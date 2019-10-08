# Stripe Payment Intents

{% hint style="info" %}
Stripe payment intents integration only supports the `purchase` payment method.
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Pay by token or source
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
{% api-method-parameter name="options.idempotency\_key" type="string" required=false %}
Send a Stripe Idempotency Key
{% endapi-method-parameter %}

{% api-method-parameter name="options.receipt\_email" type="string" required=false %}
Provide an email for Stripe receipts. `live` mode feature
{% endapi-method-parameter %}

{% api-method-parameter name="payment" type="string" required=true %}
The Stripe token or source
{% endapi-method-parameter %}

{% api-method-parameter name="options.customer" type="string" required=false %}
The Stripe customer ID \(required if sending source\)
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`purchase`
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
You will use `stripe_payment_intents` in this case
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
        "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "type": "transaction",
        "reference": "pi_1FCOZeCTrBHFHKc3aq7Y6QMe",
        "gateway": "stripe_payment_intents",
        "amount": 5499,
        "currency": "USD",
        "transaction-type": "purchase",
        "transaction_type": "purchase",
        "status": "pending",
        "payment_intent": {
            "client_secret": "pi_1FCOZeCTrBHFHKc3aq7Y6QMe_secret_USOWF0SwovdGuc78rLJqIfa7K",
            "status": "requires_action"
        },
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
                "amount": 5499,
                "currency": "USD",
                "formatted": "$54.99"
            },
            "created_at": "2019-08-28T10:40:21.925Z",
            "timestamps": {
                "created_at": "2019-08-28T10:40:21Z",
                "updated_at": "2019-08-28T10:40:23Z"
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
If you are passing a `source` instead of a `token`, you must also include the Stripe customer ID in the request
{% endhint %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/orders/:orderId/payments \
     -H "Authorization: Bearer XXXX" \
     -d $'{
        "data": {
          "gateway": "stripe_payment_intents",
          "method": "purchase",
          "payment": "pm_card_threeDSecureRequired",
          "options": {
            "receipt_email": "john@example.com"
          }
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

const id = 'XXXX'

const payment = {
  gateway: 'stripe_payment_intents',
  method: 'purchase',
  payment: 'pm_card_threeDSecureRequired'
}

Moltin.Orders.Payment(id, payment).then(() => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
It's recommended that you use the token/source with Stripe payments. See [Stripe Elements](https://stripe.com/docs/stripe-js/elements/quickstart) for generating a token on the client-side.
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:order\_id/payments" %}
{% api-method-summary %}
Pay by card
{% endapi-method-summary %}

{% api-method-description %}

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
{% api-method-parameter name="options.receipt\_email" type="string" required=false %}
Provide an email for Stripe receipts. `live` mode feature
{% endapi-method-parameter %}

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
`purchase`, `authorize`, `capture`
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
You will use `stripe` in this case
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
        "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "type": "transaction",
        "reference": "pi_1FCOZeCTrBHFHKc3aq7Y6QMe",
        "gateway": "stripe_payment_intents",
        "amount": 5499,
        "currency": "USD",
        "transaction-type": "purchase",
        "transaction_type": "purchase",
        "status": "pending",
        "payment_intent": {
            "client_secret": "pi_1FCOZeCTrBHFHKc3aq7Y6QMe_secret_USOWF0SwovdGuc78rLJqIfa7K",
            "status": "requires_action"
        },
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
                "amount": 5499,
                "currency": "USD",
                "formatted": "$54.99"
            },
            "created_at": "2019-08-28T10:40:21.925Z",
            "timestamps": {
                "created_at": "2019-08-28T10:40:21Z",
                "updated_at": "2019-08-28T10:40:23Z"
            }
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
curl -X POST https://api.moltin.com/v2/orders/:orderId/payments \
     -H "Authorization: Bearer XXXX" \
     -d $'{
        "data": {
          "gateway": "stripe_payment_intents",
          "method": "purchase",
          "first_name": "John",
          "last_name": "Smith",
          "number": "4000000000003063",
          "month": "10",
          "year": "2020",
          "verification_value": "123",
          "options": {
            "receipt_email": "john@example.com"
          }
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

const id = 'XXXX'

const payment = {
  gateway: 'stripe_payment_intents',
  method: 'purchase',
  first_name: "John",
  last_name: "Smith",
  number: "4000000000003063",
  month: "10",
  year: "2020",
  verification_value: "123"
}

Moltin.Orders.Payment(id, payment).then(() => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Pay by Stripe Connect
{% endapi-method-summary %}

{% api-method-description %}
Moltin also supports Stripe Connect. Simply pass a destination via the options object.
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
The Bearer token used to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="options.destination" type="string" required=false %}
The Stripe Connect Account ID
{% endapi-method-parameter %}

{% api-method-parameter name="options.receipt\_email" type="string" required=false %}
Provide an email for Stripe receipts. `live` mode only
{% endapi-method-parameter %}

{% api-method-parameter name="payment" type="string" required=true %}
The Stripe token or source
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`purchase`
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
You will use `stripe_payment_intents` in this case
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
        "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "type": "transaction",
        "reference": "pi_1FCOZeCTrBHFHKc3aq7Y6QMe",
        "gateway": "stripe_payment_intents",
        "amount": 5499,
        "currency": "USD",
        "transaction-type": "purchase",
        "transaction_type": "purchase",
        "status": "pending",
        "payment_intent": {
            "client_secret": "pi_1FCOZeCTrBHFHKc3aq7Y6QMe_secret_USOWF0SwovdGuc78rLJqIfa7K",
            "status": "requires_action"
        },
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
                "amount": 5499,
                "currency": "USD",
                "formatted": "$54.99"
            },
            "created_at": "2019-08-28T10:40:21.925Z",
            "timestamps": {
                "created_at": "2019-08-28T10:40:21Z",
                "updated_at": "2019-08-28T10:40:23Z"
            }
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
curl -X POST https://api.moltin.com/v2/orders/:orderId/payments \
     -H "Authorization: Bearer XXXX" \
     -d $'{
        "data": {
          "gateway": "stripe_payment_intents",
          "method": "purchase",
          "payment": "pm_card_threeDSecureRequired",
          "options": {
            "destination": "acct_XXX",
            "receipt_email": "john@example.com"
          }
        }
      }'
```
{% endtab %}
{% endtabs %}

