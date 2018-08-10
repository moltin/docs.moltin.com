# Configure Adyen

You can configure Adyen programatically using the `/gateways/adyen` endpoint.

## The Adyen gateway object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `username` | `string` | Your web service username |
| `type` | `string` | This will always be `gateway` |
| `test` | `boolean` | `true` or `false` to enable test transactions |
| `merchant_account` | `string` | Your Adyen account name |
| `name` | `string` | The display name of the gateway |
| `slug` | `string` | A unique slug for this gateway |
| `password` | `string` | Your web service user password |
| `enabled` | `boolean` | `true` or `false` that will enable the gateway |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "enabled": true,
    "merchant_account": "xxx",
    "name": "Adyen",
    "password": "xxx",
    "slug": "adyen",
    "test": false,
    "type": "gateway",
    "username": "xxx"
  }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/gateways/adyen" %}
{% api-method-summary %}
Update Adyen settings
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
{% api-method-parameter name="test" type="string" required=false %}
`true` or `false` to enable test transactions
{% endapi-method-parameter %}

{% api-method-parameter name="username" type="string" required=false %}
Your web service username
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
Your web service user password
{% endapi-method-parameter %}

{% api-method-parameter name="merchant\_account" type="string" required=false %}
Your Adyen account name
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
    "enabled": false,
    "merchant_account": "",
    "name": "Adyen",
    "password": "",
    "slug": "adyen",
    "test": false,
    "type": "gateway",
    "username": ""
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
curl -X PUT https://api.moltin.com/v2/gateways/adyen \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXX" \
     -d $'{
        "data": {
           "enabled": true,
           "merchant_account": "xxx",
           "password": "xxx",
           "test": false,
           "username": "xxx"
        }
     }'
```
{% endtab %}
{% endtabs %}

