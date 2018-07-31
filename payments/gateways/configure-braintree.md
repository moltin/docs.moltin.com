# Configure Braintree

You can configure Braintree programatically using the `/gateways/braintree` endpoint.

## The Braintree gateway object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `merchant_id` | `string` | Your Braintree merchant ID |
| `public_key` | `string` | Your Braintree public key |
| `private_key` | `string` | Your Braintree private key |
| `name` | `string` | The display name of the gateway |
| `environment` | `string` | `production` or `sandbox` |
| `slug` | `string` | A unique slug for this gateway |
| `type` | `string` | Always `gateway` |
| `enabled` | `boolean` | `true` or `false` that will enable the gateway |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "enabled": true,
    "environment": "production",
    "merchant_id": "xxx",
    "name": "Braintree",
    "private_key": "xxx",
    "public_key": "xxx",
    "slug": "braintree",
    "type": "gateway"
  }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/gateways/braintree" %}
{% api-method-summary %}
Update Braintree settings
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
{% api-method-parameter name="enabled" type="boolean" required=false %}
`true`, `false`
{% endapi-method-parameter %}

{% api-method-parameter name="environment" type="string" required=false %}
`production`, `sandbox`
{% endapi-method-parameter %}

{% api-method-parameter name="merchant\_id" type="string" required=false %}
Your Braintree merchant ID
{% endapi-method-parameter %}

{% api-method-parameter name="private\_key" type="string" required=false %}
Your Braintree private key
{% endapi-method-parameter %}

{% api-method-parameter name="public\_key" type="string" required=false %}
Your Braintree public key
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
    "enabled": true,
    "environment": "production",
    "merchant_id": "xxx",
    "name": "Braintree",
    "private_key": "xxx",
    "public_key": "xxx",
    "slug": "braintree",
    "type": "gateway"
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
curl -X PUT https://api.moltin.com/v2/gateways/braintree \
    -H "Authorization: Bearer XXXX" \
    -H "Content-Type: application/json" \
    -d $'{
      "data": {
        "enabled": true,
        "environment": "production",
        "merchant_id": "xxx",
        "private_key": "xxx",
        "public_key": "xxx",
      }
    }'
```
{% endtab %}
{% endtabs %}

