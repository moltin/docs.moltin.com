# Promotions

Promotions allow you to provide discounts to customers. A Promotion can be automatic which will be applied provided any criteria are satisfied, or require codes, which are then used by the end user to get a discount. For more details, see [How promotions work](https://www.moltin.com/developer/concepts/how-promotions-work).

### The Promotion Object

{% tabs %}
{% tab title="Attributes" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| `type` | `string` | `promotion` |
| `name` | `string` | The name of a promotion |
| `description` | `string` | The description of a promotion |
| `enabled` | `boolean` | Indicates whether a promotion is active |
| `automatic` | `boolean` | Allows promotion to be applied without the need for a code. |
| `promotion_type` | `string` | `fixed-discount`,`percent-discount`, `x-for-y`, `x-for-amount` |
| `schema` | [`object`](./#the-schema-object) | [Fixed Discount](./#fixed-discount) , [Percent Discount](./#percent-discount), [X For Y](./#x-for-y), [X For Amount](./#x-for-amount), or [Bundle Discount](./#bundle-discount) |
| `min_cart_value` | `array` | array of objects |
| `min_cart_value[].currency` | `string` | A currency code |
| `min_cart_value[].amount` | `integer` | The minimum cart value before promotion is applied |
| `max_discount_value` | `array` | array of objects |
| `max_discount_value[].currency` | `string` | A currency code |
| `max_discount_value[].amount` | `integer` | The maximum value of the discount |
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

#### Fixed Discount

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
{
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

#### Percent Discount

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
{
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

#### X for Y

An _**X** for **Y**_ discount allows items of the same product to be sold on a _2 for 1_ or _3 for 2_ \(or any other combination\) basis. 

{% tabs %}
{% tab title="Attributes" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| `x` | `integer` | Number of items required to activate promotion. |
| `y` | `integer` | Number of items that will be used to calculate the total charge. |
| `targets` | `array` | Array of strings |
| `targets[]` | `string` | A list of strings that represent the productIDs and/or SKUs. |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "type": "promotion",
    "promotion_type": "x_for_y",
    "name": "X for Y Promotion Example",
    "description": "Example description for X for Y promotion.",
    "enabled": true,
    "automatic": true,
    "schema":{
      "x": 3,
      "y": 2,
      "targets": ["SKU-1", "SKU-2"]
    },
    "start":"2020-01-01",
    "end":"2030-01-01"
  }
}
```
{% endtab %}
{% endtabs %}

Multiples will be honoured by applying a multiple of the discount, e.g. 3 for 2 with 6 of the targeted items in a cart would yield a discount value equal to the value of 2 items.

#### X for Amount

An _X for Amount_ discount allows items of the same product to be sold on a **X** for fixed amount basis. e.g. 2 for $10 or 4 for $20.

{% tabs %}
{% tab title="Attributes" %}


| Name | Type | Description |
| :--- | :--- | :--- |
| `x` | `integer` | Number of items required to activate promotion. |
| `currencies` | `array` | Array of objects |
| `currencies[].currency` | `string` | A currency code |
| `currencies[].amount` | `integer` | The amount to vend items for. |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "type": "promotion",
    "name": "BF",
    "description": "Black Friday",
    "enabled": true,
    "automatic": true,
    "promotion_type": "x_for_amount",
    "schema": {
      "x": 3,
      "currencies": [
        {"currency": "USD", "amount": 500}
      ],
      "targets": ["SKU-1","SKU-2"]
    },
    "start": "2020-01-01",
    "end": "2030-01-01"
  }
}
```
{% endtab %}
{% endtabs %}

#### Bundle Discount

A bundle discount can be used to provide a fixed price for a selection of products when bought together. E.g. buy product x, y & z for $15 or buy 2 of product x and 3 of product y or z for $25

{% tabs %}
{% tab title="Attributes" %}
| Name | Type | Description |
| :--- | :--- | :--- |
| `requirements` | `array` | Array of objects |
| `requirements[].targets` | `array` | Array of strings |
| `requirements[].targets[]` | `string` | A list of strings that represent the productIDs and/or SKUs. |
| `requirements[].quantity` | `integer` | The require number of corresponding target to satisfy the promotion. |
| `currencies` | `array` | Array of objects. |
| `currencies[].currency` | `string` | A currency code. |
| `currencies[].amount` | `integer` | The amount to vend items for. |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "type": "promotion",
    "name": "BF",
    "description": "Black Friday",
    "enabled": true,
    "automatic": true,
    "promotion_type": "bundle_fixed_discount",
    "schema": {
      "requirements": [
        {"targets":["prodID-1", "SKU-1", "prodID-2", "SKU-3"], "quantity": 1},
        {"targets":["prodID-4", "SKU-5"], "quantity": 2},
        {"targets":["prodID-12", "SKU-11"], "quantity": 1}
      ],
      "currencies": [
        {"currency": "GBP", "amount": 2500},
        {"currency": "USD", "amount": 2400}
      ]
    },
    "start": "2020-01-01",
    "end": "2030-01-01"
  }
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
| `uses` | `integer` | Limit for number of times this code can be used |
| `user` | `string` | A string used as an identifier relating to a user |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "code":"ZXY_CBA",
  "uses": 5,
  "user": "qwertyuiop"
}
```
{% endtab %}
{% endtabs %}



