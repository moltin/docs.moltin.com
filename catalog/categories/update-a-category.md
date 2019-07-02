# Update a Category

{% api-method method="put" host="https://api.moltin.com" path="/v2/categories/:id" %}
{% api-method-summary %}
Update a Category by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to gran access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the category to update.
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Represents the type of the object being returned, e.g. `category`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```bash
{
    "data": {
        "id": "57fbb8eb-34cc-4076-8ec8-7e6f52c07100",
        "type": "category",
        "status": "live",
        "name": "Womens",
        "slug": "Womens",
        "description": "Womens clothing",
        "meta": {
            "timestamps": {
                "created_at": "2018-10-05T15:18:48+00:00",
                "updated_at": "2018-10-05T15:18:48+00:00"
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
curl -X PUT https://api.moltin.com/v2/categories/:id \
    -H "Authorization: Bearer XXXX" \
    -H "Content-Type: application/json" \
    -d $'{
      "data": {
          "type": "category",
          "id": "645f97aa-ae63-4ee9-9259-062e570ba064",
          "name": "Category #1 Updated",
          "slug": "category-1-update",
          "description": "First category updated",
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

const id = 'XXXX'

const category = {
    name: "Category #1 Updated",
    slug: "category-1-update",
    description: "First category updated",
    status: "live"
}

Moltin.Categories.update(id, category).then(category => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

