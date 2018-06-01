# Parent Relationships

{% api-method method="post" host="https://api.moltin.com" path="/v2/collections/:id/relationships/parent" %}
{% api-method-summary %}
Create Parent Collection Relationship
{% endapi-method-summary %}

{% api-method-description %}
Create a relationship to a parent collection. If a relationship already exists, the one from the request will overwrite it.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the collection you wish to make relationships to
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
The type of related object. \(should be collection\)
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The ID of the parent collection
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

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/collections/:id/relationships/parent \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
      "data": {
        "type": "collection",
        "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
      }
    }'
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/collections/:id/relationships/parent" %}
{% api-method-summary %}
Update Parent Collection Relationship
{% endapi-method-summary %}

{% api-method-description %}
Change the parent of a collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the collection you wish to make relationships to
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
The type of related object. \(should be collection\)
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=false %}
The ID of the parent collection
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

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X PUT https://api.moltin.com/v2/collections/:id/relationships/parent \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
      "data": {
        "type": "collection",
        "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
      }
    }'
```
{% endtab %}
{% endtabs %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/collections/:id/relationships/parent" %}
{% api-method-summary %}
Delete Parent Collection Relationship
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the parent collection you with to delete the relationship to
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

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X DELETE https://api.moltin.com/v2/collections/:id/relationships/parent \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

