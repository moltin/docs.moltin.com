# Get Promotions

{% api-method method="get" host="https://api.moltin.com" path="/v2/promotions" %}
{% api-method-summary %}
Get all Promotions
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

{% code title="cURL" %}
```javascript
{
    "data": [
        {
            "type": "promotion",
            "id": "3cc6829b-e57f-4ead-b52e-8e23e119bfba",
            "name": "Promo #1",
            "description": "Initial Promotion",
            "enabled": true,
            "promotion_type": "fixed_discount",
            "schema": {
                "currencies": [
                    {
                        "currency": "USD",
                        "amount": 900
                    },
                    {
                        "currency": "GBP",
                        "amount": 1100
                    }
                ]
            },
            "start": "2017-01-13T00:00:00Z",
            "end": "2018-01-13T00:00:00Z",
            "created_at": "2018-05-09T20:02:01.036Z",
            "updated_at": "2018-05-09T20:02:01.036Z"
        },
        {
            "type": "promotion",
            "id": "4d04f1e7-9254-4e68-b360-f5eb5d11220f",
            "name": "Promo #1",
            "description": "Initial Promotion",
            "enabled": true,
            "promotion_type": "fixed_discount",
            "schema": {
                "currencies": [
                    {
                        "currency": "USD",
                        "amount": 900
                    },
                    {
                        "currency": "GBP",
                        "amount": 1100
                    }
                ]
            },
            "start": "2017-01-13T00:00:00Z",
            "end": "2018-01-13T00:00:00Z",
            "created_at": "2018-05-09T20:01:35.409Z",
            "updated_at": "2018-05-09T20:01:35.409Z"
        }
    ]
}
```
{% endcode %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X GET https://api.moltin.com/v2/promotions \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}



