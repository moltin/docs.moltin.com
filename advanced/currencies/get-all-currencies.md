# Get all Currencies

{% api-method method="get" host="https://api.moltin.com" path="/v2/currencies" %}
{% api-method-summary %}
Get all Currencies
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
    },
    {
      "id": "cd9f04a9-2338-469b-a1f2-096ac5973a90",
      "type": "currency",
      "code": "USD",
      "exchange_rate": 1,
      "format": "${price}",
      "decimal_point": ".",
      "thousand_separator": ",",
      "decimal_places": 2,
      "default": true,
      "enabled": true,
      "links": {
        "self":
          "https://api.moltin.com/currencies/cd9f04a9-2338-469b-a1f2-096ac5973a90"
      },
      "meta": {
        "timestamps": {
          "created_at": "2017-06-12T13:36:23.541Z",
          "updated_at": "2018-05-01T14:32:53.956Z"
        }
      }
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
curl -X GET https://api.moltin.com/v2/currencies \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Currencies.All().then(currencies => {
  // Do something
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.currency.all { result in
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

