# Errors

Any requests that return an error follow a standard format. Moltin will return an array of `errors` that contains objects containing `status`, `title` and `details`.

You'll most likely receive an error if validation fails, something doesn't exist or something went wrong on our end. We return errors inline with the [JSON API specification](http://jsonapi.org/format/#error-objects).

The most common response codes you'll get from Moltin will be:

| **Code** | **Response** |
| --- | --- |
| `201` | Created successfully |
| `200` | Updated successfully |
| `204` | Deleted successfully |
| `400` | Invalid JSON |
| `422` | Validation error |
| `500` | Something went wrong our side |

## Example errors

Below you will find some example error responses from the Moltin API.

### Forbidden

You'll most likely receive a `401: Unauthorized` response when you provide an invalid [authentication](authentication/) token.

```javascript
{
  "errors": [
    {
      "status": 401,
      "title": "Unable to validate access token"
    }
  ]
}
```

### Bad Request

You'll get a `400: Bad Request` when you you fail validation.

```javascript
{
  "errors": [
    {
      "status": 400,
      "source": "enabled",
      "title": "required",
      "detail": "enabled is required"
    }
  ]
}
```

### Rate Limited

You will receive a `429: Too Many Requests` response when you make too many requests.

```javascript
{
  "errors": [
    {
      "status": 429,
      "title": "..."
    }
  ]
}
```

### Not Found

When a resource is not found you will get a `404: Not Found` response.

```javascript
{
  "errors": [
    {
      "status": 404,
      "detail": "The requested category could not be found",
      "title": "Category not found"
    }
  ]
}
```

### Internal Server Error

You'll receive a `500: Internal Server Error` response when something goes wrong on our side. We're automatically notified of these errors and work to resolve as quickly as possible.

```javascript
{
  "errors": [
    {
      "status": 500,
      "title": "Internal Server Error",
      "title": "There was an internal server error, you can report with your request id.",
      "request_id": "XXXX"
    }
  ]
}
```

