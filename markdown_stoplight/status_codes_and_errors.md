#### HTTP status codes

The Beyond API uses the following standard HTTP status codes to indicate
success or failure of a request.


| Status code | Description |
|-------------|-------------|
| `200 OK` | Standard response for a successful HTTP request. |
| `201 Created` | A new resource has been created successfully, usually via `POST` operation. The URI of the new resource is available in the `Location` header of the response. |
| `202 Accepted` | The service successfully accepted the request, but further processing is required. |
| `204 No Content` | A successful request, e.g. for `PUT`, `PATCH`, and `DELETE` operations, though the response does not contain any data. |
| `301 Moved Permanently` | The resource is not longer available at the requested path. Future requests have to be directed to the given URI shown in the `Location` header. |
| `400 Bad Request` | The request could not be validated. The response body includes an error message providing further information. |
| `401 Unauthorized` | The request requires valid authentication. The response body includes an error message providing further information. |
| `403 Forbidden` | The request is valid, but the server refuses action. Permissions might be required to access the resource. |
| `404 Not Found` | The requested resource or item could not be found, but may be available in future, e.g. a product has been requested, that is not available. |
| `405 Method Not Allowed` | The used request method is not supported by that resource, e.g. using a `POST` on a resource that requires a `GET`. |
| `406 Not Acceptable` | The content negotiation between client and server failed. The server could not process the requested data set in the `Accept` header. |
| `409 Conflict` | The request could not be completed due to a conflict with the current state of the target resource. |
| `415 Unsupported Media Type` | The requested media type is not supported by the server or resource, e.g. the request includes an `application/json` but the server expects a `text/uri-list`. |
| `500 Server Error` | A generic error message that is given, when an unexpected condition was encountered and a no more specific message is suitable. |

#### Error responses

Whenever an error response (HTTP 4xx status code rage, except for
validation errors) is returned, the body contains a JSON object with
additional details and the following structure:

| Path                  | Type                  | Description           |
|-----------------------|-----------------------|-----------------------|
| `errorId`             | string                | The unique identifier of the error. |
| `details`             | object                | The context data to act upon the error. The content is dynamic and the object can be empty.  |
| `message`             | string                | A human-readable message. |
| `traceId`             | string                | The unique identifier of the failing request.  |


**Example response**

``` {.json}
{
  "errorId": "resource-not-found",
  "details": {
    "path" : "/categories/1234567a-8bc9-123d-e456-7f891g23456h"
  },
  "message": "Resource not found!",
  "traceId": "a12345b67891234c"
}
```

#### Common error Ids

| Error Id              | HTTP status code      | Description           |
|-----------------------|-----------------------|-----------------------|
| `conversion-failed`   | `400 Bad Request`     | A value could not be converted to its target format. |
| `data-access-error`   | `500 Internal Server Error`  | An unexpected error occurred in the data access layer. |
| `http-message-not-readable`    | `400 Bad Request`     | The JSON payload could not be deserialized.   |
| `illegal-argument`    | `400 Bad Request`     | The JSON input contained illegal values. |
| `integrity-constraint-violation`  | `409 Conflict`        | A unique constraint on the database violated, e.g. a product SKU within a shop has to be unique. An attempt to create a new product with an SKU already assigned to an existing product will cause this error.  |
| `internal-error`      | `500 Internal Server Error`  | An unknown error occurred. |
| `optimistic-locking-failure` | `409 Conflict`        | The update of the object failed because it has been changed in the meantime.   |
| `resource-not-found`  | `404 Not Found`       | The requested resource could not be found. |

#### Validation errors

Validation errors can only appear with the HTTP status code 400 and have
a complex `details` object that provides more comprehensive information
about the error.


| Path | Type | Description |
|---|---|--- |
| `entity` | string | The name of the resource or object type where this error occurred. |
| `property` | string | The property name this validation error applies to. Is `null` for object level validation errors. |
| `invalidValue` | dynamic | The specific value that is invalid. Is `null` for object level validation errors. |
| `message` | string | A human-readable message. |

**Example response**

``` {.json}
{
 "errorId" : "input-validation-failed",
 "details" : {
 "validationErrors" : [ {
 "entity" : "Shop",
 "property" : "defaultServiceableCountry",
 "invalidValue" : "EU",
 "message" : "Country code must be officially assigned. See ISO 3166-1 Alpha-2"
 }, {
 "entity" : "Shop",
 "property" : "serviceableCountries",
 "invalidValue" : [ "EU" ],
 "message" : "Each country code must be officially assigned. See ISO 3166-1 Alpha-2"
 } ]
 },
 "message" : "Input validation failed",
 "traceId" : "d0f4d57b-9a94-49e0-ae2d-d57047e9a1f8"
}
```

