# Get a Job

{% api-method method="get" host="https://api.moltin.com" path="/v2/jobs/:id" %}
{% api-method-summary %}
Get Cakes
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the requested job.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

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
  {
    "type": "job",
    "id": "5eac8cd8-78f6-4fab-9cb4-eb710e4568f7",
    "job_type": "order_export",
    "link":
    {
      "href": "http://exporter.dev.molt.in/v2/jobs/5eac8cd8-78f6-4fab-9cb4-eb710e4568f7/file"
    },
    "links":
    {
      "self": "http://exporter.dev.molt.in/v2/jobs/5eac8cd8-78f6-4fab-9cb4-eb710e4568f7"
    },
    "status": "complete",
    "timestamps":
    {
      "created_at": "2018-08-20T11:01:15.419445Z",
      "updated_at": "2018-08-20T11:01:25.3774855Z"
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
curl -X GET https://api.moltin.com/v2/jobs/:id \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

