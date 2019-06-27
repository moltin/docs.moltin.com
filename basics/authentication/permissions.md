# Permissions

Permissions are managed through tokens. There are two main token types available for use within your project.

{% page-ref page="client-credential-token.md" %}

{% page-ref page="implicit-token.md" %}

Customer tokens can be used with an Implicit Bearer token to manage user interfaces that involved sensitive data the user may need to access or modify such as reading orders, addresses and customer details.

{% page-ref page="../../orders-and-customers/customers/customer-tokens.md" %}

## Breakdown of access

{% tabs %}
{% tab title="Client Credentials" %}
A breakdown of the access given by the token can be seen in the following table.

| **Endpoint** | **Read access** | **Write access** |
| :--- | :--- | :--- |
| `/brands` | ✅ | ✅ |
| `/carts` | ✅ | ✅ |
| `/categories` | ✅ | ✅ |
| `/checkout` | ✅ | ✅ |
| `/collections` | ✅ | ✅ |
| `/currencies` | ✅ | ✅ |
| `/customers` | ✅ | ✅ |
| `/customers/addresses` | ✅ | ✅ |
| `/files` | ✅ | ✅ |
| `/flows` | ✅ | ✅ |
| `/integrations` | ✅ | ✅ |
| `/orders` | ✅ | ✅ |
| `/payment-gateways` | ✅ | ✅ |
| `/products` | ✅ | ✅ |
| `/variations` | ✅ | ✅ |
| `/promotions` | ✅ | ✅ |
| `/settings` | ✅ | ✅ |
| `/jobs` | ✅ | ✅ |
{% endtab %}

{% tab title="Implicit" %}
The table below shows a breakdown of which API endpoint actions are available to this token type. Note that you can only fetch data with live status.

| **Endpoint** | **Read access** | **Write access** |
| :--- | :--- | :--- |
| `/brands` | ✅ | ⛔️ |
| `/carts` | ✅ | ✅ |
| `/categories` | ✅ | ⛔️ |
| `/checkout` | ✅ | ✅ |
| `/collections` | ✅ | ⛔️ |
| `/currencies` | ✅ | ⛔️ |
| `/customers` | ⛔️ | ⛔️ |
| `/customers/addresses` | ⛔️ | ⛔️ |
| `/files` | ✅ | ⛔️ |
| `/flows` | ✅ | ⛔️ |
| `/integrations` | ⛔️ | ⛔️ |
| `/orders` | ⛔️ | ⛔️ |
| `/payment-gateways` | ⛔️ | ⛔️ |
| `/products` | ✅ | ⛔️ |
| `/variations` | ⛔️ | ⛔️ |
| `/promotions` | ⛔️ | ⛔️ |
| `/settings` | ⛔️ | ⛔️ |
| `/jobs` | ⛔️ | ⛔️ |
{% endtab %}

{% tab title="Implicit + Customer Token" %}


| Endpoint | Read access | Write access |
| :--- | :--- | :--- |
| `/brands` | ✅ | ⛔️ |
| `/carts` | ✅ | ✅ |
| `/categories` | ✅ | ⛔️ |
| `/checkout` | ✅ | ✅ |
| `/collections` | ✅ | ⛔️ |
| `/currencies` | ✅ | ⛔️ |
| `/customers` | ✅ | ✅ |
| `/customers/addresses` | ✅ | ✅ |
| `/files` | ✅ | ⛔️ |
| `/flows` | ✅ | ⛔️ |
| `/integrations` | ⛔️ | ⛔️ |
| `/orders` | ✅ | ⛔️ |
| `/payment-gateways` | ⛔️ | ⛔️ |
| `/products` | ✅ | ⛔️ |
| `/promotions` | ⛔️ | ⛔️ |
| `/settings` | ⛔️ | ⛔️ |
| `/jobs` | ⛔️ | ⛔️ |
{% endtab %}
{% endtabs %}



