# Create `POST /links`

Create a new link.

## Parameters

| Name | Type | Description |
|---|---|---|
| advert | String | The identifier code of the advert you wish to display with this link. |
| url | URL | The URL you wish to share. |

## Example Request

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

## Example Responses

```json
HTTP/1.1 200 OK
...

{
  "created_at": "2015-01-01 12:00:00",
  "url": "http://example.com",
  "title": "Example Domain",
  "description": "This is an example website.",
  "image": "http://example.com/image.jpg",
  "code": "abc123",
  "short_url": "http://back.ly/abc123",
  "url_host": "example.com"
}
```
