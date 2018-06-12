# Get a File

{% api-method method="get" host="https://api.moltin.com" path="/v2/files/:id" %}
{% api-method-summary %}
Get a File by ID
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the file
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
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
    "type": "file",
    "id": "f8cf26b3-6d38-4275-937a-624a83994702",
    "link": {
      "href":
        "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/f8cf26b3-6d38-4275-937a-624a83994702.png"
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
      "self":
        "https://api.moltin.com/v2/files/f8cf26b3-6d38-4275-937a-624a83994702"
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
curl -X GET https://api.moltin.com/v2/files/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

