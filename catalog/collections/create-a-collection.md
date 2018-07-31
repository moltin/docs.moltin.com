# Create a Collection

{% api-method method="post" host="https://api.moltin.com" path="/v2/collections" %}
{% api-method-summary %}
Create a Collection
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

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being returned.
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the collection.
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
A unique slug identifier for the collection.
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Any description for this collection.
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
`live`, or `draft` depending on the collection status. \(defaults to draft\)
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
        "id": "a276571c-321e-4c48-af2a-5a3895394b08",
        "type": "collection",
        "status": "live",
        "name": "Winter Season",
        "slug": "winter-season",
        "description": "Our Winter Season is now live!",
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
curl -X POST https://api.moltin.com/v2/collections \
    -H "Authorization: Bearer XXXX" \
    -H "Content-Type: application/json" \
    -d $'{
     "data": {
        "type": "collection",
        "name": "Winter Season",
        "slug": "winter-season",
        "description": "Our Winter Season is now live!",
        "status": "live"
     }
}'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'XXXX'
})

var collection = {
    name: "Winter Season",
    slug: "winter-season",
    description: "Our Winter Season is now live!",
    status: "live"
}

Moltin.Collections.Create(collection).then((response) => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

