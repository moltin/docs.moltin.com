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
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the variation you wish to update
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the variation being updated
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being created. \(should be product-variation\)
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
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

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X PUT https://api.moltin.com/v2/variation/:id \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": {
        "type": "product-variation",
        "id": "XXXX",
        "name": "Color schemes"
      }
    }'
```
{% endtab %}
{% endtabs %}

