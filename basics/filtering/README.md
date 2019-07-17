# Filtering

You can filter results returned from the API using a standard URI format.

## Supported operators

Not all supported operators work with all endpoint attributes. Each endpoint provides a list of filter attributes. Filtering on [custom data](../../advanced/custom-data/) fields \(Flows\) is not supported.

{% hint style="info" %}
You can only filter on base object attributes. Filtering through non-base attributes will not work as expected, and will return everything.
{% endhint %}

{% hint style="danger" %}
There is a maximum of 10 filters allowed on a single request.
{% endhint %}

| **Operator** | **Description** |
| :--- | :--- |
| `eq` | Equals |
| `like` | Like |
| `gt` | Greater than |
| `ge` | Greater than or equal to |
| `lt` | Less than |
| `le` | Less than or equal to |

Passing an incorrectly formatted filter or using an unsupported operator will return a `400` response with the following error:

```javascript
{
  "errors": [
    {
      "title": "Bad Request",
      "detail": "Could not parse the supplied filter"
    }
  ]
}
```

## Supported characters

As filters are passed as URL query string parameters, we must ensure all filters are URL safe and are strict about the characters that can be used in a filter.

| Characters | Can be used in filter? |
| :--- | :--- |
| `A-Z` \(upper & lower case\) | Yes |
| `0-9` | Yes |
| `$` `-` `_` `*` `.`  | Yes |
|  `` \(space\) | Yes \(an unencoded `+` will also be treated as a space\) |
| `+` | Only when URL encoded \(`%2B`\) |

Passing unsupported characters will return a `400` response with the following error:

```javascript
{
  "errors": [
    {
      "title": "Bad Request",
      "detail": "The supplied filter contained unsupported characters"
    }
  ]
}
```

## URL encoding filters

We recommend URL encoding filters before sending them to Moltin. For ease of use, you can encode the full filter, so `filter=eq(email,ron+1@swanson.com)` would become `filter=eq%28email%2Cron%2B1%40swanson.com%29`.

## Supported endpoints

* `/brands`
* `/categories`
* `/collections`
* `/customers`
* `/files`
* `/orders`
* `/products`

For more detail on filtering, see the Filtering section under each endpoint.

