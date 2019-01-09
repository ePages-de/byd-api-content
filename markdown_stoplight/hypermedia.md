#### Hypermedia

We've applied the HAL ([Hypertext Application
Language](http://stateless.co/hal_specification.html)) format to our
Beyond API to offer a consistent and simple way to create hyperlinks
between API resources. The HAL structure ensures that each resource
contains relational links, and provides a standard identifiable
structure for embedding other resources.

Most responses to a Beyond API call include

-   `links` to URIs (the string we render in our response bodies)

-   `_embedded` properties (mostly used with calls that list a
    collection of resources).

These links include

-   a target (the URI), located at the `href` string

-   a `rel` (the name of the link)

-   optional query parameters.

Use these `_links` to receive further information related to a specific
request and operate on the resource itself. That way there's no need to
compose URIs yourself, or speculate if further related resources exist,
but you can easily navigate from one resource to another. Defaults for
operations or payloads, however, are not provided with these links.

**HAL example**

``` {.json}
{
"_links" : {
   "self" : {
     "href" : "https://yoursandbox.beyondshop.cloud/api/product-management/products/2046e922-cc2c-44fc-9310-c763d5ca6f79"
   },
   "self-localized" : {
     "href" : "https://yoursandbox.beyondshop.cloud/api/product-management/products/2046e922-cc2c-44fc-9310-c763d5ca6f79?locale=en-US"
   },
   "availability" : {
     "href" : "https://yoursandbox.beyondshop.cloud/api/product-management/products/2046e922-cc2c-44fc-9310-c763d5ca6f79/availability"
   },
   "attributes" : {
     "href" : "https://yoursandbox.beyondshop.cloud/api/product-management/products/2046e922-cc2c-44fc-9310-c763d5ca6f79/attributes{?locale}",
     "templated" : true
   },
   "attachments" : {
     "href" : "https://yoursandbox.beyondshop.cloud/api/product-management/products/2046e922-cc2c-44fc-9310-c763d5ca6f79/attachments"
   },
   "images" : {
     "href" : "https://yoursandbox.beyondshop.cloud/api/product-management/products/2046e922-cc2c-44fc-9310-c763d5ca6f79/images"
   },
   "default-image" : {
     "href" : "https://yoursandbox.beyondshop.cloud/api/product-management/products/2046e922-cc2c-44fc-9310-c763d5ca6f79/default-image"
    }
  }
}
```

In many responses, you will find these link relations:

-   `self` shows the current representation of the resource

-   `self-localized`, in addition to `self`, holds the relevant
    localized parameters (mostly used with product-related resources).

You will also come across `templated` attributes (as described in
[RFC-6570](https://tools.ietf.org/html/rfc6570)), as you can see in the
above example. If `templated` is `true`, additional query parameters can
be set. For example, you can set the `{?locale}`, request specific image
dimensions with `{&width,height,upscale}`, or handle paging and sorting
with `{?page,size,sort}`, just to name a few.

