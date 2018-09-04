# Filtering

You can filter results returned from the API using a standard URI format.

## Supported operators

| **Operator** | **Description** |
| :--- | :--- |
| `eq` | Equals |
| `like` | Like |
| `gt` | Greater than |
| `ge` | Greater than or equal to |
| `lt` | Less than |
| `le` | Less than or equal to |

{% hint style="info" %}
Not all endpoint attributes are available for the supported operators below. Each endpoint provides a list of filter attributes.  You are not able to filter on custom data fields \(flows\).
{% endhint %}

## Supported endpoints

* `/brands`
* `/categories`
* `/collections`
* `/customers`
* `/files`
* `/orders`
* `/products`

For more detail on filtering, see the Filtering section under each endpoint.

