# Update Product Variation Option

{% api-method method="put" host="https://api.moltin.com" path="/v2/variations/:variationId/options/:optionId" %}
{% api-method-summary %}
Update a Product Variation Option
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="optionId" type="string" required=true %}
The **ID** of the option.
{% endapi-method-parameter %}

{% api-method-parameter name="variationId" type="string" required=true %}
The **ID** of the variation belonging to this option.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the option.
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
A human readable description of the option.
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
A human readable description of the option
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
Represents the type of the object being created.  \(should be option\)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{  
  "data":{  
    "id":"1feab4d8-25b3-40d3-8843-8056713dadfc",
    "type":"option",
    "description":"Our other most popular color",
    "name":"Green",
    "relationships":{
      "modifiers":{
        "data":[
          {  
            "type":"sku-builder",
            "id":"a43593a6-92fe-4953-bf4e-a99524918839"
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
curl -X PUT https://api.moltin.com/v2/variations/684bceee-0ee3-4f43-ac32-50bb44c1eee5/options/39148bc3-3028-4196-9350-1b4ac927c9d6 \
     -H "Authorization: Bearer XXXX" \
     -H "Content-type: application/json" \
     -d $'{
        "data": {
            "id": "39148bc3-3028-4196-9350-1b4ac927c9d6",
            "type": "option",
            "name": "Green",
            "description": "Our other most popular color"
        }
    }
```
{% endtab %}
{% endtabs %}

