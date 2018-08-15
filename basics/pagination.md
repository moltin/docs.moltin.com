# Pagination

You can easily paginate resources using `page[offset]` and `page[limit]` query string parameters on most top-level endpoints. Both of these values are **integers**.

Pagination is also supported within our JavaScript and Swift SDK.

{% hint style="info" %}
By default, page lengths are set to `100`. You can adjust this setting globally for your project via the [settings endpoint](../advanced/settings/#available-settings).
{% endhint %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/categories?page\[limit\]=2" %}
{% api-method-summary %}
Example: Get all categories, 2 per page
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="page\[limit\]" type="number" required=false %}
The number of items to return per page
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": [
        {
            "id": "521e6029-0e0e-4704-b9a5-9777047ada04",
            "type": "category",
            "status": "live",
            "name": "Bright",
            "slug": "bright",
            "description": "Bright Category",
            "meta": {
                "timestamps": {
                    "created_at": "2018-02-05T11:19:08+00:00",
                    "updated_at": "2018-03-29T10:34:13+00:00"
                }
            },
            "relationships": {
                "products": {
                    "data": [
                        {
                            "type": "product",
                            "id": "41c84c63-4d5e-4135-979f-e4b681b83dcc"
                        },
                        {
                            "type": "product",
                            "id": "bf8a9d62-6ca9-45f6-85eb-f0d1d9ae7fdd"
                        },
                        {
                            "type": "product",
                            "id": "36c21093-8996-4a9d-aacb-bf061f0769ed"
                        }
                    ]
                }
            },
            "background_colour": "#ded7cb",
            "background_image": "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/61118f21-14a2-466c-a84b-c30b1f900cf9.png"
        },
        {
            "id": "65c036ce-c13b-4c05-89d5-9a47b9763935",
            "type": "category",
            "status": "live",
            "name": "Silver",
            "slug": "Silver",
            "description": "Silver Category",
            "meta": {
                "timestamps": {
                    "created_at": "2017-07-31T20:25:44+00:00",
                    "updated_at": "2018-02-05T11:31:52+00:00"
                }
            },
            "relationships": {
                "products": {
                    "data": [
                        {
                            "type": "product",
                            "id": "2bc131a2-9cca-4a04-b40c-b19f773a1354"
                        },
                        {
                            "type": "product",
                            "id": "d77dcc0c-1e74-4e06-aff9-7f666dedafbe"
                        }
                    ]
                }
            },
            "background_colour": "#dadada",
            "background_image": "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/ca9dd645-638c-4dfa-9a60-1fa544d125fd.png"
        }
    ],
    "links": {
        "current": "https://api.moltin.com/v2/categories?page[limit]=2&page[offset]=0",
        "first": "https://api.moltin.com/v2/categories?page[limit]=2&page[offset]=0",
        "last": "https://api.moltin.com/v2/categories?page[limit]=2&page[offset]=2",
        "prev": null,
        "next": "https://api.moltin.com/v2/categories?page[limit]=2&page[offset]=2"
    },
    "meta": {
        "results": {
            "total": 2,
            "all": 4
        },
        "page": {
            "limit": 2,
            "offset": 0,
            "current": 1,
            "total": 2
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -g -X GET https://api.moltin.com/v2/products?page[limit]=2 \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.Limit(2)
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.limit(2).all {
  // Do something
}
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/categories?page\[limit\]=10&page=\[offset\]=20" %}
{% api-method-summary %}
Example: Get products 21 - 30
{% endapi-method-summary %}

{% api-method-description %}
Use page\[offset\] to get additional pages for your content.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="page\[offset\]" type="number" required=false %}
The number of pages to offset the results by
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": [
        {
            "id": "65c036ce-c13b-4c05-89d5-9a47b9763935",
            "type": "category",
            "status": "live",
            "name": "Silver",
            "slug": "Silver",
            "description": "Silver Category",
            "meta": {
                "timestamps": {
                    "created_at": "2017-07-31T20:25:44+00:00",
                    "updated_at": "2018-02-05T11:31:52+00:00"
                }
            },
            "relationships": {
                "products": {
                    "data": [
                        {
                            "type": "product",
                            "id": "2bc131a2-9cca-4a04-b40c-b19f773a1354"
                        },
                        {
                            "type": "product",
                            "id": "d77dcc0c-1e74-4e06-aff9-7f666dedafbe"
                        }
                    ]
                }
            },
            "background_colour": "#dadada",
            "background_image": "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/ca9dd645-638c-4dfa-9a60-1fa544d125fd.png"
        },
        {
            "id": "b8fac5c9-8605-48d0-bcf7-e6ada1a8c6bd",
            "type": "category",
            "status": "live",
            "name": "Modern",
            "slug": "modern",
            "description": "Modern Category",
            "meta": {
                "timestamps": {
                    "created_at": "2017-06-26T11:17:21+00:00",
                    "updated_at": "2018-02-05T11:26:12+00:00"
                }
            },
            "relationships": {
                "products": {
                    "data": [
                        {
                            "type": "product",
                            "id": "61abf56a-194e-4e13-a717-92d2f0c9d4df"
                        },
                        {
                            "type": "product",
                            "id": "4cdb1d36-19ee-48b2-a7c7-f3d4350ee45a"
                        },
                        {
                            "type": "product",
                            "id": "001b9188-3959-4269-aaf6-e4a74f8607b8"
                        }
                    ]
                }
            },
            "background_colour": "#e2d1bf",
            "background_image": "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/e490fd98-2439-46ef-88e6-20629d3bd269.png"
        }
    ],
    "links": {
        "current": "https://api.moltin.com/v2/categories?page[limit]=2&page[offset]=1",
        "first": "https://api.moltin.com/v2/categories?page[limit]=2&page[offset]=0",
        "last": "https://api.moltin.com/v2/categories?page[limit]=2&page[offset]=3",
        "prev": null,
        "next": "https://api.moltin.com/v2/categories?page[limit]=2&page[offset]=3"
    },
    "meta": {
        "results": {
            "total": 2,
            "all": 4
        },
        "page": {
            "limit": 2,
            "offset": 1,
            "current": 1,
            "total": 2
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -g -X GET https://api.moltin.com/v2/products?page[limit]=10&page[offset]=20 \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.Limit(10)
  .Offset(20)
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.product.limit(10).offset(20).all {
  // Do something
}
```
{% endtab %}
{% endtabs %}

