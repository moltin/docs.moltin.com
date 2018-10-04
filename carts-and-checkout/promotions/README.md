# Promotions

Promotions allow you to provide discounts to customers. A Promotion requires codes, which are then used by the end user to get a discount. For more details on promotions, see: [Developer Portal](https://developers.moltin.com/guides/create-a-promotion).

### The Promotion Object

{% tabs %}
{% tab title="Attributes" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| `type` | `string` | `promotion` |
| `name` | `string` | The name of a promotion |
| `description` | `string` | The description of a promotion |
| `enabled` | `boolean` | Indicates whether a promotion is active |
| `promotion_type` | `string` |  `fixed_discount` or `percent_discount` |
| `schema` | [`object`](./#the-schema-object) | [Fixed Discount](./#fixed-discount) or  [Percent Discount](./#percent-discount) |
| `start` | `string` | The start time of the promotion DateTime |
| `end` | `string` | The end time of the promotion DateTime |
{% endtab %}

{% tab title="Sample Object" %}
Sample  with `fixed_discount` as a `promotion_type`.

```javascript
{
  "data": {
    "type": "promotion",
    "id": "15bf00b3-436b-446d-bda9-c021e4e4752b",
    "name": "Promo #1",
    "description": "Initial Promotion",
    "enabled": true,
    "promotion_type": "fixed_discount",
    "schema": {
      "currencies": [
        {
          "currency": "USD",
          "amount": 900
        },
        {
          "currency": "GBP",
          "amount": 1100
        }
      ]
    },
    "start": "2017-05-12T15:04:05Z",
    "end": "2019-10-12T15:04:05Z",
    "created_at": "2017-11-13T03:00:35.381148442Z",
    "updated_at": "2017-11-13T03:00:35.381148514Z"
  }
}
```
{% endtab %}
{% endtabs %}

### The Schema Object

Moltin offers different types of Promotion all defined by a Schema. These Schemas are used internally to verify a Promotion and calculate a discount.

Below is the list of currently available promotion type Schemas - these are to be used in the [create promotion request](create-promotion.md).

### Fixed Discount

Fixed discount provides a method to give a fixed discount to a cart.

{% tabs %}
{% tab title="Attributes" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| `currencies` | `array` | An array of objects |
| `currencies[].currency` | `string` | A currency code |
| `currencies[].amount` | `integer` | The amount to discount by |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
"schema": {
  "currencies": [
    {
      "currency": "GBP",
       "amount": 1100
    }
  ]
}
```
{% endtab %}
{% endtabs %}

### Percent Discount

Percent discount provides a method to give a percentage discount to a cart based on the value of cart\_items and custom\_items.

{% tabs %}
{% tab title="Attributes" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| `currencies` | `array` | An array of objects |
| `currencies[].currency` | `string` | A currency code |
| `currencies[].percentage` | `float` | The percentage to discount by |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
 "schema": {
    "currencies": [
      {
        "currency": "GBP",
        "percentage": 12.5
      }
    ]
  }
```
{% endtab %}
{% endtabs %}

### The Promotion Code Object

A promotion code is represented by the following, very simple, object.

{% tabs %}
{% tab title="Attributes" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| `code` | `string` | Any string |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "code":"ZXY_CBA"
}
```
{% endtab %}
{% endtabs %}



