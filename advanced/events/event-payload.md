# Event Payload

The payload delivered to your webhook `url` will contain information about the fired event.

The payload attributes and types are defined below.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | A unique ID for this event |
| `integration` | `object` | The events `integration_type` being fired |
| `triggered_by` | [`string`](observable-events.md) | The [observable event](observable-events.md) that triggered this event |
| `attempt` | `integer` | The number of attempts to deliver this event |
| `resources` | `string` | The resources affected by this event |

## Example: Typical payload

Below is an example payload that [observes](observable-events.md) the `order.fulfilled` event. The configured URL will receive the following payload.

```javascript
{
  "id": "8be8422e-4408-4172-a4cd-f42181330fe6",
  "triggered_by": "order.fulfilled",
  "attempt": 1,
  "integration": {
    "id": "71679ff8-36c1-4f8f-8ed2-cea50555d78c",
    "integration_type": "webhook",
    "name": "Order shipping notification",
    "description": "Send a shipping notification via email with discount code."
  },
  "resources": {
    "type": "order",
    "id": "32f8df35-8a31-4c43-9ed8-5d87127d9fdd"
  }
}
```

## Example: Deleted Resources Payload

When resources are deleted and you observe an event you will receive a payload where the `resources` attribute is `JSON` and will **only** __contain the resource type and ID_._ **You do not need to parse the resources before handling them on your side.**

```javascript
{
  "id": "c138854a-5311-4543-a368-01e099f5519b",
  "triggered_by": "product.deleted",
  "attempt": 1,
  "integration": {
    "id": "4596d5e1-26b6-444a-964d-2b6ec46477fd",
    "integration_type": "webhook",
    "name": "Product deleted notification",
    "description": "Let me know when products are deleted from my store."
  },
  "resources": {
    "type": "product",
    "id": "ecdfb02c-3539-449c-854d-0e094a7d5c09"
  }
}
```

