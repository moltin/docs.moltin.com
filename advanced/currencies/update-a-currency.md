# Update a Currency

{% api-method method="put" host="https://api.moltin.com" path="/v2/currencies/:id" %}
{% api-method-summary %}
Update a Currency by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the requested Currency
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
The type represents the object being returned. Always `currency`
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=false %}
The currency code. Example: `YEN`
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="boolean" required=false %}
Is this currency available for products? `true` or `false`
{% endapi-method-parameter %}

{% api-method-parameter name="default" type="boolean" required=false %}
Is this the default currency? `true` or `false`
{% endapi-method-parameter %}

{% api-method-parameter name="decimal\_places" type="integer" required=false %}
How many decimal places the currency is formatted to
{% endapi-method-parameter %}

{% api-method-parameter name="thousand\_separator" type="string" required=false %}
The thousand separator character. Example: `,`
{% endapi-method-parameter %}

{% api-method-parameter name="decimal\_point" type="string" required=false %}
The decimal point character. Example: `.`
{% endapi-method-parameter %}

{% api-method-parameter name="format" type="string" required=false %}
Specify how the price currency is displayed. Example: `"¥{price}"`
{% endapi-method-parameter %}

{% api-method-parameter name="exchange\_rate" type="string" required=false %}
The exchange rate from the default currency
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
    "id": "190c3e9e-8006-4231-8c29-833fb4f6bff0",
    "type": "currency",
    "code": "YEN",
    "exchange_rate": 1.5,
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X PUT https://api.moltin.com/v2/currencies/:id \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
         "type": "currency",
         "exchange_rate": 1.5
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

const id = 'XXXX'

const currency = {
  exchange_rate: 1.5
}

Moltin.Currencies.Update(id, currency).then(currency => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

