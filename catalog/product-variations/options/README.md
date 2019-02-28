# Options

## The Product Variation Option object

A variation option represents an option for selection for a single `product-variation`. For example, if your variation is "color", you may have three possible options `red`, `green`, and `blue`.

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this option |
| `type` | `string` | Represents the type of object being returned \(should be `option`\) |
| `name` | `string` | A human readable name for this option |
| `description` | `string` | A human readable description of the product-variation object |
| `modifiers` | `array` | An array of `modifiers`objects belonging to this variation option |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
    "type": "option",
    "id": "67af507f-e901-4647-a265-3aa931382959",
    "name": "Red",
    "description": "Red"
}
```
{% endtab %}
{% endtabs %}

