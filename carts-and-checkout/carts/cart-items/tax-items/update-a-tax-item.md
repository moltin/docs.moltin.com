# Update a Tax Item

{% api-method method="put" host="https://api.moltin.com" path="/v2/carts/:cartID/items/:itemID/taxes/:id" %}
{% api-method-summary %}
Update a Tax Item
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the Tax Item to update
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
Authentication token to track down who is emptying our stocks.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
This represents the type of the object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
A new name for the tax.
{% endapi-method-parameter %}

{% api-method-parameter name="jurisdiction" type="string" required=false %}
A new jurisdiction for this tax.
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=false %}
A new unique code for the tax in this jurisdiction.
{% endapi-method-parameter %}

{% api-method-parameter name="rate" type="number" required=false %}
A new tax rate, represented as a decimal \(12.5% -&gt; 0.125\).
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Tax item successfully updated.
{% endapi-method-response-example-description %}

```javascript
{
    "data": {
      "id": "003e2458-3415-4fd2-a10c-ed422bfac4bb",
      "type": "tax_item",
      "name": "Tax Name",
      "jurisdiction" : "UK",
      "code": "MYTAX01",
      "rate": 0.2
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
curl -X PUT https://api.moltin.com/v2/carts/:cartID/items/:itemID/taxes/:taxID \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer XXXX" \
    -d $'{
        "data": {
            "type": "tax_item",
            "name": "Tax Name",
            "jurisdiction" : "UK",
            "code": "MYTAX01",
            "rate": 0.2
        }
    }'
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { MoltinClient } = require('@moltin/request')
​
const client = new MoltinClient({
  client_id: 'X'
})

const reference = 'XXXX'
const itemId = 'XXXX'
const taxItemID = 'XXXX'

client
  .put(`carts/${reference}/items/${itemId}/taxes/${taxItemID}`, {
    type: "tax_item",
    name: "Tax Name",
    jurisdiction : "UK",
    code: "MYTAX01",
    rate: 0.2
  })
  .then(items => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}
{% endtabs %}

