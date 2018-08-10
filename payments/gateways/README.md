# Gateways

You can programatically configure payment gateways using the Gateways endpoint. You can `enable` and `disable` built-in payment gateways.

{% hint style="warning" %}
Moltin provides a [Manual Gateway](../paying-for-an-order/manual-payments.md) that allows you to use another payment gateway, like PayPal. 🎉
{% endhint %}

### The gateways object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `name` | `string` | The name of the payment gateway |
| `slug` | `string` | The slug of the payment gateway |
| `type` | `string` | The type represents the object being returned |
| `enabled` | `boolean` | `true` or `false` depending on the enabled status |
{% endtab %}

{% tab title="Sample Response" %}
```javascript
{
  "data": {
    "enabled": false,
    "name": "Manual",
    "slug": "manual",
    "type": "gateway"
  }
}
```
{% endtab %}
{% endtabs %}



