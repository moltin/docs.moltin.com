# Fields

A Field represents a single Field of data \(for example a `Product Rating`\) to be applied to an entity. All Fields have a type \(`string`, `integer`, `boolean`, `date` or `relationship`\), a default value and an optional set of validation rules.

## The Field Object

| Attribute | Type | Description |
| --- | --- | --- |
| id | **string** | The unique identifier for this field |
| type | **string** | Represents the type of object being returned |
| name | **string** | The name of the field |
| slug | **string** | A unique slug identifier for the field |
| field\_type | **string** | The type of field - `string`, `integer`, `boolean`, `float`, `date`, `relationship` |
| validation\_rules | **array\[object\]** | See [`Flow Field Validation Rules`](https://docs.moltin.com/#flow-field-validation-rules) |
| description | **string** | Any description for this field |
| required | **bool** | `true` if required on input, `false` if not. Always `false` if the `field_type` is a relationship |
| unique | **bool** | `true` if each entry should be unique, `false` if not\` |
| default | **mixed** | A default value if none is supplied and field is not required |
| enabled | **bool** | If this field is enabled on the flow this should be `true`, otherwise `false` |
| order | **integer** | Denotes the order in which this field is returned relative to the rest of the flow fields |
| relationships | **object** | A relationship object to link this field to a flow |

{% api-method method="get" host="https://api.moltin.com" path="/v2/fields" %}
{% api-method-summary %}
Get a list of Fields
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "102b2087-d56a-45e7-bf1c-e9517716abb3",
        "type": "field",
        "field_type": "integer",
        "slug": "product-rating",
        "name": "Product Rating",
        "description": "Average rating as given by our users",
        "required": false,
        "unique": false,
        "default": null,
        "enabled": true,
        "validation_rules": [
            {
                "type": "between",
                "options": {
                    "from": 1,
                    "to": 5
                }
            }
        ],
        "order": 1,
        "links": {
            "self": "https://api.moltin.com/v2/flows/6d320b42-237d-4474-8452-d49f884d4ae1/fields/102b2087-d56a-45e7-bf1c-e9517716abb3"
        },
        "relationships": {
            "flow": {
                "data": {
                    "id": "6d320b42-237d-4474-8452-d49f884d4ae1",
                    "type": "flow"
                }
            }
        },
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T18:19:11.559Z",
                "updated_at": "2018-05-10T18:19:11.559Z"
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl https://api.moltin.com/v2/fields \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Fields.All().then(fields => {
  // Do something
});

```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/fields/:id" %}
{% api-method-summary %}
Get a field
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the field you are requesting.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "102b2087-d56a-45e7-bf1c-e9517716abb3",
        "type": "field",
        "field_type": "integer",
        "slug": "product-rating",
        "name": "Product Rating",
        "description": "Average rating as given by our users",
        "required": false,
        "unique": false,
        "default": null,
        "enabled": true,
        "validation_rules": [
            {
                "type": "between",
                "options": {
                    "from": 1,
                    "to": 5
                }
            }
        ],
        "order": 1,
        "links": {
            "self": "https://api.moltin.com/v2/flows/6d320b42-237d-4474-8452-d49f884d4ae1/fields/102b2087-d56a-45e7-bf1c-e9517716abb3"
        },
        "relationships": {
            "flow": {
                "data": {
                    "id": "6d320b42-237d-4474-8452-d49f884d4ae1",
                    "type": "flow"
                }
            }
        },
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T18:19:11.559Z",
                "updated_at": "2018-05-10T18:19:11.559Z"
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl https://api.moltin.com/v2/fields/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const fieldID = 'XXXX';

Moltin.Fields.Get(fieldID).then(field => {
  // Do something
});

curl https://api.moltin.com/v2/fields \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/fields" %}
{% api-method-summary %}
Create a field
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
{% api-method-parameter name="flowId" type="string" required=false %}
The **ID** of the flow you wish to tie the field too.
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the field
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
A unique slug identifier for the field
{% endapi-method-parameter %}

{% api-method-parameter name="field\_type" type="string" required=true %}
The type of field - string, integer, boolean, float, date, relationship
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=true %}
Any description for this field
{% endapi-method-parameter %}

{% api-method-parameter name="required" type="boolean" required=false %}
True if required on input, false if not. Always false if the field\_type is a relationship
{% endapi-method-parameter %}

{% api-method-parameter name="unique" type="boolean" required=true %}
true if each entry should be unique, false if not
{% endapi-method-parameter %}

{% api-method-parameter name="default" type="string" required=false %}
A default value if none is supplied and field is not required
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="boolean" required=true %}
If this field is enabled on the flow this should be true, otherwise false
{% endapi-method-parameter %}

{% api-method-parameter name="order" type="integer" required=false %}
Denotes the order in which this field is returned relative to the rest of the flow fields
{% endapi-method-parameter %}

{% api-method-parameter name="relationships" type="object" required=false %}
A relationship object to link this field to a flow
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
        "id": "102b2087-d56a-45e7-bf1c-e9517716abb3",
        "type": "field",
        "field_type": "integer",
        "slug": "product-rating",
        "name": "Product Rating",
        "description": "Average rating as given by our users",
        "required": false,
        "unique": false,
        "default": null,
        "enabled": true,
        "validation_rules": [
            {
                "type": "between",
                "options": {
                    "from": 1,
                    "to": 5
                }
            }
        ],
        "order": 1,
        "links": {
            "self": "https://api.moltin.com/v2/flows/6d320b42-237d-4474-8452-d49f884d4ae1/fields/102b2087-d56a-45e7-bf1c-e9517716abb3"
        },
        "relationships": {
            "flow": {
                "data": {
                    "id": "6d320b42-237d-4474-8452-d49f884d4ae1",
                    "type": "flow"
                }
            }
        },
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T18:19:11.559Z",
                "updated_at": "2018-05-10T18:19:11.559Z"
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X "POST" "https://api.moltin.com/v2/fields" \
     -H "Authorization: XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
  "data": {
    "type": "field",
    "name": "Product Rating",
    "slug": "product-rating",
    "field_type": "integer",
    "validation_rules": [
        {
            "type": "between",
            "options": {
                "from": 1,
                "to": 5
            }
        }
    ],
    "description": "Average rating as given by our users",
    "required": false,
    "unique": false,
    "default": 0,
    "enabled": true,
    "order": 1,
    "relationships": {
        "flow": {
            "data": {
                "type": "flow",
                "id": :flowID
            }
        }
    }
  }
}'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const data = {
  name: 'Product Rating',
  slug: 'product-rating',
  description: 'Average rating as given by our users',
  enabled: true
}

Moltin.Fields.Create(data).then(field => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/fields/:id" %}
{% api-method-summary %}
Update a Field
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the field you are requesting to be updated
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

{% api-method-parameter name="name" type="string" required=true %}
The name of the field
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
A unique slug identifier for the field
{% endapi-method-parameter %}

{% api-method-parameter name="field\_type" type="string" required=true %}
The type of field - string, integer, boolean, float, date, relationship
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=true %}
Any description for this field
{% endapi-method-parameter %}

{% api-method-parameter name="required" type="boolean" required=false %}
`true` if required on input, `false` if not. Always false if the field\_type is a relationship
{% endapi-method-parameter %}

{% api-method-parameter name="unique" type="boolean" required=true %}
`true` if each entry should be unique, `false` if not
{% endapi-method-parameter %}

{% api-method-parameter name="default" type="string" required=false %}
A default value if none is supplied and field is not required
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="boolean" required=true %}
If this field is enabled on the flow this should be `true`, otherwise `false`
{% endapi-method-parameter %}

{% api-method-parameter name="order" type="integer" required=false %}
Denotes the order in which this field is returned relative to the rest of the flow fields
{% endapi-method-parameter %}

{% api-method-parameter name="relationships" type="object" required=false %}
A relationship object to link this field to a flow
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
        "id": "102b2087-d56a-45e7-bf1c-e9517716abb3",
        "type": "field",
        "field_type": "integer",
        "slug": "start-of-life",
        "name": "start-of-life",
        "description": "day the iphone will work",
        "required": true,
        "unique": false,
        "default": "2018-01-01",
        "enabled": true,
        "validation_rules": [
            {
                "type": "between",
                "options": {
                    "from": 1,
                    "to": 5
                }
            }
        ],
        "order": 1,
        "links": {
            "self": "https://api.moltin.com/v2/flows/6d320b42-237d-4474-8452-d49f884d4ae1/fields/102b2087-d56a-45e7-bf1c-e9517716abb3"
        },
        "relationships": {
            "flow": {
                "data": {
                    "id": "6d320b42-237d-4474-8452-d49f884d4ae1",
                    "type": "flow"
                }
            }
        },
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T18:19:11.559Z",
                "updated_at": "2018-05-10T18:36:01.208Z"
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X "POST" "https://api.moltin.com/v2/fields/:id" \
     -H "Authorization: XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
  "data": {
    "id": "{FIELD_ID}",
    "type": "field",
    "name": "Average Product Rating",
  }
}'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})
var fieldId = 'xx'

const data = {
  id: '{fieldId}',
  name: 'Average Product Rating'
}

Moltin.Fields.Update('{fieldId}', data).then(field => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/fields/:id" %}
{% api-method-summary %}
Delete a Field
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** fir the field you are requesting to be deleted
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X DELETE https://api.moltin.com/v2/fields/:id \
    -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

var fieldId = 'xx'

const data = {
  id: '{fieldId}',
  name: 'Average Product Rating'
}

Moltin.Fields.Delete('{fieldId}').then(response => {
  // Do something
});

```
{% endtab %}
{% endtabs %}

