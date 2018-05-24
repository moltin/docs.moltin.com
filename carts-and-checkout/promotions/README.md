# Promotions

Promotions allow you to provide discounts to customers. By defining a promotion, and a code, you put in place the facility to offer discounts to customers, applied directly to their shopping carts.

The promotions you create will require codes to be attached to them, and these codes are subsequently used by end-users \(or your own system\) to apply promotions to carts and provide the discounts stipulated.

## The promotion object

{% tabs %}
{% tab title="Sample Response" %}
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

A promotion is represented by a promotion object.

| **Name** | **Type** | **Description** |
| --- | --- | --- |
| type | **string** | "promotion" |
| name | **string** | The name of your promotion. |
| description | **string** | A description of your promotion. |
| enabled | **boolean** | `true` if enabled, `false` if not. |
| promotion\_type | **string** | One of: `fixed_discount`, `percent_discount`. |
| schema | **object** | One of: [`fixed_schema`](https://docs.moltin.com/?javascript#fixed-discount), [`percent_schema`](https://docs.moltin.com/?javascript#percent-discount) |
| start | **string** | The start time of the promotion DateTime. |
| end | **string** | The end time of the promotion DateTime. |

## The schema object

moltin offer different types of promotion all defined by a schema. These schemas are used internally to verify a promotion and calculate a discount.

Below is the list of currently available promotion type schemas - these are to be used in the [create promotion request](https://docs.moltin.com/?javascript#create-a-promotion).

### Fixed Discount

```text
"schema": {
  "currencies": [
    {
      "currency": "GBP",
      "amount": 1100
    }
  ]
}
```

Fixed discount provides a method to give a fixed discount to a cart.

| Name | Type | Description |
| --- | --- | --- |
| currencies | **array** | An array of objects. |
| currencies\[\].currency | **string** | A currency code. |
| currencies\[\].amount | **integer** | The amount to discount by. |

### Percent Discount

```text
  "schema": {
    "currencies": [
      {
        "currency": "GBP",
        "percentage": 12.5
      }
    ]
  }
```

Percent discount provides a method to give a percentage discount to a cart based on the value of cart\_items and custom\_items.

| Name | Type | Description |
| --- | --- | --- |
| currencies | **array** | An array of objects. |
| currencies\[\].currency | **string** | A currency code. |
| currencies\[\].percentage | **float** | The percentage to discount by. |

## The promotion code object

A promotion code is represented by the following, very simple, object.

```text
{
  "code":"ZXY_CBA"
}
```

| Name | Type | Description |
| --- | --- | --- |
| code | **string** | Any string |

