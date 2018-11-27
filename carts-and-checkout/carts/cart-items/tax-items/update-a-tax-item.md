# Update a Tax Item

{% api-method method="put" host="https://api.moltin.com" path="/v2/carts/:cartID/items/:itemID/taxes/:id" %}
{% api-method-summary %}
Update by ID
{% endapi-method-summary %}

{% api-method-description %}
This endpoint will update an existing Tax Item by ID.
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

{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the requested tax item
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The name of the tax item
{% endapi-method-parameter %}

{% api-method-parameter name="code" type="string" required=false %}
A unique tax code for this kind of tax item
{% endapi-method-parameter %}

{% api-method-parameter name="rate" type="float" required=false %}
The tax rate percentage
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
        "id": "003e2458-3415-4fd2-a10c-ed422bfac4bb",
        "type": "tax_item",
        "name": "My Updated Tax Name",
        "jurisdiction" : "UK",
        "code": "MYTAX01",
        "rate": 21.5
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
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer XXXX" \
    -d $'{
        "data": {
            "type": "tax_item",
            "id": "003e2458-3415-4fd2-a10c-ed422bfac4bb",
            "name": "My Updated Tax Name",
            "jurisdiction" : "UK",
            "rate": 21.5
        }
    }' https://api.moltin.com/v2/carts/:cartID/items/:itemID/taxes/:id
```
{% endtab %}
{% endtabs %}

