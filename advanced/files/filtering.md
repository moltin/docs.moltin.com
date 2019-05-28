# Filtering

Below is a list of attributes and operators available for [filtering](../../basics/filtering/) files.

| **Attribute** | **Type** | **Operators** | **Example** |
| :--- | :--- | :--- | :--- |
| `file_name` | `string` | `eq` / `like` | `eq(file_name, my_image.jpg)` |
| `width` | `integer` | `gt` / `ge` / `lt` / `le` | `gt(with,200)` |
| `height` | `integer` | `gt` / `ge` / `lt` / `le` | `lt(height,500)` |
| `public` | `boolean` | `eq` | `eq(public,true)` |
| `file_size` | `integer` | `gt` / `ge` / `lt` / `le` | `le(file_size,20953)` |

## Supported characters

As filters are passed as URL query string parameters, we must ensure all filters are URL safe and are strict about the characters that can be used in a filter.

| Characters | Can be used in filter? |
| :--- | :--- |
| `A-Z` \(upper\) | No \(Must be lower case\) |
| `0-9` | Yes |
| `_` | Yes |
| \`\` \(space\) | No |

Example string for filtering

{% tabs %}
{% tab title="Moltin Request" %}
```javascript
const { MoltinClient } = require('@moltin/request')

const client = new MoltinClient({
  client_id: 'X',
  client_secret: 'X'
})

//Clean up the file name
const filterName = fileName.replace(/[^A-Z0-9]/gi, "_")
          .toLowerCase()

  client
  .get(`files/?filter=eq(file_name,${filterName}`);
  .then(product => {
    // Do something...
  })
  .catch(console.error)
```
{% endtab %}
{% endtabs %}

