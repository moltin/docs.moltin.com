# Update a Collection

{% api-method method="get" host="https://api.moltin.com" path="/v2/collections/:id" %}
{% api-method-summary %}
Update by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the collection to update
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The name of the collection
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=false %}
A unique slug identifier for the collection
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Any description for this collection
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
`live` or `draft` depending on the collection status
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
        "id": "645f97aa-ae63-4ee9-9259-062e570ba064",
        "type": "collection",
        "status": "draft",
        "name": "Collection #1 Updated",
        "slug": "collection-1-update",
        "description": "First collection updated",
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T14:23:18+00:00",
                "updated_at": "2018-05-10T14:23:18+00:00"
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
curl -X PUT https://api.moltin.com/v2/collections/:id \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer XXXX" \
    -d $'{
        data": {
            "type": "collection",
            "id": "645f97aa-ae63-4ee9-9259-062e570ba064",
            "name": "Collection #1 Updated",
            "slug": "collection-1-update",
            "description": "First collection updated",
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

const collectionId = 'xxxx'

const collection = {
    name: "Collection #1 Updated",
    slug: "collection-1-update",
    description: "First collection updated",
    status: "live"
}

Moltin.Collections.update(collectionId, collection).then(collection => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

