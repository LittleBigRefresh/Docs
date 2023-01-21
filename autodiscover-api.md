# Autodiscover API Documentation

## Rationale

To verify if a URL points to a custom server and if it is working, Refresher will contact the server. (well soon, anyways)

While this API originated from Refresh, it is intended to be used by any LBP custom server thus this document.

The Autodiscover API has two main purposes:

1. Verify that the URL the user has given in patching software is correct.
2. Provide extra information on how the patcher should work, and show metadata about the server to the user.

## Example

Here's an example request to the Autodiscover API:

```http
GET /autodiscover HTTP/1.1
Host: localhost:10061
User-Agent: curl/7.87.0
Accept: */*

HTTP/1.1 200 OK
Server: Bunkum
X-Digest-B: a829b69a1aeb1d74bf10572b9527f18158c77226
Content-Type: text/json
X-Digest-A: 5122a3ea060b9c4753a39a80aad659be221a5ef2
Date: Sat, 21 Jan 2023 09:21:57 GMT
Transfer-Encoding: chunked

{"version":1,"serverBrand":"Refresh","url":"http://127.0.0.1:10061"}
```

The server MUST reply with JSON data.

The client can also specify a titleId in the request:

`GET /autodiscover?titleId=NPUA80662 HTTP/1.1`

If the server wants to, it can change the output of the `url` parameter based on the given titleId. For example a LBP3 client may require HTTPS, but other clients may not be able to connect via HTTPS. In this case you would want to change to a http(s) URL for those clients.

## Parameters
`version` refers to the schema version of the Autodiscover API. This is not a server version.

### Version 1
`serverBrand`: A friendly name of the server. For Refresh it is simply `Refresh`, but you can put anything you want here. Generally it's the same as `lbpEnvVer`.

`url`: The URL that should be recommended to the client. This is the URL that you or your players will be patching and connecting with.