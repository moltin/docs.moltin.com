# Product Attributes

Below is a list of attributes available for [i](https://docs.moltin.com/~/drafts/-LZnl8KHwDn-tl_rVz1V/primary/basics/filtering)mporting a CSV file into Moltin. 

| Field name | Data type | Required? |
| :--- | :--- | :--- |
| `type` | `product` | true |
| `id` | string | true |
| `name` | string | true |
| `slug` | string | true |
| `sku` | string | true |
| `manage_stock` | boolean | true |
| `description` | string | true |
| `price` | `array` | false |
| `price.amount` | integer | true |
| `price.currency` | string | true |
| `price.includes_tax` | boolean | true |
| `status` | `live` or `draft` | true |
| `commodity_type` | `physical` or `digital` | true |
| `dimensions` | `array` | false |
| `dimensions.unit` | string | true |
| `dimensions.value` | integer | true |
| `dimensions.measurement` | `length`, `width` or `height` | true |
| `weight` | `object` | false |
| `weight.unit` | `g`, `kg`, `lb`, `oz` | true |
| `weight.value` | integer | true |
| `on_sale` | boolean | false |
| `tax-code` | string | true |

{% api-method method="get" host="https://api.moltin.com" path="/v2/products/attributes" %}
{% api-method-summary %}
Get Product Attributes
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
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
curl -X GET https://api.moltin.com/v2/products \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="Response" %}
```bash
"data": [
        {
            "label": "Type",
            "value": "type",
            "type": "enum",
            "validation": {
                "regex": "^product$"
            },
            "required": true,
            "default": "product",
            "options": [
                "product"
            ]
        },
        {
            "label": "Id",
            "value": "id",
            "type": "string",
            "required": true
        },
        {
            "label": "Name",
            "value": "name",
            "type": "string",
            "required": true
        },
        {
            "label": "Slug",
            "value": "slug",
            "type": "string",
            "required": true
        },
        {
            "label": "Sku",
            "value": "sku",
            "type": "string",
            "required": true
        },
        {
            "label": "Manage Stock",
            "value": "manage_stock",
            "type": "boolean",
            "required": true
        },
        {
            "label": "Description",
            "value": "description",
            "type": "string",
            "required": true
        },
        {
            "label": "Price",
            "value": "price",
            "type": "array",
            "required": false,
            "items": [
                {
                    "label": "Amount",
                    "value": "amount",
                    "type": "integer",
                    "required": true
                },
                {
                    "label": "Currency",
                    "value": "currency",
                    "type": "string",
                    "required": true
                },
                {
                    "label": "Includes Tax",
                    "value": "includes_tax",
                    "type": "boolean",
                    "required": true
                }
            ]
        },
        {
            "label": "Status",
            "value": "status",
            "type": "enum",
            "required": true,
            "default": "draft",
            "options": [
                "draft",
                "live"
            ]
        },
        {
            "label": "Commodity Type",
            "value": "commodity_type",
            "type": "enum",
            "required": true,
            "default": "physical",
            "options": [
                "physical",
                "digital"
            ]
        },
        {
            "label": "Dimensions",
            "value": "dimensions",
            "type": "array",
            "required": false,
            "items": [
                {
                    "label": "Unit",
                    "value": "unit",
                    "type": "string",
                    "required": true
                },
                {
                    "label": "Value",
                    "value": "value",
                    "type": "number",
                    "required": true
                },
                {
                    "label": "Measurement",
                    "value": "measurement",
                    "type": "enum",
                    "required": true,
                    "options": [
                        "length",
                        "width",
                        "height"
                    ]
                }
            ]
        },
        {
            "label": "Weight",
            "value": "weight",
            "type": "object",
            "required": false,
            "object": [
                {
                    "label": "Unit",
                    "value": "unit",
                    "type": "enum",
                    "required": true,
                    "options": [
                        "g",
                        "kg",
                        "lb",
                        "oz"
                    ]
                },
                {
                    "label": "Value",
                    "value": "value",
                    "type": "number",
                    "required": true
                }
            ]
        },
        {
            "label": "On Sale?",
            "value": "on_sale",
            "description": "Is this on sale?",
            "type": "boolean",
            "required": false,
            "default": false
        },
        {
            "label": "Tax Code",
            "value": "tax-code",
            "description": "The tax code for this product as a TaxJar category",
            "type": "string",
            "required": true,
            "default": false
        }
    ],
    "meta": {
        "entity": "product",
        "version": "2.0.0"
    }
```
{% endtab %}
{% endtabs %}

