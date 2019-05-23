# Sorting

Sort results that are returned from the API by using the `sort` parameter with the field name you wish to sort against. 

{% hint style="info" %}
To reverse the sort order, prepend the field with a minus.
{% endhint %}

Currently, sorting is supported for the following endpoints, and against the following fields:

{% hint style="warning" %}
You can not sort by created\_at or updated\_at if you are using filtering. 
{% endhint %}

| Endpoint | Fields to sort against |
| :--- | :--- |
| Brands | `created_at`, `description`, `name`, `slug`, `status`, `updated_at` |
| Categories | `created_at`, `description`, `name`, `slug`, `status`, `updated_at` |
| Collections | `created_at`, `description`, `name`, `slug`, `status`, `updated_at` |
| Products | `commodity_type`, `created_at`, `description`, `manage_stock`, `name`, `sku` ,`slug`, `status`, `updated_at` |
| Product Variations | `name` |
| Orders | `created_at`, `payment`, `shipping`, `status`, `with_tax` |

The example below shows how to make a request to get all products, and sort them by the `created_at` timestamp.

### Sort products by `created_at` ASC

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

### Sort products by `created_at` DESC

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

