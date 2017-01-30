# Introduction

Backly provides a stateless HTTP JSON API (`api.back.ly`) for the use of third-parties to interact with the service programatically on behalf of its users.

## Authentication and authorization

The API uses OAuth to authenticate and allow users to authorize your app to access the API for them.

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