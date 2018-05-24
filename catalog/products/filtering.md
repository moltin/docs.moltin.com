# Filtering

Below is a list of attributes and operators available for [filtering](../../basics/filtering/) products.

| **Attribute** | **Type** | **Operators** | **Example** |
| --- | --- | --- | --- |
| `name` | `string` | `eq` / `like` | `like(name,Deck*)` |
| `slug` | `string` | `eq` / `like` | `eq(slug,deck-shoe)` |
| `sku` | `string` | `eq` / `like` | `eq(sku,deck-shoe-001)` |
| `status` | `string` | `eq` / `like` | `eq(status,live)` |
| `description` | `string` | `like` | `like(description,*deck*)` |
| `manage_stock` | `boolean` | `eq` | `eq(commodity_type,digital)` |
| `brand.id` | `string` | `eq` | `eq(brand.id,id)` |
| `category.id` | `string` | `eq` | `eq(category.id,id)` |
| `collection.id` | `string` | `eq` | `eq(collection.id,id)` |

