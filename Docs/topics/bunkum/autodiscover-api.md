# AutoDiscover API Documentation

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", and "MAY"
in this documentation are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119).

## Rationale

To verify if a URL points to a custom server and if it is working, Refresher will contact the server.

While this API originated from Refresh, it is intended to be used by any custom server using HTTP.

The AutoDiscover API has three main purposes:

1. Verify that the URL the user has given in patching software is correct.
2. Provide extra information to the patcher on what decisions should be made.
3. Show metadata about the server to the user, to reassure the user that the settings they have chosen are correct.

## Example

Here's an example request to the AutoDiscover API using the `curl` client:

```http
GET /autodiscover HTTP/1.1
Host: localhost:10061
User-Agent: curl/8.3.0
Accept: */*

HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 287
Server: Bunkum
Connection: close
Date: Thu, 12 Oct 2023 00:47:58 GMT

{"version":3,"serverBrand":"LBR Dev (Refresh)","serverDescription":"The primary development instance for Refresh.","url":"https://lbp.littlebigrefresh.com/lbp","bannerImageUrl":"https://github.com/LittleBigRefresh/Branding/blob/main/logos/refresh_type.png?raw=true","usesCustomDigestKey":true}
```

The server MUST reply with JSON data.

The client MAY specify a `titleId` as a query parameter to identify the game in the request:

`GET /autodiscover?titleId=NPUA80662 HTTP/1.1`

If the server chooses to, it MAY change the output of the `url` parameter based on the given `titleId`. For example an LBP3 client may require HTTPS, but other clients may not be able to connect via HTTPS. In this case you would want to change to an http(s) URL for those clients.

The server MUST NOT reject a request that does not include the `titleId` parameter.

## Parameters
`version` refers to the schema version of the AutoDiscover API. This MUST be included in all responses.

The word "optional" below means that the parameter MAY be excluded or left as `null` by the server.

### Version 1
`serverBrand`: A friendly name of the server. For Refresh, it is simply `Refresh`, but you can put anything you want here. Generally it's the same as `lbpEnvVer` for LBP.

`url`: The URL that should be recommended to the client. This is the URL that you or your players will be patching and connecting with.

### Version 2

This version is the same as Version 1, with the following addition:

`usesCustomDigestKey`: An optional boolean, when true it represents that the LBP server will only accept the digest key `CustomServerDigest`. Otherwise, the server is using the default digest key included with the game.

### Version 3

This version is the same as Version 2, with the following additions:

`serverDescription`: An optional friendly description of the server. The server MAY put anything here, but it SHOULD be a short one-sentence string.

`bannerImageUrl`: An optional URL to the image that the client may retrieve. The URL MAY be `null`, however if it is a string it MUST point to a widely-supported image format, either `.png` or `.jp(e)g`.

## Errors

The AutoDiscover protocol in general SHOULD NOT purposefully return any errors, instead the server SHOULD try to correct/disregard information by the client.

For example, if a client sends a `titleId` that points to a game that does not actually exist, the server SHOULD disregard the `titleId` entirely and pick a generic URL to return.

Clients MUST NOT stop AutoDiscover if the version they are expecting differs from the server; AutoDiscover is meant to be forwards-and-backwards compatible. The client MAY, however, simply warn the user.

## Implementations

So far, there are only a few known implementations of AutoDiscover.

### Servers

- [Bunkum.AutoDiscover](https://www.nuget.org/packages/Bunkum.AutoDiscover), a service for Bunkum to implement the protocol.
- Refresh (via `Bunkum.AutoDiscover`)
- SoundShapesServer (via `Bunkum.AutoDiscover`)

### Clients

- [Refresher](https://github.com/LittleBigRefresh/Refresher)
