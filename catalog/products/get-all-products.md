# Get all Products

{% hint style="info" %}
Products with a `live` status will only be returned when requesting via [implicit](../../basics/authentication/implicit-token.md) authentication.
{% endhint %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/products" %}
{% api-method-summary %}
Get all Products
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}

{% api-method-parameter name="X-Moltin-Currency" type="string" required=false %}
Format display prices with an enabled store currency code
{% endapi-method-parameter %}

{% api-method-parameter name="X-Moltin-Language" type="string" required=false %}
Return a specific translation with enabled store translations.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="page\[limit\]" type="string" required=false %}
The number of items to return per page
{% endapi-method-parameter %}

{% api-method-parameter name="page\[offset\]" type="string" required=false %}
The number of pages to offset the results by
{% endapi-method-parameter %}

{% api-method-parameter name="sort" type="string" required=false %}
Sort the attributes
{% endapi-method-parameter %}

{% api-method-parameter name="filter" type="string" required=false %}
Filter the results
{% endapi-method-parameter %}

{% api-method-parameter name="include" type="string" required=false %}
`main_image`, `files`, `brands`, `categories`, `collections`
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
            "type": "product",
            "id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
            "name": "Crown",
            "slug": "crown",
            "sku": "CWLP100BLK",
            "manage_stock": true,
            "description": "Abstract, sculptural, refined and edgy with a modern twist. Its symmetrical, spoked structure generates a clever geometric presence, which works well in a contemporary environment.",
            "price": [
                {
                    "amount": 47500,
                    "currency": "USD",
                    "includes_tax": true
                }
            ],
            "status": "live",
            "commodity_type": "physical",
            "meta": {
                "timestamps": {
                    "created_at": "2017-06-19T14:58:42+00:00",
                    "updated_at": "2018-04-10T09:12:05+00:00"
                },
                "display_price": {
                    "with_tax": {
                        "amount": 47500,
                        "currency": "USD",
                        "formatted": "$475.00"
                    },
                    "without_tax": {
                        "amount": 47500,
                        "currency": "USD",
                        "formatted": "$475.00"
                    }
                },
                "stock": {
                    "level": 500,
                    "availability": "in-stock"
                }
            },
            "relationships": {
                "files": {
                    "data": [
                        {
                            "type": "file",
                            "id": "7cc08cbb-256e-4271-9b01-d03a9fac9f0a"
                        }
                    ]
                },
                "categories": {
                    "data": [
                        {
                            "type": "category",
                            "id": "a636c261-0259-4975-ac8e-77246ec9cfe0"
                        }
                    ]
                },
                "main_image": {
                    "data": {
                        "type": "main_image",
                        "id": "7cc08cbb-256e-4271-9b01-d03a9fac9f0a"
                    }
                }
            },
            "material": null,
            "max_watt": null,
            "bulb_qty": null,
            "bulb": null,
            "new": null,
            "on_sale": null,
            "background_colour": "#d9d9d9",
            "finish": "test"
        }
    ],
    "links": {
        "current": "https://api.moltin.com/v2/products?page[limit]=100&page[offset]=0",
        "first": "https://api.moltin.com/v2/products?page[limit]=100&page[offset]=0",
        "last": null
    },
    "meta": {
        "results": {
            "total": 10,
            "all": 10
        },
        "page": {
            "limit": 100,
            "offset": 0,
            "current": 1,
            "total": 1
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
curl -X GET https://api.moltin.com/v2/products \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Products.All().then(products => {
  // Do something
})
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

self.moltin.product.include([.mainImage]).all { (result: Result<PaginatedResponse<[moltin.Product]>>) in
   switch result {
       case .success(let response):
            DispatchQueue.main.async {
                self.products = response.data ?? []
            }
        case .failure(let error):
            print("Products error", error)
        }
    }
}
```
{% endtab %}
{% endtabs %}

