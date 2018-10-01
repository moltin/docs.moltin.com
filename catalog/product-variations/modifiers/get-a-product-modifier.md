# Get a Product Modifier

{% api-method method="get" host="https://api.moltin.com" path="/v2/variations/:variationId/options/:optionId/modifiers/:modifierId" %}
{% api-method-summary %}
Get a Product Modifier
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="variationId" type="string" required=true %}
ID of the variation
{% endapi-method-parameter %}

{% api-method-parameter name="optionId" type="string" required=true %}
ID of the option
{% endapi-method-parameter %}

{% api-method-parameter name="modifierId" type="string" required=true %}
 ID of the modifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A single modifier successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "aabc3e8e-c6a6-42aa-a64b-9a7dbefedd9f",
    "type": "modifier",
    "modifier_type": "price_increment",
    "value": [{
      "currency": "FJT",
      "amount": 46008803,
      "includes_tax": false
      }, {
      "currency": "YZK",
      "amount": 4011039,
      "includes_tax": false
    }]
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
curl -X GET https://api.moltin.com/v2/variations/:variationId/options/:optionId/modifiers/:modifierId \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

