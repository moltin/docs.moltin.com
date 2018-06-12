# Flows

A flow describes a collection of fields. It is named after the internal entity type you wish to associate it with. For example a flow with a slug of `products` will be applied to all product responses in your store.

## The flow object

| **Attribute** | **Type** | **Description**                              |
| ------------- | -------- | -------------------------------------------- |
| `id`          | `string` | The unique identifier for this flow.         |
| `type`        | `string` | Represents the type of object being returned |
| `name`        | `string` | The name of the flow                         |
| `slug`        | `string` | A unique slug identifier for the flow        |
| `description` | `string` | Any description for this flow                |
| `enabled`     | `bool`   | `true` if enabled, `false` if not            |

{% api-method method="get" host="https://api.moltin.com" path="/v2/flows/:id" %}
{% api-method-summary %}
Get a Flow
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the flow you are requesting
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

```javascript
{
    "data": {
        "id": "38ba1451-efa4-4361-9ca6-3fb646490f37",
        "type": "flow",
        "name": "extraFieldRenamed",
        "slug": "products",
        "description": "Extends the default product object",
        "enabled": true,
        "links": {
            "self": "https://api.moltin.com/v2/flows/38ba1451-efa4-4361-9ca6-3fb646490f37"
        },
        "relationships": {},
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T01:41:36.009Z",
                "updated_at": "2018-05-10T15:27:26.241Z"
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
```bash
curl https://api.moltin.com/v2/flows/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const flowId = 'XXXX';

Moltin.Flows.Get(flowId).then(flows => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/flows" %}
{% api-method-summary %}
Create a Flow
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
{% api-method-parameter name="enabled" type="boolean" required=true %}
true if enabled, false if not
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=true %}
Any description for this flow
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
A unique slug identifier for the flow
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the flow
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object being returned.
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
        "id": "6d320b42-237d-4474-8452-d49f884d4ae1",
        "type": "flow",
        "name": "Products-1",
        "slug": "products-1",
        "description": "Extends the default product object",
        "enabled": true,
        "links": {
            "self": "https://api.moltin.com/v2/flows/6d320b42-237d-4474-8452-d49f884d4ae1"
        },
        "relationships": {},
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T18:04:26.623Z",
                "updated_at": "2018-05-10T18:04:26.623Z"
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
```bash
curl -X POST "https://api.moltin.com/v2/flows" \
     -H "Authorization: XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
        "data": {
            "type": "flow",
            "name": "Products",
            "slug": "products",
            "description": "Extends the default product object",
            "enabled": true
        }
     }'
```
{% endtab %}

{% tab title="JavaScript SDL" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const data = {
  name: 'Products flow',
  slug: 'products',
  description: 'Extends the default product object',
  enabled: true
}

Moltin.Flows.Create(data).then(flow => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/flows/:id" %}
{% api-method-summary %}
Update a Flow
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the flow you are changing.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="string" required=false %}

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
        "id": "6d320b42-237d-4474-8452-d49f884d4ae1",
        "type": "flow",
        "name": "extraFieldRenamed",
        "slug": "products-1",
        "description": "Extends the default product object",
        "enabled": true,
        "links": {
            "self": "https://api.moltin.com/v2/flows/6d320b42-237d-4474-8452-d49f884d4ae1"
        },
        "relationships": {},
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T18:04:26.623Z",
                "updated_at": "2018-05-10T18:11:47.469Z"
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
```bash
curl -X POST "https://api.moltin.com/v2/flows/:id" \
     -H "Authorization: XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
        "data": {
            "id": "{FLOW_ID}",
            "type": "flow",
            "name": "Categories",
            "slug": "categories",
            "description": "Extends the default category object",
            "enabled": true
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

const flowId = 'XXX'

const data = {
  name: 'Categories',
  slug: 'categories',
  description: 'Extends the default category object'
}

Moltin.Flows.Update(flowId, data).then(flow => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/flows/:id" %}
{% api-method-summary %}
Delete a Flow
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the field you are requesting to be deleted
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
```bash
curl -X DELETE https://api.moltin.com/v2/flows/:id \
    -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="Second Tab" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const flowId = 'XXX'

Moltin.Flows.Delete(flowId).then(flow => {
  // Do something
});
```
{% endtab %}
{% endtabs %}

