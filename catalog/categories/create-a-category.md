# Create a Category

{% api-method method="post" host="https://api.moltin.com" path="/v2/categories" %}
{% api-method-summary %}
Create a Category
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

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of the object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the category
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
A unique slug identifier for the category
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Any description for this category
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
live or draft depending on the category status. \(defaults to `draft`\)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "9dd56fc2-5746-46a2-bdf6-fe396bb6b7af",
        "type": "category",
        "status": "live",
        "name": "Clothing",
        "slug": "clothing",
        "description": "Browse our clothing line",
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
curl -X POST https://api.moltin.com/v2/categories \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer XXXX" \
    -d $'{
     "data": {
        "type": "category",
        "name": "Clothing",
        "slug": "clothing",
        "description": "Browse our clothing line",
        "status": "live"
     }
}'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const category = {
  name: 'Clothing',
  slug: 'clothing',
  description: 'Browse our clothing line',
  status: 'live'
}

Moltin.Categories.Create(category).then(category => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

