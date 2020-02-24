# Create Promotion

{% hint style="info" %}
There are two available types of promotion: [**fixed discount**](./#fixed-discount) and [**percent discount**](./#percent-discount). Be sure to look at the [example payloads](create-promotion.md#example-payloads) below when creating a new promotion record. For more details, see [How promotions work](https://www.moltin.com/developer/concepts/how-promotions-work).
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
{% api-method-parameter name="type" type="string" required=true %}
`promotion`
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
A general name for the promotion
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=true %}
A general description for the promotion
{% endapi-method-parameter %}

{% api-method-parameter name="enabled" type="boolean" required=true %}
`true` , `false`
{% endapi-method-parameter %}

{% api-method-parameter name="automatic" type="boolean" required=false %}
`true` or `false` if promotion can be added automatically or require a code. `default: false`
{% endapi-method-parameter %}

{% api-method-parameter name="promotion\_type" type="string" required=true %}
The type of schema being used for the promotion. `fixed_discount` , `percent_discount`, `x_for_y`, `x_for_amount` , `bundle_fixed_discount`,
{% endapi-method-parameter %}

{% api-method-parameter name="schema" type="object" required=true %}
Definition of the promotion based on `promotion_type`. See examples below
{% endapi-method-parameter %}

{% api-method-parameter name="min\_cart\_value" type="array" required=false %}
An array of currency-value objects that define a minimum value of a cart required before discount is applied
{% endapi-method-parameter %}

{% api-method-parameter name="min\_cart\_value\[\].currency" type="string" required=false %}
The currency of the minimum cart value threshold
{% endapi-method-parameter %}

{% api-method-parameter name="min\_cart\_value\[\].amount" type="string" required=false %}
The minimum cart value threshold before discount can be applied.
{% endapi-method-parameter %}

{% api-method-parameter name="max\_discount\_value" type="array" required=false %}
An array of currency-value objects that define the maximum value of the discount
{% endapi-method-parameter %}

{% api-method-parameter name="max\_discount\_value\[\].currency" type="string" required=false %}
The currency of the maximum discount value
{% endapi-method-parameter %}

{% api-method-parameter name="max\_discount\_value\[\].amount" type="integer" required=false %}
The maximum value of the discount..
{% endapi-method-parameter %}

{% api-method-parameter name="start" type="string" required=true %}
The start time of the promotion datetime \(`yyyy-mm-dd`, `yyyy-mm-ddThh:mm:ss+hh:mm`\). The simpler format will start the promotion at 00:00 UTC of the datetime specified. If time is not specified, it will default to the time at which the request was created. 
{% endapi-method-parameter %}

{% api-method-parameter name="end" type="string" required=true %}
The end time of the promotion datetime \(`yyyy-mm-dd`, `yyyy-mm-ddThh:mm:ss+hh:mm`\). The simpler format will start the promotion at 00:00 UTC. If time's not provided, it will default to the time at which the request was created.
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

### Example Request Payloads

{% tabs %}
{% tab title="Fixed Discount" %}
```bash
curl -X "POST" "https://api.moltin.com/v2/promotions" \
     -H 'Content-Type: application/json' \
     -H 'Authorization: 1af41d46cb18d11b3abffb66c3cb20944d3452e7' \
     -d $'{
  "data": {
    "type": "promotion",
    "name": "BF",
    "description": "Black Friday",
    "enabled": true,
    "automatic": false,
    "promotion_type": "fixed_discount",
    "schema": {
      "currencies": [
        {
          "currency": "GBP",
          "amount": 10
        },
        {
          "currency": "USD",
          "amount": 10
        }
      ]
    },
    "min_cart_value": [
      {"GBP": 20000},
      {"USD": 19000}
    ],
    "end": "2018-06-12",
    "start": "2017-05-12"
  }
}'
```
{% endtab %}

{% tab title="Percent Discount" %}
```bash
curl -X "POST" "https://api.moltin.com/v2/promotions" \
     -H 'Content-Type: application/json' \
     -H 'Authorization: 1af41d46cb18d11b3abffb66c3cb20944d3452e7' \
     -d $'{
  "data": {
    "type": "promotion",
    "name": "BF",
    "description": "Black Friday",
    "enabled": true,
    "automatic": true,
    "promotion_type": "percent_discount",
    "schema": {
      "currencies": [
        {
          "currency": "USD",
          "percentage": 10
        }
      ]
    },
    "min_cart_value": [
      {"GBP": 20000},
      {"USD": 19000}
    ],
    "start": "2017-05-12T15:04:05+00:00",
    "end": "2018-06-12T15:04:05+00:00"
  }
}'
```
{% endtab %}

{% tab title="X For Y Discount" %}
```bash
curl -X "POST" "https://api.moltin.com/v2/promotions" \
     -H 'Content-Type: application/json' \
     -H 'Authorization: 1af41d46cb18d11b3abffb66c3cb20944d3452e7' \
     -d $'{
  "data": {
    "type": "promotion",
    "name": "BF",
    "description": "Black Friday",
    "enabled": true,
    "automatic": false,
    "promotion_type": "x_for_y",
    "schema": {
      "x": 3,
      "y": 2,
      "targets": ["prodID1","prodSKU2"],
    },
    "end": "2018-06-12",
    "start": "2017-05-12"
  }
}'
```
{% endtab %}

{% tab title="X For Amount Discount" %}
```bash
curl -X "POST" "https://api.moltin.com/v2/promotions" \
     -H 'Content-Type: application/json' \
     -H 'Authorization: 1af41d46cb18d11b3abffb66c3cb20944d3452e7' \
     -d $'{
  "data": {
    "type": "promotion",
    "name": "BF",
    "description": "Black Friday",
    "enabled": true,
    "automatic": false,
    "promotion_type": "x_for_amount",
    "schema": {
      "x": 3,
      "currencies": [
        {"currency": "GBP", "amount": 500},
        {"currency": "USD", "amount": 500}
      ],
      "targets": ["prodID1","prodSKU2"],
    },
    "end": "2018-06-12",
    "start": "2017-05-12"
  }
}'
```
{% endtab %}

{% tab title="Fixed Bundle Discount" %}
```bash
curl -X "POST" "https://api.moltin.com/v2/promotions" \
     -H 'Content-Type: application/json' \
     -H 'Authorization: 1af41d46cb18d11b3abffb66c3cb20944d3452e7' \
     -d $'{
  "data": {
    "type": "promotion",
    "name": "BF",
    "description": "Black Friday",
    "enabled": true,
    "automatic": false,
    "promotion_type": "bundle_fixed_discount",
    "schema": {
      "requirements":[
        {"targets":["prod1","prodX"],"quantity": 2},
        {"targets":["prod3","prodW"],"quantity": 1},
      ],
      "currencies": [
        {
          "currency": "GBP",
          "amount": 10
        },
        {
          "currency": "USD",
          "amount": 10
        }
      ]
    },
    "min_cart_value": [
      {"GBP": 20000},
      {"USD": 19000}
    ],
    "end": "2021-06-12",
    "start": "2017-05-12"
  }
}'
```
{% endtab %}
{% endtabs %}

