# Modifiers

## Product Modifiers

Product modifiers create the variation products \(child products\) from your base product by augmenting different properties of that base product. In each case, you will specify a modifier type and its value. This will define how that property changes as the child products are built. There is currently a limit on the number of child products you can build from a base product set at 200. This means the maximum number of child products generated from a base product cannot exceed this figure.

## Price Modifiers

These obviously help adjust the price of a product. As this kind of modifier deals with prices, it should come as no surprise to you that the **value** of this modifier must be a collection of currency values similar to that when specifying a product price. While the modifier can have any number of currencies applied to it, only the currencies specified on the actual base product will be subjected to any modifiers, i.e. If you have USD and GBP values on a base product, and apply a modifier that alters GBP, AUD and EUR the ONLY currency value affected will be GBP; the USD value will remain the same and no other currencies will be set on the variation product.

## SKU/Slug Builder Modifiers

These modifiers can help you fulfil a robust SKU and slug strategy. The value of the modifier must contain two property-value pairs: `"seek": "XXX"` and `"set" : "YYY"`. In order for this kind of modifier to participate in the variation products building process, the base product should have a SKU/slug set with a place holder like: `{XXX}`. The modifier works by replacing the placeholder with the value you wish to set. You should only specify the contents of the `{ }` in the seek property - the modifier will take care of the rest.

The builder is worthy of a brief example...

BaseProduct SKU: `BP01-{COLOUR}-{SIZE}` Modifier1:`{"seek":"COLOUR", "set":"BLU"}` Modifier2:`{"seek":"COLOUR", "set":"RED"}`

ModifierA:`{"seek":"SIZE", "set":"LRG"}` ModifierB:`{"seek":"SIZE", "set":"SML"}`

The above modifiers applied via variations for size and colour would produce the following SKUs in the corresponding variation product:

`BP01-BLU-LRG` `BP01-BLU-SML` `BP01-RED-LRG` `BP01-RED-SML`

You _could_ create the same via sku\_append modifier using values like `-RED` and `-LRG`; the advantage of the builder modifiers is that they are agnostic of the order the modifiers are applied.

## The Product Modifier Objects

### Price modifiers

{% tabs %}
{% tab title="Attributes" %}
| Attribute | Type | Description |
| :--- | :--- | :--- |
| id | **string** | The unique identifier for this product |
| type | **string** | Represents the type of object \(should be `modifier`\) |
| modifier\_type | **string** | `price_increment`, `price_decrement`, `price_equals` |
| value.amount | **integer** | Value of the price modifier |
| value.currency | **string** | Currency of this price modifier \(3 letter ISO\) |
| value.includes\_tax | **boolean** | `true` if relevant taxes have been included in the value `false` if not |
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

