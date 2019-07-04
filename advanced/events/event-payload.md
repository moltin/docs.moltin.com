# Event Payload

The payload delivered to your webhook `url` will contain information about the fired event.

The payload attributes and types are defined below.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | A unique ID for this event |
| `integration` | `object` | The events `integration_type` being fired |
| `triggered_by` | [`string`](observable-events.md) | The [observable event](observable-events.md) that triggered this event |
| `attempt` | `integer` | The number of attempts to deliver this event |
| `resources` | `string` | The resources affected by this event.  This field is now deprecated, please use `payload` instead. |
| `payload` | `object` | The resources affected by this event |

## Example: Typical payload

Below is an example payload that [observes](observable-events.md) the `order.paid` event. The configured URL will receive the following payload.

```javascript
{
  "id": "21a361c9-b117-4d16-be2d-5ed2dbdaa95b",
  "triggered_by": "order.paid",
  "attempt": 1,
  "integration": {
    "id": "af7bbcc7-f77f-4a8f-abdb-4f039c5c9d81",
    "integration_type": "webhook",
    "name": "Order paid notification",
    "description": "Fire an event on order paid"
  },
  "resources": "{\"data\":{\"type\":\"order\",\"id\":\"1d67160d-dacb-43ed-80ef-c3c4e7ddf764\",\"status\":\"complete\",\"payment\":\"paid\",\"shipping\":\"unfulfilled\",\"customer\":{\"name\":\"Ron Swanson\",\"email\":\"ron.swanson@moltin.com\"},\"shipping_address\":{\"first_name\":\"Jack\",\"last_name\":\"Macdowall\",\"phone_number\":\"123456789\",\"company_name\":\"Macdowalls\",\"line_1\":\"Second Floor, British India House\",\"line_2\":\"15 Carliol Square\",\"city\":\"Newcastle upon Tyne\",\"postcode\":\"NE1 6UF\",\"county\":\"Tyne and Wear\",\"country\":\"GB\",\"instructions\":\"Leave in porch\"},\"billing_address\":{\"first_name\":\"Jack\",\"last_name\":\"Macdowall\",\"company_name\":\"Macdowalls\",\"line_1\":\"Second Floor, British India House\",\"line_2\":\"15 Carliol Square\",\"city\":\"Newcastle upon Tyne\",\"postcode\":\"NE1 6UF\",\"county\":\"Tyne and Wear\",\"country\":\"GB\"},\"links\":{},\"meta\":{\"display_price\":{\"with_tax\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"},\"without_tax\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"},\"tax\":{\"amount\":0,\"currency\":\"GBP\",\"formatted\":\"£0.00\"}},\"timestamps\":{\"created_at\":\"2019-07-04T11:12:23Z\",\"updated_at\":\"2019-07-04T11:12:23Z\"}},\"relationships\":{\"items\":{\"data\":[{\"type\":\"item\",\"id\":\"395763ee-1878-4aa0-a7a2-8d4877310d6b\"}]}}},\"included\":{\"items\":[{\"type\":\"order_item\",\"id\":\"395763ee-1878-4aa0-a7a2-8d4877310d6b\",\"quantity\":1,\"product_id\":\"4f28f222-aa5b-442c-9ce9-c223dc7cf15a\",\"name\":\"Spam Fritters\",\"sku\":\"spam-fritters-0716\",\"unit_price\":{\"amount\":10000,\"currency\":\"GBP\",\"includes_tax\":false},\"value\":{\"amount\":10000,\"currency\":\"GBP\",\"includes_tax\":false},\"links\":{},\"meta\":{\"display_price\":{\"with_tax\":{\"unit\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"},\"value\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"}},\"without_tax\":{\"unit\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"},\"value\":{\"amount\":10000,\"currency\":\"GBP\",\"formatted\":\"£100.00\"}},\"tax\":{\"unit\":{\"amount\":0,\"currency\":\"GBP\",\"formatted\":\"£0.00\"},\"value\":{\"amount\":0,\"currency\":\"GBP\",\"formatted\":\"£0.00\"}}},\"timestamps\":{\"created_at\":\"2019-07-04T11:12:23Z\",\"updated_at\":\"2019-07-04T11:12:23Z\"}},\"relationships\":{\"cart_item\":{\"data\":{\"type\":\"cart_item\",\"id\":\"a498b15a-2cc7-49ea-93b3-22143bb403ac\"}}}}]}}",
  "payload": {
    "data": {
      "type": "order",
      "id": "1d67160d-dacb-43ed-80ef-c3c4e7ddf764",
      "status": "complete",
      "payment": "paid",
      "shipping": "unfulfilled",
      "customer": {
        "name": "Ron Swanson",
        "email": "ron.swanson@moltin.com"
      },
      "shipping_address": {
        "first_name": "Jack",
        "last_name": "Macdowall",
        "phone_number": "123456789",
        "company_name": "Macdowalls",
        "line_1": "Second Floor, British India House",
        "line_2": "15 Carliol Square",
        "city": "Newcastle upon Tyne",
        "postcode": "NE1 6UF",
        "county": "Tyne and Wear",
        "country": "GB",
        "instructions": "Leave in porch"
      },
      "billing_address": {
        "first_name": "Jack",
        "last_name": "Macdowall",
        "company_name": "Macdowalls",
        "line_1": "Second Floor, British India House",
        "line_2": "15 Carliol Square",
        "city": "Newcastle upon Tyne",
        "postcode": "NE1 6UF",
        "county": "Tyne and Wear",
        "country": "GB"
      },
      "links": {},
      "meta": {
        "display_price": {
          "with_tax": {
            "amount": 10000,
            "currency": "GBP",
            "formatted": "£100.00"
          },
          "without_tax": {
            "amount": 10000,
            "currency": "GBP",
            "formatted": "£100.00"
          },
          "tax": {
            "amount": 0,
            "currency": "GBP",
            "formatted": "£0.00"
          }
        },
        "timestamps": {
          "created_at": "2019-07-04T11:12:23Z",
          "updated_at": "2019-07-04T11:12:23Z"
        }
      },
      "relationships": {
        "items": {
          "data": [
            {
              "type": "item",
              "id": "395763ee-1878-4aa0-a7a2-8d4877310d6b"
            }
          ]
        }
      }
    },
    "included": {
      "items": [
        {
          "type": "order_item",
          "id": "395763ee-1878-4aa0-a7a2-8d4877310d6b",
          "quantity": 1,
          "product_id": "4f28f222-aa5b-442c-9ce9-c223dc7cf15a",
          "name": "Spam Fritters",
          "sku": "spam-fritters-0716",
          "unit_price": {
            "amount": 10000,
            "currency": "GBP",
            "includes_tax": false
          },
          "value": {
            "amount": 10000,
            "currency": "GBP",
            "includes_tax": false
          },
          "links": {},
          "meta": {
            "display_price": {
              "with_tax": {
                "unit": {
                  "amount": 10000,
                  "currency": "GBP",
                  "formatted": "£100.00"
                },
                "value": {
                  "amount": 10000,
                  "currency": "GBP",
                  "formatted": "£100.00"
                }
              },
              "without_tax": {
                "unit": {
                  "amount": 10000,
                  "currency": "GBP",
                  "formatted": "£100.00"
                },
                "value": {
                  "amount": 10000,
                  "currency": "GBP",
                  "formatted": "£100.00"
                }
              },
              "tax": {
                "unit": {
                  "amount": 0,
                  "currency": "GBP",
                  "formatted": "£0.00"
                },
                "value": {
                  "amount": 0,
                  "currency": "GBP",
                  "formatted": "£0.00"
                }
              }
            },
            "timestamps": {
              "created_at": "2019-07-04T11:12:23Z",
              "updated_at": "2019-07-04T11:12:23Z"
            }
          },
          "relationships": {
            "cart_item": {
              "data": {
                "type": "cart_item",
                "id": "a498b15a-2cc7-49ea-93b3-22143bb403ac"
              }
            }
          }
        }
      ]
    }
  },
  "configuration": {
    "secret_key": "secret_squirrel",
    "url": "https://webhook.url"
  }
}
```

## Example: Deleted Resources Payload

When resources are deleted and you observe an event you will receive a payload will **only** __contain the resource type and ID_._ 

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
    "id": "a34a378b-2c39-41e4-a240-6b7e65f5bb55",
    "type": "product"
  },
  "payload": {
    "type": "product",
    "id": "a34a378b-2c39-41e4-a240-6b7e65f5bb55"
  },
  "configuration": {
    "secret_key": "secret_squirrel",
    "url": "https://webhook.url"
  }
}
```

