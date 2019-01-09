#### HTTP Verbs

The following HTTP verbs are used throughout the API:

| Verb                  | CRUD                  | Description           |
|-----------------------|-----------------------|-----------------------|
| `GET`                 | Read                  | Used to read/retrieve the information of a resource. A successful request returns the status code `200 (OK)` with a JSON  representation. In  case of an error, usually a `404 (Not Found)` or `400 (Bad Request)` is returned.  |
| `POST`                | Create                | Used to create a resource. A successful request returns a `201 (Created)`.       |
| `PATCH`               | Update/Modify         | Used to apply changes to a resource. A successful update either returns a `200 (OK)` with a JSON representation or a `204 (No Content)` if not returning any content in the body. |
| `PUT`                 | Update/Replace        | Used to update or replace resource information. A successful update returns a `200 (OK)` with a JSON representation. |
| `DELETE`              | Delete                | Used to delete an existing resource. A successful request returns a `204 (No Content)`.  |

#### API Operations

To build a REST call, combine this:

-   HTTP method

-   full URI to the resource

-   HTTP headers (if required)

-   JSON body (if required)

For example, this request creates a product:

``` {.bash}
$ curl 'https://yoursandbox.beyondshop.cloud/api/products/management/products'
-i -X POST
-H 'Content-Type: application/json'
-H 'Authorization: < Access Token >'
-d '{
  "name": "New product",
  "salesPrice" : {
    "taxModel" : "GROSS",
        "currency" : "EUR",
    "amount" : 99.90
},
  "description": "This is a brand new product."
}'
```

