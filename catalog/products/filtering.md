# Filtering

Below is a list of attributes and operators available for [filtering](../../basics/filtering/) products.

| **Attribute** | **Type** | **Operators** | **Example** |
| :--- | :--- | :--- | :--- |
| `name` | `string` | `eq` / `like` | `like(name,Deck*)` |
| `slug` | `string` | `eq` / `like` | `eq(slug,deck-shoe)` |
| `sku` | `string` | `eq` / `like` | `eq(sku,deck-shoe-001)` |
| `status` | `string` | `eq` / `like` | `eq(status,live)` |
| `description` | `string` | `like` | `like(description,*deck*)` |
| `commodity_type` | `string` | `eq` | `eq(commodity_type,digital)` |
| `manage_stock` | `boolean` | `eq` | `eq(manage_stock,true)` |
| `brand.id` | `string` | `eq` | `eq(brand.id,id)` |
| `category.id` | `string` | `eq` | `eq(category.id,id)` |
| `collection.id` | `string` | `eq` | `eq(collection.id,id)` |

### Get all products for one category

In the example below, we will make a request to get all products that belong to one category.

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?filter=eq(category.id,XXXX) \
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
    category: {
      id: 'XXXX'
    }
  } 
})
  .With(["category"])
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { MoltinClient } = require('@moltin/request')

const client = new MoltinClient({
  client_id: 'X'
})

client
  .get('products?filter=eq(category.id,XXXX)')
  .then(products => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.filter(operator: .eq, key: "category.id", value: "xxxx").all {
response in
// Do something
}
```
{% endtab %}
{% endtabs %}



