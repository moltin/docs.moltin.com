# Category Relationships

{% api-method method="post" host="https://api.moltin.com" path="/v2/categories/:id/relationships/categories" %}
{% api-method-summary %}
Create Category Relationship
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the Category you want to modify relationships for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="parent.type" type="string" required=true %}
The type of the related object \(should be `category`\)
{% endapi-method-parameter %}

{% api-method-parameter name="parent.id" type="string" required=true %}
The **ID** of the parent Category
{% endapi-method-parameter %}

{% api-method-parameter name="children\[\].type" type="string" required=true %}
The type of related object \(should be `category`\)
{% endapi-method-parameter %}

{% api-method-parameter name="children\[\].id" type="string" required=true %}
The **ID** of the Category
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "id": "59a8c4e2-bd2d-4a14-9f1a-a497330cdf11",
    "type": "category",
    "status": "live",
    "name": "Mens",
    "slug": "mens",
    "description": "Browse our mens clothing line",
    "meta": {
        "timestamps": {
            "created_at": "2019-07-04T13:18:53+00:00",
            "updated_at": "2019-07-04T14:29:45+00:00"
        }
    },
    "relationships": {}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/categories/:id/relationships/categories \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
        "data": {
            "parent": {
                "type": "category",
                "id": "6272a049-dc98-428b-ad90-65572add46c0"
            },
            "children": [
                {
                "type": "category",
                "id": "b438be03-9ae7-4e6a-8fb6-7ee41ce0ae71"
                }
            ]
        }
    }'
```
{% endtab %}
{% endtabs %}

