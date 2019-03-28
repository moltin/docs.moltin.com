# Add Product to Cart

Adding a Product to Cart is the most common Cart action. If you wish to add any [custom products](add-product-to-cart.md) or [promotions](add-promotion-to-cart.md), you'll need to do that separately.

{% hint style="info" %}
Any requests to add a product to cart will return a collection of [cart items](cart-items/).
{% endhint %}

{% hint style="warning" %}
Please note that there is a soft limit of up to 100 unique items in a cart at any one time.
{% endhint %}

{% hint style="danger" %}
There are a number of actions that happen to your [inventory](https://docs.moltin.com/~/drafts/-LJsFeY2nae5ndXehUDs/primary/catalog/inventory) when checking out and paying for an order. For more information please be sure to evaluate our [detailed article](https://developers.moltin.com/guides/work-with-inventory) explaining the processes.
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/carts/:reference/items" %}
{% api-method-summary %}
Add Product to Cart
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="reference" type="string" required=true %}
A custom reference for this cart created by you
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-MOLTIN-CURRENCY" type="string" required=false %}
Specifies the currency to be used for the products in the cart.  Your site's default will be used if not specified
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="quantity" type="integer" required=true %}
The amount of products to add to cart
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
`cart_item`
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the product you wish to add to cart
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": [
        {
            "id": "8838d444-87f4-411f-9d89-9fc809f0b1cb",
            "type": "cart_item",
            "product_id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
            "name": "Crown",
            "description": "Abstract, sculptural, refined and edgy with a modern twist. Its symmetrical, spoked structure generates a clever geometric presence, which works well in a contemporary environment.",
            "sku": "CWLP100BLK",
            "image": {
                "mime_type": "image/png",
                "file_name": "lamp7-trans.png",
                "href": "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/7cc08cbb-256e-4271-9b01-d03a9fac9f0a.png"
            },
            "quantity": 1,
            "manage_stock": true,
            "unit_price": {
                "amount": 47500,
                "currency": "USD",
                "includes_tax": true
            },
            "value": {
                "amount": 47500,
                "currency": "USD",
                "includes_tax": true
            },
            "links": {
                "product": "https://api.moltin.com/products/9eda5ba0-4f4a-4074-8547-ccb05d1b5981"
            },
            "meta": {
                "display_price": {
                    "with_tax": {
                        "unit": {
                            "amount": 47500,
                            "currency": "USD",
                            "formatted": "47500"
                        },
                        "value": {
                            "amount": 47500,
                            "currency": "USD",
                            "formatted": "475.00"
                        }
                    },
                    "without_tax": {
                        "unit": {
                            "amount": 47500,
                            "currency": "USD",
                            "formatted": "47500"
                        },
                        "value": {
                            "amount": 47500,
                            "currency": "USD",
                            "formatted": "475.00"
                        }
                    }
                },
                "timestamps": {
                    "created_at": "2018-05-08T10:00:20.171620445Z",
                    "updated_at": "2018-05-08T10:00:20.171620445Z"
                }
            }
        }
    ],
    "meta": {
        "display_price": {
            "with_tax": {
                "amount": 47500,
                "currency": "USD",
                "formatted": "475.00"
            },
            "without_tax": {
                "amount": 47500,
                "currency": "USD",
                "formatted": "475.00"
            }
        },
        "timestamps": {
            "created_at": "2018-05-08T10:00:20.171620445Z",
            "updated_at": "2018-05-08T10:00:20.171620445Z"
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/carts/:reference/items \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": {
          "id": "df32387b-6ce6-4802-9b90-1126a5c5a54f",
          "type": "cart_item",
          "quantity": 1
        }
      }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const referenceId = 'XXXX'
const productId = 'XXXX'
const quantity = 1

Moltin.Cart(referenceId)
  .AddProduct(productId, quantity)
  .then(cart => {
    // Do something
  })
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { createClient } = require('@moltin/request')
​
const client = new createClient({
  client_id: 'X'
})

const reference = 'XXXX'
const productId = 'XXXX'
const quantity = 1

client
  .post(`carts/${reference}/items`, {
    type: "cart_item",
    id: productId,
    quantity
  })
  .then(cart => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let referenceId = 'XXXX'
let productId = 'XXXX'
let productQty = 'XXXX'


self.moltin.cart.addProduct(withID: productId , ofQuantity: productQty, toCart: referenceId, completionHandler: { (_) in

})

```
{% endtab %}
{% endtabs %}

