# Flow Field Validation

When creating a Flow field, you can add validation to values that are stored. The validation you can use depends on the `field_type` and each one is expressed as a validation rule object:

## `string` / `enum`

```javascript
{
    "type": "enum",
    "options": [
        "fast",
        "slow"
    ]
}
```

Must be one of a predefined collection of strings.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `enum` |
| `options` | `array[string]` | An array of valid string values. |

## `string` / `email`

```javascript
{
    "type": "email"
}
```

Must be a valid email address.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `email` |

## `string` / `slug`

```javascript
{
    "type": "slug"
}
```

Can contain only letters, numbers, hyphens and underscores.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `slug` |

## `integer` / `between`

```javascript
{
    "type": "between",
    "options": {
        "from": 1,
        "to": 5
    }
}
```

Must be between the two provided values.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `enum` |
| `options` | `object` | an object containing `from` and `to` integers. |

## `integer` / `enum`

```javascript
{
    "type": "enum",
    "options": [
        1,
        2,
        3,
        4,
        5
    ]
}
```

Must be one of a predefined collection of integers.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `enum` |
| `options` | `array[integer]` | An array of valid integer values. |

## `float` / `between`

```javascript
{
    "type": "between",
    "options": {
        "from": 0.0,
        "to": 5.0
    }
}
```

Must be between the two provided values.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `enum` |
| `options` | `object` | An object containing `from` and `to` floats. |

## `float` / `enum`

```javascript
{
    "type": "enum",
    "options": [
        0.0,
        0.5,
        1.0
    ]
}
```

Must be one of a predefined collection of floats.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `enum` |
| `options` | `array[float]` | An array of valid float values. |

## `date` / `enum`

```javascript
{
    "type": "enum",
    "options": [
        "2017-12-25",
        "2017-12-26"
    ]
}
```

Must be one of a predefined collection of dates.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `enum` |
| `options` | `array[string]` | An array of valid date values as strings \(`YYYY-MM-DD HH:MM:SS` - time is optional\). |

## `relationship` / `one-to-many`

```javascript
{
    "type": "one-to-many",
    "to": "product"
}
```

Allows multiple relationships to be created.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `one-to-many` |
| `to` | `string` | The entity type you are making relationships with in singular form \(eg: `product`\) |

## `relationship` / `one-to-one`

```javascript
{
    "type": "one-to-one",
    "to": "customer"
}
```

Allows only a single relationships to be created on an entry.

| **Attribute** | **Type** | **Description** |
| :--- | :--- | :--- |
| `type` | `string` | `one-to-one` |
| `to` | `string` | The entity type you are making relationships with in singular form \(eg `customer`\) |

