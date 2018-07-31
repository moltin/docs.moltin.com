# Update a Product

{% api-method method="put" host="https://api.moltin.com" path="/v2/products/:id" %}
{% api-method-summary %}
Update by ID
{% endapi-method-summary %}

{% api-method-description %}
Updating an existing product.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the product you wish to update
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Language" type="string" required=false %}
If set, the system will store a record of the translation in the specific language
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant the API access
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being created. \(should be product\)
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
A human readable name for this product
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=false %}
A unique slug for this product
{% endapi-method-parameter %}

{% api-method-parameter name="sku" type="string" required=false %}
A unique SKU for this product
{% endapi-method-parameter %}

{% api-method-parameter name="mange\_stock" type="boolean" required=false %}
True if moltin should manage stock, false if not
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
A human readable description of the product
{% endapi-method-parameter %}

{% api-method-parameter name="price" type="array" required=false %}
An array of prices, one for each currency
{% endapi-method-parameter %}

{% api-method-parameter name="price.amount" type="string" required=false %}
Value of the price
{% endapi-method-parameter %}

{% api-method-parameter name="price.currency" type="string" required=false %}
Currency of this price. \(3 letter ISO\)
{% endapi-method-parameter %}

{% api-method-parameter name="price.includes\_tax" type="boolean" required=false %}
`true` if relevant taxes have been included in the price. `false` if not
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
`draft`, `live`
{% endapi-method-parameter %}

{% api-method-parameter name="commodity\_type" type="string" required=false %}
physical/digital
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "type": "product",
        "id": "b47372eb-6f13-4bcb-ad06-329f4ffee69d",
        "name": "A Product",
        "slug": "a-product-1",
        "sku": "SP01-{COLOUR}-new-2",
        "manage_stock": false,
        "description": "Some description",
        "price": [
            {
                "amount": 6999,
                "currency": "GBP",
                "includes_tax": true
            },
            {
                "amount": 7499,
                "currency": "USD",
                "includes_tax": true
            }
        ],
        "status": "live",
        "commodity_type": "physical",
        "meta": {
            "timestamps": {
                "created_at": "2018-05-11T20:07:56+00:00",
                "updated_at": "2018-05-12T00:50:11+00:00"
            },
            "display_price": {
                "with_tax": {
                    "amount": 7499,
                    "currency": "USD",
                    "formatted": "$74.99"
                },
                "without_tax": {
                    "amount": 7499,
                    "currency": "USD",
                    "formatted": "$74.99"
                }
            },
            "stock": {
                "level": 0,
                "availability": "out-stock"
            }
        },
        "relationships": {
            "categories": {
                "data": [
                    {
                        "type": "category",
                        "id": "3acf1815-ef09-44df-a6d3-e3e702663524"
                    }
                ]
            },
            "collections": {
                "data": [
                    {
                        "type": "collection",
                        "id": "10229491-7dbb-424d-be08-80c5735795cc"
                    }
                ]
            }
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
curl -X "PUT" https://api.moltin.com/v2/products/:id \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -H "X-Moltin-Language: en" \ # Optional language header
     -d $'{
        "data": {
            "type": "product",
            "id": "XXXX",
            "name": "Updated product name"
        }
    }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X',
  client_secret: 'X'
})

const id = 'XXXX'

const product = {
  'name': 'Updated product name'
}

Moltin.Products.Update(id, data).then(product => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

