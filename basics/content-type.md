# Content Type

## Authentication

The [oauth](https://oauth.net/2/) endpoint for `implicit` and `client_credentials` [authentication](authentication/) requests must contain the header `Content-Type: application/x-www-form-urlencoded`.

## Core resources

Requests made to the API must be encoded as **JSON** and contain the header `Content-Type: application/json` .

## Files

Requests to create a new [File](../advanced/files/) must contain the header `Content-Type: multipart/form-data`.

## Response encoding

Responses from the Moltin API, including errors, are encoded as **JSON**.

