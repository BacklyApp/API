# Introduction

Backly provides a stateless HTTP JSON API (`api.back.ly`) for the use of third-parties to interact with the service programatically on behalf of its users.

## Authentication and authorization

The API uses OAuth to authenticate and allow users to authorize your app to access the API for them.

## Encryption

It's strongly recommended that you use the API over a secure connection to protect the secrecy of your connection and your authorization tokens.

## Example request

An example request for creating a Backly link:
```
POST /links HTTP/1.1
Host: api.back.ly
Authorization: Bearer ...
Accept: application/json
Content-Type: application/json
...

{
  "advert": "abc123",
  "url": "http://example.com?page=123#section"
}
```

# Obtaining Access

The API is free to use. To apply for access contact us at [support@back.ly](mailto:support@back.ly), or come and chat with us in-app!

# Using the API

The Backly API returns data in JSON format and accepts either JSON or URL-encoded input for [`POST`ed data](/auth#post-requets).

You must include an `Accept: application/json` header to ensure the JSON formatting of any error responses because the response will be formatted in HTML by default.
