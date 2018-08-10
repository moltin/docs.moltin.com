# Filtering

Below are a list of attributes and operators available for [filtering](../../basics/filtering/) orders.

| **Attribute** | **Type** | **Operator** | **Example** |
| :--- | :--- | :--- | :--- |
| `status` | `string` | `eq` | `eq(status,complete)` |
| `payment` | `string` | `eq` | `eq(payment,paid)` |
| `shipping` | `string` | `eq` | `eq(shipping,unfulfilled)` |
| `name` \(`customer.name`\) | `string` | `eq` / `like` | `like(name,Brad*)` |
| `email` \(`customer.email`\) | `string` | `eq` / `like` | `like(email,*@moltin.com)` |
| `customer_id` | `string` | `eq` / `like` | `eq(customer_id, e5a0d684-a4af-4919-a348-f66b0b4955e0)` |
| `shipping_name` | `string` | `eq` / `like` | `like(shipping_name,home)` |
| `shipping_postcode` | `string` | `eq` / `like` | `like(shipping_postcode,117*)` |
| `billing_name` | `string` | `eq` / `like` | `like(billing_name,home)` |
| `billing_postcode` | `string` | `eq` / `like` | `like(billing_postcode,117*)` |
| `with_tax` | `integer` | `gt`/`ge`/`lt`/`le` | `ge(with_tax,10000)` |
| `without_tax` | `integer` | `gt`/`ge`/`lt`/`le` | `ge(without_tax,10000)` |
| `currency` | `string` | `eq` | `eq(currency,USD)` |
| `product_id` | `string` | `eq` | `eq(product_id,6837058c-ae42-46db-b3c6-7f01e0c34b40)` |
| `product_sku` | `string` | `eq` | `eq(product_sku,deck-shoe-001)` |
| `created_at` | `date` | `eq` / `gt` / `lt` | `gt(created_at,2018-01-01)` |
| `updated_at` | `date` | `eq` / `gt` / `lt` | `lt(updated_at,2018-01-01)` |

### **Notes**

* `with_tax` and `without_tax` should be integers without currency decimals so a value of `10000` would be equivalent to `$100.00`
* `product_id` and `product_sku` match orders where matching product has been ordered \(but they may not have been the only ordered items\)

