# Filtering

You can filter results returned from the API using a standard URI format.

## Supported operators

Not all supported operators work with all endpoint attributes. Each endpoint provides a list of filter attributes. Filtering on [custom data](../../advanced/custom-data/) fields \(Flows\) is not supported.

{% hint style="info" %}
You can only filter on base object attributes. Filtering through non-base attributes will not work as expected, and will return everything.
{% endhint %}

| **Operator** | **Description** |
| :--- | :--- |
| `eq` | Equals |
| `like` | Like |
| `gt` | Greater than |
| `ge` | Greater than or equal to |
| `lt` | Less than |
| `le` | Less than or equal to |

## Supported endpoints

* `/brands`
* `/categories`
* `/collections`
* `/customers`
* `/files`
* `/orders`
* `/products`

For more detail on filtering, see the Filtering section under each endpoint.

