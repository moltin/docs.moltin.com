# Get all Jobs

{% api-method method="get" host="https://api.moltin.com" path="/v2/jobs" %}
{% api-method-summary %}
Get all Jobs
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```bash
{
    "data": [
        {
            "id": "974c9db4-38da-4dbf-90c2-33eed5f3e77c",
            "type": "job",
            "job_type": "order_export",
            "status": "failed",
            "error": "No results matched the supplied filter",
            "link": {
                "href": ""
            },
            "links": {
                "self": "https://api.moltin.com/v2/jobs/974c9db4-38da-4dbf-90c2-33eed5f3e77c"
            },
            "timestamps": {
                "created_at": "2018-10-04T11:08:49.156490335Z",
                "updated_at": "2018-10-04T11:08:49.162867081Z"
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

