# Relationships

You can use the Categories API to associate categories with each other in a hierarchical tree structure. The relationship between Categories is known as `parents` and `children`.

You can create relationships between categories by attaching `parent` and `child` category IDs to the category of interest. **A category can have 1 parent but many children.** 

The Category Relationship endpoint  allows you to specify the parent and children of a category in one request.

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
      "id": "59a8c4e2-bd2d-4a14-9f1a-a497330cdf11",
      "type": "category",
      "status": "live",
      "name": "Mens",
      "slug": "mens",
      "description": "Browse our mens clothing line",
      "children": [
        {
          "id": "b438be03-9ae7-4e6a-8fb6-7ee41ce0ae71",
          "type": "category",
          "status": "live",
          "name": "Mens apparel",
          "slug": "mens-apparel",
          "description": "Browse our mens apparel",
          "children": [
            {
              "id": "6272a049-dc98-428b-ad90-65572add46c0",
              "type": "category",
              "status": "live",
              "name": "Clothing",
              "slug": "clothing",
              "description": "Browse our clothing line"
                }
              ]
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

