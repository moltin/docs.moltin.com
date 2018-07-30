# Delete Promotion Codes

{% api-method method="delete" host="https://api.moltin.com" path="/v2/promotions/:id/codes" %}
{% api-method-summary %}
Delete Promotion Codes
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
The unique promotion identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```javascript
curl -X DELETE https://api.moltin.com/v2/promotions/:id/codes \
     -H "Authorization: Bearer XXXX"
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
