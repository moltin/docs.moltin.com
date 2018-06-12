# Equals

In the example below, we will make a request to get all digital products from the Moltin catalogue.

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?filter=eq(commodity_type,digital) \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.Filter({ eq: { commodity_type: 'digital' } })
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.filter(operator: .eq, key: "commodity_type", value: "digital").all {
  // Do something
}
```
{% endtab %}
{% endtabs %}



