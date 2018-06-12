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
{
    "data": [
        {
            "id": "ce1f0b19-23c3-487b-aa2a-552b77abdf0c",
            "type": "entry",
            "brand-image": "https://s3-eu-west-1.amazonaws.com/bkt-svc-files-cmty-api-moltin-com/e8c53cb0-120d-4ea5-8941-ce74dec06038/61118f21-14a2-466c-a84b-c30b1f900cf9.png",
            "meta": {
                "timestamps": {
                    "created_at": "2018-06-05T20:58:25.596Z",
                    "updated_at": "2018-06-05T20:58:25.596Z"
                }
            },
            "links": {
                "self": "https://api.moltin.com/v2/flows/brands/entries/ce1f0b19-23c3-487b-aa2a-552b77abdf0c"
            }
        },
        {
            "id": "a5fcf6bc-233f-44d7-a3b0-0961eed3df9d",
            "type": "entry",
            "brand-image": "someimage for brand x",
            "meta": {
                "timestamps": {
                    "created_at": "2018-06-06T14:48:59.006Z",
                    "updated_at": "2018-06-06T14:48:59.006Z"
                }
            },
            "links": {
                "self": "https://api.moltin.com/v2/flows/brands/entries/a5fcf6bc-233f-44d7-a3b0-0961eed3df9d"
            }
        }
    ]
}
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
{
    "data": {
        "id": "06de90b0-5426-4f61-bcd2-fcdeab40b806",
        "type": "flow",
        "name": "Brands",
        "slug": "Brands",
        "description": "Extends the default brand object",
        "enabled": true,
        "links": {
            "self": "https://api.moltin.com/v2/flows/06de90b0-5426-4f61-bcd2-fcdeab40b806"
        },
        "relationships": {},
        "meta": {
            "timestamps": {
                "created_at": "2018-06-06T14:56:20.860Z",
                "updated_at": "2018-06-06T14:56:20.860Z"
            }
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
https://api.moltin.com/v2/flows
 {
  "data": {
    "type": "flow",
    "name": "Brands",
    "slug": "brands",
    "description": "Extends the default brand object",
    "enabled": true
   }
 }
```
{% endtab %}
{% endtabs %}

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
The slug for the Flow you are requesting an entry for
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
The **ID** of the entry you are updating
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

{% api-method-parameter name="entryID" type="string" required=false %}
The **ID** of the entry
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "id": "03224af8-da41-4761-99fb-a125fa81ed99",
        "type": "entry",
        "brand-image": "someimage new things",
        "meta": {
            "timestamps": {
                "created_at": "2018-06-06T14:42:39.312Z",
                "updated_at": "2018-06-06T14:42:39.312Z"
            }
        },
        "links": {
            "self": "https://api.moltin.com/v2/flows/brands/entries/03224af8-da41-4761-99fb-a125fa81ed99"
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="cURL" %}
```javascript
{
  "data": {
    	"type": "brands",
    	"brand-image": "someimage new things"
	}
}
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

{% hint style="info" %}
You can have multiple `{FIELD_SLUG}`s in the request body if they are related to the flow.
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
The **ID** of the entry you are requesting to delete
{% endapi-method-parameter %}

{% api-method-parameter name="slug" type="string" required=true %}
The slug for the Flows you are requesting entries for
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

