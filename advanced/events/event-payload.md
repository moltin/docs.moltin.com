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

Below is an example payload that [observes](observable-events.md) the `order.paid` event. The configured URL will receive the following payload. **Note: the resource is passed as a string in this payload, so you must decode it in the consuming code.**

```javascript
{
  "id": "23bdb7d7-f081-4cfd-bfac-b05fdd306c51",
  "triggered_by": "order.paid",
  "attempt": 1,
  "integration": {
    "id": "af7bbcc7-f77f-4a8f-abdb-4f039c5c9d81",
    "integration_type": "webhook",
    "name": "Order paid notification",
    "description": "Fire an event on order paid"
  },
  "resources": "{\"data\":{\"type\":\"order\",\"id\":\"7286ae06-7be6-4609-bd6e-3159810d78ee\",\"status\":\"complete\",\"payment\":\"paid\",\"shipping\":\"unfulfilled\",\"customer\":{\"name\":\"Brad Bobley\",\"email\":\"example@moltin.com\"},\"shipping_address\":{\"first_name\":\"Jack\",\"last_name\":\"Macdowall\",\"phone_number\":\"123434\",\"company_name\":\"Macdowalls\",\"line_1\":\"Second Floor, British India House\",\"line_2\":\"15 Carliol Square\",\"city\":\"Newcastle upon Tyne\",\"postcode\":\"NE1 6UF\",\"county\":\"Tyne and Wear\",\"country\":\"GB\",\"instructions\":\"Leave in porch\"},\"billing_address\":{\"first_name\":\"Jack\",\"last_name\":\"Macdowall\",\"company_name\":\"Macdowalls\",\"line_1\":\"Second Floor, British India House\",\"line_2\":\"15 Carliol Square\",\"city\":\"Newcastle upon Tyne\",\"postcode\":\"NE1 6UF\",\"county\":\"Tyne and Wear\",\"country\":\"GB\"},\"links\":{},\"meta\":{\"display_price\":{\"with_tax\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"},\"without_tax\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"},\"tax\":{\"amount\":0,\"currency\":\"GBP\",\"formatted\":\"£0.00\"}},\"timestamps\":{\"created_at\":\"2019-06-24T13:14:03Z\",\"updated_at\":\"2019-06-24T13:14:03Z\"}},\"relationships\":{\"items\":{\"data\":[{\"type\":\"item\",\"id\":\"c9d6d790-e7be-4193-b7f2-9d02b9dbbf57\"}]}}},\"included\":{\"items\":[{\"type\":\"order_item\",\"id\":\"c9d6d790-e7be-4193-b7f2-9d02b9dbbf57\",\"quantity\":1,\"product_id\":\"4f28f222-aa5b-442c-9ce9-c223dc7cf15a\",\"name\":\"Spam Fritters\",\"sku\":\"spam-fritters-0716\",\"unit_price\":{\"amount\":10000,\"currency\":\"GBP\",\"includes_tax\":false},\"value\":{\"amount\":10000,\"currency\":\"GBP\",\"includes_tax\":false},\"links\":{},\"meta\":{\"display_price\":{\"with_tax\":{\"unit\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"},\"value\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"}},\"without_tax\":{\"unit\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"},\"value\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"}},\"tax\":{\"unit\":{\"amount\":0,\"currency\":\"GBP\",\"formatted\":\"£0.00\"},\"value\":{\"amount\":0,\"currency\":\"GBP\",\"formatted\":\"£0.00\"}}},\"timestamps\":{\"created_at\":\"2019-06-24T13:14:03Z\",\"updated_at\":\"2019-06-24T13:14:03Z\"}},\"relationships\":{\"cart_item\":{\"data\":{\"type\":\"cart_item\",\"id\":\"16f16999-1d04-4060-9a53-8d1623b57a7e\"}}}}]}}"
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

