# Add Promotion to Cart

You can use the Promotions API to apply discounts to your cart as a special cart item type.

{% hint style="info" %}
Any requests to add a product to Cart will return a Collection of [cart items](cart-items/).
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/carts/:reference/items" %}
{% api-method-summary %}
Add Promotion to Cart
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="reference" type="string" required=true %}
A custom reference for the cart
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="code" type="string" required=false %}
The promotion code
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
`promotion_item`
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
      "id": "ea5b0837-d841-490e-a3ff-ac54707ee71b",
      "type": "promotion_item",
      "promotion_id": "4e2a79a5-1969-460e-b7ff-3efa81814fc2",
      "name": "testing",
      "description": "Promotion",
      "sku": "test",
      "image": {
        "mime_type": "",
        "file_name": "",
        "href": ""
      },
      "quantity": 1,
      "manage_stock": false,
      "unit_price": {
        "amount": -500,
        "currency": "USD",
        "includes_tax": false
      },
      "value": {
        "amount": -500,
        "currency": "USD",
        "includes_tax": false
      },
      "links": {},
      "meta": {
        "display_price": {
          "with_tax": {
            "unit": {
              "amount": -500,
              "currency": "USD",
              "formatted": "-$5.00"
            },
            "value": {
              "amount": -500,
              "currency": "USD",
              "formatted": "-$5.00"
            }
          },
          "without_tax": {
            "unit": {
              "amount": -500,
              "currency": "USD",
              "formatted": "-$5.00"
            },
            "value": {
              "amount": -500,
              "currency": "USD",
              "formatted": "-$5.00"
            }
          }
        },
        "timestamps": {
          "created_at": "2018-05-03T14:41:10.620170449Z",
          "updated_at": "2018-05-03T14:41:10.620171005Z"
        }
      }
    },
    {
      "id": "ee044aec-fa4f-47b1-98c5-ec4b86cc7839",
      "type": "cart_item",
      "product_id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
      "name": "Crown",
      "description":
        "Abstract, sculptural, refined and edgy with a modern twist. Its symmetrical, spoked structure generates a clever geometric presence, which works well in a contemporary environment.",
      "sku": "CWLP100BLK",
      "image": {
        "mime_type": "image/png",
        "file_name": "lamp7-trans.png",
        "href":
          "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/7cc08cbb-256e-4271-9b01-d03a9fac9f0a.png"
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
        "product":
          "https://api.moltin.com/products/9eda5ba0-4f4a-4074-8547-ccb05d1b5981"
      },
      "meta": {
        "display_price": {
          "with_tax": {
            "unit": {
              "amount": 47500,
              "currency": "USD",
              "formatted": "$475.00"
            },
            "value": {
              "amount": 47500,
              "currency": "USD",
              "formatted": "$475.00"
            }
          },
          "without_tax": {
            "unit": {
              "amount": 47500,
              "currency": "USD",
              "formatted": "$475.00"
            },
            "value": {
              "amount": 47500,
              "currency": "USD",
              "formatted": "$475.00"
            }
          }
        },
        "timestamps": {
          "created_at": "2018-05-03T10:07:49.952Z",
          "updated_at": "2018-05-03T10:07:49.952Z"
        }
      }
    }
  ],
  "meta": {
    "display_price": {
      "with_tax": {
        "amount": 47000,
        "currency": "USD",
        "formatted": "$470.00"
      },
      "without_tax": {
        "amount": 47000,
        "currency": "USD",
        "formatted": "$470.00"
      }
    },
    "timestamps": {
      "created_at": "2018-05-03T10:07:49.952Z",
      "updated_at": "2018-05-03T10:07:49.952Z"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
If you try to add a code that does not exist, you will get a `404` response.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "status": 404,
      "title": "Not Found",
      "detail": "No promotion could be found with the given code."
    }
  ]
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
     -d $'{
       "data": {
         "type": "promotion_item",
         "code": "PROMO_CODE"
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
const promoCode = 'XXXX'

Moltin.Cart(reference)
  .AddPromotion(promoCode)
  .then(cart => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift

```
{% endtab %}
{% endtabs %}

