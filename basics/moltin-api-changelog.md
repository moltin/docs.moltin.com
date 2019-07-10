# API Changelog

This changelog is a list of backwards-compatible updates and fixes in the API and [dashboard](https://dashboard.moltin.com/app). These updates are rolled out automatically, but we would still like to keep you informed about the most current state of our API.

### 2019, July 10

* **`MINOR`** Fixed a bug where new store settings could be empty.
* **`MINOR`** Added new readonly settings.

### 2019, July 4

* **`MINOR`** Improved validation when creating and updating integrations.
* **`MAJOR`** Added a new [`payload` field to webhooks](https://docs.moltin.com/api/advanced/events/event-payload) with the JSON representation of the updated object. _`resources` is now deprecated but will remain in place for the foreseeable future._

### 2019, July 2

* **`MINOR`** Fixed a bug where incorrect error messages could be returned if there was an error when making a payment. For example you could get an `Insufficient Stock` error because of an incorrectly formatted payment request. 

### 2019, June 24

* **`MAJOR`** Added new methods, `simple` \(default\) and `line`, to [calculate totals](https://www.moltin.com/developer/concepts/how-to-calculate-cart-and-order-totals) for carts and orders.

  **`MINOR`** Fixed a bug where a PUT to a cart item with a quantity of `0` would return a `404`.

* **`MINOR`** Fixed a bug where passing mismatched IDs in the URL and body, or not passing an ID in the body would cause a `5xx` error.
* **`MINOR`** You can now add a tax item at the same time as adding a cart item. See [Add Product to Cart](../carts-and-checkout/carts/add-product-to-cart.md) or [Add Custom Item to Cart](../carts-and-checkout/carts/add-custom-item-to-cart.md) and for tax item reference see [Tax Items](../carts-and-checkout/carts/cart-items/tax-items/#the-tax-item-object).

### 2019, June 21

* **`MINOR`** Improved error handling when making payments.

### 2019, June **19**

* **`MINOR`** Fixed a bug where attempting to disable any currency would result in a `Cannot disable the default currency` error.

### 2019, June **18**

* **`MAJOR`** Added a [settings option](https://docs.moltin.com/api/advanced/settings#calculation-method) to allow store owners to specify [how taxes and promotions are calculated on their carts](https://docs.moltin.com/guides/calculation-methods).

### 2019, June 11

* **`MINOR`** Fixed bug where in some cases cart totals did not exactly reflect the order totals created after the cart was checked out. Cart totals and order totals now exactly match.
* **`MINOR`** Fixed bug where phone number associated with address would not update correctly on PUT

### **2019, May 28**

* **`MINOR`** Cart items now returned with GET cart call.
* **`MINOR`** Adding a promo code to an empty cart now returns 422: "At least one product must be included in your cart to qualify for this offer"
* **`MINOR`** Adding the same promo code to a cart more than once returns 201 but ensures the code is applied only once.
* **`MINOR`** Updating a modifier no longer changes the child product IDs on rebuild

### 2019, May 23

* **`MINOR`** Added ability to [update tax items](../carts-and-checkout/carts/cart-items/tax-items/update-a-tax-item.md) \(PUT\) once added to a cart item.

### 2019, May 21

* **`MINOR`** Improved the safety of carts using different currencies by rejecting requests which would mix up currencies. The following use cases apply:

1. If you attempt to add a product to a cart which contains items in a different currency, you will receive a 400 error.
2. If you attempt to check out a cart in a different currency than the products that exist in the cart, you will receive a 400 error.
3. If you attempt to GET a cart in a different currency than the items in the cart, then the currency header should be ignored and you will see it in the original currency.
4. If you attempt to GET cart items in a different currency than the items in the cart, then the currency header should be ignored and you will see it in the original currency.

* **`MINOR`** Fixed an issue with carts whereby changing the product quantity would change the order of cart items. This will now be preserved.
* **`MINOR`** Added attribute validation so that only [known events](https://docs.moltin.com/api/advanced/events/observable-events) are accepted.
* **`MINOR`** DELETE calls are now rejected to remove a relationship from a collection for incorrectly formatted requests.
* **`MINOR`** Checkout call now returns order items in the response

### **2019, April 17**

* [**DASHBOARD**](https://dashboard.moltin.com/) Fixed inconsistent behavior of pagination in the UI.
* Fixed an issue whereby an invalid slug would cause an error with the `flows` endpoint.
* Fixed an issue whereby a payment request without an object would cause an error.
* Fixed an issue with the validation issue being logged as error.

### **2019, April 9**

* Pagination on the [`/v2/flows/:flowSlug/entries`](../advanced/custom-data/entries.md#get-all-entries) endpoint now defaults to 100 entries per page.

### **2019, April 4**

* **`MAJOR`** Released a [caching layer](https://www.moltin.com/blog/were-releasing-a-new-edge-caching-layer) for `/products` endpoints. Cached data is now served to stores from edge locations around the world.
* **`MAJOR`** Released live version of the [Self Checkout ](https://moltin.com/commerce-solutions/mobile-self-checkout/)solutions.

### **2019, March 19**

* **`MAJOR`** Added pagination to the [`/v2/flows/:flowSlug/entries`](../advanced/custom-data/entries.md#get-all-entries) endpoint with default set to 1000 entries per page.

### **2019, March 12**

### **2019, March 27**

* Fixed issue with timestamp on inventory record.

### 2019, March 4

* Validation error code now returns a helpful message for SingleEqualsPriceModifierViolation.
* Fixed an issue whereby newly created Flow Field wouldn't immediately present on resource.
* **`MAJOR`** Added Zendesk integration for improved customer support.

### **2019, February 4**

* **`MAJOR`** Moltin's architecture now incorporates [Kubernetes](https://moltin.com/blog/2019/01/moltin-kubernetes/).
* Successful request to orders/:ID/payments endpoint now returns information about the transaction which was created.
* Validation on files endpoint now checks the file parameter is passed, that it is an actual file and returns a 422 if it is not.

### **2018, December 18** <a id="2018-december-18"></a>

* **`MAJOR`** Created a tax item to calculate sales tax for individual cart items. GitHub now includes an [example app](https://github.com/moltin/taxjar-example) showcasing TaxJar integration.
* [**DASHBOARD**](https://dashboard.moltin.com/) Transactions now include the `date` field and show formatted values. 
* Fixed issue with filtering orders.
* Added validation checks for file import.

### 2019, February 27

### **2018, December 11** <a id="2018-december-11"></a>

* Added the `formatted` field to `transaction.data.meta` showing the formatted display price.
* `transaction` response now includes the `created_at` field.

### **2018, December 4** <a id="2018-december-4"></a>

* Updated search to return a 400 error explaining the search contains [unsupported characters](https://docs.moltin.com/~/drafts/-LTg_WTtsk_fgq6z4BWy/primary/basics/filtering#supported-characters).

### **2018, November 20** <a id="2018-november-20"></a>

* Fixed an issue whereby GET `orders.flow` fields would return 404 when flow exists.
* Fixed issue with accessing dashboard.
* Fixed issue with stores list visible when there are no stores.

### **2018, November 13** <a id="2018-november-13"></a>

* **`MAJOR`** [**DASHBOARD**](https://dashboard.moltin.com/) Customers can now bulk add promo codes.
* Fixed issue with initial POST to cart returning unformatted `meta.display_price`.
* Fixed issue with child Product `sku` and `slug` not reflecting API response.
* Fixed an issue with deleting customers through dashboard and API.

### **2018, November 6** <a id="2018-november-6"></a>

* **​**[**DASHBOARD**](https://dashboard.moltin.com/) Customers can now easily delete promo codes.
* Fixed issue with using modifier placeholder in `product.slug` field.
* Fixed issue with assigning Inventory.
* Fixed issue whereby `id` fields on update user and delete user are returned as integers instead of strings.
* Fixed issue with deleting a user from a store.

### **2018, October 30** <a id="2018-october-30"></a>

* Fixed an issue whereby adding a second `cart_item` or deleting a `cart_item` wouldn’t return `flow.entries` for all `cart_items` in the cart.

### **2018, October 23** <a id="2018-october-23"></a>

* Fixed issue with creating `product` relationships.

### **2018, October 16** <a id="2018-october-16"></a>

* **`MAJOR`​**[**DASHBOARD**](https://dashboard.moltin.com/) Added product variations.
* **`MAJOR`** [Facebook lookbook](https://github.com/moltin/moltin-facebook-shop) is now available to allow brands to showcase their catalog on their business Facebook page.
* Updated validation rules for POST requests on `addresses`.
* Fixed issue with additional key returned with `product` response.
* Added validation for `price` object when adding a price modifier.

### **2018, September 25** <a id="2018-september-25"></a>

* Fixed issue with filtering on email.
* **​**[**DASHBOARD**](https://dashboard.moltin.com/) Added pagination to Customers grid.

### **2018, September 18** <a id="2018-september-18"></a>

* **`MAJOR`** Added pagination to `customers`.

### **2018, September 4** <a id="2018-september-4"></a>

* Fixed issue with `flow` to `flow` custom relationship.

### **2018, August 28** <a id="2018-august-28"></a>

* Added allocate and deallocate actions to inventory service.
* Fixed issue around `product` to `product` relationships and pagination.

### **2018, August 21** <a id="2018-august-21"></a>

* **`MAJOR`** Added ​Inventory Management is now available.
* **`MAJOR`** Order exporting is now available.
* POST to `variation.option` returns the newly created `option` object instead of the parent `variation`.
* PUT to `variation.modifier` returns the updated `modifier` object instead of the parent `variation`.
* POST to `variation.modifiers` returns the newly created `modifier` instead of the parent `variation`.
* **`MAJOR`** [**DASHBOARD**](https://dashboard.moltin.com/) Customers can now easily export order data into a CSV file.

### **2018, August 14** <a id="2018-august-14"></a>

* **`MAJOR`** Added Beta access to Inventory Management with `orders`.

### **2018, June 19** <a id="2018-june-19"></a>

* Added validation for the `currencies` array in the promotions schema.

### **2018, June 5** <a id="2018-june-5"></a>

* Resolved an issue with using payment captured events.
* Child `products` now display `main_images`.
* **`MAJOR`** ​Stripe Connect payment method now available.

### **2018, May 15** <a id="2018-may-15"></a>

* Resolved issue that prevented some users from working with Promotions API correctly.
* `flow` to `flow` relationships are now available.
* **`MAJOR`** CardConnect `gateway` now available.

