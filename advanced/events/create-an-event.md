# Create an Event

## Create an Event

{% api-method method="post" host="https://api.moltin.com" path="/v2/integrations" %}
{% api-method-summary %}
Create an Event
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
{% api-method-parameter name="configuration" type="object" required=true %}
The webhook configuration object
{% endapi-method-parameter %}

{% api-method-parameter name="observes" type="array" required=true %}
An array of events you want to observe
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="boolean" required=false %}
Should the event trigger or not. Default:`false`
{% endapi-method-parameter %}

{% api-method-parameter name="integration\_type" type="string" required=true %}
`webhook`
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=true %}
A description for the event
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the event
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
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
        "enabled": true,
        "configuration": {
            "url": "https://yourwebsite.com/order-created-notification"
        },
        "observes": [
            "order.fulfilled"
        ],
        "links": {
            "self": "https://api.moltin.com/v2/integrations/8cb9e689-ede7-4f6d-b61a-6aa970d572dd"
        },
        "meta": {
            "timestamps": {
                "created_at": "2018-04-30T09:35:32.202Z",
                "updated_at": "2018-04-30T09:35:32.202Z"
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
curl -X POST https://api.moltin.com/v2/integrations \
     -H "Authorization: Bearer: XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": {
        "type": "integration",
        "name": "Order shipping notification",
        "description": "Send a shipping notification via email with discount code.",
        "enabled": true,
        "observes": [
          "order.fulfilled"
        ],
        "integration_type": "webhook",
        "configuration": {
          "url": "https://yourwebsite.com/order-created-notification"
        }
      }
    }'
```
{% endtab %}
{% endtabs %}

## Configuration Object

So that we can properly fire a `webhook`, you will need to provide some configuration when creating a new event.

### Configuring a webhook

Webhooks are delivered using `POST` to the configured `url`. You may specify a `secret_key` which we will forward \_\_`X-MOLTIN-SECRET-KEY` along with the request as a header.

{% hint style="info" %}
`X-MOLTIN-INTEGRATION-TRIGGER` will also be added to the request headers, this allows you to process several events at the same `url`. This will be in the format of an [observable event](https://github.com/moltin/api.docs.moltin.com/tree/5428af44944131bca0a50421e5078ffbbdafbe7a/advanced/observable-events.md) key.
{% endhint %}

The webhook configuration object has the following structure.

{% tabs %}
{% tab title="Summary" %}
| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `url` | string | A **required** URL the observable event will fire. |
| `secret_key` | string | A _optional_ header. Useful to authenticate the response came from Moltin. Will be sent as `X-MOLTIN-SECRET-KEY` |
{% endtab %}

{% tab title="JSON" %}
```javascript
{
  "url": "https://yourwebsite.com/order-created-notification", // Required
  "secret_key": "secret_key_to_validate_on_your_endpoint" // Optional
}
```
{% endtab %}
{% endtabs %}

