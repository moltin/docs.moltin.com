# Implicit token

An `implicit` token is typically used for situations where you are requesting data on the client side and you are exposing your public key.

You will use most likely use an `implicit` token inside client-side applications, such as JavaScript.

{% hint style="warning" %}
An `implicit` token can be thought of as a **READ ONLY** token.
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/oauth/access\_token" %}
{% api-method-summary %}
Create an implicit token
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="client\_id" type="string" required=true %}
Your **client\_id**
{% endapi-method-parameter %}

{% api-method-parameter name="grant\_type" type="string" required=true %}
The grant type, in this case it must be **implicit**
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "expires": 1524486008,
    "identifier": "client_credentials",
    "expires_in": 3600,
    "access_token": "xa3521ca621113e44eeed9232fa3e54571cb08bc",
    "token_type": "Bearer"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X "POST" "https://api.moltin.com/oauth/access_token" \
     -d "client_id=XXXX" \
     -d "grant_type=implicit"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")
```
{% endtab %}
{% endtabs %}

