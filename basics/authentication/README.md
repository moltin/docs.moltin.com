# Authentication

All requests to the API need to be accompanied by an authorization header with an authentication token:

`Authorization: Bearer 212LJ3k0i2382364HIUEjfeJB98yvH`

Authentication token gives permissions for the client to access their data, and is used to authenticate a request to the API endpoint.

{% hint style="info" %}
Read our [Quick Start guide](https://developers.moltin.com/your-first-api-request) on how to make your first API request.
{% endhint %}

Authentication tokens are generated via the `authentication` endpoint and expire within 1 hour. They need to be then regenerated. If you're using our [JavaScript SDK](https://github.com/moltin/js-sdk) this is automatically handled for you.

There are two main token types available for use within your store `client_credentials` and `implicit`. The [implicit token](implicit-token.md) is the more limited of the two, restricting access to mostly read-only, whereas [client credential token](client-credential-token.md) has full read and write access. 

* For more details on token formatting, see: [Content Type](../content-type.md).

{% hint style="warning" %}
You should never use or disclose your `client_secret` in public.
{% endhint %}

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
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

### Client credentials vs. implicit use case scenarios

Typically, you'd use the implicit authentication method for client-side browser based applications \(i.e. frontend\), and client credentials for all administrative tasks \(CRUD\) you'd need to perform at the backend.

### Handle customer logging

Additional to endpoint authentication, you can provide logging capability. Use [customer token](../../orders-and-customers/customers/customer-tokens.md) to authenticate your customers with email and password.

