# Delete a Tax Item

{% api-method method="delete" host="https://api.moltin.com" path="/v2/carts/:cartID/items/:itemID/taxes/:id" %}
{% api-method-summary %}
Delete by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the Tax Item to delete
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X DELETE https://api.moltin.com/v2/carts/:cartID/items/:itemID/taxes/:taxItemID \
     -H "Authorization: Bearer XXXX"
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
  .delete(`carts/${reference}/items/${itemId}/taxes/${taxItemID}`)
  .then(items => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}
{% endtabs %}

