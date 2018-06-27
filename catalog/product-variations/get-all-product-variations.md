# Get All Product Variations

{% api-method method="get" host="https://api.moltin.com" path="/v2/variations" %} {% api-method-summary %} Get product variations {% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %} {% api-method-request %} {% api-method-path-parameters %} {% api-method-parameter name="Authorization" type="string" required=true %} The Bearer token that is used access to the API {% endapi-method-parameter %} {% endapi-method-path-parameters %} {% endapi-method-request %}

{% api-method-response %} {% api-method-response-example httpCode=200 %} {% api-method-response-example-description %}

{% endapi-method-response-example-description %}

{
    "data": [
        {
            "type": "product-variation",
            "id": "f714ec07-b031-4528-b5ae-f4fd9d660d54",
            "name": "Colour",
            "options": [
                {
                    "id": "5536826a-f277-4dd7-9d44-3949b95ab8e7",
                    "name": "RED",
                    "description": "Reddish",
                    "modifiers": []
                },
                {
                    "id": "adaa2cab-94e5-4ec8-835f-dbb03494be3b",
                    "name": "Blue",
                    "description": "Our most popular color",
                    "modifiers": []
                },
                {
                    "id": "685fef4a-5cf8-496b-a58e-001580f280ea",
                    "name": "Blue",
                    "description": "Our most popular color",
                    "modifiers": []
                },
                {
                    "id": "e191781e-88e1-4b12-a423-a1b4cc926051",
                    "name": "Blue",
                    "description": "Our most popular color",
                    "modifiers": []
                },
                {
                    "id": "a7e28b0c-d991-4c17-a7c3-b5b78817f3c9",
                    "name": "Blue",
                    "description": "Our most popular color",
                    "modifiers": []
                }
            ],
            "relationships": {
                "options": {
                    "data": [
                        {
                            "type": "option",
                            "id": "5536826a-f277-4dd7-9d44-3949b95ab8e7"
                        },
                        {
                            "type": "option",
                            "id": "adaa2cab-94e5-4ec8-835f-dbb03494be3b"
                        },
                        {
                            "type": "option",
                            "id": "685fef4a-5cf8-496b-a58e-001580f280ea"
                        },
                        {
                            "type": "option",
                            "id": "e191781e-88e1-4b12-a423-a1b4cc926051"
                        },
                        {
                            "type": "option",
                            "id": "a7e28b0c-d991-4c17-a7c3-b5b78817f3c9"
                        }
                    ]
                }
            }
        },
        {
            "type": "product-variation",
            "id": "f43de422-b69c-4343-a08d-125dee7fb8d2",
            "name": "Paint colour"
        },
        {
            "type": "product-variation",
            "id": "18589b01-ce2a-4fbb-883d-231f16dc9786",
            "name": "Paint colour"
        },
        {
            "type": "product-variation",
            "id": "2af2a2b1-9af9-4d5c-9757-d89ba7f602a8",
            "name": "Paint colour"
        },
        {
            "type": "product-variation",
            "id": "4c897928-31bc-4bfe-aa4d-b7b9b96500b2",
            "name": "Paint colour"
        }
    ],
    "links": {
        "current": "https://api.moltin.com/v2/variations?page[limit]=100&page[offset]=0",
        "first": "https://api.moltin.com/v2/variations?page[limit]=100&page[offset]=0",
        "last": null
    }
}

{% endapi-method-response-example %} {% endapi-method-response %} {% endapi-method-spec %} {% endapi-method %}

curl -X GET https://api.moltin.com/v2/variations \
     -H "Authorization: Bearer 965baf46f390879c213e48cf84dcda16bb6d0819"
