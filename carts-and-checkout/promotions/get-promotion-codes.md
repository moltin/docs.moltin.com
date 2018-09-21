# Get Promotion Codes

{% api-method method="get" host="https://api.moltin.com" path="/v2/promotions/:id/codes" %}
{% api-method-summary %}
Get Codes by Promotion ID
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": [
        {
            "code": "ZXY_CBA"
        },
        {
            "code": "ABC_XYZ"
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
curl https://api.moltin.com/v2/promotions/:id/codes \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

