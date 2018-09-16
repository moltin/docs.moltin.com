# Delete Promotion Codes

{% api-method method="delete" host="https://api.moltin.com" path="/v2/promotions/:id/codes" %}
{% api-method-summary %}
Delete promotion codes
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to delete one or more promotion codes
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the promotion associated with the codes
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="codes\[\].code" type="object" required=true %}
the code you want to delete
{% endapi-method-parameter %}

{% api-method-parameter name="codes\[\]" type="array" required=true %}
an array of codes
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
`promotion_codes`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}
This response indicates your delete request has succeeded
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X DELETE https://api.moltin.com/v2/promotions/:id/codes \
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



