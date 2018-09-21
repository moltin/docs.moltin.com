# Get a Promotion

{% api-method method="get" host="https://api.moltin.com" path="/v2/promotions/:id" %}
{% api-method-summary %}
Get by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the promotion
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "type": "promotion",
        "id": "3cc6829b-e57f-4ead-b52e-8e23e119bfba",
        "name": "Promo #1",
        "description": "Initial Promotion",
        "enabled": true,
        "promotion_type": "fixed_discount",
        "schema": {
            "currencies": [
                {
                    "currency": "GBP",
                    "amount": 1100
                },
                {
                    "currency": "USD",
                    "amount": 900
                }
            ]
        },
        "start": "2017-01-13T00:00:00Z",
        "end": "2018-01-13T00:00:00Z",
        "meta": {
            "timestamps": {
                "created_at": "2018-05-09T20:02:01.036Z",
                "updated_at": "2018-05-09T20:02:01.036Z"
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
curl -X GET https://api.moltin.com/v2/promotions/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

