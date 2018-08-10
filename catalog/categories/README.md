# Categories

Categories allow you to organize your Products into hierarchical groups. That means these groups can also contain other Categories, which can then be viewed in a tree structure.

## The Category Object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this category |
| `type` | `string` | Represents the type of object being returned |
| `name` | `string` | The name of the category |
| `slug` | `string` | A unique slug identifier for the category |
| `description` | `string` | Any description for this category |
| `status` | `string` | `live` or `draft`depending on the category status |
| `meta` | `object` | The [meta object](./#the-meta-object) |
| `relationships` | `object` | The [relationships object](./#the-relationships-object) |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "id": "39a13b7e-f2d3-47a5-9bc5-1e98b198748c",
    "type": "category",
    "name": "Clothing",
    "slug": "clothing",
    "description": "Browse our clothing line",
    "status": "live"
  }
}
```
{% endtab %}
{% endtabs %}

## The `meta` Object

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `meta.timestamps` | `object` | Timestamps for this category |
| `meta.timestamps.created_at` | `string` | The creation date of this category |
| `meta.timestamps.updated_at` | `string` | The updated date of this category |

## The `relationships` Object

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `relationships.products` | `array[object]` | An array of products for this category |
| `relationships.products.data` | `array[object]` | An array of relationships from this category to products resources |
| `relationships.products.data.type` | `string` | Always `product` |
| `relationships.products.data.id` | `string` | the unique identifier of the related product |

