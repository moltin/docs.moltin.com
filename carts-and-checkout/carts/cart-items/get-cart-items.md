# Get Cart Items

{% hint style="info" %}
An empty cart items array will be returned for any carts that don't currently exist using the provided cart reference.
{% endhint %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/carts/:reference/items" %}
{% api-method-summary %}
Get Cart Items by Cart reference
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
    "data": [],
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
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/carts/:reference/items \
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
  .Items()
  .then(cart => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let referenceId = 'XXXX'

self.moltin.cart.items(forCartID: referenceId) { (result) in
    switch result {
        case .success(let result):
            DispatchQueue.main.async {
                 print("Cart items:", result.data)
            }
            case .failure(let error):
                print("Cart error:", error)
            }
        }
    }

```
{% endtab %}
{% endtabs %}

