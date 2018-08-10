# Customers

You can use the Customer API to store customer addresses. The Customer API allows you to generate JSON Web Tokens inside your client-side applications to authenticate requests to get all customer orders.

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

