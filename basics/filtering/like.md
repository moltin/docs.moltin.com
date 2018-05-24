# Like

## Begins with

In the example below we will make a request to get all products where the SKU **begins with** `SHOE_DECK`_._

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?filter=like(sku,SHOE_DECK_*) \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.Filter({ like: { sku: 'SHOE_DECK_*' } })
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.filter(operator: .like, key: "sku", value: "SHOE_DECK_*").all {
  // Do something
}
```
{% endtab %}
{% endtabs %}

## Contains

In the example below we will make a request to get all products where the SKU **contains** `_DECK_`.

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?filter=like(sku,*_DECK_*) \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.Filter({ like: { sku: '*_DECK_*' } })
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.filter(operator: .like, key: "sku", value: "*_DECK_*").all {
  // Do something
}
```
{% endtab %}
{% endtabs %}

## Ends with

In the example below we will make a request to all all products where the SKU **ends with** `_RED`.

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?filter=like(sku,*_RED) \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.Filter({ like: { sku: '*_RED' } })
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.filter(operator: .like, key: "sku", value: "*_RED").all {
  // Do something
}
```
{% endtab %}
{% endtabs %}

