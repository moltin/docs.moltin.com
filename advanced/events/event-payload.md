# Event Payload

The payload delivered to your webhook `url` will contain information about the fired event.

The payload attributes and types are defined below.

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `id` | `string` | A unique ID for this event. |
| `integration` | `object` | The events `integration_type` being fired. |
| `trigger` | [`string`](observable-events.md) | The [observable event](observable-events.md) that triggered this event. |
| `attempt` | `integer` | The number of attempts to deliver this event. |
| `resources` | `string` | Resources affected by this event. |

## Example payload

Below is an example payload that [observes](observable-events.md) the `order.fulfilled` event. The configured URL will receive the following payload.

```javascript
{
  "id": "8be8422e-4408-4172-a4cd-f42181330fe6",
  "integration": {
    "id": "71679ff8-36c1-4f8f-8ed2-cea50555d78c",
    "integration_type": "webhook",
    "name": "Order shipping notification",
    "description": "Send a shipping notification via email with discount code."
  },
  "trigger": "order.fulfilled",
  "attempt": 1,
  "resources": {
    "type": "order",
    "id": "32f8df35-8a31-4c43-9ed8-5d87127d9fdd"
  }
}
```

