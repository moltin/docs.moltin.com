# Create a Currency

{% api-method method="post" host="https://api.moltin.com" path="/v2/currencies" %}
{% api-method-summary %}
Create a Currency
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

{% api-method-body-parameters %}
{% api-method-parameter name="enabled" type="boolean" required=true %}
Is this currency available for products? `true` or `false`
{% endapi-method-parameter %}

{% api-method-parameter name="default" type="boolean" required=true %}
Is this the default currency? `true` or `false`
{% endapi-method-parameter %}

{% api-method-parameter name="decimal\_places" type="string" required=true %}
How many decimal places the currency is formatted to
{% endapi-method-parameter %}

{% api-method-parameter name="thousand\_separator" type="string" required=true %}
The thousand separator character. Example: `,`
{% endapi-method-parameter %}

{% api-method-parameter name="decimal\_point" type="string" required=true %}
The decimal point character. Example: `.`
{% endapi-method-parameter %}

{% api-method-parameter name="format" type="string" required=true %}
Specify how the price currency is displayed. Example: `"¥{price}"`
{% endapi-method-parameter %}

{% api-method-parameter name="exchange\_rate" type="integer" required=true %}
The exchange rate from the default currency
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=true %}
The currency code. Example: `YEN`
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
The type represents the object being returned
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
    "id": "190c3e9e-8006-4231-8c29-833fb4f6bff0",
    "type": "currency",
    "code": "YEN",
    "exchange_rate": 1,
    "format": "¥{price}",
    "decimal_point": ",",
    "thousand_separator": ".",
    "decimal_places": 2,
    "default": false,
    "enabled": true,
    "links": {
      "self":
        "https://api.moltin.com/currencies/190c3e9e-8006-4231-8c29-833fb4f6bff0"
    },
    "meta": {
      "timestamps": {
        "created_at": "2018-05-02T09:01:56.303640168Z",
        "updated_at": "2018-05-02T09:01:56.303641068Z"
      }
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
You'll get an error if you try to create a currency with an existing `code`
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "status": 400,
      "title": "Currency already exists",
      "detail": "The specified currency code already exists for this store"
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
curl -X POST https://api.moltin.com/v2/currencies \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
       "data": {
         "type": "currency",
         "code": "YEN",
         "exchange_rate": 1,
         "format": "¥{price}",
         "decimal_point": ".",
         "thousand_separator": ",",
         "decimal_places": 2,
         "default": false,
         "enabled": true
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

const currency = {
  code: 'YEN',
  exchange_rate: 1,
  format: '¥{price}',
  decimal_point: '.',
  thousand_separator: ',',
  decimal_places: 2,
  default: false,
  enabled: true
}

Moltin.Currencies.Create(id, currency).then(currency => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

