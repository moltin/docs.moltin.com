# Relationships

You can use the Brands API to associate brands with each other in a hierarchical tree structure. The relationship between brands is known as `parents` and `children`.

{% api-method method="get" host="https://api.moltin.com" path="/v2/brands/tree" %}
{% api-method-summary %}
Get the Brands tree
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
      "type": "brand",
      "id": "9185d4ff-a484-408b-8c1a-d4de1ca20736",
      "name": "Cool Shoes",
      "status": "live",
      "slug": "cool-shoes",
      "description": "Our main shoes brand",
      "children": [
        {
          "type": "brand",
          "id": "c902aea9-ec90-4fdd-8084-3c2d879a2c52",
          "name": "MixiMax",
          "status": "live",
          "slug": "miximax",
          "description": "MixiMax brand"
        },
        {
          "type": "brand",
          "id": "43b70fc1-ed2f-45e0-b9e1-212b5e95e809",
          "name": "AirPair",
          "status": "live",
          "slug": "airpair",
          "description": "AirPair brand"
        }
      ]
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
curl -X GET https://api.moltin.com/v2/brands/tree \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Brands.Tree().then(brands => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { MoltinClient } = require('@moltin/request')

const client = new MoltinClient({
  client_id: 'X'
})

client
  .get('brands/tree')
  .then(brands => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.brand.tree { result in
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

