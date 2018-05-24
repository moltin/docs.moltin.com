# Checkout

Once a [Cart](carts/) is ready to checkout, you can easily convert your Cart to an [Order](https://github.com/moltin/api.docs.moltin.com/tree/cbfae6cc90f263c65a62c5eab62b2212cd61695a/orders-and-customers/orders/README.md). The Cart will remain and can be modified and checked out again if required.

Once a successful Checkout is completed, the response will contain [payment ](../payments/gateways/)gateways `data.meta.payment_gateways` that can be used when [paying for an order](../payments/paying-for-an-order/).

{% hint style="warning" %}
We'll automatically delete carts 7 days after they were last updated.
{% endhint %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/carts/:reference/checkout" %}
{% api-method-summary %}
With Customer ID
{% endapi-method-summary %}

{% api-method-description %}
You can checkout a Cart with an existing customer ID
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="reference" type="string" required=true %}
The reference for the cart to checkout
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "type": "order",
        "id": "c79a24c1-d639-4ac7-9eb5-3565efd9c84b",
        "status": "incomplete",
        "payment": "unpaid",
        "shipping": "unfulfilled",
        "customer": {
            "name": "Ron Swanson",
            "email": "ronswanson@example.com"
        },
        "shipping_address": {
            "first_name": "Ron",
            "last_name": "Swanson",
            "phone_number": "",
            "company_name": "Moltin",
            "line_1": "British India House",
            "line_2": "15 Carliol Square",
            "city": "Newcastle upon Tyne",
            "postcode": "NE1 6UF",
            "county": "Tyne & Wear",
            "country": "UK",
            "instructions": ""
        },
        "billing_address": {
            "first_name": "Ron",
            "last_name": "Swanson",
            "company_name": "Moltin",
            "line_1": "British India House",
            "line_2": "15 Carliol Square",
            "city": "Newcastle upon Tyne",
            "postcode": "NE1 6UF",
            "county": "Tyne & Wear",
            "country": "UK"
        },
        "links": {},
        "meta": {
            "display_price": {
                "with_tax": {
                    "amount": 47500,
                    "currency": "USD",
                    "formatted": "$475.00"
                },
                "without_tax": {
                    "amount": 47500,
                    "currency": "USD",
                    "formatted": "$475.00"
                }
            },
            "timestamps": {
                "created_at": "2018-05-09T09:53:16.045565913Z",
                "updated_at": "2018-05-09T09:53:16.045566558Z"
            }
        },
        "relationships": {
            "items": {
                "data": [
                    {
                        "type": "item",
                        "id": "5ff8e482-da0b-4c43-b9ae-a13d384f10bd"
                    }
                ]
            }
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
curl -X POST https://api.moltin.com/v2/carts/:reference/checkout \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
       "data": {
         "customer": {
           "id": "c8c1c511-beef-4812-9b7a-9f92c587217c"
         },
         "billing_address": {
           "first_name": "John",
           "last_name": "Doe",
           "company_name": "Moltin",
           "line_1": "2nd Floor British India House",
           "line_2": "15 Carliol Square",
           "city": "Newcastle upon Tyne",
           "postcode": "NE1 6UF",
           "county": "Tyne & Wear",
           "country": "UK"
         },
         "shipping_address": {
           "first_name": "John",
           "last_name": "Doe",
           "phone_number": "(555) 555-1234",
           "company_name": "Moltin",
           "line_1": "2nd Floor British India House",
           "line_2": "15 Carliol Square",
           "city": "Newcastle upon Tyne",
           "postcode": "NE1 6UF",
           "county": "Tyne & Wear",
           "country": "UK"
           "instructions": "Leave in porch"
         }
       }
    }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const address = {
  first_name: 'John',
  last_name: 'Doe',
  line_1: '2nd Floor British India House',
  line_2: '15 Carliol Square',
  city: 'Newcastle Upon Tyne',
  postcode: 'NE1 6UF',
  county: 'Tyne & Wear',
  country: 'United Kingdom'
}

const reference = 'XXXX'
const customerId = 'XXXX'

Moltin.Cart(reference).Checkout(customerId, address)
```
{% endtab %}
{% endtabs %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/carts/:reference/checkout" %}
{% api-method-summary %}
With Customer object
{% endapi-method-summary %}

{% api-method-description %}
You can checkout a Cart with an associated customer name and email.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="reference" type="string" required=true %}
The reference for the cart to checkout
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "type": "order",
        "id": "5a9b6d0a-3e88-43d5-a12e-e5dedbac517d",
        "status": "incomplete",
        "payment": "unpaid",
        "shipping": "unfulfilled",
        "customer": {
            "name": "Ron Swanson",
            "email": "ronswanson@example.com"
        },
        "shipping_address": {
            "first_name": "Ron",
            "last_name": "Swanson",
            "phone_number": "",
            "company_name": "Moltin",
            "line_1": "British India House",
            "line_2": "15 Carliol Square",
            "city": "Newcastle upon Tyne",
            "postcode": "NE1 6UF",
            "county": "Tyne & Wear",
            "country": "UK",
            "instructions": ""
        },
        "billing_address": {
            "first_name": "Ron",
            "last_name": "Swanson",
            "company_name": "Moltin",
            "line_1": "British India House",
            "line_2": "15 Carliol Square",
            "city": "Newcastle upon Tyne",
            "postcode": "NE1 6UF",
            "county": "Tyne & Wear",
            "country": "UK"
        },
        "links": {},
        "meta": {
            "display_price": {
                "with_tax": {
                    "amount": 47500,
                    "currency": "USD",
                    "formatted": "$475.00"
                },
                "without_tax": {
                    "amount": 47500,
                    "currency": "USD",
                    "formatted": "$475.00"
                }
            },
            "timestamps": {
                "created_at": "2018-05-09T09:53:16.045565913Z",
                "updated_at": "2018-05-09T09:53:16.045566558Z"
            }
        },
        "relationships": {
            "items": {
                "data": [
                    {
                        "type": "item",
                        "id": "5ff8e482-da0b-4c43-b9ae-a13d384f10bd"
                    }
                ]
            }
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
curl -X POST https://api.moltin.com/v2/carts/:reference/checkout \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer XXXX" \
     -d $'{
       "data": {
         "customer": {
           "email": "john@moltin.com",
           "name": "John Doe"
         },
         "billing_address": {
           "first_name": "John",
           "last_name": "Doe",
           "company_name": "Moltin",
           "line_1": "2nd Floor British India House",
           "line_2": "15 Carliol Square",
           "city": "Newcastle upon Tyne",
           "postcode": "NE1 6UF",
           "county": "Tyne & Wear",
           "country": "UK"
         },
         "shipping_address": {
           "first_name": "John",
           "last_name": "Doe",
           "company_name": "Moltin",
           "phone_number": "(555) 555-1234",
           "line_1": "2nd Floor British India House",
           "line_2": "15 Carliol Square",
           "city": "Newcastle upon Tyne",
           "postcode": "NE1 6UF",
           "county": "Tyne & Wear",
           "country": "UK"
           "instructions": "Leave in porch"
         }
       }
    }'
```
{% endtab %}

{% tab title="JavaScript SDK" %}
```javascript
const MoltinGateway = require('@moltin/sdk').gateway

const Moltin = MoltinGateway({
  client_id: 'X'
})

const customer = {
  email: 'john@moltin.com',
  name: 'John Doe'
}

const address = {
  first_name: 'John',
  last_name: 'Doe',
  line_1: '2nd Floor British India House',
  line_2: '15 Carliol Square',
  city: 'Newcastle Upon Tyne',
  postcode: 'NE1 6UF',
  county: 'Tyne & Wear',
  country: 'United Kingdom'
}

const reference = 'XXXX'
const customerId = 'XXXX'

Moltin.Cart(reference).Checkout(customerId, address)
```
{% endtab %}

{% tab title="Swift SDK" %}
```swift
let moltin = Moltin(withClientID: "<your client ID>")

moltin.cart.checkout(
    cart: ...,
    withCustomer: ...,
    withBillingAddress: ...,
    withShippingAddress: ...) { (result) in
    switch result {
        case .success(let order):
            ...
        default: break
    }
}
```
{% endtab %}
{% endtabs %}

