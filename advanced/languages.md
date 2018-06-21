# Languages

Moltin provides a multilingual service for the [Product API](../catalog/products/). Using the [Settings API](settings/update-settings.md#update-project-settings) you can add additional supported languages, and when you [update a product](../catalog/products/update-a-product.md), you can specify the `X-Moltin-Language` header.

{% hint style="info" %}
You can create translations for both product `name` and `description` fields.
{% endhint %}

{% api-method method="put" host="https://api.moltin.com" path="/v2/products/:id" %}
{% api-method-summary %}
Create a Translation
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the product you wish to update
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="description" type="string" required=false %}
The translated `description` value
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The translated `name` value
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The Product **ID**
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Always `product`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X PUT https://api.moltin.com/v2/products/:id \
    -H "Authorization: Bearer XXXX" \ 
    -H "X-Moltin-Language: es" \ 
    -H "Content-Type: application/json" \
    -d $'{
      "data": {
        "type": "product",
        "id": "{PRODUCT_ID}",
        "name": "nombre del producto"
        "description": "descripción del producto"
      }
    }'
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
If the requested language does not have a translation availabe, the default language will be returned.
{% endhint %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/products" %}
{% api-method-summary %}
Get all Products by Preferred Language
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Language" type="string" required=false %}
The language code as defined in project settings
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
    "data": [
        {
            "type": "product",
            "id": "9eda5ba0-4f4a-4074-8547-ccb05d1b5981",
            "name": "nombre del producto",
            "slug": "crown",
            "sku": "CWLP100BLK",
            "manage_stock": true,
            "description": "descripción del producto",
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
    -H "Authorization: Bearer XXXX" \ 
    -H "X-Moltin-Language: es"
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/products/:id" %}
{% api-method-summary %}
Get a translated Product by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the product
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Language" type="string" required=false %}
The language code as defined in project settings
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
  "data": {
    "type": "product",
    "id": "6837058c-ae42-46db-b3c6-7f01e0c34b40",
    "name": "nombre del producto",
    "description": "descripción del producto.",
    // ...
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
curl -X GET https://api.moltin.com/v2/products/:id \
    -H "Authorization: Bearer XXXX" \ 
    -H "X-Moltin-Language: es"
```
{% endtab %}
{% endtabs %}

