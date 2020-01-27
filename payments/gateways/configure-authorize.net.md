# Configure Authorize.net

You can configure Authorize.net programatically using the `/gateways/authorize_net` endpoint.

## The Authorize.net gateway object <a id="the-stripe-gateway-object"></a>

{% tabs %}
{% tab title="Attributes" %}
| Attribute | Type | Descripttion |
| :--- | :--- | :--- |
| login | `string` | Your `live` or `test` API Login ID |
| password | `string` | Your `live` or `test` Transaction Key |
| type | `string` | This will always be `gateway` |
| name | `string` | The display name of the gateway |
| slug | `string` | A unique slug for this gateway |
| enabled | `boolean` | `true` or `false` that will enable the gateway |
| test | `boolean` | `true` or `false` that will enable test mode |
{% endtab %}

{% tab title="Sample Object" %}
```text
{
  "data": {
    "enabled": true,
    "login": "xxx",
    "password": "xxx",
    "name": "Stripe",
    "slug": "stripe",
    "type": "gateway",
    "test": false
  }
}
Update Stripe settings
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/gateways/authorize\_net" %}
{% api-method-summary %}
Update Authorize.net Settings
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
Authorize.net API Login ID
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
Authorize.net Transaction Key
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="string" required=false %}
`true`, `false`
{% endapi-method-parameter %}

{% api-method-parameter name="test" type="string" required=false %}
`true`, `false`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```text
curl -X PUT https://api.moltin.com/v2/gateways/authorize_net \
     -H "Authorization: Bearer XXX" \
     -H "Content-Type: application/json" \
     -d $'{
       "data": {
         "enabled": true,
         "login": "xxx",
         "password": "xxx",
         "test": true
       }
     }'
```

