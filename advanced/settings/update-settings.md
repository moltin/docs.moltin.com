# Update Settings

You can use the Settings endpoint to update your project settings at anytime. These global settings take immediate effect.

{% api-method method="put" host="https://api.moltin.com" path="/v2/settings" %}
{% api-method-summary %}
Update project settings
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="additional\_languages" type="array" required=false %}
An array of `alpha2` codes for supported languages
{% endapi-method-parameter %}

{% api-method-parameter name="list\_child\_products" type="boolean" required=false %}
Display child products or not in product listings
{% endapi-method-parameter %}

{% api-method-parameter name="page\_length" type="integer" required=false %}
Number of results per page \(**max**: `100`\)
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
This describes the type of request payload you're sending
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
        "type": "settings",
        "page_length": 50,
        "list_child_products": true,
        "additional_languages": []
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
curl -X PUT https://api.moltin.com/v2/settings \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
       "data": {
         "type": "settings",
         "page_length": 70,
         "list_child_products": false,
         "additional_languages": ["es","fr","de","pr-BR"]
       }
     }'
```
{% endtab %}
{% endtabs %}

