# Tax Items

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
| `rate` | `float` | The tax rate percentage |
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
        "rate": 20.5
    }
}
```
{% endtab %}
{% endtabs %}

