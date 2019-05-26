# Create a File

{% api-method method="post" host="https://api.moltin.com" path="/v2/files" %}
{% api-method-summary %}
Create a File
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

{% api-method-form-data-parameters %}
{% api-method-parameter name="file" type="string" required=true %}
The file you want to upload
{% endapi-method-parameter %}

{% api-method-parameter name="public" type="boolean" required=true %}
`true`, `false`
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
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
curl -X POST https://api.moltin.com/v2/files \
    -H "Content-Type: multipart/form-data" \
    -H "Authorization: Bearer XXXX" \
    -F file=@path/to/file \
    -F public=true
```
{% endtab %}

{% tab title="Moltin Request" %}
```javascript
const { MoltinClient } = require('@moltin/request')
const FormData = require("form-data")
​
const moltin = new MoltinClient({
  client_id: 'X',
  client_secret: 'X'
})
​
const formData = new FormData()
​
formData.append("file_name", fileName)
formData.append("public", "true")
formData.append("file", buffer, { filename: fileName })
​
const headers = {
  "Content-Type": formData.getHeaders()["content-type"]
}
​
const data = {
  body: formData
}
​
moltin
  .post("files", data, headers)
  .then(console.log(data))
  .error(console.error(error))
```
{% endtab %}
{% endtabs %}

