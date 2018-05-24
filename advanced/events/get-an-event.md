# Get an Event

{% api-method method="get" host="https://api.moltin.com" path="/v2/integrations/:id" %}
{% api-method-summary %}
Get an Event by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the event
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

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
    "id": "71679ff8-36c1-4f8f-8ed2-cea50555d78c",
    "type": "integration",
    "integration_type": "webhook",
    "name": "Order shipping notification",
    "description": "Send a shipping notification via email with discount code.",
    "enabled": true,
    "configuration": {
      "url": "https://yourwebsite.com/order-created-notification"
    },
    "observes": ["order.fulfilled"],
    "links": {
      "self":
        "https://api.moltin.com/v2/integrations/5f2c7366-c97f-4047-b3f3-a603270db189"
    },
    "meta": {
      "timestamps": {
        "created_at": "2018-04-19T10:21:06.747Z",
        "updated_at": "2018-04-19T10:40:19.805Z"
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
```javascript
curl -X GET https://api.moltin.com/v2/integrations/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

