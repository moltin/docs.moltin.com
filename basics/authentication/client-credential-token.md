# Client credential token

A `client_credentials` token is used when the credentials are not publicly exposed, usually a server-side language such as PHP or Node.js. This type of authentication enables CRUD access to all resources.

{% hint style="warning" %}
`client_credentials` allows full read and write access to endpoints.
{% endhint %}

The diagram below illustrates the process flow for authentication for a server-side client credential application and a subsequent request to POST products.

![](../../.gitbook/assets/authentication-flow-client-credentials-2x.png)

{% api-method method="post" host="https://api.moltin.com" path="/oauth/access\_token" %}
{% api-method-summary %}
Create a client credential token
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="grant\_type" type="string" required=true %}
The grant type, in this case it must be **client\_credentials**
{% endapi-method-parameter %}

{% api-method-parameter name="client\_secret" type="string" required=true %}
Your **client\_secret**
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
Your **client\_id**
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
     -d "client_secret=XXXX" \
     -d "grant_type=client_credentials"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})
```
{% endtab %}
{% endtabs %}

