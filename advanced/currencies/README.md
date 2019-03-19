# Currencies

{% hint style="info" %}
There is a soft limit of 10 currencies per store.
{% endhint %}

## The Currency object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this currency |
| `type` | `string` | The type represents the object being returned |
| `code` | `string` | The currency code |
| `exchange_rate` | `float` | The exchange rate |
| `format` | `string` | How to structure a currency, E.g. `"${price}"` |
| `decimal_point` | `string` | The decimal point character |
| `thousand_separator` | `string` | The thousand separator character |
| `decimal_places` | `integer` | The amount of decimal places the currency is formatted to |
| `default` | `boolean` | `true` or `false` \(default: `false`\) |
| `links` | [`object`](./#the-links-object) | The links object |
| `meta` | [`object`](./#the-meta-object) | The meta object |
{% endtab %}

{% tab title="Sample Response" %}
```javascript
{
  "id": "451b94f8-0536-4580-91e1-68bad2f05925",
  "type": "currency",
  "code": "GBP",
  "exchange_rate": 1,
  "format": "£{price}",
  "decimal_point": ".",
  "thousand_separator": ",",
  "decimal_places": 0,
  "default": false,
  "enabled": true,
  "links": {
    "self":
      "https://api.moltin.com/currencies/451b94f8-0536-4580-91e1-68bad2f05925"
  },
  "meta": {
    "timestamps": {
      "created_at": "2017-09-27T08:48:01.821Z",
      "updated_at": "2018-04-24T19:19:40.941Z"
    }
  }
}
```
{% endtab %}
{% endtabs %}

## The `links` object

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `links.self` | `string` | The URL of this currency |

## The `meta` object

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `meta.timestamps` | `object` | Timestamps for this currency |
| `meta.timestamps.created_at` | `string` | The creation date of this currency |
| `meta.timestamps.updated_at` | `string` | The updated date of this currency |

