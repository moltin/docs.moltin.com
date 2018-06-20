# Brand Relationship

{% api-method method="post" host="https://api.moltin.com" path="/v2/products/:productId/relationships/brands " %}
{% api-method-summary %}
Create Brand Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Create a Product relationship to one or more Brand.  If any relationships already exist, the one's made in the request will be added to them.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** of the product you wish to relate to the brand\(s\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer used to access the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **brand**\)
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the brand
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "type": "brand",
      "id": "d1e04526-7870-469c-a940-8f3033893084"
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
```javascript
curl -X "PUT" https://api.moltin.com/v2/products/:productID/relationships/brands \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "brand",
      "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
    }
  ]
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

const productId = 'XXXX'

var brandIds = [
    '8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c'
]

Moltin.Products.UpdateRelationships(productId, 'brand', brandIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/products/:productId/relationships/brands" %}
{% api-method-summary %}
Update Brand Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Replace the relationships between a Product and a Brand.  Unlike a **POST** to this endpoint, a **PUT** overrides any existing relationships.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** of the product you wish to relate to the brand\(s\).
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **brand**\)
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the brand
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X "PUT" https://api.moltin.com/v2/products/:productId/relationships/brands \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "brand",
      "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const productId = 'XXXX'

var brandIds = [
    '8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c'
];

Moltin.Products.UpdateRelationships(productId, 'brand', brandIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/products/:productId/relationships/brands" %}
{% api-method-summary %}
Delete Brand Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Removing a relationship between a Product and Brand\(s\) deletes the relationships specified in the payload.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=false %}
The **id** of the product you wish to relate to the brand.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **brand**\).
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **id** of the brand.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X "DELETE" https://api.moltin.com/v2/products/:productId/relationships/brands \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "brand",
      "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
    }
  ]
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const productId = 'XXXX'

var brandIds = [
    '8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c'
];

Moltin.Products.DeleteRelationships(productId, 'brand', brandIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

