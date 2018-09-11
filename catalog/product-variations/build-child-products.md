# Build Child Products

You will need to run the following request to build child variations.

{% api-method method="post" host="https://api.moltin.com" path="/v2/products/:id/build" %}
{% api-method-summary %}
Build Child Products
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the base product to be built
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Currency" type="string" required=false %}
ISO code of the required currency
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "type": "product",
    "id": "d8e64f88-7bb4-4095-a7e8-a55d094648bb",
    "name": "SPCA",
    "slug": "shirt",
    "sku": "1",
    "manage_stock": false,
    "description": "A shirt",
    "price": [
        {
            "amount": 500,
            "currency": "USD",
            "includes_tax": true
        }
    ],
    "status": "live",
    "commodity_type": "digital",
    "meta": {
        "timestamps": {
            "created_at": "2018-05-03T19:36:31+00:00",
            "updated_at": "2018-08-06T09:40:46+00:00"
        },
        "stock": {
            "level": 0,
            "availability": "out-stock"
        },
        "variations": {
                "id": "ccfb0d2c-8ed5-4dd8-ab41-ba883f4d3fbb",
                "name": "Shirt size",
                "options": [
                    {
                        "id": "581dd431-38f0-415f-98fc-ec64b5aa7f9d",
                        "name": "small",
                        "description": "Size small"
                    },
                    {
                        "id": "f4413e4d-8258-4510-87f9-4af0d75bfcb1",
                        "name": "medium",
                        "description": "Size medium"
                    },
                    {
                        "id": "143814e1-c75f-46d4-8d14-97d15405321f",
                        "name": "large",
                        "description": "Size large"
                    }
                ]
            }
        ]
    },
    "relationships": {
        "variations": {
            "data": [
                {
                    "type": "product-variation",
                    "id": "0c02ca9f-27be-48a8-89d9-cd7c30699343"
                }]
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
curl -X POST https://api.moltin.com/v2/products/:id/build/ \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

