# Get all Product Variation Options

{% api-method method="get" host="https://api.moltin.com" path="/v2/variations/:id/options" %}
{% api-method-summary %}
Get all Product Variation Options
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the variation
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to get access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "data": [
        {
            "type": "option",
            "id": "13633d24-67bf-4736-b753-f093257d05cb",
            "name": "Little",
            "description": "Our smallest size.",
            "relationships": {
                "modifiers": {
                    "data": [
                        {
                            "name_prepend": "Little "
                        },
                        {
                            "slug_append": "-little"
                        },
                        {
                            "sku_append": "-LITTLE"
                        },
                        {
                            "price_decrement": [
                                {
                                    "currency": "GBP",
                                    "amount": 1500,
                                    "includes_tax": true
                                },
                                {
                                    "currency": "USD",
                                    "amount": 2000,
                                    "includes_tax": true
                                }
                            ]
                        }
                    ]
                }
            }
        },
        {
            "type": "option",
            "id": "fd1c0f24-2810-4d19-8fed-40be18f35bc3",
            "name": "Regular",
            "description": "Our regular size.",
            "relationships": {
                "modifiers": {
                    "data": [
                        {
                            "sku_append": "-REGULAR"
                        },
                        {
                            "slug_append": "-regular"
                        },
                        {
                            "name_prepend": "Regular "
                        }
                    ]
                }
            }
        },
        {
            "type": "option",
            "id": "9ba2e929-1e95-4d20-a0c7-67c911d4e9c8",
            "name": "Large",
            "description": "Our large size.",
            "relationships": {
                "modifiers": {
                    "data": [
                        {
                            "name_prepend": "Large "
                        },
                        {
                            "sku_append": "-LARGE"
                        },
                        {
                            "slug_append": "-large"
                        },
                        {
                            "price_increment": [
                                {
                                    "currency": "GBP",
                                    "amount": 1500,
                                    "includes_tax": true
                                },
                                {
                                    "currency": "USD",
                                    "amount": 2000,
                                    "includes_tax": true
                                }
                            ]
                        }
                    ]
                }
            }
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X GET https://api.moltin.com/v2/variations/:id/options \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

