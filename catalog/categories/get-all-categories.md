# Get All Categories

{% api-method method="get" host="https://api.moltin.com" path="/v2/categories" %}
{% api-method-summary %}
Get all Categories
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

{% api-method-query-parameters %}
{% api-method-parameter name="include" type="string" required=false %}
`categories`, `products`
{% endapi-method-parameter %}

{% api-method-parameter name="filter" type="string" required=false %}
Filter the results.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": [
        {
            "id": "9dd56fc2-5746-46a2-bdf6-fe396bb6b7af",
            "type": "category",
            "status": "live",
            "name": "Clothing",
            "slug": "clothing",
            "description": "Browse our clothing line",
            "meta": {
                "timestamps": {
                    "created_at": "2018-05-10T14:11:32+00:00",
                    "updated_at": "2018-05-10T14:11:32+00:00"
                }
            },
            "relationships": {}
        },
        {
            "id": "75542cfa-38e2-4a48-8416-74055af7d62e",
            "type": "category",
            "status": "live",
            "name": "Clothing",
            "slug": "clothing",
            "description": "Browse our clothing line",
            "meta": {
                "timestamps": {
                    "created_at": "2018-05-10T02:20:47+00:00",
                    "updated_at": "2018-05-10T02:24:10+00:00"
                }
            },
            "relationships": {}
        }
    ],
    "links": {
        "current": "https://api.moltin.com/v2/categories?page[limit]=100&page[offset]=0",
        "first": "https://api.moltin.com/v2/categories?page[limit]=100&page[offset]=0",
        "last": null
    },
    "meta": {
        "results": {
            "total": 2,
            "all": 2
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
curl https://api.moltin.com/v2/categories \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Categories.All().then(categories => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

