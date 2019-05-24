# Get All Collections

{% api-method method="get" host="https://api.moltin.com" path="/v2/collections" %}
{% api-method-summary %}
Get All Collections
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="include" type="string" required=false %}
collection, products
{% endapi-method-parameter %}

{% api-method-parameter name="filter" type="string" required=false %}
Filter the results
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
            "id": "645f97aa-ae63-4ee9-9259-062e570ba064",
            "type": "collection",
            "status": "live",
            "name": "Winter Season",
            "slug": "winter-season",
            "description": "Our Winter Season is now live!",
            "meta": {
                "timestamps": {
                    "created_at": "2018-05-10T14:23:18+00:00",
                    "updated_at": "2018-05-10T14:23:18+00:00"
                }
            },
            "relationships": {}
        },
        {
            "id": "fbc05bbb-638a-4d36-998b-005c7bdf3dc9",
            "type": "collection",
            "status": "live",
            "name": "Winter Season",
            "slug": "winter-season",
            "description": "Our Winter Season is now live!",
            "meta": {
                "timestamps": {
                    "created_at": "2018-05-10T02:36:29+00:00",
                    "updated_at": "2018-05-10T02:36:29+00:00"
                }
            },
            "relationships": {}
        }
    ],
    "links": {
        "current": "https://api.moltin.com/v2/collections?page[limit]=100&page[offset]=0",
        "first": "https://api.moltin.com/v2/collections?page[limit]=100&page[offset]=0",
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
            "total": 2
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
```javascript
curl -X GET https://api.moltin.com/v2/collections \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'XXXX'
})

Moltin.Collections.all().then(collections => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const MoltinClient = require('@moltin/request')
​
const client = new createClient({
  client_id: 'X'
})
​
client
  .get('collections')
  .then(collections => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.collection.all { result in
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

