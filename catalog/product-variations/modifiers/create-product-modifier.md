# Create Product Modifier

{% api-method method="post" host="https://api.moltin.com" path="/v2/variations/:variationId/options/:optionId/modifiers" %}
{% api-method-summary %}
Create a new product modifier
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="variationId" type="string" required=true %}
The **ID** of the variation belonging to this modifier.
{% endapi-method-parameter %}

{% api-method-parameter name="optionId" type="string" required=true %}
The **ID** of the option belonging to the modifier.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object being created \(should be **modifier**\).
{% endapi-method-parameter %}

{% api-method-parameter name="modifier\_type" type="string" required=false %}
`price_increment`, `price_decrement`, `price_equals`, `sku_builder`, `slug_builder`, `description_equals`, `description_prepend`, `description_append`, `commoditytype`, `name_equals`, `name_prepend`, `name_append`, `slug_equals`, `slug_append`, `sku_equals`, `sku_prepend`, `sku_append`, `status`
{% endapi-method-parameter %}

{% api-method-parameter name="value" type="string" required=false %}
A payload specific to the type of modifier.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "5ecf77e7-047a-4a3d-ad8c-b559ecd3df36",
        "name": "Paint colour",
        "options": [
            {
                "description": "Our most popular color",
                "id": "71784b68-9d82-420b-a5fc-00fe4bca8b2e",
                "modifiers": [
                    {
                        "id": "8080083a-4765-47ac-9ea8-ea875acd0f92",
                        "type": "name_equals",
                        "value": "Updated product name"
                    }
                ],
                "name": "Blue"
            }
        ],
        "relationships": {
            "options": {
                "data": [
                    {
                        "id": "71784b68-9d82-420b-a5fc-00fe4bca8b2e",
                        "type": "option"
                    }
                ]
            }
        },
        "type": "product-variation"
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
curl -X POST https://api.moltin.com/v2/variations/:variationId/options/:optionId/modifiers \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": {
        "type": "modifier",
        "modifier_type": "name_equals",
        "value": "Updated product name"
      }
    }
```
{% endtab %}
{% endtabs %}

