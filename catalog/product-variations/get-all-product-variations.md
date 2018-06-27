# Get All Product Variations

{% api-method method="get" host="https://api.moltin.com" path="/v2/variations" %}
{% api-method-summary %}
Get product variations
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token that is used access to the API
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

curl -X GET [https://api.moltin.com/v2/variations](https://api.moltin.com/v2/variations)  -H "Authorization: Bearer 965baf46f390879c213e48cf84dcda16bb6d0819"

