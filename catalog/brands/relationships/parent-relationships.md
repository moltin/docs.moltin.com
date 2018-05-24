# Parent Relationships

{% api-method method="post" host="https://api.moltin.com" path="/v2/brands/:id/relationships/parent" %}
{% api-method-summary %}
Create Parent Brand Relationship
{% endapi-method-summary %}

{% api-method-description %}
Create a relationship to a parent brand. If a relationship already exists, the one from the request will overwrite it
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the brand you wish to make relationships to
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
The type of related object \(should be brand\)
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The ID of the parent brand
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
curl -X "POST" https://api.moltin.com/v2/brands/:id/relationships/parent \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
      "data": {
        "type": "brand",
        "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
      }
    }'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/brands/:id/relationships/parent" %}
{% api-method-summary %}
Update Parent Brand Relationship
{% endapi-method-summary %}

{% api-method-description %}
Change the parent of a brand.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the brand you wish to make relationships to.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
The type of related object \(should be brand\).
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
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
curl -X "PUT" https://api.moltin.com/v2/brands/:id/relationships/parent \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
      "data": {
        "type": "brand",
        "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
      }
    }'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/brands/:id/relationships/parent" %}
{% api-method-summary %}
Delete Parent Brand Relationship
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the parent brand you with to delete the relationship to
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

```bash
curl -X "DELETE" https://api.moltin.com/v2/brands/:id/relationships/parent \
     -H "Authorization: Bearer XXXX"}'
```

