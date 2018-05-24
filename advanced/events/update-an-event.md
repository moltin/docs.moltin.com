# Update an Event

{% api-method method="put" host="https://api.moltin.com" path="/v2/integrations/:id" %}
{% api-method-summary %}
Update by ID
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
{% api-method-parameter name="configuration" type="object" required=false %}
The webhook configuration object
{% endapi-method-parameter %}

{% api-method-parameter name="observes" type="array" required=false %}
An array of events you want to observe
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="boolean" required=false %}
Should the event trigger or not. Default:`false`
{% endapi-method-parameter %}

{% api-method-parameter name="integration\_type" type="string" required=false %}
`webhook`
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
A description for the event
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The name of the event
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object
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
    "id": "8cb9e689-ede7-4f6d-b61a-6aa970d572dd",
    "type": "integration",
    "integration_type": "webhook",
    "name": "Order shipping notification",
    "description": "Send a shipping notification via email with discount code.",
    "enabled": false,
    "configuration": {
      "url": "https://yourwebsite.com/order-created-notification"
    },
    "observes": ["order.fulfilled"],
    "links": {
      "self":
        "https://api.moltin.com/v2/integrations/8cb9e689-ede7-4f6d-b61a-6aa970d572dd"
    },
    "meta": {
      "timestamps": {
        "created_at": "2018-04-30T09:35:32.202Z",
        "updated_at": "2018-04-30T09:48:24.816Z"
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
curl -X PUT https://api.moltin.com/v2/integrations/:id \
     -H "Authorization: Bearer: XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": {
        "type": "integration",
        "enabled": false
      }
    }'
```
{% endtab %}
{% endtabs %}

