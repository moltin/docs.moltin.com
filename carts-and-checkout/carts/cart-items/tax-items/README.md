# Tax Items

{% hint style="info" %}
Tax items can only be added and removed using [client\_credentials](../../../../basics/authentication/client-credential-token.md) tokens.
{% endhint %}

## The Tax Item Object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this cart item |
| `type` | `string` | `tax_item` |
| `name` | `string` | Denotes the name of this tax item |
| `jurisdiction` | `string` | The jurisdiction in which this tax applies |
| `code` | `string` | A tax code for this type of tax item |
| `rate` | `float` | The tax rate as a decimal \(20.5% -&gt; 0.205\) |
{% endtab %}

{% tab title="Sample Response" %}
```javascript
{
    "data": {
        "id": "003e2458-3415-4fd2-a10c-ed422bfac4bb",
        "type": "tax_item",
        "name": "Tax Name",
        "jurisdiction" : "UK",
        "code": "MYTAX01",
        "rate": 0.205
    }
}
```
{% endtab %}
{% endtabs %}

