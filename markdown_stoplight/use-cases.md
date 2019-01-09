# Use cases
You plan an integration with ePages? That’s great! Here are some use cases we can think of:

### Integrate a Payment Solution

Enable merchants to offer more payment options by integrating your own payment solution. Create your own payment method so that merchants can later activate it for their shops. This way, a merchant's customers will find a more diverse set of possibilities to pay for their purchase.</br>

For detailed instructions, see our [Integrate a payment solution tutorial](http://docs.beyondshop.cloud/#_integrate_a_payment_solution).

### Social Commerce

Enable merchants to use social media platforms like Facebook or blogging platforms to showcase their products. Put together a custom catalog and redirect customers directly to a shop. This way, a merchant can advertise with just a few clicks.</br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET` |[/products](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/products-list)
|`GET`| [/categories](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/categories/categories-list)
|`POST` |[/carts](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-create)
|`PUT` |[/carts/{cartId}/line-items/{lineItemId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-replace-line-item)
|`POST` |[/carts/{cartId}/order](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-order)
|`GET`|[/legal-content](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/legal-content/merchant-legal-content-list) 

### Shipping

Enable merchants to print shipping labels, automate parts of their shipping process, and track the status of orders, or implement notifications. Aggregate address and weight information to generate ready-made shipping labels or help a merchant spot issues with orders that have been pending for too long. This way, you can facilitate the shipping of goods for a merchant.</br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET`|[/orders](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/orders-list)
|`GET`|[/products/{productId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-get)
|`GET`|[/order/{orderId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/order-get)
|`GET`|[/orders/{orderId}/processes/shippings](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/get-shipping-processes) |`GET`|[/orders/{orderId}/processes/shippings/{shippingProcessId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/get-shipping-process)

### Accounting

Enable merchants to track payments more easily, spot unpaid orders, or quickly evaluate the performance of their shop. You can offer notifications for payments that have been pending for too long or monitor single orders. Aggregating the turnover from orders in a specific timeframe, separately displaying net and gross orders and more can help the merchant extract relevant accounting information more comfortably.</br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET`|[/orders](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/orders-list) 
|`GET`|[/order/{orderId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/order-get)
|`GET`|[/orders/{orderId}/processes](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/get-order-processes)
|`GET`|[/orders/{orderId}/order-note](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/order-note-update)

### Content Optimization and Marketing

Enable merchants to give their product descriptions and collections an SEO check, automate parts of the marketing, or help them with translation. Improve product names and descriptions and immediately update a shop. Rearrange and create collections for a better UX or for seasonal offers. This way, simplify large parts of marketing for merchants and help them stand out in search engine results and advertising campaigns.</br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET`|[/products](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/products-list)
|`PATCH`|[/products/{productId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-patch-json)
|`GET`|[/products/{productId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-get)
|`GET`|[/categories](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/categories/categories-list)
|`POST`|[/categories](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/categories/category-create)
|`PUT`|[/categories/{categoryId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/categories/category-put)

### Legal Service

Enable automatic updates and notifications to everything relating to legal content. Retrieve the legal content that merchants display to their customers, give it a check and, if you have the merchant's consent, write an improved version of the texts back to the shop. You can also create templates and update certain variables at regular intervals. This way, a shop's terms and conditions, imprint etc. can be handled more easily and kept up to date. </br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET`|[/legal-content](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/legal-content/merchant-legal-content-list)
|`PUT`|[/legal-content/{name}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/legal-content/merchant-legal-content-edit)

### Point of Sale (POS)/Marketplace

Enable automatic stock tracking and easy stock management for merchants. Retrieve the products a shop offers at regular intervals to keep an up-to-date list. Check and update stock levels on every purchase. Notify a merchant if supply runs low or make suggests for reordering or producing more. This way, you help a merchant avoid revenue loss due to insufficient stock levels and can even help them optimize the amounts they'd like to keep in store.</br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET`|[/products](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/products-list)
|`GET`|[/products/{productId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-get)
|`GET`|[/products/{productId}/availability](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-availability-get)
|`PATCH`|[/products/{productId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-patch-json) 
|`POST`|[/products/{productId}/availability/adjust-available-stock](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-availability-adjust-available-stock)

### Sales Analytics

Enable custom analytics that give merchants the full picture of how well certain parts of their shop are performing. Aggregate information from orders on products to generate best-seller lists, generate graphs of a shop's performance through time or use postal codes to see what regions a shop is most popular in. This way, you can present data in a more approachable form to a merchant and thus help them evaluate advertising campaigns, reconsider their range of products, or plan expansions.</br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET`|[/products](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/products-list) 
|`GET`|[/orders](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/orders-list)
|`GET`|[/categories](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/categories/categories-list)

### Image Service

Enable immediate editing of product images, or link a shop up with image sites. You can offer filtering capabilities and put the edited pictures back into the shop, offer insertion of new images from the app, or create whole slideshows and collages from the available product images. You can even have your app integrate with image sites like Instagram and give the merchant the possibility to bring images over to their shop, or reversely get product images out on different platforms. This way, you can make modeling the visual appearance of their shop easier for merchants and help them with all task revolving the presentation of their products.</br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET`|[/products](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/products-list) 
|`GET`|[/product/{productId}/images](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-images-list)
|`POST`|[/products/{productId}/images](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-images-create)
|`DELETE`|[/products/{productId}/images/{imageId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-image-delete) 

### Enterprise Management Systems (EMS)

Enable a comprehensive look at a shop's performance and all related workflows by providing a complete system. Add and delete products or optimize product descriptions. Give an even more detailed insight by retrieving orders, calculating turnover, or notifying merchants about unpaid orders. Stock management and customer support can just as well be part of the system. This way, parts of the business workflows can be automated, the merchant can be kept up to date about the performance of the shop, and shop management as a whole can be facilitated.</br>

A few of the endpoints to achieve this:

| HTTP Verb | Endpoint
|---|---
|`GET`|[/products](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/products-list)
|`GET`|[/products/{productId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-get)
|`POST`|[/products](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/products-create) 
|`DELETE`|[/products/{productId}](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/products/product-delete)
|`GET`|[/orders](https://beyond-rest-api.docs.stoplight.io/beyond-rest-api/api-reference/orders/orders-list)