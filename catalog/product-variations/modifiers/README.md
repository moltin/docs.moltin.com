# Modifiers

Modifiers help augmenting properties of a variation of a product, price, etc., by creating an array of child products or prices. In each case you specify a `modifier type` and its `value`, which define how that property changes the variation option.

See [Modifiers](https://developers.moltin.com/~/drafts/-LJTp18a2-7cLeeCK3px/primary/guides/modifiers) for conceptual details. 

{% hint style="info" %}
`variations` are containers for `options` which in turn are containers for `modifiers`.
{% endhint %}

### Modifier types

There's several types of modifiers, and each has a different effect on a property.

| Modifier | Data Type | Effect |
| :--- | :--- | :--- |
| `name_equals` | `string` | Overrides the name of the product with the name specified by the modifier. |
| `name_append` | `string` | Appends the string specified in the modifier to the product's name. |
| `name_prepend` | `string` | Prepends the string specified in the modifier to the product's name. |
| `description_equals` | `string` | Overrides the description of the product. |
| `description_append` | `string` | Appends the string specified in the modifier to the product's description. |
| `description_prepend` | `string` | Prepends the string specified in the modifier to the product's description. |
| `commoditytype` | `string` | Sets the commodity type. |
| `price_increment` | [price collection](./#price-modifiers) | Increases the price of the product. |
| `price_decrement` | [price collection](./#price-modifiers) | Decreases the price of the product. |
| `price_equals` | [price collection](./#price-modifiers) | Sets the price of the product. Cannot be further modified. |
| `slug_equals` | `string` | Sets the slug of the product. |
| `slug_append` | `string` | Appends the string specified in the modifier to the product's slug. |
| `slug_prepend` | `string` | Prepends the string specified in the modifier to the product's slug. |
| `slug_builder` | [seek/set object](./#sku-slug-builder-modifiers) | Sets a part of the product's slug. |
| `sku_equals` | `string` | Sets the SKU of the product. |
| `sku_appends` | `string` | Appends the string specified in the modifier to the product's SKU. |
| `sku_prepends` | `string` | Prepends the string specified in the modifier to the product's SKU. |
| `sku_builder` | [seek/set object](./#sku-slug-builder-modifiers) | Sets a part of the product's SKU. |
| `status` | `string` | Sets the status of the product. |

### Seek/set modifier type

Used with `sku` and `slug` builder modifiers, must contain two property-value pairs: `seek`: "xxx" and `set`: "xxxx". Use a placeholder { } so that a variation can replace it with a value you wish to set.  

> For example, use the property-value pairs to specify a color modifier: `seek`: {COLOR}, `set`: {GREEN}.

* For more details, see: [Product SKU/Slug Builder Modifiers](https://developers.moltin.com/guides/product/modifiers).

### Price modifiers objects

{% tabs %}
{% tab title="Attributes" %}
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this product |
| `type` | `string` | Represents the type of object \(should be `modifier`\) |
| `modifier_type` | `string` | `price_increment`, `price_decrement`, `price_equals` |
| `value.amount` | `integer` | Value of the price modifier |
| `value.currency` | `string` | Currency of this price modifier \(3 letter ISO\) |
| `value.includes_tax` | `boolean` | `true` if relevant taxes have been included in the value `false` if not |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "type": "modifier",
  "id": "6d31b2d1-6a26-47e5-9ea0-96b392490ab7",
  "modifier_type": "price_increment",
  "value": [
    {
      "currency": "FJT",
      "amount": 46008803,
      "includes_tax": false
    },
    {
      "currency": "YZK",
      "amount": 4011039,
      "includes_tax": false
    }
  ]
}
```
{% endtab %}
{% endtabs %}

### SKU/Slug builder modifiers

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this product |
| `type` | `string` | Represents the type of object \(should be `modifier`\) |
| `modifier_type` | `string` | `sku_builder`, `slug_builder` |
| `value.seek` | `string` | A search string for the find / replace |
| `value.set` | `string` | Replacement string |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "type": "modifier",
  "id": "6d31b2d1-6a26-47e5-9ea0-96b392490ab7",
  "modifier_type": "sku-builder",
  "value": {
    "seek": "{PLACEHOLDER}",
    "set": "SKU001-",
  }
}
```
{% endtab %}
{% endtabs %}

### Field override modifiers

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this product |
| `type` | `string` | Represents the type of object \(should be `modifier`\) |
| `modifier_type` | `string` | `description_equals`, `description_prepend`, `description_append`, `commoditytype`, `name_equals`, `name_prepend`, `name_append`, `slug_equals`, `slug_prepend`, `slug_append`, `sku_equals`, `sku_prepend`, `sku_append`, `status` |
| `value` | `string` | A string to be used in place of the product property |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "type": "modifier",
  "id": "6d31b2d1-6a26-47e5-9ea0-96b392490ab7",
  "modifier_type": "name_equals",
  "value": "Overrode product name"
}
```
{% endtab %}
{% endtabs %}

