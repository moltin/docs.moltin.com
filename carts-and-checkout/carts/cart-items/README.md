# Cart Items

## The Cart Item object

Products add to a cart are referred to as a cart\_item.

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `id` | `string` | The unique identifier for this cart item |
| `type` | `string` | `cart_item`, `custom_item` or `promotion_item` |
| `name` | `string` | Denotes the name of this item |
| `description` | `string` | A description of the cart item |
| `sku` | `string` | The SKU code for the item |
| `image` | [`object`](./#the-cart-item-image-object) | The product image |
| `quantity` | `integer` | How many of this item have been added to the cart |
| `unit_price` | [`object`](./#the-cart-item-unit_price-object) | Contains pricing information about a single instance of this item |
| `value` | [`object`](./#the-cart-item-value-object) | Contains pricing information total value of this item line based on the quantity |
| `links` | [`object`](./#the-cart-item-links-object) | A collection of URLs related to this resource |
| `meta` | [`object`](./#the-cart-item-meta-object) | Additional information calculated for this cart |
{% endtab %}

{% tab title="Sample Response" %}
```javascript
{
    "data": {
        "id": "6aa9580e-3a27-49fb-8af3-3b93a71add91",
        "type": "cart_item",
        "product_id": "df32387b-6ce6-4802-9b90-1126a5c5a54f",
        "name": "Deck Shoe",
        "description": "Modern boat shoes were invented in 1935 by American Paul A. Sperry of New Haven, Connecticut after noticing his dog's ability to run easily over ice without slipping. Using a knife, he cut siping into his shoes' soles, inspiring a shoe perfect for boating and a company called Sperry Top-Sider.",
        "sku": "DS.001",
        "quantity": 1,
        "unit_price": {
            "amount": 8950,
            "currency": "GBP",
            "includes_tax": true
        },
        "value": {
            "amount": 8950,
            "currency": "GBP",
            "includes_tax": true
        },
        "image": {
            "file_name": "deck-shoe.jpg",
            "mime_type": "image/jpeg",
            "href": "http://example.com/deck-shoe.jpg"
        },
        "links": {
            "product": "https://api.moltin.com/v2/products/df32387b-6ce6-4802-9b90-1126a5c5a54f"
        },
        "meta": {
            "display_price": {
                "with_tax": {
                    "unit": {
                        "amount": 8950,
                        "currency": "GBP",
                        "formatted": "£89.50"
                    },
                    "value": {
                        "amount": 8950,
                        "currency": "GBP",
                        "formatted": "£89.50"
                    }
                },
                "without_tax": {
                    "unit": {
                        "amount": 8950,
                        "currency": "GBP",
                        "formatted": "£89.50"
                    },
                    "value": {
                        "amount": 8950,
                        "currency": "GBP",
                        "formatted": "£89.50"
                    }
                }
            },
        "timestamps": {
            "created_at": "2017-10-25T14:08:28.569Z",
            "updated_at": "2017-10-25T14:08:28.569Z"
        }
    }
}
```
{% endtab %}
{% endtabs %}

## The Cart Item `image` object

| **Attribute** | **Type** | **Description** |
| --- | --- |
| `file_name` | `string` | The name of the image file that was uploaded |
| `mime_type` | `string` | The MIME type for the uploaded file |
| `href` | `string` | The link to the image |

## The Cart Item `unit_price` object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `unit_price.amount` | `integer` | The singular price of this item as an integer |
| `unit_price.currency` | `string` | The currency this item was added to the cart as |
| `unit_price.includes_tax` | `boolean` | Whether or not this price is tax inclusive |

## The Cart Item `value` object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `value.amount` | `integer` | The total price for this item line \(quantity \* unit\_price.amount\) |
| `value.currency` | `string` | The currency this item was added to the cart as |
| `value.includes_tax` | `boolean` | Whether or not this price is tax inclusive |

## The Cart Item `links` object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `links.product` | `string` | A link to the product this cart item is a snapshot of \(not for `custom_items`\) |
| `value.currency` | `string` | The currency this item was added to the cart as |

## The Cart Item `meta` object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `meta.display_price` | `object` | A collection of fields related to the totals and currency of this cart item |
| `meta.display_price.with_tax` | `object` | Tax inclusive totals |
| `meta.display_price.with_tax.unit` | `object` | Tax inclusive totals for a single instance of this cart item |
| `meta.display_price.with_tax.unit.amount` | `integer` | The raw price of a single instance this cart item \(inc tax\) |
| `meta.display_price.with_tax.currency` | `string` | The currency set for this cart item |
| `meta.display_price.with_tax.formatted` | `string` | The tax inclusive formatted total of a single instance of this cart item based on the currency |
| `meta.display_price.with_tax.value` | `object` | Tax inclusive totals for this cart item based on the quantity |
| `meta.display_price.with_tax.value.amount` | `integer` | The raw total price this cart item line \(inc tax\) |
| `meta.display_price.with_tax.value.currency` | `string` | The currency set for this cart item |
| `meta.display_price.with_tax.value.formatted` | `string` | The tax inclusive formatted total of this cart item line based on the currency |
| `meta.display_price.without_tax` | `object` | Tax exclusive totals |
| `meta.display_price.without_tax.unit` | `object` | Tax exclusive totals for a single instance of this cart item |
| `meta.display_price.without_tax.unit.amount` | `integer` | The raw price of a single instance this cart item \(ex tax\) |
| `meta.display_price.without_tax.currency` | `string` | The currency set for this cart item |
| `meta.display_price.without_tax.formatted` | `string` | The tax exclusive formatted total of a single instance of this cart item based on the currency |
| `meta.display_price.without_tax.value` | `object` | Tax exclusive totals for this cart item based on the quantity |
| `meta.display_price.without_tax.value.amount` | `integer` | The raw total price this cart item line \(ex tax\) |
| `meta.display_price.without_tax.value.currency` | `string` | The currency set for this cart item |
| `meta.display_price.without_tax.value.formatted` | `string` | The tax inclusive formatted total of this cart item line based on the currency |
| `meta.timestamps` | `object` | Timestamps for this cart item |
| `meta.timestamps.created_at` | `string` | The creation date of this cart item |
| `meta.timestamps.updated_at` | `string` | The last updated date of this cart item |

