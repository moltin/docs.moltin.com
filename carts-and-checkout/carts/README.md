# Carts

A Cart contains the product and custom cart items that a user may wish to purchase. Once a Cart is ready for Checkout, you can use the [Checkout](../checkout.md) endpoint to convert the cart to an order.

{% hint style="info" %}
Adding, modifying or removing any cart items, custom items or promotions will always return the cart meta. **This is useful to update the client with up-to-date totals.**
{% endhint %}

{% hint style="warning" %}
We'll automatically delete carts 7 days after they were last updated.
{% endhint %}

## The Cart Object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifer for the cart |
| `type` | `string` | This represents the type of object being returned |
| `links` | [`object`](./#the-links-object) | The links object |
| `meta` | [`object`](./#the-meta-object) | The meta object |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
    "data": {
        "id": "mycartreference",
        "type": "cart",
        "links": {
            "self": "https://api.moltin.com/v2/carts/mycartreference"
        },
        "meta": {
            "display_price": {
            "with_tax": {
                "amount": 5891,
                "currency": "USD",
                "formatted": "$58.91"
            },
            "without_tax": {
                "amount": 5891,
                "currency": "USD",
                "formatted": "$58.91"
            }
            },
            "timestamps": {
            "created_at": "0001-01-01T00:00:00Z",
            "updated_at": "0001-01-01T00:00:00Z"
            }
        }
    }
}
```
{% endtab %}
{% endtabs %}

## The Cart `links` object

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `self` | `string` | The URL of this cart |

## The Cart `meta` object

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `meta.display_price` | `object` | A collection of fields related to the total and currency of this cart |
| `meta.display_price.with_tax` | object | Tax inclusive totals |
| `meta.display_price.with_tax.amount` | integer | The raw total of this cart \(inc tax\) |
| `meta.display_price.with_tax.currency` | string | The currency set for this cart |
| `meta.display_price.with_tax.formatted` | string | The tax inclusive formatted total based on the currency |
| `meta.display_price.without_tax` | object | Tax exclusive totals |
| `meta.display_price.without_tax.amount` | integer | The raw total of this cart \(ex tax\) |
| `meta.display_price.without_tax.currency` | string | The currency set for this cart |
| `meta.display_price.without_tax.formatted` | string | The tax exclusive formatted total based on the currency |
| `meta.timestamps` | object | Timestamps for this cart |
| `meta.timestamps.created_at` | string | The creation date of this cart |
| `meta.timestamps.updated_at` | string | The last updated date of this cart |

