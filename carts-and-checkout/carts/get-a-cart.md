# Get a Cart

You can easily get a new or existing cart by providing the unique cart reference in the request.

{% hint style="warning" %}
An empty cart will be returned for any carts that don't currently exist. See [Get Cart Items](cart-items/get-cart-items.md#get-cart-items-by-cart-reference) for how the cart items object looks.
{% endhint %}

{% hint style="info" %}
We don't handle creating cart references. **You will need to create your own.**
{% endhint %}

{% hint style="warning" %}
If you do not pass a **`X-MOLTIN-CURRENCY`** header specifying what currency you would like the cart retrieved in, it will be returned with values in your default currency.
{% endhint %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/carts/:reference" %}
{% api-method-summary %}
Get a Cart by reference
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "360acb59-3fb7-4150-8066-ea54e850015b",
        "type": "cart",
        "links": {
            "self": "https://api.moltin.com/carts/360acb59-3fb7-4150-8066-ea54e850015b"
        },
        "meta": {
            "display_price": {
                "with_tax": {
                    "amount": 0,
                    "currency": "",
                    "formatted": "0"
                },
                "without_tax": {
                    "amount": 0,
                    "currency": "",
                    "formatted": "0"
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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/carts/:reference \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const reference = 'XXXX'

Moltin.Cart(reference)
  .Get()
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

client
  .get(`carts/${reference}`)
  .then(cart => {
    // Do something...
  })
  .catch(console.error)
```

{% hint style="info" %}
You can import `createCartIdentifier` from `@moltin/request` to create a Cart ID. **See below.**
{% endhint %}

```javascript
const { createClient, createCartIdentifier } = require('@moltin/request')
​
const client = new createClient({
  client_id: 'X'
})

const cartId = createCartIdentifier()​

client
  .get(`carts/${cartId}`)
  .then(cart => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

self.moltin.cart.get(forID: AppDelegate.cartID, completionHandler: { (result) in
    switch result {    
        case .success(let result):
            DispatchQueue.main.async {
                print("Cart:", result)
                }
            case .failure(let error):
                print("Cart error:", error)
            }
    })
```
{% endtab %}
{% endtabs %}

