# Create a Brand

{% api-method method="post" host="https://api.moltin.com" path="/v2/brands" %}
{% api-method-summary %}
Create a Brand
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
{% api-method-parameter name="status" type="string" required=false %}
`live` or `draft` depending on the status. Defaults to `draft`
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Any description for this brand
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
A unique slug identifier for the brand
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the brand
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
This represents the type of object being returned
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
    "id": "06e510ae-4ddd-4150-a721-561ca5c4ce31",
    "type": "brand",
    "status": "live",
    "name": "Cool Clothing",
    "slug": "cool-clothing",
    "description": "Cool clothing make cool clothes!",
    "relationships": {}
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
In this example we skip passing `name` to fail validation
{% endapi-method-response-example-description %}

```javascript
{
    "errors": [
        {
            "title": "Failed Validation",
            "detail": "The data.name field is required."
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
curl -X POST https://api.moltin.com/v2/brands \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
          "type": "brand",
          "name": "Cool Clothing",
          "slug": "cool-clothing",
          "description": "Cool clothing make cool clothes!",
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
  name: 'Cool Clothing',
  slug: 'cool-clothing',
  description: 'Cool clothing make cool clothes.',
  status: 'live'
}

Moltin.Brands.Create(id, brand).then(brand => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { createClient } = require('@moltin/request')
​
const client = new createClient({
  client_id: 'X',
  client_secret: 'X'
})
​
const data = {
  type: 'brand',
  name: 'Cool Clothing',
  slug: 'cool-clothing',
  description: 'Cool clothing make cool clothes.',
  status: 'live'
}
​
client
  .post('brands', data)
  .then(brand => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}
{% endtabs %}

