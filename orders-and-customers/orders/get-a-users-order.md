# Get Users Order

Using a customers token you are able to get all of the users order.

{% page-ref page="../customers/customer-tokens.md" %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/orders" %}
{% api-method-summary %}
Get Users Orders
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="customerId" type="string" required=true %}
A customer **ID** that has addresses
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="X-Moltin-Customer-Token" type="string" required=true %}
A customer token used to access customer data.
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
            "type": "order",
            "id": "7f1dbd02-a623-4175-803b-987816508120",
            "status": "incomplete",
            "payment": "unpaid",
            "shipping": "unfulfilled",
            "customer": {
                "name": "George example",
                "email": "ron@swanson.com"
            },
            "shipping_address": {
                "first_name": "John",
                "last_name": "Doe",
                "phone_number": "(555) 555-1234",
                "company_name": "Moltin",
                "line_1": "2nd Floor British India House",
                "line_2": "15 Carliol Square",
                "city": "Newcastle upon Tyne",
                "postcode": "NE1 6UF",
                "county": "Tyne & Wear",
                "country": "UK",
                "instructions": "Leave in porch"
            },
            "billing_address": {
                "first_name": "John",
                "last_name": "Doe",
                "company_name": "Moltin",
                "line_1": "2nd Floor British India House",
                "line_2": "15 Carliol Square",
                "city": "Newcastle upon Tyne",
                "postcode": "NE1 6UF",
                "county": "Tyne & Wear",
                "country": "UK"
            },
            "links": {},
            "meta": {
                "display_price": {
                    "with_tax": {
                        "amount": 1269,
                        "currency": "USD",
                        "formatted": "$12.69"
                    },
                    "without_tax": {
                        "amount": 1269,
                        "currency": "USD",
                        "formatted": "$12.69"
                    }
                },
                "timestamps": {
                    "created_at": "2018-08-29T19:24:59.851Z",
                    "updated_at": "2018-08-29T19:24:59.851Z"
                }
            },
            "relationships": {
                "items": {
                    "data": [
                        {
                            "type": "item",
                            "id": "f84c4720-7f7f-4c30-89ac-1556636fbafb"
                        }
                    ]
                },
                "customer": {
                    "data": {
                        "type": "customer",
                        "id": "b57022cf-c80e-4b85-9fd1-5af3156d8adf"
                    }
                }
            }
        }
    ],
    "links": {
        "current": "https://api.moltin.com/v2/orders?page[offset]=0&page[limit]=100&filter=",
        "first": "https://api.moltin.com/v2/orders?page[offset]=0&page[limit]=100&filter=",
        "last": "https://api.moltin.com/v2/orders?page[offset]=0&page[limit]=100&filter=",
        "prev": "https://api.moltin.com/v2/orders?page[offset]=0&page[limit]=100&filter=",
        "next": "https://api.moltin.com/v2/orders?page[offset]=0&page[limit]=100&filter="
    },
    "meta": {
        "page": {
            "limit": 100,
            "offset": 0,
            "current": 1,
            "total": 1
        },
        "results": {
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
```javascript
curl -X GET https://api.moltin.com/v2/orders/:id \
     -H "Authorization: Bearer XXXX"
     -H "X-Moltin-Customer-Token: XXXX"
```
{% endtab %}
{% endtabs %}

## 

