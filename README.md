# Table of contents

1. [About the API](#about)
2. [Authorization](#authorization)
3. [API Endpoints](#api)
  1. [Links](#api-links)
    1. [Create](#api-links-create)
  2. [Adverts](#api-adverts)
    1. [Recent](#api-adverts-get)

<div id="#about"></div>
# About the API

Backly provides an HTTP API for the use of third-parties to interact with the service programatically.

<div id="authorization"></div>
# Authorization (via OAuth API)

Backly uses an OAuth based authorization with long lived **Access Tokens** to allow third-party apps access to the API on behalf of Backly users.

## Getting Started

You will need a few things before you will be able to make requests to our OAuth API.

- **App ID** and **App Secret**. These were automatically generated for you when your app was created.

- **Redirect URL**. This is a location on your app that the OAuth API can redirect a user back to once they have performed a successful authorization request with Backly. This must match the redirect URL that your app was created with and it must be updated if your app's redirect URL is changed.

## Requesting Authorization

First your app should direct a users browser to `http://app.back.ly/oauth/authorize` with the following query string parameters.

- `client_id`: Your App ID.
- `redirect_uri`: Your Redirect URL.
- `response_type`: Set to `code`.

For example:

```
http://app.back.ly/oauth/authorize?client_id=123&redirect_uri=http://my.app/oauth/callback&response_type=code
```

On this page users will be shown a prompt to authorize your app to access their Backly account. If they accept they will be redirected back to the Redirect URL with the **Authorization Code** set in the query string parameter `code`.

For example:

```
http://my.app/callback?code=...
```

## Obtaining an Access Token

When a user is redirected back to your Redirect URL after a successful authorization request your app should then issue a `POST` request to `http://app.back.ly/oauth/token` with the Authorization Code, along with these other parameters in the body of the request.

- `client_id`: Your App ID.
- `client_secret`: Your App Secret.
- `code`: The Authorization Code returned by the successful authorization request.
- `grant_type`: Set to `authorization_code`.
- `redirect_uri`: Your Redirect URL.

This request will return a JSON response containing an `access_token` token attribute. This **Access Token** can then be used to make API requests on behalf of the Backly user who authorized your app to do so.

<div id="post-requets"></div>
### POST Requests

When making a `POST` request two formats are accepted by the Backly API. Set your `Content-Type` header according to the format of the data you are sending.

- **URL-encoded** (`application/x-www-form-urlencoded`)
- **JSON** (`application/json`)

<div id="api"></div>
# API Endpoints

All endpoints are accesible from the API server which is located at `http://api.back.ly`. The API returns data in JSON format and accepts either JSON or URL-encoded input for [`POST` requests](#post-requets).

<div id="api-links"></div>
## Links

<div id="api-links-create"></div>
### Create `POST /links`

Create a new link.

#### Parameters

| Name | Type | Description |
|---|---|---|
| `advert` | String | The identifier code of the advert you wish to display with this link. |
| `url` | URL | The URL you wish to share. |

#### Example Request

```
POST /links HTTP/1.1
Host: api.back.ly
```

#### Example Response

```
{
  ---
}
```

<div id="api-adverts"></div>
## Adverts

<div id="api-adverts-get"></div>
### Recent `GET /adverts/recent`

Return a list of the 10 most recently used adverts.

#### Parameters

| Name | Type | Description |
|---|---|---|
| `offset` | Integer | The number of adverts to offset the search by. |

#### Example Request

```
GET /adverts/recent HTTP/1.1
Host: api.back.ly
```

#### Example Response

```
{
  ---
}
```
