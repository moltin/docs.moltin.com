# CyberSource Payments

{% hint style="info" %}
​CyberSource integration supports the `purchase` payment method.
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
{% api-method-parameter name="verification\_value" type="string" required=false %}
The CVV/CVC code from the back of the card
{% endapi-method-parameter %}

{% api-method-parameter name="year" type="string" required=false %}
The expiry year of the card
{% endapi-method-parameter %}

{% api-method-parameter name="month" type="string" required=false %}
The expiry month of the card
{% endapi-method-parameter %}

{% api-method-parameter name="number" type="string" required=false %}
The full card number
{% endapi-method-parameter %}

{% api-method-parameter name="last\_name" type="string" required=false %}
The last name of the card owner
{% endapi-method-parameter %}

{% api-method-parameter name="first\_name" type="string" required=false %}
The first name of the card owner
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=false %}
`purchase`
{% endapi-method-parameter %}

{% api-method-parameter name="gateway" type="string" required=false %}
You will use `cyber_source` in this case
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
          "gateway": "cyber_source",
          "method": "purchase",
          "first_name": "John",
          "last_name": "Smith",
          "number": "4111111111111111",
          "month": "10",
          "year": "2020",
          "verification_value": "123"
        }
      }'
```

