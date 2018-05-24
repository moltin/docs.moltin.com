# Get all Settings

You can get all of the project settings via one API call using a `client_credential` token. The response will be in object format as shown below.

{% api-method method="get" host="https://api.moltin.com" path="/v2/settings" %}
{% api-method-summary %}
Get all project settings
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "type": "settings",
        "page_length": 100,
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
curl -X GET https://api.moltin.com/v2/settings \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

