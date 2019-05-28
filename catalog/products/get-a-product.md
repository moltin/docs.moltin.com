# Get a Product

{% api-method method="get" host="https://api.moltin.com" path="/v2/products/:id" %}
{% api-method-summary %}
Get by ID
{% endapi-method-summary %}

{% api-method-description %}
This endpoint retrieves an existing Product by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID for the requested Product
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API. Implicit Bearer token only returns products with live status; products with draft status won't be included.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
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
    "data": {
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
            },
            "variation_matrix": []
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
        "material": null, // Custom flow field
        "max_watt": null, // Custom flow field
        "bulb_qty": null, // Custom flow field
        "bulb": null, // Custom flow field
        "new": null, // Custom flow field
        "on_sale": null, // Custom flow field
        "background_colour": "#d9d9d9", // Custom flow field
        "finish": "test" // Custom flow field
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
Please note that there will only be a display\_price in your response if the product you are requesting has a price in the currency you are using as a header. If a header is not passed, the product must have a price in your default currency.
{% endhint %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/products/:id \
     -H "Authorization: Bearer XXXX" \
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const id = 'XXXX'

Moltin.Products.Get(id).then(product => {
  // Do something
})
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { MoltinClient } = require('@moltin/request')

const client = new MoltinClient({
  client_id: 'X'
})

const id = 'XXXX'

client
  .get(`products/${id}`)
  .then(product => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

let id = "XXXX"

moltin.product.get(forID: id) { result in
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

