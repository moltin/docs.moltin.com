# Create Product Variation Option

{% api-method method="post" host="https://api.moltin.com" path="/v2/variations/:id/options" %}
{% api-method-summary %}
Create a Product Variation Option
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the variation belonging to this option
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of the object being created. \(should be `option`\)
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
A human readable name for this variation option
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=true %}
A human readable description of the option
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
        "id": "615e4e5a-e43d-4679-9900-191af4724f6d",
        "name": "Paint colour",
        "options": [
            {
                "id": "aabc3e8e-c6a6-42aa-a64b-9a7dbefedd9f",
                "name": "Blue",
                "description": "Our most popular color",
                "modifiers": []
            }
        ],
        "relationships": {
            "options": {
                "data": [
                    {
                        "type": "option",
                        "id": "aabc3e8e-c6a6-42aa-a64b-9a7dbefedd9f"
                    }
                ]
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
curl -X POST https://api.moltin.com/v2/variations/:variationId/options \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
        "data": {
            "type": "option",
            "name": "Blue",
            "description": "Our most popular color"
        }
    }'
```
{% endtab %}
{% endtabs %}

