# Custom Data \(Flows\)

Create and manage custom data through Flows. Flows allow you to extend an existing or create a new resource.

### Core vs. non-core Flow <a id="core-vs-non-core-flow"></a>

The table below describes main differences between core and non-core Flows.

| Core Flows | Non-core Flows |
| :--- | :--- |
| Extend an existing resource. | Create a new resource. |
| Entries managed automatically by Moltin. | Need to manually create and manage Entries. |
| Requests are sent to the Fields endpoint. | Requests are sent to the Entries endpoint. |

### Extend a resource <a id="extend-a-resource"></a>

Extending a resource is applicable only to core flows. When creating a new flow, make sure the `slug` matches that of a core resource listed below.

| Flow `slug` | Description |
| :--- | :--- |
| `addresses` | Extend the [`address`](https://docs.moltin.com/orders-and-customers/addresses#the-address-object) object |
| `products` | Extend the [`product`](https://docs.moltin.com/catalog/products#the-product-object) object |
| `variations` | Extend the [`variation`](https://docs.moltin.com/catalog/product-variations#the-variation-object) object |
| `brands` | Extend the [`brand`](https://docs.moltin.com/catalog/brands#the-brand-object) object |
| `collections` | Extend the [`collection`](https://docs.moltin.com/catalog/collections#the-collection-object) object |
| `categories` | Extend the [`category`](https://docs.moltin.com/catalog/categories#the-category-object) object |
| `currencies` | Extend the [`currency`](https://docs.moltin.com/advanced/currencies#the-currency-object) object |
| `customers` | Extend the [`customer`](https://docs.moltin.com/orders-and-customers/customers#the-customer-object) object |
| `cart_items` | Extend the [`cart_item`](https://docs.moltin.com/carts-and-checkout/carts/cart-items#the-cart-item-object) object |
| `orders` | Extend the [`order`](https://docs.moltin.com/orders-and-customers/orders#the-order-object) object |
| `order_items` | Extend the [`order_item`](https://docs.moltin.com/orders-and-customers/orders/order-items#the-order-item-object) object |
| `promotions` | Extend the [`promotion`](https://docs.moltin.com/carts-and-checkout/promotions#the-promotion-object) object |

### Add a new resource <a id="add-a-new-resource"></a>

Adding a new resource is applicable only to non-core \(custom\) flows.

### Resource structure <a id="resource-structure"></a>

A **Flow** describes a collection of Fields. It is named after the internal entity type you wish to associate it with. For example, a Flow with a slug of `products` will be applied to all product responses in your store.

A **Field** represents a single field of data \(for example a `Product Rating`\) to be applied to an entity. All Fields have a type \(`string`, `integer`, `boolean`, `date` or `relationship`\), a default value and an optional set of validation rules.

An **Entry** is a specific instance of a Flow, and is associated with a specific instance of an entity \(for example, a single product\). Use Entries for custom flows \(non-core\) only. For core flows, these are managed for you.

