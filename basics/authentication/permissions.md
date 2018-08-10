# Permissions

Permissions are managed through tokens. There are two main token types available for use within your project.

{% page-ref page="client-credential-token.md" %}

{% page-ref page="implicit-token.md" %}

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
| `/files` | ✅ | ✅ |
| `/flows` | ✅ | ✅ |
| `/integrations` | ✅ | ✅ |
| `/orders` | ✅ | ✅ |
| `/payment-gateways` | ✅ | ✅ |
| `/products` | ✅ | ✅ |
| `/promotions` | ✅ | ✅ |
| `/settings` | ✅ | ✅ |
{% endtab %}

{% tab title="Implicit" %}
The table below shows a breakdown of which API endpoint actions are available to this token type.

| **Endpoint** | **Read access** | **Write access** |
| :--- | :--- | :--- |
| `/brands` | ✅ | ⛔️ |
| `/carts` | ✅ | ✅ |
| `/categories` | ✅ | ⛔️ |
| `/checkout` | ✅ | ✅ |
| `/collections` | ✅ | ⛔️ |
| `/currencies` | ✅ | ⛔️ |
| `/customers` | ⛔️ | ⛔️ |
| `/files` | ✅ | ⛔️ |
| `/flows` | ✅ | ⛔️ |
| `/integrations` | ⛔️ | ⛔️ |
| `/orders` | ⛔️ | ⛔️ |
| `/payment-gateways` | ⛔️ | ⛔️ |
| `/products` | ✅ | ⛔️ |
| `/promotions` | ⛔️ | ⛔️ |
| `/settings` | ⛔️ | ⛔️ |
{% endtab %}
{% endtabs %}

