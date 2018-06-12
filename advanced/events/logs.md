# Logs

As events may fail overtime, we provide the ability to browse all logs for your events. The Moltin API provides various endpoints to get all logs and jobs.

{% api-method method="get" host="https://api.moltin.com" path="/v2/integrations/logs" %}
{% api-method-summary %}
Get all logs
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

```javascript
{
  "data": [
    {
      "id": "11de4222-fbda-498c-9ecb-cd46d598712f",
      "type": "integration-log",
      "succeeded": false,
      "attempt": 1,
      "processing_time": 0.2529,
      "body": "Not found",
      "status_code": 404,
      "error_detail":
        "Received a status code outside of 2xx range - treating webhook as a fail",
      "relationships": {
        "integration": {
          "data": {
            "type": "integration",
            "id": "8edd44ef-1856-4456-90ec-d9fab8a25049"
          }
        },
        "job": {
          "data": {
            "type": "integration-job",
            "id": "3b69a7e2-78ad-4ee6-8a81-c9b1b8a9cd26"
          }
        }
      },
      "meta": {
        "timestamps": {
          "created_at": "2017-10-30T18:15:40.087650928Z"
        }
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
curl -X GET https://api.moltin.com/v2/integrations/logs \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/integrations/:id/logs" %}
{% api-method-summary %}
Get logs for an Event
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the event
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
  "data": [
    {
      "id": "11de4222-fbda-498c-9ecb-cd46d598712f",
      "type": "integration-log",
      "succeeded": false,
      "attempt": 1,
      "processing_time": 0.2529,
      "body": "Not found",
      "status_code": 404,
      "error_detail":
        "Received a status code outside of 2xx range - treating webhook as a fail",
      "relationships": {
        "integration": {
          "data": {
            "type": "integration",
            "id": "8edd44ef-1856-4456-90ec-d9fab8a25049"
          }
        },
        "job": {
          "data": {
            "type": "integration-job",
            "id": "3b69a7e2-78ad-4ee6-8a81-c9b1b8a9cd26"
          }
        }
      },
      "meta": {
        "timestamps": {
          "created_at": "2017-10-30T18:15:40.087650928Z"
        }
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
curl -X GET https://api.moltin.com/v2/integrations/:id/logs \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/integrations/:id/jobs" %}
{% api-method-summary %}
Get jobs for an Event
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the event
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
  "data": [
    {
      "id": "6560f600-b610-4c02-88ac-0d120e3d5071",
      "type": "integration-job"
    },
    {
      "id": "353c015a-92ab-4c06-ab8a-bef8a451b9be",
      "type": "integration-job"
    },
    {
      "id": "4af82fba-8f0a-41b1-add6-0fa16fe3579e",
      "type": "integration-job"
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
curl -X GET https://api.moltin.com/v2/integrations/:id/jobs \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/integrations/:event\_id/jobs/:id/logs" %}
{% api-method-summary %}
Get all logs for a job
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The **ID** for the job
{% endapi-method-parameter %}

{% api-method-parameter name="event\_id" type="string" required=true %}
The **ID** for the event
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

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET https://api.moltin.com/v2/integrations/:event_id/jobs/:id/logs \
     -H "Authorization: Bearer XXXX"
```
{% endtab %}
{% endtabs %}

