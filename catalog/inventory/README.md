# Inventory

The Moltin Inventory API allows you to manage stock for products in your project catalog. Each product keeps a history of inventory transactions, enabling easier stock auditing.

{% hint style="danger" %}
This feature is currently in **BETA** and you **should** expect it to change.
{% endhint %}

{% hint style="info" %}
You can specify an initial stock level when you create a product. Otherwise set to`0`by default, if not specified.
{% endhint %}

{% hint style="danger" %}
There are a number of actions that happen to your [inventory](https://docs.moltin.com/catalog/inventory) when checking out and paying for an order. For more information please be sure to evaluate our [detailed article](https://developers.moltin.com/guides/work-with-inventory) explaining the processes.
{% endhint %}

### The Stock object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for the stock |
| `type` | `string` | The type represents the object being returned |
| `total` | `integer` | The total amount of stock we have |
| `available` | `integer` | The amount of stock available for purchase |
| `allocated` | `integer` | The amount of paid for stock, also known as "reserved" |
{% endtab %}

{% tab title="Sample Object" %}
```javascript
{
  "data": {
    "id": "15fbeab0-75a3-4d6b-b23b-9db7455c077e",
    "type": "stock",
    "total": 100,
    "available": 90,
    "allocated": 10
  }
}
```
{% endtab %}
{% endtabs %}

