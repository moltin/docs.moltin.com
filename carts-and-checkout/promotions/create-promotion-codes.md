# Create Promotion codes

{% api-method method="post" host="https://api.moltin.com" path="/v2/promotions/:id/codes" %}
{% api-method-summary %}
Create Promotion Codes
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The unique promotion identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
`promotion_codes`
{% endapi-method-parameter %}

{% api-method-parameter name="codes\[\]" type="array" required=true %}
An array of objects
{% endapi-method-parameter %}

{% api-method-parameter name="codes\[\].code" type="string" required=true %}
A string to use as a code for the promotion
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
curl -X POST https://api.moltin.com/v2/promotions/:id/codes \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data":{
        "type":"promotion_codes",
        "codes": [
          {"code":"ZXY_CBA"},
          {"code":"ABC_XYZ"}
        ]
      }
    }'
```
{% endtab %}
{% endtabs %}

