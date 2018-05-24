# Authentication

All requests to the API need to be accompanied by an authorisation header with a authentication token:

`Authorization: Bearer 212LJ3k0i2382364HIUEjfeJB98yvH`

Authentication tokens are generated via the authentication endpoint.

There are two main token types available for use within your store `client_credentials` and `implicit`. The implicit token is the more limited of the two, restricting access to mostly read-only whereas `client_credentials` has full read and write access.

{% hint style="warning" %}
You should never use or disclose your `client_secret` in public.
{% endhint %}

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `expires` | `timestamp` | The epoch time that this token expires at. |
| `identifier` | `string` | The type of token requested. This can be a `client_credentials` or `implicit`. |
| `expires_in` | `integer` | The duration in seconds in which the token will expire. |
| `access_token` | `string` | The access token you will use for subsequent authenticated requests to the API. |
| `token_type` | `string` | Right now this will only be `Bearer`. |
{% endtab %}

{% tab title="Sample Response" %}
```javascript
{
  "expires": 1500638876,
  "identifier": "client_credentials",
  "expires_in": 3600,
  "access_token": "xa3521ca621113e44eeed9232fa3e54571cb08bc",
  "token_type": "Bearer"
}
```
{% endtab %}
{% endtabs %}

