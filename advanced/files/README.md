# Files

The immutable files API is available via the `multipart/form-data` [Content-Type](../../basics/content-type.md#files) for image uploads.

{% hint style="warning" %}
Accept file types are `jpg`, `jpeg`, `png` and `gif`.
{% endhint %}

## The file object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `id` | `string` | The unique identifier for this file |
| `type` | `string` | The type represents the object being returned |
| `link` | [`object`](./#the-file-link-object) | The file [link object](./#the-file-link-object) |
| `file_name` | `string` | The name of the file |
| `mime_type` | `string` | The mime type of the file |
| `file_size` | `integer` | The size of the file |
| `public` | `boolean` | ~~Is this file public or not~~ |
| `meta` | [`object`](./#the-file-meta-object) | The additional [meta object](./#the-file-meta-object) |
| `links` | [`object`](./#the-file-links-object) | The file [links object](./#the-file-links-object) |

## The file link object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `link.href` | `string` | The publicly available URL for this file |

## The file meta object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `meta.dimensions.width` | `integer` | The width of the file |
| `meta.dimensions.height` | `integer` | The height of the file |
| `meta.timestamps.created_at` | `string` | The creation date of the file |

## The file links object

| **Attribute** | **Type** | **Description** |
| --- | --- | --- |
| `links.self` | `string` | The URL of this file object |

## Example response

```javascript
{
  "data": {
    "id": "272d3ff0-5034-4986-8786-0ff97450745d",
    "type": "file",
    "link": {
      "href": "https://s3-eu-west-1.amazonaws.com/bkt-api-moltin-com/2a85964e-cb3d-482a-ab02-0f0e47ab5662/273d3ff0-5034-4986-8786-0ff97450745.jpg"
    },
    "file_name": "image.jpg",
    "mime_type": "image/jpeg",
    "file_size": 20953,
    "public": true,
    "meta": {
      "dimensions": {
        "width": 1600,
        "height": 800
      },
      "timestamps": {
        "created_at": "2017-08-14T10:47:45.191Z"
      }
    },
    "links": {
      "self": "https://api.moltin.com/v2/files/272d3ff0-5034-4986-8786-0ff97450745d"
    }
  }
}
```

