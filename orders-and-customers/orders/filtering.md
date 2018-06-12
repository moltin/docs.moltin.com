# Filtering

Below are a list of attributes and operators available for [filtering](../../basics/filtering/) orders.

| **Attribute** | **Type** | **Operator** | **Example** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| status | string | eq | `eq(status,complete)` |
| payment | string | eq | `eq(payment,paid)` |
| shipping | string | eq | `eq(shipping,unfulfilled)` |
| name \(customer name\) | string | eq / like | `like(name,Brad*)` |
| email \(customer email\) | string | eq / like | `like(email,*@moltin.com)` |
| customer\_id \(relationships.customer.data.id\) | string | eq / like | `eq(customer_id, e5a0d684-a4af-4919-a348-f66b0b4955e0)` |
| shipping\_name \(shipping.name\) | string | eq / like | like\(shipping\_name,home\) |
| shipping\_postcode \(shipping.postcode\) | string | eq / like | like\(shipping\_postcode,117\*\) |
| billing\_name \(billing.name\) | string | eq / like | like\(billing\_name,home\) |
| billing\_postcode \(billing.postcode\) | string | eq / like | like\(billing\_postcode,117\*\) |
| with\_tax | integer | `gt`/`ge`/`lt`/`le` |  |
| without\_tax | integer | gt/ge/lt/le |  |
| currency | string | eq |  |
| product\_id | string | eq |  |
| product\_sku | string | eq | eq\(product\_sku,deck-shoe-001\) |

### **Notes**

* `with_tax` and `without_tax` should be integers without currency decimals so a value of `10000` would be equivalent to `$100.00`
* `product_id` and `product_sku` match orders where matching product has been ordered \(but they may not have been the only ordered items\)

