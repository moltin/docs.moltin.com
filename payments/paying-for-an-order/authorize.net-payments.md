# Authorize.net Payments

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:orderId/payments" %}
{% api-method-summary %}
Pay by token
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
{% api-method-parameter name="payment" type="string" required=true %}
The Authorize.net customer profile ID
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`purchase`, `authorize`, `capture`
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=true %}
You will use `authorize_net` in this case
{% endapi-method-parameter %}

{% api-method-parameter name="options.customer\_payment\_profile\_id" type="string" required=true %}
The Authorize.net customer payment profile ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "data": {
        "id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "type": "transaction",
        "reference": "xxx",
        "gateway": "authorize_net",
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

```text
curl -X POST https://api.moltin.com/v2/orders/:orderId/payments \
     -H "Authorization: Bearer XXXX" \
     -d $'{
        "data": {
          "gateway": "authorize_net",
          "method": "purchase",
          "payment": "xxx",
          "options": {
            "customer_payment_profile_id": "xxx"
          }
        }
      }'
```

{% api-method method="post" host="https://api.moltin.com" path="/v2/orders/:order\_id/payments" %}
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
{% api-method-parameter name="gateway" type="string" required=true %}
You will use `authorize_net` in this case
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
`purchase`, `authorize`, `capture`
{% endapi-method-parameter %}

{% api-method-parameter name="number" type="string" required=true %}
The full card number
{% endapi-method-parameter %}

{% api-method-parameter name="month" type="string" required=true %}
The expiry month of the card
{% endapi-method-parameter %}

{% api-method-parameter name="year" type="string" required=true %}
The expiry year of the card
{% endapi-method-parameter %}

{% api-method-parameter name="verification\_value" type="string" required=true %}
The CVV/CVC code from the back of the card
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

```text
curl -X POST https://api.moltin.com/v2/orders/:orderId/payments \
     -H "Authorization: Bearer XXXX" \
     -d $'{
        "data": {
          "gateway": "authorize_net",
          "method": "purchase",
          "number": "4007000000027",
          "month": "10",
          "year": "2020",
          "verification_value": "123"
        }
      }'
```

