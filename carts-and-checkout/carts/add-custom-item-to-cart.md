# Add Custom Item to Cart

You will want to add a custom item to the cart to handle things like shipping, taxes and inventory you don't manage with Moltin.

{% hint style="info" %}
Any requests to add a product to cart will return a collection of [cart items](cart-items/).
{% endhint %}

{% hint style="warning" %}
Custom Cart Items are available via [**implicit authentication**](../../basics/authentication/implicit-token.md). You should **always check** each order has the correct details for each item, most importantly, price.
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/carts/:reference/items" %}
{% api-method-summary %}
Add Custom Item to Cart
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
Specifies the currency to be used for the products in the cart. Your site's default will be used if not specified
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
`custom_item`
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the custom item
{% endapi-method-parameter %}

{% api-method-parameter name="sku" type="string" required=false %}
The SKU code to use for the custom item
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
A description of the custom item
{% endapi-method-parameter %}

{% api-method-parameter name="quantity" type="integer" required=true %}
The amount of custom items to add to cart
{% endapi-method-parameter %}

{% api-method-parameter name="price.amount" type="integer" required=true %}
The price of the custom item
{% endapi-method-parameter %}

{% api-method-parameter name="price.includes\_tax" type="boolean" required=false %}
`true` if relevant taxes have been included in the price, `false` if not. Defaults to `true`
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
            "id": "581db51b-d4df-4aff-855d-e8ddbcf81b0c",
            "type": "custom_item",
            "name": "My Custom Item",
            "description": "My first custom item!",
            "sku": "my-custom-item",
            "image": {
                "mime_type": "",
                "file_name": "",
                "href": ""
            },
            "quantity": 1,
            "manage_stock": false,
            "unit_price": {
                "amount": 10000,
                "currency": "USD",
                "includes_tax": true
            },
            "value": {
                "amount": 10000,
                "currency": "USD",
                "includes_tax": true
            },
            "links": {},
            "meta": {
                "display_price": {
                    "with_tax": {
                        "unit": {
                            "amount": 10000,
                            "currency": "USD",
                            "formatted": "$100.00"
                        },
                        "value": {
                            "amount": 10000,
                            "currency": "USD",
                            "formatted": "$100.00"
                        }
                    },
                    "without_tax": {
                        "unit": {
                            "amount": 10000,
                            "currency": "USD",
                            "formatted": "$100.00"
                        },
                        "value": {
                            "amount": 10000,
                            "currency": "USD",
                            "formatted": "$100.00"
                        }
                    }
                },
                "timestamps": {
                    "created_at": "2018-05-08T10:11:17.871313413Z",
                    "updated_at": "2018-05-08T10:11:17.871313413Z"
                }
            }
        }
    ],
    "meta": {
        "display_price": {
            "with_tax": {
                "amount": 57500,
                "currency": "USD",
                "formatted": "$575.00"
            },
            "without_tax": {
                "amount": 57500,
                "currency": "USD",
                "formatted": "$575.00"
            }
        },
        "timestamps": {
            "created_at": "2018-05-08T10:00:20.171Z",
            "updated_at": "2018-05-08T10:11:17.871313413Z"
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
        "type": "custom_item",
        "name": "My Custom Item",
        "sku": "my-custom-item",
        "description": "My first custom item!",
        "quantity": 1,
        "price": {
          "amount": 10000
        }
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

const reference = 'XXXX'
const item = {
  name: 'My Custom Item',
  sku: 'my-custom-item',
  description: 'My first custom item!',
  quantity: 1,
  price: {
    amount: 10000
  }
}

Moltin.Cart(reference)
  .AddCustomItem(item)
  .then(cart => {
    // Do something
  })
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const MoltinClient = require('@moltin/request')
​
const client = new createClient({
  client_id: 'X'
})

const reference = 'XXXX'

client
  .post(`carts/${reference}/items`, {
    type: "custom_item",
    name: 'My Custom Item',
    sku: 'my-custom-item',
    description: 'My first custom item!',
    quantity: 1,
    price: {
      amount: 10000
    }
  })
  .then(cart => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}
{% endtabs %}

