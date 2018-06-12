# Update a Product Variation

{% api-method method="put" host="https://api.moltin.com" path="/v2/variation/:id" %}
{% api-method-summary %}
Update a Product Variation
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the variation you wish to update
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
The **ID** of the variation being updated
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object being created. \(should be product-variation\)
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
A human readable name for this variation.
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
        "type": "product-variation",
        "id": "1838ded2-3726-4288-bd82-7c4f14376aac",
        "name": "Colour"
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```bash
curl -X PUT https://api.moltin.com/v2/variation/{VARIATION_ID} \
     -H "Authorization: Bearer 965baf46f390879c213e48cf84dcda16bb6d0819" \
     -d $'{
  "data": {
    "type": "product-variation",
    "id": :id,
    "name": "Color schemes"
  }
}'
```

