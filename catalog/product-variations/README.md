# Product Variations

## Product Variations

Variations allow you to create the variations that your products have. Things like size or colour are examples of a variation. Using this system you can reliably create all possible combinations of your product.

### The variation object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `id` | `string` | The unique identifier for this variation |
| `type` | `string` | Represents the type of object being returned \(should be `product-variation`\) |
| `name` | `string` | A human readable name for this variation |
| `relationships` | `object` | Relationships to other resources |
| `relationships.options` | `object` | Relationships information regarding options for this variation |
| `relationships.options.data` | `array` | An array of relationships from this variation to options |
| `relationships options.data.id` | `string` | The unique identifier for the option |
| `relationships.options.data.type` | `string` | The type \(`option`\) |
| `included` | `object` | Included resources |
| `included.options` | `array` | Array of options that constitute the variation |
| `included.options.id` | `string` | The unique identifier for the option |
| `included.options.type` | `string` | Represents the type of object \(`option`\) |
| `included.options.name` | `string` | A human readable name for the option |
| `included.options.description` | `string` | A human readable description for the option |
| `included.options.relationships` | `object` | Relationships to other resources |
| `included.options.relationships.data` | `array[object]` | An array of relationships from this option to modifiers |
| `included.options.relationships.data.id` | `string` | The unique identifier for the modifier |
| `included.options.relationships.data.type` | `string` | The type \(`modifier`\) |
| `included.modifiers` | `array` | Array of modifiers that constitute the variation options |
| `included.modifiers.id` | `string` | The unique identifier for the modifier |
| `included.modifiers.type` | `string` | The type \(`modifier`\) |
| `included.modifiers.modifier_type` | `string` | One of the modifier types available |
| `included.modifiers.value` | `mixed` | Value the modifier type allows |

The variation object is delivered as a compound document \(it includes the attached options and modifiers\). This is because the options and modifiers that constitute the variation are integral to its function and have no relevance in any other context.

