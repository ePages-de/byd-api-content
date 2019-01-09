#### Request headers

Public API requests are authenticated by the following request headers.
Not all resources require `Accept` and `Content-Type`, but some do. To
ensure that all your calls are processed successfully, we encourage you
to always include these headers.

| Header                | Type                  | Description       |
|---|---|---|
| `Authorization`       | String                | The OAuth 2.0 bearer token to secure the request for accessing the API. Example (shortened): `Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0ZW5hbnRJZCI6MTQzOCwidXNlcl9uYW1lIjoidXNlciI`  |
| `Accept`              | String                | The media type acceptable for the response. Can be one of `application/json` or `application/hal|json`. |
| `Content-Type`        | String                | Specifies the Media Type of the request body. Can be one of `application/json`, `application/hal|json`, `application/json-patch|json` or `text/uri-list`.  |
| `If-Match`            | String                | Makes a request conditional and returns the requested resource only if it matches the `ETag` listed in this header. The `ETag` has to be set in quotes, otherwise a Bad Request will be returned.|
| `If-None-Match`       | String                | Makes a request conditional and returns the requested resource only if it doesn't match the `ETag` listed in this header. The `ETag` has to be set in quotes, otherwise a Bad Request will be returned.   |

#### Response headers

A successfully sent request is followed by an HTTP response. The below
table contains the response headers that can be returned by our server.
In addition, we issue a number of Spring Security response headers, that
are not specifically listed below, such as `Cache Control`,
`Strict-Transport-Security`, `X-Content-Type-Options`, `Expires`, and
more. You can easily look them up in the [Spring Security
documentation](https://docs.spring.io/spring-security/site/docs/current/reference/html/web-app-security.html#headers).

| Header                | Type                  | Description           |
|-----------------------|-----------------------|-----------------------|
| `Date`                | String                | The date and time the response was sent. In \"HTTP-date\" format as defined by [RFC 7231](https://tools.ietf.org/html/rfc7231). Example: `Fri, 04 Aug 2017 06: 54:30 GMT`|
| `Content-Type`        | String                | The media type of this content, e.g. `application/hal|json;charset=UTF-8`, `` application/json;charset=UTF-8, or `text/plain ``.   |
| `Transfer-Encoding`   | String                | The form of encoding used to safely transfer the entity to the user, e.g. `chunked`. |
| `Connection`          | String                | Controls whether or not the network connection stays open after the current transaction finishes. Can be `keep alive` or `close`. |
| `Location`            | String                | The direct URL to access a resource. Appears whenever a new resource has been created. Example: `https://yoursandbox.beyondshop.cloud/api/product-management/products/98aed1aa-72dc-4b9e-ac18-c9daa57cb245`   |
| `X-Request-Time`      | String                | The time in seconds for processing the request. Example: `0.053`.  |
| `X-B3-TraceId`        | String                | [OpenZipkin TraceId](https://github.com/openzipkin/b3-propagation#traceid)          |
| `Last-Modified`       | String                | The date and time the resource was last modified. In  \"HTTP-date\" format as defined by RFC 7231. Example: `Tue, 23 May 2017 09: 13:48 GMT`.  |
| `ETag`                | String                | Identifies a specific version of a resource. Allows more efficient caches as the server does not need to send the full response if the content did not change. Example: `"2"`.  |