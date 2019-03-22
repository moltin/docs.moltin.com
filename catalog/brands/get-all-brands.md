# Get all Brands

{% api-method method="get" host="https://api.moltin.com" path="/v2/brands" %}
{% api-method-summary %}
Get all Brands
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

{% api-method-query-parameters %}
{% api-method-parameter name="filter" type="string" required=false %}
Filter attributes
{% endapi-method-parameter %}

{% api-method-parameter name="include" type="string" required=false %}
`brands`, `products`
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "id": "c46e07d2-23ef-4b3b-8437-7bcdbf38bc4c",
      "type": "brand",
      "status": "live",
      "name": "I Love Lamp",
      "slug": "i-love-lamp",
      "description": "A lamp brand.",
      "meta": {
        "timestamps": {
          "created_at": "2018-04-05T08:48:39+00:00",
          "updated_at": "2018-04-23T11:09:30+00:00"
        }
      },
      "relationships": {}
    }
  ],
  "links": {
    "current":
      "https://api.moltin.com/v2/brands?page[limit]=100&page[offset]=0",
    "first": "https://api.moltin.com/v2/brands?page[limit]=100&page[offset]=0",
    "last": null
  },
  "meta": {
    "page": {
      "limit": 100,
      "offset": 0,
      "current": 1,
      "total": 1
    },
    "results": {
      "total": 1
    }
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
You can use pagination with this resource. See: [Settings](../../advanced/settings/#page-length) for details.
{% endhint %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/brands \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="Javascript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Brands.All().then(brands => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { createClient } = require('@moltin/request')

const client = new createClient({
  client_id: 'X'
})

client
  .get('brands')
  .then(brands => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.brand.all { result in
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

