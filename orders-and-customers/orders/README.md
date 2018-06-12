# Orders

### The Order object {#the-order-object}

The order object is a representation of an order in moltin.

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| id | string | The unique identifier for this order. |
| type | string | Represents the type of object being returned. `order`. |
| status | string | `incomplete`, `cancelled`, `complete`. |
| payment | string | `unpaid`, `authorized`, `paid`, `refunded`. |
| shipping | string | `fulfilled`, `unfulfilled`. |
| customer | object | The customer object associated with this order. |
| customer.name | string | The customers name. |
| customer.email | string | The customers email. |
| shipping\_address | object | The shipping address object. |
| shipping\_address.first\_name | string | The first name of the address holder. `required` |
| shipping\_address.last\_name | string | The last name of the address holder. `required` |
| shipping\_address.phone\_number | string | The phone number of the address holder. `optional` |
| shipping\_address.company\_name | string | The company name. `optional` |
| shipping\_address.line\_1 | string | First line of the address. `required` |
| shipping\_address.line\_2 | string | Second line of the address. `optional` |
| shipping\_address.city | string | City. `optional` |
| shipping\_address.postcode | string | Postcode or Zip Code of the address. `required` |
| shipping\_address.county | string | County or State of the address. `required` |
| shipping\_address.country | string | Country. `required` |
| shipping\_address.instructions | string | Any instructions with the shipping address. `optional` |
| billing\_address | object | The billing address object. |
| billing\_address.first\_name | string | The first name of the billing address holder. `required` |
| billing\_address.last\_name | string | The last name of the billing address holder. `required` |
| billing\_address.company\_name | string | The billing company name. `optional` |
| billing\_address.line\_1 | string | First line of the billing address. `required` |
| billing\_address.line\_2 | string | Second line of the billing address. `optional` |
| billing\_address.city | string | City. `optional` |
| billing\_address.postcode | string | Postcode or Zip Code of the billing address. `required` |
| billing\_address.county | string | Country. `required` |
| billing\_address.country | string | Any instructions with the shipping address. `optional` |
| links | object | A collection of URLs related to this resource. |
| meta | object | Additional information calculated for this order. |
| meta.display\_price | object | A collection of fields related to the totals and currency of this order. |
| meta.display\_price. with\_tax | object | Tax inclusive totals. |
| meta.display\_price. with\_tax.amount | integer | The raw total of this order \(inc tax\). |
| meta.display\_price. with\_tax.currency | string | The currency set for this order. |
| meta.display\_price. with\_tax.formatted | string | The tax inclusive formatted total based on the currency. |
| meta.display\_price. without\_tax | object | Tax exclusive totals. |
| meta.display\_price. without\_tax.amount | integer | The raw total of this cart \(ex tax\). |
| meta.display\_price. without\_tax.currency | string | The currency set for this order. |
| meta.display\_price. without\_tax.formatted | string | The tax exclusive formatted total based on the currency. |
| meta.timestamps | object | Timestamps for this order. |
| meta.timestamps. created\_at | string | The creation date of this order. |
| meta.timestamps. updated\_at | string | The last updated date of this order. |
| relationships | object | A collection of relationships related to this resource. |
| relationships.items | object | The order items object. |
| relationships.items.data | array | An array of order items. |
| relationships.items.data.type | string | Represents the type of object being returned. `item`. |
| relationships.items.data.id | string | The unique identifier for this order item. |
| relationships.customer | object | The customer object. |
| relationships.customer.data | object | The customer object associated with this order. |
| relationships.customer.data.type | string | Represents the type of object being returned. `customer`. |
| relationships.customer.data.id | string | The unique identifier for this customer.  |
{% endtab %}

{% tab title="Sample object" %}
```javascript
{
  "data": {
      "type": "order",
      "id": "6d809942-da51-4f07-9350-47fe759b2369",
      "status": "incomplete",
      "payment": "unpaid",
      "shipping": "unfulfilled",
      "customer": {
        "name": "Brad",
        "email": "brad@bobley.com"
      },
      "shipping_address": {
        "first_name": "Otis",
        "last_name": "Sedmak",
        "phone_number": "(555) 555-1234",
        "company_name": "Sedmak & Co.",
        "line_1": "1251, Rexmere Ave",
        "line_2": "Farmingville, Suffolk",
        "city": "shipping city",
        "postcode": "11738",
        "county": "Farmingville, Suffolk",
        "country": "US",
        "instructions": "Leave in porch"
      },
      "billing_address": {
        "first_name": "Jack",
        "last_name": "Macdowall",
        "company_name": "Macdowalls",
        "line_1": "1225 Invention Avenue",
        "line_2": "Birmingham",
        "city": "billing city",
        "postcode": "B21 9AF",
        "county": "West Midlands",
        "country": "US"
      },
      "links": {},
      "meta": {
        "display_price": {
          "with_tax": {
            "amount": 45598,
            "currency": "USD",
            "formatted": "$455.98"
          },
          "without_tax": {
            "amount": 45598,
            "currency": "USD",
            "formatted": "$455.98"
          }
        },
        "timestamps": {
          "created_at": "2017-09-25T14:13:18.738Z",
          "updated_at": "2017-09-25T14:13:18.738Z"
        }
      },
      "relationships": {
        "items": {
          "data": [
            {
              "type": "item",
              "id": "52a88bad-16c4-49ff-8684-089cec3e3f35"
            }
          ]
        },
        "customer": {
          "data": {
            "type": "customer",
            "id": "c8c1c511-beef-4812-9b7a-9f92c587217c"
          }
        }
      }
    }
}
```
{% endtab %}
{% endtabs %}

### The Order Item object {#the-order-item-object}

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| id | **string** | The unique identifier for this order item. |
| type | **string** | Represents the type of object being returned. `order_item` |
| product\_id | **string** | The unique identifier for the product for this order item. |
| name | **string** | Denotes the name of this order item. |
| sku | **string** | The SKU code for the order item. |
| quantity | **integer** | How many of this item have been added to the cart. |
| unit\_price | **object** | Contains pricing information about a single instance of this item |
| unit\_price.amount | **integer** | The singular price of this item as an integer |
| unit\_price.currency | **string** | The currency this item was added to the cart as |
| unit\_price.includes\_tax | **boolean** | Whether or not this price is tax inclusive |
| value | **object** | Contains pricing information total value of this item line based on the quantity |
| value.amount | **integer** | The total price for this item line \(quantity \* unit\_price.amount\) |
| value.currency | **string** | The currency this item was added to the cart as |
| value.includes\_tax | **boolean** | Whether or not this price is tax inclusive |
| links | **object** | A collection of URLs related to this resource |
| meta | **object** | Additional information calculated for this cart |
| meta.display\_price | **object** | A collection of fields related to the totals and currency of this cart item |
| meta.display\_price. with\_tax | **object** | Tax inclusive totals |
| meta.display\_price. with\_tax.unit | **object** | Tax inclusive totals for a single instance of this cart item |
| meta.display\_price. with\_tax.unit.amount | **integer** | The raw price of a single instance this cart item \(inc tax\) |
| meta.display\_price. with\_tax.unit.currency | **string** | The currency set for this cart item |
| meta.display\_price. with\_tax.unit.formatted | **string** | The tax inclusive formatted total of a single instance of this cart item based on the currency |
| meta.display\_price. with\_tax.value | **object** | Tax inclusive totals for this cart item based on the quantity |
| meta.display\_price. with\_tax.value.amount | **integer** | The raw total price this cart item line \(inc tax\) |
| meta.display\_price. with\_tax.value.currency | **string** | The currency set for this cart item |
| meta.display\_price. with\_tax.value.formatted | **string** | The tax inclusive formatted total of this cart item line based on the currency |
| meta.display\_price. without\_tax | **object** | Tax exclusive totals |
| meta.display\_price. without\_tax.unit | **object** | Tax exclusive totals for a single instance of this cart item |
| meta.display\_price. without\_tax.unit.amount | **integer** | The raw price of a single instance this cart item \(ex tax\) |
| meta.display\_price. without\_tax.unit.currency | **string** | The currency set for this cart item |
| meta.display\_price. without\_tax.unit.formatted | **string** | The tax exclusive formatted total of a single instance of this cart item based on the currency |
| meta.display\_price. without\_tax.value | **object** | Tax exclusive totals for this cart item based on the quantity |
| meta.display\_price. without\_tax.value.amount | **integer** | The raw total price this cart item line \(ex tax\) |
| meta.display\_price. without\_tax.value.currency | **string** | The currency set for this cart item |
| meta.display\_price. without\_tax.value.formatted | **string** | The tax exclusive formatted total of this cart item line based on the currency |
| meta.timestamps | **object** | Timestamps for this cart item |
| meta.timestamps.created\_at | **string** | The creation date of this cart item |
| meta.timestamps.updated\_at | **string** | The last updated date of this cart item |
| relationships.cart\_item | **object** | The customer object. |
| relationships.cart\_item.data | **object** | The customer object associated with this order. |
| relationships.cart\_item.data.type | **string** | Represents the type of object being returned. `cart_item`. |
| relationships.cart\_item.data.id | **string** | The unique identifier for this cart item. |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "id": "52a88bad-16c4-49ff-8684-089cec3e3f35",
    "type": "order_item",
    "product_id": "fc6122b9-de9d-4d08-9fa6-0f4a69459dc6",
    "name": "My Great Product",
    "sku": "MGP_001",
    "quantity": 4,
    "unit_price": {
      "amount": 7150,
      "currency": "USD",
      "includes_tax": true
    },
    "value": {
      "amount": 28600,
      "currency": "USD",
      "includes_tax": true
    },
    "links": {},
    "meta": {
      "display_price": {
        "with_tax": {
          "unit": {
            "amount": 7150,
            "currency": "USD",
            "formatted": "$71.50"
          },
          "value": {
            "amount": 28600,
            "currency": "USD",
            "formatted": "$286.00"
          }
        },
        "without_tax": {
          "unit": {
            "amount": 7150,
            "currency": "USD",
            "formatted": "$71.50"
          },
          "value": {
            "amount": 28600,
            "currency": "USD",
            "formatted": "$286.00"
          }
        }
      },
      "timestamps": {
        "created_at": "2017-09-25T14:13:18.738031028Z",
        "updated_at": "2017-09-25T14:13:18.738031028Z"
      }
    },
    "relationships": {
      "cart_item": {
        "data": {
          "type": "cart_item",
          "id": "56b18551-6baa-4e07-b3f7-19794359e962"
        }
      }
    }
  }
```
{% endtab %}
{% endtabs %}

### Order filtering {#order-filtering}

The following attributes are available to [filter](https://docs.moltin.com/#filtering) by:

| **Attribute** | **Type** | **Acceptable Operators** | **Example** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| status | string | `eq` | `eq(status,complete)` |
| payment | string | `eq` | `eq(payment,paid)` |
| shipping | string | `eq` | `eq(shipping,unfulfilled)` |
| name \(customer.name\) | string | `eq`, `like` | `like(name,Brad*)` |
| email \(customer.email\) | string | `eq`, `like` | `like(email,*@moltin.com)` |
| customer\_id \(relationships.customer.data.id\) | string | `eq`, `like` | `eq(customer_id,e5a0d684-a4af-4919-a348-f66b0b4955e0)` |
| shipping\_name \(shipping.name\) | string | `eq`, `like` | `like(shipping_name,home)` |
| shipping\_postcode \(shipping.postcode\) | string | `eq`, `like` | `like(shipping_postcode,117*)` |
| billing\_name \(billing.name\) | string | `eq`, `like` | `like(billing_name,home)` |
| billing\_postcode \(billing.postcode\) | string | `eq`, `like` | `like(billing_postcode,117*)` |
| with\_tax | integer | `gt`, `ge`, `lt`, `le` | `ge(with_tax,10000)` |
| without\_tax | integer | `gt`, `ge`, `lt`, `le` | `ge(without_tax,10000)` |
| currency | string | `eq` | `eq(currency,USD)` |
| product\_id | string | `eq` | `eq(product_id,6837058c-ae42-46db-b3c6-7f01e0c34b40)` |
| product\_sku | string | `eq` | `eq(product_sku,deck-shoe-001)` |

**Notes:**

* `with_tax` and `without_tax` should be integers without currency decimals so a value of `10000` would be equivalent to `$100.00`
* `product_id` and `product_sku` match orders where matching product has been ordered \(but they may not have been the only ordered items\)

