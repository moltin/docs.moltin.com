# Paying for an order

When you [checkout](../../carts-and-checkout/checkout.md) a [cart](../../carts-and-checkout/carts/), you will be returned an unpaid [order](../../orders-and-customers/orders/). You can handle payment via a number of payment gateways.

{% hint style="info" %}
You will need to configure and enable a payment gateway before you can accept payments for orders.
{% endhint %}

{% hint style="warning" %}
You can use the [Manual Gateway](manual-payments.md) to handle payments from non-supported payment providers, such as PayPal. 🎉
{% endhint %}

{% hint style="danger" %}
There are a number of actions that happen to your [inventory](https://docs.moltin.com/~/drafts/-LJsFeY2nae5ndXehUDs/primary/catalog/inventory) when checking out and paying for an order. For more information please be sure to evaluate our [detailed article](https://developers.moltin.com/guides/work-with-inventory) explaining the processes.
{% endhint %}

## Payment methods

Depending on the chosen gateway, you may or may **not** have access to `capture` funds immediately or `authorize` for later payment.

{% page-ref page="../transactions.md" %}

### Purchase

The simplest method is `purchase`. The gateway will attempt to charge the customer immediately, and the result of the attempt will be returned.

### Authorize

You may wish to `authorize` a payment so funds can later be captured when an item is dispatched or restocked.

### Capture

Once you have an authorized transaction, you will want to `capture` the authorized funds.

### **Refund**

You can mark a transaction refunded at anytime.

