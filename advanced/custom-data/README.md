# Custom Data

Create and mange custom data through Flows. Flows allow you to extend an existing or create a new resource.

### Core vs. non-core Flow {#core-vs-non-core-flow}

The table below describes main differences between core and non-core Flows.

| Core Flows | Non-core Flows |
| :--- | :--- |
| Extend an existing resource. | Create a new resource. |
| Entries managed automatically by Moltin. | Need to manually create and manage Entries. |
| Requests are sent to the Fields endpoint. | Requests are sent to the Entries endpoint. |

### Extend a resource {#extend-a-resource}

Extending a resource is applicable only to core flows.

`addresses`, `products`, `inputs`, `variations`, `brands`, `collections`, `categories`, `currencies`, `customers`, `groups`, `files`, `inventories`, `carts`, `cart_items`, `orders`, `order_items`, `promotions`, `shipping`, `taxes`

### Add a new resource {#add-a-new-resource}

Adding a new resource is applicable only to non-core \(custom\) flows.

### Resource structure {#resource-structure}

A **Flow** describes a collection of Fields. It is named after the internal entity type you wish to associate it with. For example, a Flow with a slug of `products` will be applied to all product responses in your store.

A **Field** represents a single field of data \(for example a `Product Rating`\) to be applied to an entity. All Fields have a type \(`string`, `integer`, `boolean`, `date` or `relationship`\), a default value and an optional set of validation rules.

An **Entry** is a specific instance of a Flow, and is associated with a specific instance of an entity \(for example, a single product\). Use Entries for custom flows \(non-core\) only. For core flows, these are managed for you.

