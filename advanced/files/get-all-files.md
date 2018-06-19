# Get all Files

{% api-method method="get" host="https://api.moltin.com" path="/v2/files" %}
{% api-method-summary %}
Get all Files
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

{% api-method-query-parameters %}
{% api-method-parameter name="filter" type="string" required=false %}
Filter attributes
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
            "type": "file",
            "id": "f8cf26b3-6d38-4275-937a-624a83994702",
            "link": {
                "href": "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/f8cf26b3-6d38-4275-937a-624a83994702.png"
            },
            "file_name": "f6669358-85db-4367-9cde-1deb77acb5f4.png",
            "mime_type": "image/png",
            "file_size": 110041,
            "public": true,
            "meta": {
                "dimensions": {
                    "width": 1000,
                    "height": 1000
                },
                "timestamps": {
                    "created_at": "2018-03-13T13:45:21.673Z"
                }
            },
            "links": {
                "self": "https://api.moltin.com/v2/files/f8cf26b3-6d38-4275-937a-624a83994702"
            }
        }
    ],
    "links": {
        "self": "https://api.moltin.com/v2/files?page[offset]=0&page[limit]=100&filter=",
        "first": "https://api.moltin.com/v2/files?page[offset]=0&page[limit]=100&filter=",
        "last": null
    },
    "meta": {
        "results": {
            "total": 1
        },
        "page": {
            "limit": 100,
            "offset": 0,
            "self": 1,
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
curl -X GET https://api.moltin.com/v2/files \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

Moltin.Files.All().then(files => {
  // Do something
})
```
{% endtab %}
{% endtabs %}

