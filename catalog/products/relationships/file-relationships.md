# File Relationships

{% api-method method="post" host="https://api.moltin.com" path="/v2/products/:productId/relationships/files" %}
{% api-method-summary %}
Create File Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Create a product relationship to one ore more **file**.  If any relationship already exist, the one's made in the request will be added to them.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **id**  of the product you wish to relate to the file\(s\).
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **file\).**
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **id** of the file.
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
curl -X "POST" https://api.moltin.com/v2/products/:productId/relationships/files \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "file",
      "id": "82c51711-35f9-403e-aa73-8e6c80c2258b"
    },
    {
      "type": "file",
      "id": "c090e3c8-0206-4243-9a3b-f28175f7e9de"
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

var fileIds = [
    '82c51711-35f9-403e-aa73-8e6c80c2258b',
    'c090e3c8-0206-4243-9a3b-f28175f7e9de'
];

Moltin.Products.CreateRelationships(productId, 'file', fileIds).then((relationships) => {
    // Do something
});T
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="" %}
{% api-method-summary %}
Update File Relationship\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Replace the relationships between a product and a file.  Unlike a **POST**  to this endpoint, a **PUT** overrides any existing relationships.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=true %}
The **id** of the product you wish to relate to the file\(s\).
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **file\).**
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **id** of the file.
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
curl -X "PUT" https://api.moltin.com/v2/products/:productId/relationships/files \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "file",
      "id": "82c51711-35f9-403e-aa73-8e6c80c2258b"
    }
  ]
}
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

var fileIds = [
    '82c51711-35f9-403e-aa73-8e6c80c2258b'
];

Moltin.Products.UpdateRelationships(productId, 'file', fileIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/products/:productId/relationships/file" %}
{% api-method-summary %}
Delete File Relationships\(s\)
{% endapi-method-summary %}

{% api-method-description %}
Removing a relationship between a product and file\(s\) deletes the relationships specified in the payload.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="productId" type="string" required=false %}
The **id** of the product you wish to delete the relationship with file\(s\).
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object \(should be **file\).**
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The **id** of the file.
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
curl -X "DELETE" https://api.moltin.com/v2/products/:productId/relationships/files \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": [
    {
      "type": "file",
      "id": "82c51711-35f9-403e-aa73-8e6c80c2258b"
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

var fileIds = [
    '82c51711-35f9-403e-aa73-8e6c80c2258b'
];

Moltin.Products.DeleteRelationships(productId, 'file', fileIds).then((relationships) => {
    // Do something
});
```
{% endtab %}
{% endtabs %}

