# Get a Category

{% api-method method="get" host="https://api.moltin.com" path="/v2/categories/:id" %}
{% api-method-summary %}
Get by ID
{% endapi-method-summary %}

{% api-method-description %}
This endpoint retrieves an existing Category by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the requested Category
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
        "id": "65c036ce-c13b-4c05-89d5-9a47b9763935",
        "type": "category",
        "status": "live",
        "name": "Bright",
        "slug": "bright",
        "description": "Bright Category",
        "meta": {
            "timestamps": {
                "created_at": "2017-07-31T20:25:44+00:00",
                "updated_at": "2018-04-28T12:00:05+00:00"
            }
        },
        "relationships": {
            "products": {
                "data": [
                    {
                        "type": "product",
                        "id": "2bc131a2-9cca-4a04-b40c-b19f773a1354"
                    },
                    {
                        "type": "product",
                        "id": "d77dcc0c-1e74-4e06-aff9-7f666dedafbe"
                    }
                ]
            }
        },
        "background_colour": "#dadada", // Custom flow field
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
curl -X GET https://api.moltin.com/v2/categories/:id \
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

Moltin.Categories.Get(id).then(category => {
  // Do something
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.category.get(forID: id) { result in
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

