# Update Promotions

{% api-method method="put" host="https://api.moltin.com" path="/v2/promotions/:id" %}
{% api-method-summary %}
Update a Promotion
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The unique promotion identifier
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
"promotion"
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="number" required=false %}
The unique promotion identifier
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The name of your promotion
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
A description of your promotion
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="boolean" required=false %}
`true` if enabled, `false` if not
{% endapi-method-parameter %}

{% api-method-parameter name="promotion\_type" type="string" required=false %}
One of: fixed\_discount or percent\_discount
{% endapi-method-parameter %}

{% api-method-parameter name="schema" type="object" required=false %}
One of: fixed schema, percent schema
{% endapi-method-parameter %}

{% api-method-parameter name="start" type="string" required=false %}
The start time of the promotion datetime \(yyyy-mm-dd, yyyy-mm-ddThh:mm:ss+hh::mm\). The simpler format will start the promotion at 00:00 UTC of the date specified
{% endapi-method-parameter %}

{% api-method-parameter name="end" type="string" required=false %}
The end time of the promotion datetime \(yyyy-mm-dd, yyyy-mm-ddTh:mm:ss+hh::mm\). The simpler format will end the promotion at 00:00UTC of the date specified
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
cURL
{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "type": "promotion",
        "id": "7005b249-300b-4cf6-964e-e663278af218",
        "name": "Promo #1",
        "description": "Initial Promotion",
        "enabled": true,
        "promotion_type": "fixed_discount",
        "schema": {
            "currencies": [
                {
                    "currency": "USD",
                    "amount": 900
                },
                {
                    "currency": "GBP",
                    "amount": 1100
                }
            ]
        },
        "start": "2017-11-13T00:00:00Z",
        "end": "2019-11-13T00:00:00Z",
        "created_at": "2018-05-10T15:25:21.164Z",
        "updated_at": "2018-05-10T15:26:18.203942092Z"
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl -X PUT https://api.moltin.com/v2/promotions/:id \
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
     -d $'{
      "data": {
        "type":"promotion",
        "id": "PROMOTION_ID",
        "name": "Promo #1",
        "description": "Initial Promotion",
        "enabled": true,
        "promotion_type": "fixed_discount",
        "schema":{
          "currencies":[
            {"currency":"USD", "amount":900},
            {"currency":"GBP", "amount":1100}
          ]
        },
        "start":"2017-11-13",
        "end":"2019-11-13"
      }
    }
```
{% endtab %}
{% endtabs %}

```javascript

```



