# Get a Collection

{% api-method method="get" host="https://api.moltin.com" path="/v2/collections/:id" %}
{% api-method-summary %}
Get by ID
{% endapi-method-summary %}

{% api-method-description %}
This endpoint retrieves an existing Collection by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the requested Collection.
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
        "id": "12912957-4159-4eea-b1c4-685876588300",
        "type": "collection",
        "status": "live",
        "name": "Top Picks",
        "slug": "top_picks",
        "description": "Top Picks Collection",
        "meta": {
            "timestamps": {
                "created_at": "2017-06-26T11:18:05+00:00",
                "updated_at": "2018-04-04T10:56:47+00:00"
            }
        },
        "relationships": {
            "products": {
                "data": [
                    {
                        "type": "product",
                        "id": "36c21093-8996-4a9d-aacb-bf061f0769ed"
                    },
                    {
                        "type": "product",
                        "id": "61abf56a-194e-4e13-a717-92d2f0c9d4df"
                    },
                    {
                        "type": "product",
                        "id": "d77dcc0c-1e74-4e06-aff9-7f666dedafbe"
                    },
                    {
                        "type": "product",
                        "id": "001b9188-3959-4269-aaf6-e4a74f8607b8"
                    },
                    {
                        "type": "product",
                        "id": "a6fa6cbe-a718-45ab-ae1e-883c5a72ee61"
                    }
                ]
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
curl -X GET https://api.moltin.com/v2/collections/:id \
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

Moltin.Collections.Get(id).then(collection => {
  // Do something
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.collection.get(forID: id) { result in
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

