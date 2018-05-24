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

{% code-tabs %}
{% code-tabs-item title="cURL" %}
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
        },
        {
            "type": "promotion",
            "id": "6c6149d6-a477-4634-94ce-e91011e0198a",
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
            "created_at": "2018-05-09T19:59:11.533Z",
            "updated_at": "2018-05-09T19:59:11.533Z"
        },
        {
            "type": "promotion",
            "id": "7005b249-300b-4cf6-964e-e663278af218",
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
            "start": "2017-11-13T00:00:00Z",
            "end": "2019-11-13T00:00:00Z",
            "created_at": "2018-05-10T15:25:21.164Z",
            "updated_at": "2018-05-10T15:26:18.203Z"
        },
        {
            "type": "promotion",
            "id": "ad89899d-e69e-47df-8169-10b100265c97",
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
            "created_at": "2018-05-09T20:18:20.91Z",
            "updated_at": "2018-05-09T20:18:20.91Z"
        }
    ]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/promotions \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

