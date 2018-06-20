# Category Relationship

{% api-method method="post" host="https://api.moltin.com" path="/v2/products/:productId/relationships/categories" %}
{% api-method-summary %}
Create Category Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Create a Product relationship to on or more C**ategories.**  If any relationships already exist, the one's made in the request will be added to them.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** of the product you wish to relate to the category\(s\).
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **category**\).
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the category.
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
curl -X "POST" https://api.moltin.com/v2/products/:productId/relationships/categories \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "category",
      "id": "39a13b7e-f2d3-47a5-9bc5-1e98b198748c"
    },
    {
      "type": "category",
      "id": "0c108707-bb4a-4eda-95e3-f51b35122cb4"
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

var categoryIds = [
    '39a13b7e-f2d3-47a5-9bc5-1e98b198748c',
    '0c108707-bb4a-4eda-95e3-f51b35122cb4'
];

Moltin.Products.CreateRelationships(productId, 'category', categoryIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/products/:productId/relationships/categories" %}
{% api-method-summary %}
Update Category Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Replace the relationships between a Product and a Category. Unlike a **POST** to this endpoint a **PUT** overrides any existing relationships. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** of the product you wish to relate to the category\(s\).
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of objects \(should be **category**\).
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the category.
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
curl -X "PUT" https://api.moltin.com/v2/products/:productId/relationships/categories \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "category",
      "id": "d7290481-8d03-4fe0-a7df-23fc05498a46"
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

var categoryIds = [
    'd7290481-8d03-4fe0-a7df-23fc05498a46'
];

Moltin.Products.UpdateRelationships(productId, 'category', categoryIds).then((relationships) => {
    // Do something
});

```
{% endtab %}
{% endtabs %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/products/:productId/relationships/categories" %}
{% api-method-summary %}
Delete Category Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Removing a relationships between a Product and Category\(s\) deletes the relationships specified in the payload.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **ID** of the product you wish to delete.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **category**\).
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the category.
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
curl -X "DELETE" https://api.moltin.com/v2/products/:productId/relationships/categories \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "category",
      "id": "0c108707-bb4a-4eda-95e3-f51b35122cb4"
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

var categoryIds = [
    '0c108707-bb4a-4eda-95e3-f51b35122cb4
];

Moltin.Products.DeleteRelationships(productId, 'category', categoryIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}



