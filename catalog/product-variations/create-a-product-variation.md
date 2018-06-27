# Create a Product Variation

{% api-method method="post" host="https://api.moltin.com" path="/v2/variations " %}
{% api-method-summary %}
Create a product variation
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
Represents the type of object being created. \(should be product-variation\)
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
A human readable name for this variation.
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
        "type": "product-variation",
        "id": "615e4e5a-e43d-4679-9900-191af4724f6d",
        "name": "Paint colour"
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
curl -X POST https://api.moltin.com/v2/variations \
     -H "Authorization: Bearer 965baf46f390879c213e48cf84dcda16bb6d0819" \
     -d $'{
  "data": {
    "type": "product-variation",
    "name": "Paint colour"
  }
}'
```
{% endtab %}
{% endtabs %}

