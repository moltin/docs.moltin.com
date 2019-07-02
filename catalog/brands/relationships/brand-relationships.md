# Brand Relationships

{% api-method method="post" host="https://api.moltin.com" path="/v2/brands/:id/relationships/brands" %}
{% api-method-summary %}
Create Brand Relationships
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the brand you want to modify relationships for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="parent.type" type="string" required=true %}
The type of the related object \(should be `brand`\)
{% endapi-method-parameter %}

{% api-method-parameter name="parent.id" type="string" required=true %}
The **ID** of the parent brand
{% endapi-method-parameter %}

{% api-method-parameter name="children\[\].type" type="string" required=true %}
The type of related object \(should be `brand`\)
{% endapi-method-parameter %}

{% api-method-parameter name="children\[\].id" type="string" required=true %}
The **ID** of the brand
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```bash
{
  "data": [
    {
      "type": "brand",
      "id": "9185d4ff-a484-408b-8c1a-d4de1ca20736",
      "name": "Cool Shoes",
      "status": "live",
      "slug": "cool-shoes",
      "description": "Our main shoes brand",
      "children": [
        {
          "type": "brand",
          "id": "c902aea9-ec90-4fdd-8084-3c2d879a2c52",
          "name": "MixiMax",
          "status": "live",
          "slug": "miximax",
          "description": "MixiMax brand"
        },
        {
          "type": "brand",
          "id": "43b70fc1-ed2f-45e0-b9e1-212b5e95e809",
          "name": "AirPair",
          "status": "live",
          "slug": "airpair",
          "description": "AirPair brand"
        }
      ]
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.moltin.com/v2/brands/:id/relationships/brands \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
        "data": {
            "parent": {
                "type": "brand",
                "id": "8a43aea7-79f0-4bcf-9bc8-a0f5d3d3642c"
            },
            "children": [
                {
                "type": "brand",
                "id": "1334e667-7b2b-4159-9e36-8a3b404901c8"
                }
            ]
            }
        }'
```
{% endtab %}
{% endtabs %}

