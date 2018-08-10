# Observable Events

You can pass multiple observable keys to the `observes` field of the [event object](./#event-object), or you can create individual events. You may wish to use an array when you handle multiple webhooks at the same URL.

| **Entity/Resource** | **Action** | **Observable Key** |
| :--- | :--- | :--- |
| **Brand** | Created | `brand.created` |
|  | Updated | `brand.updated` |
|  | Deleted | `brand.deleted` |
| **Cart** | Updated | `cart.updated` |
|  | Deleted | `cart.deleted` |
| **Category** | Created | `category.created` |
|  | Updated | `category.updated` |
|  | Deleted | `category.deleted` |
| **Collection** | Created | `collection.created` |
|  | Updated | `collection.updated` |
|  | Deleted | `collection.deleted` |
| **Currency** | Created | `currency.created` |
|  | Updated | `currency.updated` |
|  | Deleted | `currency.deleted` |
| **File** | Created | `file.created` |
|  | Deleted | `file.deleted` |
| **Integration \(events\)** | Created | `integrations.created` |
|  | Updated | `integrations.updated` |
|  | Deleted | `integrations.deleted` |
| **Order** | Created | `order.created` |
|  | Updated | `order.updated` |
|  | Fulfilled | `order.fulfilled` |
|  | Authorized | `order.authorized` |
|  | Paid/Captured | `order.paid` |
|  | Refunded | `order.refunded` |
| **Payment Gateway** | Updated | `payment-gateway.updated` |
| **Product** | Created | `product.created` |
|  | Updated | `product.updated` |
|  | Deleted | `product.deleted` |
| **Settings** | Created | `settings.created` |
|  | Updated | `settings.updated` |
|  | Deleted | `settings.deleted` |
| **Stock Transaction** | Created | `stock-transaction.created` |
| **Transaction** | Created | `transaction.created` |
|  | Updated | `transaction.updated` |

