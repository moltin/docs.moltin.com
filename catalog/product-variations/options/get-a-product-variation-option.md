# Get a Product Variation Option

{% api-method method="get" host="https://api.moltin.com" path="/v2/variations/:variationId/options/:optionId" %}
{% api-method-summary %}
Get a Product Variation Option
{% endapi-method-summary %}

{% api-method-description %}
Use this endpoint to retrieve a single variation option.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="variationId" type="string" required=true %}
ID of the variation.
{% endapi-method-parameter %}

{% api-method-parameter name="optionId" type="string" required=true %}
ID of the option.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Single option successfully retrieved.
{% endapi-method-response-example-description %}

```bash
{
  "data": {
    "type": "option",
    "id": "aabc3e8e-c6a6-42aa-a64b-9a7dbefedd9f",
    "name": "Blue",
    "description": "Our most popular color",
    "relationships": {
      "modifiers": {
        "data": []
      }
    }
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
curl -X GET https://api.moltin.com/v2/variations/:id/options/:Id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}



