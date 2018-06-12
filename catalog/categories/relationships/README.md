# Relationships

You can use the Categories API to associate categories with each other in a hierarchical tree structure. The relationship between Categories is known as `parents` and `children`.

{% api-method method="get" host="https://api.moltin.com" path="/v2/categories/tree" %}
{% api-method-summary %}
Get the Categories tree
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
            "id": "a636c261-0259-4975-ac8e-77246ec9cfe0",
            "type": "category",
            "status": "live",
            "name": "Unique",
            "slug": "unique",
            "description": "Unique Category"
        },
        {
            "id": "b8fac5c9-8605-48d0-bcf7-e6ada1a8c6bd",
            "type": "category",
            "status": "live",
            "name": "Modern",
            "slug": "modern",
            "description": "Modern Category"
        },
        {
            "id": "521e6029-0e0e-4704-b9a5-9777047ada04",
            "type": "category",
            "status": "live",
            "name": "Bright",
            "slug": "bright",
            "description": "Bright Category"
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
curl -X GET https://api.moltin.com/v2/categories/tree \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Categories.Tree().then(categories => {
  // Do something
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.category.tree { result in
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

