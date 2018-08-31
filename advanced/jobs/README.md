# Jobs

The jobs endpoint provides a programmatic way of running long running background tasks with Moltin.

An example job would be exporting all orders from your store.

## Job object

{% tabs %}
{% tab title="Attributes" %}
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `id` | `string` | The unique ID for this job |
| `type` | `string` | This represents the type of object being returned. Always `job` |
| `job_type` | `string` | This represents the type of job. E.g. `order_export` |
| `link` | `object` | The link object associated with this job |
| `link.href` | `string` | The endpoint which returns a link to the exported data |
| `status` | `string` | Displays the current status for the given job. Types: `pending`, `completed`, `failed` |
| `timestamps` | `object` | Timestamps for this export |
| `timestamps.created_at` | `string` | The creation date of this job |
| `timestamps.updated_at` | `string` | The last updated date of this job |
{% endtab %}

{% tab title="Sample object" %}
```javascript
{
  "data": {
    "type": "job",
    "id": "4eac8cd8-68f6-4fab-9cb4-eb710e4568f7",
    "job_type": "order_export",
    "link": {
      "href": ""
    },
    "links": {
      "self": "http://api.moltin.com/v2/jobs/4eac8cd8-68f6-4fab-9cb4-eb710e4568f7"
    },
    "status": "pending",
    "timestamps": {
      "created_at": "2018-08-20T11:01:15.419445Z",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  }
}
```
{% endtab %}
{% endtabs %}

