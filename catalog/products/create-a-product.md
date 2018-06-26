# Create a Product

{% api-method method="post" host="https://api.moltin.com" path="/v2/products" %}
{% api-method-summary %}
Create a Product
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

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being created
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
A human readable name for this product
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
A unique slug for this product
{% endapi-method-parameter %}

{% api-method-parameter name="sku" type="string" required=true %}
A unique SKU for this product
{% endapi-method-parameter %}

{% api-method-parameter name="manage\_stock" type="boolean" required=true %}
True if moltin should manage stock, `false` if not
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
A human readable description of the product
{% endapi-method-parameter %}

{% api-method-parameter name="price" type="array" required=true %}
An array of prices, one for each currency
{% endapi-method-parameter %}

{% api-method-parameter name="price.amount" type="integer" required=true %}
Value of the price
{% endapi-method-parameter %}

{% api-method-parameter name="price.currency" type="string" required=true %}
Currency of this price \(3 letter ISO\)
{% endapi-method-parameter %}

{% api-method-parameter name="price.includes\_tax" type="boolean" required=false %}
true if relevant taxes have been included in the price, `false` if not
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
`draft`, `live`
{% endapi-method-parameter %}

{% api-method-parameter name="commodity\_type" type="string" required=false %}
`physical`, `digital`
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
        "id": "e41f25d8-a2c2-4af2-b316-364f3fc8048d",
        "name": "Deck Shoe",
        "slug": "deck-shoe_33",
        "sku": "deck-shoe_33",
        "manage_stock": false,
        "description": "Modern boat shoes were invented in 1935 by American Paul A. Sperry",
        "price": [
            {
                "amount": 5891,
                "currency": "USD",
                "includes_tax": true
            }
        ],
        "status": "live",
        "commodity_type": "physical",
        "relationships": {},
        "meta": {
            "display_price": {
                "with_tax": {
                    "amount": 5891,
                    "currency": "USD",
                    "formatted": "$58.91"
                },
                "without_tax": {
                    "amount": 5891,
                    "currency": "USD",
                    "formatted": "$58.91"
                }
            },
            "stock": {
                "level": 0,
                "availability": "out-stock"
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
curl -X POST https://api.moltin.com/v2/products \
     -H "Authorization: Bearer XXXX" \
     -d $'{
        "data": {
            "type": "product",
            "name": "Deck Shoe",
            "slug": "deck-shoe",
            "sku": "deck-shoe-001",
            "description": "Modern boat shoes were invented in 1935 by American Paul A. Sperry",
            "manage_stock": true,
            "price": [
            {
                "amount": 5891,
                "currency": "USD",
                "includes_tax": true
            }
            ],
            "status": "live",
            "commodity_type": "physical"
        }
    }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const product = {
  name: 'Deck Shoe',
  slug: 'deck-shoe',
  sku: 'deck-shoe-001',
  description: 'A product for testing purposes',
  manage_stock: false,
  price: [
    {
      amount: 5891,
      currency: 'USD',
      includes_tax: true
    }
  ],
  status: 'live',
  commodity_type: 'physical'
}

Moltin.Products.Create(product).then(product => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

