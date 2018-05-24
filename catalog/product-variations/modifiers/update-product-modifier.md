# Update Product Modifier

{% api-method method="put" host="https://api.moltin.com" path="/v2/variations/:variationId/options/:optionId/modifiers/:modifierId" %}
{% api-method-summary %}
Update a product modifier
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="variationId" type="string" required=true %}
The ID of the variation belonging to this modifier.
{% endapi-method-parameter %}

{% api-method-parameter name="optionId" type="string" required=true %}
The ID of the option belonging to the modifier.
{% endapi-method-parameter %}

{% api-method-parameter name="modifierId" type="string" required=true %}
The ID of the modifier to be updated
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
The unique identifier for this modifier
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object being updated. \(should be modifier\)
{% endapi-method-parameter %}

{% api-method-parameter name="modifier\_type" type="string" required=false %}
`price_increment`, `price_decrement`, `price_equals`, `sku_builder`, `slug_builder`, `description_equals`, `description_prepend`, `description_append`, `commoditytype`, `name_equals`, `name_prepend`, `name_append`, `slug_equals`, `slug_prepend`, `slug_append`, `sku_equals`, `sku_prepend`, `sku_append`, `status`
{% endapi-method-parameter %}

{% api-method-parameter name="value" type="string" required=false %}
A payload specific to the type of modifier
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

```bash
curl -X "PUT" https://api.moltin.com/v2/variations/:variationId/options/:optionId/modifiers/:modifierId \
     -H "Authorization: Bearer XXXX" \
     -d $'{
  "data": {
    "type": "modifier",
    "id": modifierId,
    "modifer_type": "name_equals"
    "value": "Updated product name"
  }
}'
```

