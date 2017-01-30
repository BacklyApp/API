# Introduction

The Backly API uses OAuth authorization to allow third-party apps access to the API on behalf of Backly users once authorized to do so.

# Authorization

To authenticate an app's requets the API uses long lived Access Tokens granted by your app's users to access the API on their behalf. To obtain an access token you must be authorized by the user.

## Getting Started

You will need a few things before you will be able to make authorization requests to the API.

- **App ID** and **App Secret**. These were automatically generated for you when your app was created.

- **Redirect URL**. This is a location that the OAuth API will redirect a user back to once they have performed a successful authorization request. This must match the redirect URL that your app was created with and it must be updated if your app's redirect URL is changed.

## Requesting Authorization

First your app should direct a users browser to `http://app.back.ly/oauth/authorize` with the following query string parameters.

- `client_id`: Your App ID.
- `redirect_uri`: Your Redirect URL.
- `response_type`: Set to `code`.

For example:

```
http://app.back.ly/oauth/authorize?client_id=123&redirect_uri=http://my.app/oauth/callback&response_type=code
```

On this page users will be shown a prompt to authorize your app. If they accept they will be redirected back to the Redirect URL with the **Authorization Code** set in the query string parameter named `code`.

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

For example:

```
POST /oauth/token HTTP/1.1
Host: app.back.ly.localhost
Content-Type: application/x-www-form-urlencoded
...

code=...
```

This request will return a JSON response containing an `access_token` token attribute. This **Access Token** can then be used to make API requests.

### POST Requests

When making a `POST` request two formats are supported in the request body. Set your `Content-Type` header according to the format of the data you are sending.

- **URL-encoded** (`application/x-www-form-urlencoded`)
- **JSON** (`application/json`)

# Authentication

## Using the Access Token

To access the rest of the API in these docs you must use your Access Token as a Bearer Token in the `Authorization` header of every request you make.

For example:

```
POST /links HTTP/1.1
Authorization: Bearer <access-token>
...
```
