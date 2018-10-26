# Links

Links are used to allow you as an API consumer to move between requests.

Single entities use a `self` parameter with a link to that specific resource:

```text
"links": {"self": "https://api.moltin.com/carts/1"},
```

Listing pages use `current`, `first`, `last`, `next`, `previous`:

```text
"links": {
    "current": "https://api.moltin.com/v2/products?page[limit]=100&page[offset]=0",
    "first": "https://api.moltin.com/v2/products?page[limit]=100&page[offset]=0",
    "last": "https://api.moltin.com/v2/products?page[limit]=100&page[offset]=600",
    "prev": null,
    "next": "https://api.moltin.com/v2/products?page[limit]=100&page[offset]=100"
},
```

Sometimes, there may not be enough entities for a store to fill multiple pages. In this situation, we will return some defaults, instead of expecting you as a consumer to check for these special cases.

| Property | ​ |
| :--- | :--- |
| `current` | Always the current page |
| `first` | Always the first page |
| `last` | `null` if there is only one page |
| `prev` | `null` if the user is on the first page |
| `next` | `null` if there is only one page |



