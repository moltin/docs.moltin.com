# Child Relationships

{% api-method method="post" host="https://api.moltin.com" path="/v2/brands/:brandId/relationships/children" %}
{% api-method-summary %}
Create Child Brand Relationships
{% endapi-method-summary %}

{% api-method-description %}
Create a relationship to a parent brand. If any relationship(s) already exists, new ones will be added to the,
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="brandId" type="string" required=true %}
The ID of the brand you wish to make relationships to.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
The type of related object (should be be brand).
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The ID of the parent brand.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% code-tabs %}
{% code-tabs-item title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/brands/:brandId/relationships/children \
     -H "Content-Type: application/json" \
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
{% endcode-tabs-item %}
{% endcode-tabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/brands/:brandId/relationships/children" %}
{% api-method-summary %}
Update Child Brand Relationship
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="brandId" type="string" required=true %}
The ID of the brand you wish to make relationships to.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
The type of related object (should be brand).
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The ID of the parent brand.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% code-tabs %}
{% code-tabs-item title="cURL" %}
```bash
curl -X PUT https://api.moltin.com/v2/brands/:brandId/relationships/children \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
      "data": [
        {
          "type": "brand",
          "id": "c902aea9-ec90-4fdd-8084-3c2d879a2c52"
        }
      ]
    }'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% api-method method="get" host="https://api.moltin.com/" path="/v2/brands/:brandId/relationships/parent" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="brandId" type="string" required=true %}
The ID of the brand you wish to update relationships to.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="data" type="object" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="data[].type" type="string" required=false %}
The type of related object. (should be brand)
{% endapi-method-parameter %}

{% api-method-parameter name="data[].id" type="string" required=false %}
The ID of the child brand.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% code-tabs %}
{% code-tabs-item title="cURL" %}
```bash
curl -X DELETE https://api.moltin.com/v2/brands/:brandId/relationships/parent \
     -H "Authorization: Bearer XXXX" \
     -d $'{
       "data": [{
         "type": "brand",
         "id": "c902aea9-ec90-4fdd-8084-3c2d879a2c52"
         }]
      }'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

