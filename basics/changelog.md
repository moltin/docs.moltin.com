# Changelog

## Aug 21, 2018

### Added

* [Inventory Management](../catalog/inventory/) is now available
* [Order exporting]() is now available

### Changes

* `POST` to variation option returns the newly created option object instead of the parent variation
* `PUT` to variation modifier returns the updated modifier object instead of the parent variation
* `POST` to variation modifiers returns the newly created modifier instead of the parent variation

## Aug 14, 2018

### Added

* Beta access to [inventory management](https://developers.moltin.com/guides/work-with-inventory) with orders

## June 19, 2018

### Added

* Added validation for the currencies array in the promotions schema

## June 5, 2018

### Fixed

* A bug which prevented the use of payment captured event is now resolved.
* Child products now display main images.

### Added

* [Stripe Connect](../payments/paying-for-an-order/stripe-payments.md#pay-by-stripe-connect) payment method now available.
* Public facing changelog now available within the API reference.

## May 15, 2018

### Fixed

* Resolved issue that prevented some users from working with [Promotions API](../carts-and-checkout/promotions/) correctly.

### Added

* Flow to Flow relationships are now available.
* [Card Connect](../payments/gateways/configure-cardconnect.md) gateway now available.

