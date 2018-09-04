# Sorting

You can easily sort results that are returned from the API. **For example** you could make the following request to get all products and sort them by the `created_at` timestamp.

## Sort products by `created_at` ASC

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?sort=created_at
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.All()
  .Sort('created_at')
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.sort("created_at").all {
  // Do something
}
```
{% endtab %}
{% endtabs %}

## Sort products by `created_at` DESC

{% hint style="info" %}
To reverse the sort order, you must prepend a minus.
{% endhint %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?sort=-created_at
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.All()
  .Sort('-created_at')
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.sort("-created_at").all {
  // Do something
}
```
{% endtab %}
{% endtabs %}

