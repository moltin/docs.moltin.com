# Orders

An Order is created via the [checkout](../../carts-and-checkout/checkout.md) endpoint within the Carts API.

### The Order Object <a id="the-order-object"></a>

The Order object is a representation of an order in Moltin.

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this order |
| `type` | `string` | Represents the type of object being returned. `order` |
| `status` | `string` | `incomplete`, `complete` |
| `payment` | `string` | `unpaid`, `authorized`, `paid`, `refunded` |
| `shipping` | `string` | `fulfilled`, `unfulfilled` |
| `customer` | `object` | The customer object associated with this order |
| `customer.name` | `string` | The customer's name |
| `customer.email` | `string` | The customer's email |
| `shipping_address` | `object` | The shipping address object |
| `shipping_address.first_name` | `string` | The first name of the address holder |
| `shipping_address.last_name` | `string` | The last name of the address holder |
| `shipping_address.phone_number` | `string` | The phone number of the address holder |
| `shipping_address.company_name` | `string` | The company name |
| `shipping_address.line_1` | `string` | First line of the address |
| `shipping_address.line_2` | `string` | Second line of the address |
| `shipping_address.city` | `string` | City |
| `shipping_address.postcode` | `string` | Postcode or Zip Code of the address |
| `shipping_address.county` | `string` | County or State of the address |
| `shipping_address.country` | `string` | Country |
| `shipping_address.instructions` | string | Any instructions with the shipping address |
| `billing_address` | object | The billing address object |
| `billing_address.first_name` | string | The first name of the billing address holder |
| `billing_address.last_name` | string | The last name of the billing address holder |
| `billing_address.company_name` | string | The billing company name |
| `billing_address.line_1` | string | First line of the billing address |
| `billing_address.line_2` | string | Second line of the billing address |
| `billing_address.city` | `string` | City |
| `billing_address.postcode` | `string` | Postcode or Zip Code of the billing address |
| `billing_address.county` | `string` | Country |
| `billing_address.country` | `string` | Any instructions with the shipping address |
| `links` | `object` | A collection of URLs related to this resource |
| `meta` | `object` | Additional information calculated for this order |
| `meta.display_price` | `object` | A collection of fields related to the totals and currency of this order |
| `meta.display_price. with_tax` | `object` | Tax inclusive totals |
| `meta.display_price. with_tax.amount` | `integer` | The raw total of this order \(inc tax\) |
| `meta.display_price. with_tax.currency` | `string` | The currency set for this order |
| `meta.display_price. with_tax.formatted` | `string` | The tax inclusive formatted total based on the currency |
| `meta.display_price. without_tax` | `object` | Tax exclusive totals |
| `meta.display_price. without_tax.amount` | `integer` | The raw total of this cart \(ex tax\) |
| `meta.display_price. without_tax.currency` | `string` | The currency set for this order |
| `meta.display_price. without_tax.formatted` | `string` | The tax exclusive formatted total based on the currency |
| `meta.timestamps` | `object` | Timestamps for this order |
| `meta.timestamps. created_at` | `string` | The creation date of this order |
| `meta.timestamps. updated_at` | `string` | The last updated date of this order |
| `relationships` | `object` | A collection of relationships related to this resource |
| `relationships.items` | `object` | The order items object |
| `relationships.items.data` | `array` | An array of order items |
| `relationships.items.data.type` | `string` | Represents the type of object being returned. `item` |
| `relationships.items.data.id` | `string` | The unique identifier for this order item |
| `relationships.customer` | `object` | The customer object |
| `relationships.customer.data` | `object` | The customer object associated with this order |
| `relationships.customer.data.type` | `string` | Represents the type of object being returned. `customer` |
| `relationships.customer.data.id` | `string` | The unique identifier for this customer |
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

### Payments

Once an order is created, it is marked unpaid. See [Paying for an order](../../payments/paying-for-an-order/) for how you can mark this order as paid.

