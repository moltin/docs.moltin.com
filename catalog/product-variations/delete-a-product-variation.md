# Delete a Product Variation

{% api-method method="delete" host="https://api.moltin.com" path="/v2/variation/:id" %}
{% api-method-summary %}
Delete a product variation
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
The ID of the variation you wish to delete.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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
curl -X DELETE https://api.moltin.com/v2/variation/:id \
     -H "Authorization: Bearer 965baf46f390879c213e48cf84dcda16bb6d0819"
```

