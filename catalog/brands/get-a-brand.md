# Get a Brand

{% api-method method="get" host="https://api.moltin.com" path="/v2/brands/:id" %}
{% api-method-summary %}
Get by ID
{% endapi-method-summary %}

{% api-method-description %}
This endpoint retrieves an existing Brand by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the requested Brand.
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
    "id": "c46e07d2-23ef-4b3b-8437-7bcdbf38bc4c",
    "type": "brand",
    "status": "live",
    "name": "I Love Lamp",
    "slug": "ilovelamp",
    "description": "A lamp brand.",
    "meta": {
      "timestamps": {
        "created_at": "2018-04-05T08:48:39+00:00",
        "updated_at": "2018-04-23T11:09:30+00:00"
      }
    },
    "relationships": {}
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
curl -X GET https://api.moltin.com/v2/brands/:id \
     -H "Authorization: Bearer XXXX" \
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const id = 'XXXX'

Moltin.Brands.Get(id).then(brand => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { createClient } = require('@moltin/request')
​
const client = new createClient({
  client_id: 'X'
})
​
const id = 'XXXX'
​
client
  .get(`brands/${id}`)
  .then(brands => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.brand.get(forID: id) { result in
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

