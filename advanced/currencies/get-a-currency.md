# Get a Currency

{% api-method method="get" host="https://api.moltin.com" path="/v2/currencies/:id" %}
{% api-method-summary %}
Get a Currency by ID
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "451b94f8-0536-4580-91e1-68bad2f05925",
    "type": "currency",
    "code": "GBP",
    "exchange_rate": 1,
    "format": "£{price}",
    "decimal_point": ".",
    "thousand_separator": ",",
    "decimal_places": 0,
    "default": false,
    "enabled": true,
    "links": {
      "self":
        "https://api.moltin.com/currencies/451b94f8-0536-4580-91e1-68bad2f05925"
    },
    "meta": {
      "timestamps": {
        "created_at": "2017-09-27T08:48:01.821Z",
        "updated_at": "2018-04-24T19:19:40.941Z"
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
curl -X GET https://api.moltin.com/v2/currencies/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const id = 'XXXX'

Moltin.Currencies.Get(id).then(currency => {
  // Do something
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.currency.get(forID: id) { result in
    switch result {
        case .success(let response):
            print(response)
        case .failure(let error):
            print(error)
    }
}
```
{% endtab %}
{% endtabs %}

