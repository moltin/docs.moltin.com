# Delete a Brand

{% api-method method="delete" host="https://api.moltin.com" path="/v2/brands/:id" %}
{% api-method-summary %}
Delete by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the Brand to delete
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
curl -X DELETE https://api.moltin.com/v2/brands/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const id = 'XXXX'

Moltin.Brands.Delete(id).then(response => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const MoltinClient = require('@moltin/request')
​
const client = new createClient({
  client_id: 'X',
  client_secret: 'X'
})

const id = 'XXXX'​
​
client
  .delete(`brands/${id}`)
  .then(brand => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}
{% endtabs %}

