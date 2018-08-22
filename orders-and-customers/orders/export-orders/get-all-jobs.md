# Get all Jobs

{% api-method method="get" host="https://api.moltin.com" path="/v2/jobs" %}
{% api-method-summary %}
Get a list of all jobs
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

```javascript
{
  "data":
  [
    {
      "type": "job",
      "id": "3c88c530-a3d2-5413-83fe-3c156ae559a5",
      "job_type": "order_export",
      "link":
      {
        "href": ""
      },
      "links":
      {
        "self": "http://exporter.dev.molt.in/v2/jobs/3c88c530-a3d2-5413-83fe-3c156ae559a5"
      },
      "status": "pending",
      "timestamps": {
        "created_at": "2018-08-17T12:12:45.2902988Z",
        "updated_at": "2018-08-17T12:12:45.3116542Z"
      }
    },
    {
      "type": "job",
      "id": "01242c7c-d288-4526-8420-6b1426225b59",
      "job_type": "order_export",
      "link":
      {
        "href": ""
      },
      "links":
      {
        "self": "http://exporter.dev.molt.in/v2/jobs/01242c7c-d288-4526-8420-6b1426225b59"
      },
      "status": "processing",
      "timestamps": {
        "created_at": "2018-08-17T13:15:05.8594991Z",
        "updated_at": "2018-08-17T13:15:05.8599298Z"
      }
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
curl -X GET https://api.moltin.com/v2/jobs \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

