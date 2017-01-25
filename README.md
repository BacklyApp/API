# Authorisation (via OAuth API)

Backly uses an OAuth based authentication with long lived **Access Tokens** to allow third-party apps access to the API on behalf of Backly users.

## Getting Started

You will need a few things before you will be able to make requests to our OAuth API.

- **App ID** and **App Secret**. These were automatically generated for you when your app was created.

- **Redirect URL**. This is a location on your app that the OAuth API can redirect a user back to once they have performed a successful authorization request with Backly. This must match the redirect URL that your app was created with and it must be updated if your app's redirect URL is changed.

## Requesting Authorization

First your app should direct a users browser to `http://app.back.ly/oauth/authorize` with the following query string parameters.

- **client_id**: Your App ID.
- **redirect_uri**: Your Redirect URL.
- **response_type**: Set to `code`.

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

- **client_id**: Your App ID.
- **client_secret**: Your App Secret.
- **code**: The Authorization Code returned by the successful authorization request.
- **grant_type**: Set to `authorization_code`.
- **redirect_uri**: Your Redirect URL.

Set your `Content-Type` header according to the format of the data you are sending. Two formats are accepted.

- **URL encoded** (`application/x-www-form-urlencoded`)
- **JSON** (`application/json`)

This request will return a JSON response containing an `access_token` token attribute. This **Access Token** can then be used to make API requests on behalf of the Backly user who authorized your app to do so.

# Endpoints

