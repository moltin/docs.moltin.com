# Filtering

Below is a list of attributes and operators available for [filtering](../../basics/filtering/) files.

| **Attribute** | **Type** | **Operators** | **Example** |
| --- | --- | --- | --- |
| `file_name` | `string` | `eq` / `like` | `eq(file_name,'My-Image.jpg')` |
| `width` | `integer` | `gt` / `ge` / `lt` / `le` | `gt(with,200)` |
| `height` | `integer` | `gt` / `ge` / `lt` / `le` | `lt(height,500)` |
| `public` | `boolean` | `eq` | `eq(public,true)` |
| `file_size` | `integer` | `gt` / `ge` / `lt` / `le` | `le(file_size,20953)` |

