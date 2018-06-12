# Includes

You can easily include resource relationships on most top-level resources. Multiple includes are defined using comma delimited values.

Each supported resource includes its own documentation on the available resources that can be included.

Below are some common include examples.

{% api-method method="get" host="https://api.moltin.com" path="/v2/categories/:id?include=products" %}
{% api-method-summary %}
Include Category products
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the product
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="include" type="string" required=true %}
`products`
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
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
                    }
                ]
            }
        },
        "background_colour": "#ded7cb",
        "background_image": "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/61118f21-14a2-466c-a84b-c30b1f900cf9.png"
    },
    "included": {
        "products": [
            {
                "type": "product",
                "id": "41c84c63-4d5e-4135-979f-e4b681b83dcc",
                "name": "Orb",
                "slug": "orb",
                "sku": "ORLP100WHI",
                "manage_stock": false,
                "description": "Abstract, sculptural, refined and edgy with a modern twist. Its symmetrical, spoked structure generates a clever geometric presence, which works well in a contemporary environment.",
                "price": [
                    {
                        "amount": 45000,
                        "currency": "USD",
                        "includes_tax": true
                    }
                ],
                "status": "live",
                "commodity_type": "physical",
                "meta": {
                    "timestamps": {
                        "created_at": "2017-06-19T13:26:03+00:00",
                        "updated_at": "2018-03-13T13:43:57+00:00"
                    },
                    "display_price": {
                        "with_tax": {
                            "amount": 45000,
                            "currency": "USD",
                            "formatted": "$450.00"
                        },
                        "without_tax": {
                            "amount": 45000,
                            "currency": "USD",
                            "formatted": "$450.00"
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
                                "id": "61118f21-14a2-466c-a84b-c30b1f900cf9"
                            }
                        ]
                    },
                    "categories": {
                        "data": [
                            {
                                "type": "category",
                                "id": "521e6029-0e0e-4704-b9a5-9777047ada04"
                            }
                        ]
                    },
                    "main_image": {
                        "data": {
                            "type": "main_image",
                            "id": "61118f21-14a2-466c-a84b-c30b1f900cf9"
                        }
                    }
                }
            }
        ]
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
curl -X GET https://api.moltin.com/v2/categories/:id?include=products \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const id = 'XXXX'

Moltin.Categories.With('products')
  .Get(id)
  .then(category => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.category.include([.products]).get(forID: id) { result in
    switch result {
        case .success(let response):
            print(response)
        case .failure(let error):
            print(error)
    }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/products?include=main\_image" %}
{% api-method-summary %}
Include product main\_image
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="include" type="string" required=true %}
`main_image`
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?include=main_image \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const id = 'XXXX'

Moltin.Products.With('main_image')
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.product.include([.main_image]).all { result in
    switch result {
        case .success(let response):
            print(response)
        case .failure(let error):
            print(error)
    }
}
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/products?include=main\_images,category" %}
{% api-method-summary %}
Multiple includes
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="include" type="string" required=true %}
`main_images,category`
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token used to access the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products?include=main_image,category \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const id = 'XXXX'

Moltin.Products.With(['main_image', 'category'])
  .All()
  .then(products => {
    // Do something
  })
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.product.include([.main_image, .category]).all { result in
    switch result {
        case .success(let response):
            print(response)
        case .failure(let error):
            print(error)
    }
}
```
{% endtab %}
{% endtabs %}

