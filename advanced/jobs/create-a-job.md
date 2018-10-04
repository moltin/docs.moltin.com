# Create a Job

You can invoke the jobs service on any of the resources below that support jobs.

* Also, see: [Export orders](https://docs.moltin.com/orders-and-customers/orders/exporting)

{% api-method method="post" host="https://api.moltin.com" path="/v2/jobs" %}
{% api-method-summary %}
Create a Job
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to access the API.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="filter" type="string" required=true %}
This is the same filter you would use when getting all orders.
{% endapi-method-parameter %}

{% api-method-parameter name="job\_type" type="string" required=true %}
The type of task you want to run, e.g. `order_export`
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=false %}
Must be set to `job`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```bash
{
    "data": {
        "type": "job",
        "id": "v4154f5b-df0c-4781-be28-c2d5669b29f9",
        "job_type": "order_export",
        "link": {
            "href": ""
        },
        "links": {
            "self": "http://exporter.dev.molt.in/v2/jobs/v4154f5b-df0c-4781-be28-c2d5669b29f9"
        },
        "status": "pending",
        "timestamps": {
            "created_at": "2018-08-20T15:01:13.0194505Z",
            "updated_at": "0001-01-01T00:00:00Z"
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
curl -X POST https://api.moltin.com/v2/jobs \
     -H "Authorization: Bearer XXXX"
     -d $'{
       "data": {
         "type": "job",
         "filter": "gt(created_at,2018-09-01):lt(created_at,2018-10-01):eq(payment,refunded)",
         "job_type": "order_export"
       }
     }'
```
{% endtab %}
{% endtabs %}

