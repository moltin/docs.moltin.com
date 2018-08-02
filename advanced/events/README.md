# Events

Moltin [observes several events](observable-events.md) that you can attach webhooks to. With a webhook you can attach custom code that performs actions outside of the Moltin ecosystem.

You may want to send a discount code or a NPS survey email a few days after an order is fulfilled. You can do this via a webhook that sends event data to your custom function.

{% hint style="warning" %}
Webhooks that return anything other than a 2XX status code will be considered failed.
{% endhint %}

## Event object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `id` | `string` | The unique identifier for the event |
| `type` | `string` | This represents the type of object being returned |
| `name` | `string` | The name of the event |
| `description` | `string` | A description for this event |
| `integration_type` | `string` | This will be `webhook` |
| `enabled` | `boolean` | This will enable the event to fire |
| `observes` | [`array[string]`](observable-events.md) | An array of [observable events](observable-events.md) |
| `configuration` | [`object`]() | A `webhook` [configuration object]() |

## Example response

```javascript
{
  "data": {
    "id": "328b4e0b-4032-48d0-8c85-04cc4c0a331d",
    "type": "integration",
    "name": "Order shipping notification",
    "description": "Send a shipping notification via email with discount code.",
    "integration_type": "webhook",
    "enabled": true,
    "observes": [
      "order.fulfilled"
    ],
    "configuration": {
      "url": "https://ilovelamp.now.sh/send-shipped-email",
      "secret_key": "SOME_SECRET_KEY"
    }
  }
}
```

