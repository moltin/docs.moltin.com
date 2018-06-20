# Variations Relationship

{% api-method method="post" host="https://api.moltin.com" path="/v2/products/:productId/relationships/variations" %}
{% api-method-summary %}
Create Variations Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** of the product you wish to relate to the variation\(s\).
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **product-variation**\).
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the product-variation.
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
curl -X "POST" https://api.moltin.com/v2/products/:productId/relationships/variations \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "product-variation",
      "id": "3ab3deca-1f11-47b7-a409-24ea3234d72c"
    },
    {
      "type": "product-variation",
      "id": "7c740aa0-7fb7-4bd6-9347-78988cf60f9a"
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

var variationIds = [
    '5ab3deca-1f11-47b7-a409-24ea3234d72c',
    '2c740aa0-7fb7-4bd6-9347-78988cf60f9a'
];

Moltin.Products.CreateRelationships('{PRODUCT_ID}', 'product-variation', variationIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/products/:productId/relationships/variations" %}
{% api-method-summary %}
Update Variation Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Replace the relationships between a product and a variation. Unlike a **POST** to this endpoint, a **PUT** overrides any existing relationships. ****
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** of the product you wish to relate to the variation\(s\).
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **product-variation\).**
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the variation.
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
url -X "PUT" https://api.moltin.com/v2/products/:productId/relationships/variations \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "product-variation",
      "id": "2c740aa0-7fb7-4bd6-9347-78988cf60f9a"
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

var variationIds = [
    '2c740aa0-7fb7-4bd6-9347-78988cf60f9a'
];

Moltin.Products.UpdateRelationships(productId, 'variation', variationIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/products/:productId/relationships/variations" %}
{% api-method-summary %}
Delete Variation Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Remove a relationship between a Product and a Variation\(s\). This deletes the relationships specified in the payload.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** of the product you wish to relate to the variations\(s\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **product-variation\).**
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the variation.
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
curl -X "DELETE" https://api.moltin.com/v2/products/:productId/relationships/variations \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "product-variation",
      "id": "2c740aa0-7fb7-4bd6-9347-78988cf60f9a"
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

var variationIds = [
    '2c740aa0-7fb7-4bd6-9347-78988cf60f9a'
];

Moltin.Products.DeleteRelationships(productId, variationIds, 'variation', variationIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

