# Update a Brand

{% api-method method="put" host="https://api.moltin.com" path="/v2/brands/:id" %}
{% api-method-summary %}
Update by ID
{% endapi-method-summary %}

{% api-method-description %}
This endpoint will update an existing Brand by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the requested Brand
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
This represents the type of object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the requested brand
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
`live` or `draft` depending on the status
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Any description for this brand
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=false %}
A unique slug identifier for the brand
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The name of the brand
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
    "id": "c46e07d2-23ef-4b3b-8437-7bcdbf38bc4c",
    "type": "brand",
    "status": "live",
    "name": "Trendy Lamp Co",
    "slug": "trendy-lamp-co",
    "description": "Trendy lamps.",
    "meta": {
      "timestamps": {
        "created_at": "2018-04-05T08:48:39+00:00",
        "updated_at": "2018-04-23T11:09:30+00:00"
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
curl -X PUT https://api.moltin.com/v2/brands/:id \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
         "type": "brand",
         "id": "c46e07d2-23ef-4b3b-8437-7bcdbf38bc4c",
         "name": "Trendy Lamp Co.",
         "slug": "trendy-lamp-co",
         "description": "Trendy lamps.",
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

const brand = {
  name: 'Trendy Lamp Co',
  slug: 'trendy-lamp-co',
  description: 'Trendy lamps.',
  status: 'live'
}

Moltin.Brands.Update(id, brand).then(brand => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

