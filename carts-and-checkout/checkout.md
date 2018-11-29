# Checkout

Once a [Cart](carts/) is ready to checkout, you can easily convert your Cart to an [Order](https://github.com/moltin/api.docs.moltin.com/tree/cbfae6cc90f263c65a62c5eab62b2212cd61695a/orders-and-customers/orders/README.md). The Cart will remain and can be modified and checked out again if required.

Once a successful Checkout is completed, the response will contain the order.

{% hint style="warning" %}
We'll automatically delete carts 7 days after they were last updated.
{% endhint %}

{% hint style="danger" %}
There are a number of actions that happen to your [inventory](../catalog/inventory/) when checking out and paying for an order. For more information please be sure to evaluate our [detailed article](https://developers.moltin.com/guides/work-with-inventory) explaining the processes.
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
{% api-method-body-parameters %}
{% api-method-parameter name="customer.id" type="string" required=true %}
The **ID** of the customer
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.first\_name" type="string" required=true %}
First name of the billing recipient
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.last\_name" type="string" required=true %}
Last name of the billing recipient
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.company\_name" type="string" required=false %}
Company name of the billing recipient
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.line\_1" type="string" required=true %}
First line of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.line\_2" type="string" required=false %}
Second line of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.postcode" type="string" required=true %}
Postcode of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="bililng\_address.county" type="string" required=true %}
County / state /  region of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.country" type="string" required=true %}
Country of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.first\_name" type="string" required=true %}
First name of the shipping recipient
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.last\_name" type="string" required=true %}
Last name of the shipping recipient
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.phone\_number" type="string" required=false %}
Phone number of the shipping recipient
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.company\_name" type="string" required=false %}
Company of the shipping recipient
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.line\_1" type="string" required=true %}
First line of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.line\_2" type="string" required=false %}
Second line of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.city" type="string" required=false %}
City of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.postcode" type="string" required=true %}
Post code of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.county" type="string" required=true %}
County / state/ region of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.country" type="string" required=true %}
Country of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.instructions" type="string" required=false %}
Shipping instructions
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
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
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
           "country": "UK",
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

const reference = 'XXXX'
const customerId = 'XXXX'

const billing = {
  first_name: 'John',
  last_name: 'Doe',
  line_1: '2nd Floor British India House',
  line_2: '15 Carliol Square',
  city: 'Newcastle Upon Tyne',
  postcode: 'NE1 6UF',
  county: 'Tyne & Wear',
  country: 'United Kingdom'
}

Moltin.Cart(reference)
  .Checkout(customerId, billing, shipping)
  .then(order => {
    // Do something
  })
```

{% hint style="info" %}
`shipping` is optional. `billing` will be `shipping` if not provided.
{% endhint %}
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

{% api-method-body-parameters %}
{% api-method-parameter name="customer.email" type="string" required=true %}
Customer email address
{% endapi-method-parameter %}

{% api-method-parameter name="customer.name" type="string" required=true %}
Full name of the customer
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.first\_name" type="string" required=true %}
First name of the billing recipient
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.last\_name" type="string" required=true %}
Last name of the billing recipient
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.company\_name" type="string" required=false %}
Company name of the billing recipient
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.line\_1" type="string" required=true %}
First line of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.line\_2" type="string" required=false %}
Second line of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.city" type="string" required=false %}
/city of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.postcode" type="string" required=true %}
Postcode of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.county" type="string" required=true %}
County / state / region of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="billing\_address.country" type="string" required=true %}
Country of the billing address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.first\_name" type="string" required=true %}
First name of the shipping recipient
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.last\_name" type="string" required=true %}
Last name of the shipping recipient
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.company\_name" type="string" required=false %}
Company name of the shipping recipient
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.phone\_number" type="string" required=false %}
Phone number of the shipping recipient
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.line\_1" type="string" required=true %}
First line of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.line\_2" type="string" required=false %}
Second line of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.city" type="string" required=false %}
City of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.postcode" type="string" required=true %}
Postcode of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.county" type="string" required=true %}
County / state / region of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.country" type="string" required=true %}
Country of the shipping address
{% endapi-method-parameter %}

{% api-method-parameter name="shipping\_address.instructions" type="string" required=false %}
Shipping instructions
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
                "tax": {
                    "amount": 0,
                    "currency": "",
                    "formatted": ""
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
     -H "Authorization: Bearer XXXX" \
     -H "Content-Type: application/json" \
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
           "country": "UK",
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

const reference = 'XXXX'

const customer = {
  email: 'john@moltin.com',
  name: 'John Doe'
}

const billing = {
  first_name: 'John',
  last_name: 'Doe',
  line_1: '2nd Floor British India House',
  line_2: '15 Carliol Square',
  city: 'Newcastle Upon Tyne',
  postcode: 'NE1 6UF',
  county: 'Tyne & Wear',
  country: 'United Kingdom'
}

const shipping = {
  first_name: 'John',
  last_name: 'Doe',
  line_1: '2nd Floor British India House',
  line_2: '15 Carliol Square',
  city: 'Newcastle Upon Tyne',
  postcode: 'NE1 6UF',
  county: 'Tyne & Wear',
  country: 'United Kingdom'
}

Moltin.Cart(reference)
  .Checkout(customer, billing, shipping)
  .then(order => {
    // Do something
  })
```

{% hint style="info" %}
`shipping` is optional. `billing` will be `shipping` if not provided.
{% endhint %}
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

## Next steps

Once a Cart has been converted to an Order using either of the methods above, you will most likely want to capture payment for order.

{% page-ref page="../payments/paying-for-an-order/" %}



