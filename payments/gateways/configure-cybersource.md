---
description: >-
  You can configure Stripe programatically using the `/gateways/cyber_source`
  endpoint.
---

# Configure CyberSource

### The CyberSource gateway object

{% tabs %}
{% tab title="Attributes" %}
| Attribute | Type | Description |
| :--- | :--- | :--- |
| login | `string` | Your live or test CyberSource merchant ID |
| password | `string` | Your live or test CyberSource SOAP key |
| type | `string` | This will always be `gateway` |
| name | `string` | The display name of the gateway |
| slug | `string` | A unique slug for the gateway |
| enabled | `boolean` | `true` or `false` that will enable the gateway |
| test | `boolean` | `true` or `false` that will enable test mode for the gateway |
{% endtab %}

{% tab title="Sample object" %}
```text
{
  "data": {
    "enabled": true,
    "test": true,
    "login": "xxx",
    "password": "xxx",
    "name": "CyberSource",
    "slug": "cyber_source",
    "type": "gateway"
  }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/gateways/cyber\_source" %}
{% api-method-summary %}
Update CyberSource settings
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
true or false that will enable the gateway
{% endapi-method-parameter %}

{% api-method-parameter name="test" type="boolean" required=false %}
true or false that will enable test mode for the gateway
{% endapi-method-parameter %}

{% api-method-parameter name="login" type="string" required=false %}
Your live or test CyberSource merchant ID
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
Your live or test CyberSource SOAP key
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

