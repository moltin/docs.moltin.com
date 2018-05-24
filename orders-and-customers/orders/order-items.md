# Order Items

## The order item object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `id` | `string` | The unique identifier for this order item |
| `type` | `string` | The type represents the object being returned |
| `product_id` | `string` | The unique identifier for this order item |
| `name` | `string` | The name of this order item |
| `sku` | `string` | The SKU code for the order item |
| `quantity` | `integer` | The quantity of this item were ordered |
| `unit_price` | `object` | The [unit price object](order-items.md#the-unit-price-object) |
| `value` | `object` | The [value object](order-items.md#the-value-object) |
| `links` | `object` | The [links object](order-items.md#the-links-object) |
| `meta` | `object` | The [meta object](order-items.md#the-links-object) |
| `relationships` | `object` | The [relationships object](order-items.md#the-relationships-object) |

## The unit price object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- |
| `unit_price.amount` | `integer` | The singular price of this item |
| `unit_price.currency` | `string` | The unit price currency of this item |
| `unit_price.includes_tax` | `boolean` | Is the price inclusive of tax |

## The value object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- |
| `value.amount` | `integer` | The total price for this item \(`quantity` \* `unit_price.amount`\) |
| `value.currency` | `string` | The value currency of this item |
| `value.includes_tax` | `boolean` | Is the price inclusive of tax |

## The links object

| **Attribute** | **Type** | **Description** |
| --- | --- |
|  |  |  |

## The meta object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- | --- |
| `meta.display_price` | `object` | A collection of fields related to the totals and currency of this item |
| `meta.display_price.with_tax` | `object` | Tax inclusive totals |
| `meta.display_price.with_tax.unit` | `object` | Tax inclusive totals for a single |
|  |  |  |

## The relationships object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- | --- |
| `relationships.cart_item` | `object` | The cart item |
| `relationships.cart_item.data` | `object` | The associated cart |
| `relationships.cart_item.data.type` | `string` | The type represents the object being returned |
| `relationships.cart_item.data.id` | `string` | The unique identifier for this cart item |

{% api-method method="get" host="https://api.moltin.com" path="/v2/orders/:id/items" %}
{% api-method-summary %}
Get order items
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the order
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "type": "order_item",
      "id": "e8e2655f-3365-49f9-a2f0-1360a295019b",
      "quantity": 1,
      "product_id": "bf8a9d62-6ca9-45f6-85eb-f0d1d9ae7fdd",
      "name": "Woodsy",
      "sku": "WDLP100BRO",
      "unit_price": {
        "amount": 0,
        "currency": "GBP",
        "includes_tax": false
      },
      "value": {
        "amount": 0,
        "currency": "GBP",
        "includes_tax": false
      },
      "links": {},
      "meta": {
        "display_price": {
          "with_tax": {
            "unit": {
              "amount": 0,
              "currency": "GBP",
              "formatted": "£0"
            },
            "value": {
              "amount": 0,
              "currency": "GBP",
              "formatted": "£0"
            }
          },
          "without_tax": {
            "unit": {
              "amount": 0,
              "currency": "GBP",
              "formatted": "£0"
            },
            "value": {
              "amount": 0,
              "currency": "GBP",
              "formatted": "£0"
            }
          }
        },
        "timestamps": {
          "created_at": "2018-04-30T10:26:13.342815487Z",
          "updated_at": "2018-04-30T10:26:13.342815487Z"
        }
      },
      "relationships": {
        "cart_item": {
          "data": {
            "type": "cart_item",
            "id": "62d93144-74ab-4acc-9151-0c96d683c201"
          }
        }
      }
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/orders/:id/items \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const orderId = 'XXXX'

Moltin.Orders.Items(orderId).then(items => {
  // Do something
})

// Or using includes
Moltin.Orders.With('items').All().then(orders => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

