# Delete Product Modifier

{% api-method method="delete" host="https://api.moltin.com" path="/v2/variation/:variationId/option/:optionId/modifiers/:modifierId" %}
{% api-method-summary %}
Delete a product modifier
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="variationId" type="string" required=true %}
The ID of the variation belonging to this modifier
{% endapi-method-parameter %}

{% api-method-parameter name="optionId" type="string" required=true %}
The ID of the option belonging to the modifier
{% endapi-method-parameter %}

{% api-method-parameter name="modifierId" type="string" required=true %}
The ID of the modifier to be deleted
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
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

```bash
curl -X "DELETE" https://api.moltin.com/v2/variation/:variationID/option/:optionId/modifiers/:modifierId \
     -H "Authorization: Bearer XXXXX"
```

