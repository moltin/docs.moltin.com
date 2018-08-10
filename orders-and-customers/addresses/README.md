# Addresses

The Addresses API allows you to organize customer addresses. Addresses are a sub-resource of a [Customer](https://github.com/moltin/api.docs.moltin.com/tree/b8200284da4b87dabc0ac52bd3e38b0fd3943097/orders-and-customers/customers/README.md). A Customer may have multiple addresses, such as `home`, `work` and `neighbor`.

{% hint style="danger" %}
This feature is currently in **BETA** and you **should** expect it to change.
{% endhint %}

## The Address object

{% tabs %}
{% tab title="Attributes" %}
| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `id` | `string` | The unique identifier for this address |
| `type` | `string` | The type represents the object being returned |
| `first_name` | `string` | The first name of the recipient on this address |
| `last_name` | `string` | The last name of the recipient on this address |
| `name` | `string` | The name for the address saved. Such as `home`, `work` or `wife's office` |
| `phone_number` | `string` | A phone number for this address |
| `instructions` | `string` | Any delivery instructions associated with this addresses |
| `company_name` | `string` | The company name at this address |
| `line_1` | `string` | Usually the street name |
| `line_2` | `string` | Usually the unit or apartment number |
| `city` | `string` | The city for this address |
| `county` | `string` | The county for this address |
| `postcode` | `string` | The ZIP, postcode or other postal reference for this address |
| `country` | `string` | A two digit code for this country address. This is a `ISO 3166-2` standard. |
{% endtab %}

{% tab title="Sample Response" %}
```javascript

```
{% endtab %}
{% endtabs %}

