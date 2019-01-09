## Pagination

When making calls to our Beyond API you will be returned lots of
results. A lot more than you might want to handle with a single request.
That's why we paginate the results to ensure the responses are easier
for you to manage.

Even though we've built in a default limit, we recommend to use the
following query parameters to get more streamlined results.

#### Query parameters 

| Parameter             | Type                  | Description           |
|-----------------------|-----------------------|-----------------------|
| `page`                | number                | The page of results to be returned (indexed: `0`, default: `0`).    |
| `size`                | number                | The maximum number of results per page (default: `20`). |
| `sort`                | string                | The sort order of results by `propertyname`, optionally followed by `,ASC` for ascending or `,DESC` for descending sort order.   |



**Example request**

``` {.bash}
$ curl 'https://yoursandbox.beyondshop.cloud/api/products/management/products?page=1&sort=salesPrice,ASC&size=2'
-i -X GET
-H 'Content-Type: application/hal+json'
-H 'Accept: application/hal+json'
-H 'Authorization: < Access Token >'
```

#### Response parameters 

Response pagination is represented with the following JSON fields inside
the response body.


| Path                  | Type                  | Description           |
|-----------------------|-----------------------|-----------------------|
| `page.size`           | number                | The requested number of results per page. |
| `page.totalElements`  | number                | The total number of elements available.   |
| `page.totalPages`     | number                | The total number of pages available.  |
| `page.number`         | number                | The number of the current page. The first page is indexed with `0`.    |

**Example response**

``` {.http}
HTTP/1.1 200 OK
Content-Type: application/hal|json;charset=UTF-8

{
  "_embedded" : {
    "products" : [ {
      "_id" : "a7e2c07a-390e-42c5-8c8d-ac53569eda7d",
      "sku" : "1006",
      "name" : "Black Wooden Table",
      "salesPrice" : {
        "taxModel" : "GROSS",
        "currency" : "EUR",
        "amount" : 52.76,
        "derivedPrice" : {
          "taxModel" : "NET",
          "currency" : "EUR",
          "amount" : 44.33613,
          "taxRate" : 0.19
        }
      },
      "listPrice" : {
        "taxModel" : "GROSS",
        "currency" : "EUR",
        "amount" : 79.85,
        "derivedPrice" : {
          "taxModel" : "NET",
          "currency" : "EUR",
          "amount" : 67.10084,
          "taxRate" : 0.19
        }
      },
      "_embedded" : {
        "availability" : {
          "availabilityState" : "IN_STOCK",
          "availableStock" : null,
          "stockThreshold" : null,
          "_links" : {
            "self" : {
              "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/a7e2c07a-390e-42c5-8c8d-ac53569eda7d/availability"
            }
          }
        }
      },
      "_links" : {
        "self" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/a7e2c07a-390e-42c5-8c8d-ac53569eda7d"
        },
        "self-localized" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/a7e2c07a-390e-42c5-8c8d-ac53569eda7d?locale=en-US"
        },
        "product" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/a7e2c07a-390e-42c5-8c8d-ac53569eda7d{?locale}",
          "templated" : true
        },
        "attributes" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/a7e2c07a-390e-42c5-8c8d-ac53569eda7d/attributes{?locale}",
          "templated" : true
        },
        "attachments" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/a7e2c07a-390e-42c5-8c8d-ac53569eda7d/attachments"
        },
        "images" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/a7e2c07a-390e-42c5-8c8d-ac53569eda7d/images"
        },
        "default-image" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/a7e2c07a-390e-42c5-8c8d-ac53569eda7d/default-image"
        },
        "default-image-data" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/core-storage/images/black-wooden-table.jpg?hash=f639d991b0e8908f6389b0ffa23393aab2ca9079{&width,height,upscale}",
          "templated" : true
        },
        "default-image-metadata" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/core-storage/images/black-wooden-table.jpg?hash=f639d991b0e8908f6389b0ffa23393aab2ca9079&download=no"
        }
      }
    }, {
      "_id" : "d2f63d54-41c6-4fb4-a467-c8388a693525",
      "sku" : "1005",
      "name" : "Retro Pouffe",
      "salesPrice" : {
        "taxModel" : "GROSS",
        "currency" : "EUR",
        "amount" : 159,
        "derivedPrice" : {
          "taxModel" : "NET",
          "currency" : "EUR",
          "amount" : 133.61345,
          "taxRate" : 0.19
        }
      },
      "listPrice" : null,
      "_embedded" : {
        "availability" : {
          "availabilityState" : "IN_STOCK",
          "availableStock" : null,
          "stockThreshold" : null,
          "_links" : {
            "self" : {
              "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/d2f63d54-41c6-4fb4-a467-c8388a693525/availability"
            }
          }
        }
      },
      "_links" : {
        "self" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/d2f63d54-41c6-4fb4-a467-c8388a693525"
        },
        "self-localized" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/d2f63d54-41c6-4fb4-a467-c8388a693525?locale=en-US"
        },
        "product" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/d2f63d54-41c6-4fb4-a467-c8388a693525{?locale}",
          "templated" : true
        },
        "attributes" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/d2f63d54-41c6-4fb4-a467-c8388a693525/attributes{?locale}",
          "templated" : true
        },
        "attachments" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/d2f63d54-41c6-4fb4-a467-c8388a693525/attachments"
        },
        "images" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/d2f63d54-41c6-4fb4-a467-c8388a693525/images"
        },
        "default-image" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/d2f63d54-41c6-4fb4-a467-c8388a693525/default-image"
        },
        "default-image-data" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/core-storage/images/retro-pouffe.jpg?hash=89489738342f8b407a46fe8ab70cdd5decf84667{&width,height,upscale}",
          "templated" : true
        },
        "default-image-metadata" : {
          "href" : "https://yoursandbox.beyondshop.cloud/api/core-storage/images/retro-pouffe.jpg?hash=89489738342f8b407a46fe8ab70cdd5decf84667&download=no"
        }
      }
    } ]
  },
  "_links" : {
    "first" : {
      "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products?page=0&size=2&sort=salesPrice,asc"
    },
    "prev" : {
      "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products?page=0&size=2&sort=salesPrice,asc"
    },
    "self" : {
      "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products?page=1&size=2&sort=salesPrice,asc"
    },
    "next" : {
      "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products?page=2&size=2&sort=salesPrice,asc"
    },
    "last" : {
      "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products?page=2&size=2&sort=salesPrice,asc"
    },
    "profile" : {
      "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/profile/products"
    },
    "search" : {
      "href" : "https://yoursandbox.beyondshop.cloud/api/products/management/products/search"
    }
  },
  "page" : {
    "size" : 2,
    "totalElements" : 6,
    "totalPages" : 3,
    "number" : 1
  }
```

