# Delete a Cart

You can easily remove all items from a cart.

{% api-method method="delete" host="https://api.moltin.com" path="/v2/carts/:reference" %}
{% api-method-summary %}
Delete cart by Reference
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
    "data": [
        {
            "type": "cart",
            "id": "360acb59-3fb7-4150-8066-ea54e850015b"
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
curl -X DELETE https://api.moltin.com/v2/carts/:reference \
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
  .Delete()
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
  .delete(`carts/${reference}`)
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

self.moltin.cart.deleteCart(referenceId, completionHandler: { (result)    in
    switch result {
        case .success(let result):
            print("Cart error:", result)
        case .failure(let error):
            print("Cart error:", error)
        }
})
```
{% endtab %}
{% endtabs %}

