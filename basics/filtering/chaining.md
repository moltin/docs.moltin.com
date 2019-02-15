# Chaining

{% hint style="danger" %}
This feature is currently in **BETA** and you **should** expect it to change.
{% endhint %}

You can chain filters to a query by using a colon \(`:`\) to separate your filters.

For example, to find all draft products which are physical and sorted by `created_at`, you can make the following request:

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?filter=eq(status,draft):eq(commodity_type,physical) \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.Filter({
      eq: {
        status: 'live',
        slug: 'new-slug'
      },
      gt: {
        stock: 2
      }
    })
  .All()
  .Sort('created_at')
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product
  .filter(operator: .eq, key: "commodity_type", value: "physical")
  .sort("created_at")
  .all {
  // Do something
}
```
{% endtab %}
{% endtabs %}

