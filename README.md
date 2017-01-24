# Introduction

Hello World!

# Authorisation (via OAuth)

## Redirecting For Authorization

Once a client has been created, developers may use their client ID and secret to request an authorization code and access token.

First, your app should direct your users to http://app.back.ly/oauth/authorize with the following parameters.

| Parameter | Description | Required? |
---------------------------------------
| client_id | Your application's ID | Yes |
| redirect_uri | The URL your users should be redirected back to | No |
| response_type | Must be set to 'code' for this part of the authorisation process | Yes |

For example: http://app.back.ly/oauth/authorize?client_id=123&redirect_uri=http://my.app/oauth/callback&response_type=code

# Endpoints
