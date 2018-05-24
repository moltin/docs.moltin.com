# Configure Stripe

You can configure Stripe programatically using the `/gateways/stripe` endpoint.

## The Stripe gateway object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| --- | --- | --- | --- | --- | --- |
| `login` | `string` | Your `live` or `test` Stripe secret key |
| `type` | `string` | This will always be `gateway` |
| `name` | `string` | The display name of the gateway |
| `slug` | `string` | A unique slug for this gateway |
| `enabled` | `boolean` | `true` or `false` that will enable the gateway |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "enabled": true,
    "login": "xxx",
    "name": "Stripe",
    "slug": "stripe",
    "type": "gateway"
  }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/gateways/stripe" %}
{% api-method-summary %}
Update Stripe settings
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
{% api-method-parameter name="login" type="string" required=false %}
Stripe `test` or `live` secret key
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
    "enabled": true,
    "login": "xxx",
    "name": "Stripe",
    "slug": "stripe",
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
curl -X PUT https://api.moltin.com/v2/gateways/stripe \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXX" \
     -d $'{
       "data": {
         "enabled": true,
         "login": "xxx"
       }
     }'
```
{% endtab %}
{% endtabs %}

