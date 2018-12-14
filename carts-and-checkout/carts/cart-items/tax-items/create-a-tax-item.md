# Create a Tax Item

{% api-method method="post" host="https://api.moltin.com" path="/v2/carts/:cartID/items/:itemID/taxes" %}
{% api-method-summary %}
Create a Tax Item
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
This represents the type of object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the tax item
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=true %}
A unique tax code for this kind of tax item
{% endapi-method-parameter %}

{% api-method-parameter name="rate" type="float" required=true %}
The tax rate percentage represented as a float
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "003e2458-3415-4fd2-a10c-ed422bfac4bb",
        "type": "tax_item",
        "name": "Tax Name",
        "jurisdiction" : "UK",
        "code": "MYTAX01",
        "rate": 0.2
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
In this example, we skip passing `name` to fail validation.
{% endapi-method-response-example-description %}

```javascript
{
    "errors": [
        {
            "title": "Failed Validation",
            "detail": "The data.name field is required."
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
curl -X POST https://api.moltin.com/v2/carts/:cartID/items/:itemID/taxes \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer XXXX" \
    -d $'{
        "data": {
            "type": "tax_item",
            "name": "Tax Name",
            "jurisdiction" : "UK",
            "code": "MYTAX01",
            "rate": 0.2
        }
    }'
```
{% endtab %}
{% endtabs %}
