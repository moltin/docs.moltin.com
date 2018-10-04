# Create Promotion

{% hint style="info" %}
There are two available types of promotion: [**fixed discount**](./#fixed-discount) and [**percent discount**](./#percent-discount). Be sure to look at the [example payloads](create-promotion.md#example-payloads) below when creating a new promotion record. For more details, see: [Developer Portal](https://developers.moltin.com/guides/working-with-promotions).
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/promotions" %}
{% api-method-summary %}
Create a Promotion
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

{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
A general name for the promotion.
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=true %}
A general description for the promotion.
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
The type should be promotion.
{% endapi-method-parameter %}

{% api-method-parameter name="promotion\_type" type="string" required=true %}
The type of schema being used for the promotion.  \(fixed\_discount or percent\_discount\)
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="string" required=true %}
True or False
{% endapi-method-parameter %}

{% api-method-parameter name="start" type="string" required=true %}
The date at which the promotion starts.
{% endapi-method-parameter %}

{% api-method-parameter name="end" type="string" required=true %}
The date at which the promotion ends.
{% endapi-method-parameter %}

{% api-method-parameter name="schema" type="object" required=true %}
See example payloads below.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "type": "promotion",
    "id": "15bf00b3-436b-446d-bda9-c021e4e4752b",
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
    "start": "2017-05-12T15:04:05Z",
    "end": "2019-10-12T15:04:05Z",
    "created_at": "2017-11-13T03:00:35.381148442Z",
    "updated_at": "2017-11-13T03:00:35.381148514Z"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example Payloads

#### Fixed Discount Request

{% tabs %}
{% tab title="cURL" %}
```javascript
//Create a Fixed  Promotion

curl -X "POST" "https://api.moltin.com/v2/promotions" \
     -H 'Content-Type: application/json' \
     -H 'Authorization: 1af41d46cb18d11b3abffb66c3cb20944d3452e7' \
     -d $'{
  "data": {
    "schema": {
      "currencies": [
        {
          "currency": "USD",
          "amount": 10
        }
      ]
    },
    "end": "2018-06-12T15:04:05+00:00",
    "enabled": true,
    "start": "2017-05-12T15:04:05+00:00",
    "promotion_type": "fixed_discount",
    "type": "promotion",
    "description": "Black Friday",
    "name": "BF"
  }
}'
```
{% endtab %}
{% endtabs %}

#### Percent Discount Request

{% tabs %}
{% tab title="cURL" %}
```javascript
//Create a Percent  Request

curl -X "POST" "https://api.moltin.com/v2/promotions" \
     -H 'Content-Type: application/json' \
     -H 'Authorization: 1af41d46cb18d11b3abffb66c3cb20944d3452e7' \
     -d $'{
  "data": {
    "schema": {
      "currencies": [
        {
          "currency": "USD",
          "percentage": 10
        }
      ]
    },
    "end": "2018-06-12T15:04:05+00:00",
    "enabled": true,
    "start": "2017-05-12T15:04:05+00:00",
    "promotion_type": "percent_discount",
    "type": "promotion",
    "description": "Black Friday",
    "name": "BF"
  }
}'
```
{% endtab %}
{% endtabs %}

