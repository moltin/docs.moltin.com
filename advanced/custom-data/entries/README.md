# Entries

| Attribute | Type | Description |
| --- | --- | --- |
| id | **string** | The unique identifier for this entry. |
| type | **string** | Represents the type of object being returned. |
| fieldSlug | **mixed** | The `:fieldSlug` key depends on the field's slug value. The value is of fields `field_type`. |

If your flow has more than one field related to it, you will see multiple field slugs.

{% api-method method="get" host="https://api.moltin.com" path="/v2/flows/:slug/entries/:id" %}
{% api-method-summary %}
Get an Entry
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the entry you are requesting
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
The slug for the flow you are requesting an entry for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "4abb8316-d0a2-4c91-bf29-4d19ba932227",
        "type": "entry",
        "meta": {
            "timestamps": {
                "created_at": "2018-05-10T15:28:59.192Z",
                "updated_at": "2018-05-10T15:28:59.192Z"
            }
        },
        "links": {
            "self": "https://api.moltin.com/v2/flows/products/entries/4abb8316-d0a2-4c91-bf29-4d19ba932227"
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.moltin.com" path="/v2/flows/:slug/entries" %}
{% api-method-summary %}
Get a list of Entries
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="slug" type="string" required=true %}
The slug for the flow you are requesting entries for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/flows/:slug/entries" %}
{% api-method-summary %}
Create an Entry
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="slug" type="string" required=true %}
The slug for the Flow you are requesting an Entry for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="fieldSlug" type="string" required=true %}
The name of the Flow
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.moltin.com" path="/v2/flows/:slug/entries/:id" %}
{% api-method-summary %}
Update an entry
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="slug" type="string" required=true %}
The slug for the flow you are requesting an entry for
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The ID of the entry you are updating
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="type" type="string" required=true %}
Represents the type of object being returned
{% endapi-method-parameter %}

{% api-method-parameter name="fieldSlug" type="string" required=true %}
The name of the flow
{% endapi-method-parameter %}

{% api-method-parameter name="entryID" type="string" required=false %}
The ID of the entry
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
You can have multiple `{FIELD_SLUG}`'s in the request body if they are related to the flow.
{% endhint %}

{% api-method method="delete" host="https://api.moltin.com" path="/v2/flows/:slug/entries/:id" %}
{% api-method-summary %}
Delete an Entry
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The ID of the entry you are requesting to delete
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
The slug for the flows you are requesting entries for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The Bearer token to grant access to the API
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

