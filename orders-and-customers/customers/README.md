# Customers

You can use the Customer endpoint to store customer addresses and other information.  

The Customer endpoint allows you to generate JSON Web Tokens inside your client-side applications to authenticate requests to get all customer orders.  

{% page-ref page="customer-tokens.md" %}

You are able to use a [customer](customer-tokens.md) token with an [implicit](../../basics/authentication/implicit-token.md#create-an-implicit-token) Bearer token.  This is recommend for client-side interactions.  Or you can use a [client\_credentials](../../basics/authentication/client-credential-token.md#create-a-client-credential-token) Bearer token.  This is recommended for back end interactions.

### The Customer object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this customer |
| `type` | `string` | The type represents the object being returned |
| `name` | `string` | The `name` of the customer |
| `email` | `string` | The `email` of the customer |
| `password` | `string` | `true` |
{% endtab %}

{% tab title="Sample Response" %}
```javascript
{
    "data": {
        "type": "customer",
        "id": "f260b17a-390f-4b37-bf9d-f62c45a95865",
        "name": "Ron Swanson",
        "email": "ron@swanson.com",
        "password": true
    }
}
```
{% endtab %}
{% endtabs %}

