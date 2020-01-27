# Settings

The Settings endpoint allows you to configure global settings for your project.

## Page length

This defines the number of results per page when paginating results \(**max**: `100`\).

| **Name** | **Type** | **Default** | **Max** |
| :--- | :--- | :--- | :--- |
| `page_length` | `integer` | `100` | `100` |

Resources that support pagination:

* `brands`, `categories`, `collections`, `customers`, `files`, `flows/:slug/entries`, `inventory`, `orders`, `products`

## List child products

This defines whether you wish to display child products in product listings.

| **Name** | **Type** | **Default** |
| :--- | :--- | :--- |
| `list_child_products` | `boolean` | `true` |

## Additional languages

You can define additional language codes that are enabled for a project \(**max**: `5`\).

| **Name** | **Type** | **Default** | **Max** |
| :--- | :--- | :--- | :--- |
| `additional_languages` | `array` | `[]` | `5` |

## Calculation method

This option defines the method used to calculate cart and order totals. Currently there are two methods: `{simple}` and `{line}`

The `{simple}` method is our previous method for calculating cart and order totals which focuses on the total value of the cart. This should only be used in the case where Moltin is not utilised for tax calculations. The `{line}` method treats each line item individually resulting in more accurate figures after taxes and promotions are applied.

| **Name** | **Type** | **Value** | **Default** |
| :--- | :--- | :--- | :--- |
| `calculation_method` | `string` | `simple` | ✓ |
| `calculation_method` | `string` | `line` |  |
|  |  |  |  |

## Readonly settings

Readonly settings are used for internal store configuration and attempts to update them will fail silently.

| Name | Type | Default |
| :--- | :--- | :--- |
| `currency_limit` | `integer` | `10` |

