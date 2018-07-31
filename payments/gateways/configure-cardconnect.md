# Configure CardConnect

You can configure CardConnect programatically using the `/gateways/card_connect` endpoint.

## The CardConnect Gateway Object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `type` | `string` | Always `gateway` |
| `name` | `string` | The display name of the gateway |
| `merchant_id` | `string` | Your CardConnect Merchant ID |
| `username` | `string` | Your CardConnect username |
| `password` | `string` | Your CardConnect password |
| `slug` | `string` | A unique slug for this gateway |
| `enabled` | `boolean` | `true` or `false` that will enable the gateway |
| `test` | `boolean` | `true` or `false` to enable test transactions |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "type": "gateway"
    "name": "CardConnect",
    "merchant_id": "xxx",
    "username": "xxx"
    "password": "xxx",
    "slug": "cardconnect",
    "enabled": true,
    "test": false
  }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/gateways/card\_connect" %}
{% api-method-summary %}
Update CardConnect settings
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="test" type="boolean" required=false %}
Indicates whether test transactions are enabled
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
A unique slug for this gateway
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The display name of the gateway
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Always `gateway`
{% endapi-method-parameter %}

{% api-method-parameter name="username" type="string" required=false %}
Your CardConnect username
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
Your CardConnect password
{% endapi-method-parameter %}

{% api-method-parameter name="merchant\_id" type="string" required=false %}
Your CardConnect Merchant ID
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="boolean" required=false %}
`true`, `false`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "type": "gateway",
    "name": "CardConnect",
    "merchant_id": "",
    "username": ""
    "password": "",
    "slug": "cardconnect",
    "test": false,
    "enabled": false
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
curl -X PUT https://api.moltin.com/v2/gateways/card_connect \
     -H "Authorization: Bearer XXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
         "type": "gateway",
         "name": "CardConnect",
         "merchant_id": "",
         "username": ""
         "password": "",
         "slug": "cardconnect",
         "test": false,
         "enabled": false
       }
     }'
```
{% endtab %}
{% endtabs %}

