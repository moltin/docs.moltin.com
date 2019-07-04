# Child Relationships

{% api-method method="post" host="https://api.moltin.com" path="/v2/categories/:categoryId/relationships/children" %}
{% api-method-summary %}
Create Child Category Relationships
{% endapi-method-summary %}

{% api-method-description %}
Create a relationship to a parent Category. If any relationship\(s\) already exists, new ones will be added.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="categoryId" type="string" required=true %}
The **ID** of the category you wish to make relationships to
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
The type of related object \(should be be `category`\)
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the parent category
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "59a8c4e2-bd2d-4a14-9f1a-a497330cdf11",
        "type": "category",
        "status": "live",
        "name": "Mens",
        "slug": "mens",
        "description": "Browse our mens clothing line",
        "meta": {
            "timestamps": {
                "created_at": "2019-07-04T13:18:53+00:00",
                "updated_at": "2019-07-04T13:18:53+00:00"
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
curl -X POST https://api.moltin.com/v2/categories/:categoryId/relationships/children \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": [
        {
          "type": "category",
          "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
        }
      ]
    }'
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/categories/:categoryId/relationships/children" %}
{% api-method-summary %}
Update Child Category Relationship
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="categoryId" type="string" required=true %}
The **ID** of the category you wish to make relationships to
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
The type of related object \(should be `category`\)
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the parent category
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X PUT https://api.moltin.com/v2/categories/:categoryId/relationships/children \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": [
        {
          "type": "category",
          "id": "c902aea9-ec90-4fdd-8084-3c2d879a2c52"
        }
      ]
    }'
```
{% endtab %}
{% endtabs %}

{% api-method method="delete" host="https://api.moltin.com/" path="v2/categories/:categoryId/relationships/parent" %}
{% api-method-summary %}
Delete Child Category Relationship
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="categoryId" type="string" required=true %}
The ID of the category you wish to update relationships to.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="data" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="data\[\].type" type="string" required=true %}
The type of related object. \(should be `category`\)
{% endapi-method-parameter %}

{% api-method-parameter name="data\[\].id" type="string" required=true %}
The ID of the child category
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X DELETE https://api.moltin.com/v2/categories/:categoryId/relationships/parent \
     -H "Authorization: Bearer XXXX" \
     -d $'{
       "data": [{
         "type": "category",
         "id": "c902aea9-ec90-4fdd-8084-3c2d879a2c52"
        }]
      }'
```
{% endtab %}
{% endtabs %}

