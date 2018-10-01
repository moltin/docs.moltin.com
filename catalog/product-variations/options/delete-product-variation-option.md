# Delete Product Variation Option

{% api-method method="delete" host="https://api.moltin.com" path="/v2/variation/:variationId/option/:optionId" %}
{% api-method-summary %}
Delete a Product Variation Option
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="optionId" type="string" required=true %}
The **ID** of the option.
{% endapi-method-parameter %}

{% api-method-parameter name="variationId" type="string" required=true %}
The **ID** of the variation belonging to the option.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -v -X "DELETE" https://api.moltin.com/v2/variations/684bceee-0ee3-4f43-ac32-50bb44c1eee5/options/39148bc3-3028-4196-9350-1b4ac927c9d6 \
-H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

