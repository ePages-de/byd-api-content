### Change Log

This change log covers significant updates and changes to the Beyond REST API.

**2019-05-09**

**Update**

* Added `productIdentifiers` property to [Show variation details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/variation-get) and [Update variation partially](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/variation-patch-json).

* Added `workflow` property to [Show payment method details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-methods/payment-method-get).

* Added query parameter `fileName` and header `Content-Type` to request parameters of [Add product image](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/product-images-create).

* Added `bankName`, `iban`, `bic`, `bankAccount`, and `bankIdentifier` properties to *legal* resource.

**2019-04-23**

**New**

Add *Events* section. This section explains how applications can receive information about customer actions in ePages online shops.

**2019-04-17**

**New**

* [Create script tag](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/script-tags/script-tags-create)

* [List script tags](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/script-tags/script-tags-get-all)

* [Show script tag details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/script-tags/script-tags-get) 

* [Update script tag](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/script-tags/script-tags-update)

* [Delete script tag](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/script-tags/script-tags-delete)

* [Create newsletter target](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/newsletter-target/newsletter-target-create)

* [Show newsletter target details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/newsletter-target/newsletter-target-get)

* [Update newsletter target](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/newsletter-target/newsletter-target-update)

* [Delete newsletter target](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/newsletter-target/newsletter-target-delete)

**2019-03-08**

**Deprecate**

* Removed endpoint *List products by category*.

**2019-03-06**

**Update**

* Added `externalPaymentUri` and `externalPaymentId` to *Set a payment status*.

**2019-02-28**

**Update**

* Added `externalPaymentUri` and `externalPaymentId` to [Show order details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/orders/order-get).

**2019-02-26**

**Update**

* Added `embeddedApprovalUri` to [Create payment](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-create-payment) and [Create payment and order](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-create-payment-and-order).

**2019-02-22**

**New**

* [Show variation product details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/product-view/find-variation-product-by-id)

* [Show variation details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/variation-get)

**2019-01-15**

**New**

* We now allow user creation without specifying a password.

* [Create variation product](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/products-create-with-variations)

**Update**

* Added field `captureWorkflow` to payment method definitions.

**2018-12-18**

**Update**

* Added optional field `dependentLocality` to billing and shipping address properties.

* Added payment status for prepayment-style payments (e.g. OVERPAID, UNDERPAID). Allow passing the actual amount paid to the [Set payment status with amount](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payments/set-payment-status-with-amount) endpoint (first implementation step).

**2018-11-20**

**New**

* [Create a payment method from a payment method definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/create-payment-method)

* [Delete a payment method from a payment method definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/delete-payment-method)

**Update**

* Added  `paymentNote`  poperty to payments.

* [Create payment](http://docs.beyondshop.cloud/#_payment_flow) provides an `errorUri` to the payment app.

**2018-11-12**

**New**

* [Delete Shipping Address](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-remove-shipping-address)

**2018-11-07**

**New**

* [Delete Payment Method Definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/delete-payment-method-definition)

**Update**

* Included possibility to add a payment note upon [creation of a payment](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-create-payment).

**2018-10-30**

**Update**

* Reworked [Product Attribute Definitions](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/product-attribute-definitions/product-attribute-definitions-list) and [Product Attributes](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/product-attributes-list) to reduce complexity by simplifying object structure.

**2018-10-29**

**New**

* [List Payment Method Definitions](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/list-payment-method-definition)

* [Create Payment Method Definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/create-payment-method-definition)

* [Get Payment Method Definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/get-payment-method-definition)

* [Update Payment Method Definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/update-payment-method-definition)

**2018-10-18**

**Update**

* Changed several paths on [payment signup](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-signup/merchant-account) to comply with a name change grom {paymentIntegration} to {paymentMethodDefinition}.

**2018-09-11**

**Update**

* Simplify [creation of product images](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/product-images-create).

**2018-08-28**

**New**

* [Create shop attribute](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-shop-attribute-create)

* [Show legal details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-legal-get)

* [Open shop](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-shop-open)

* [Close shop](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-shop-close)

* Added `manufacturerPrice` in the [product details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/product-view/product-view-find-by-id) payload.

**Update**

* Reworked structure and content of the [shop resource's body](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-shop-get).


**2018-08-14**

**Update**

* Added `mustAcceptTermsAndConditions` property in the [cart details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-create) payload.

* Added `termsAndConditionsExplicitlyAccepted` property in the [Create order from cart](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-order) payload.

**2018-07-17**

**New**

* [Change username](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/user-change-username) 
* [Trigger email address change](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/change-email-request)

**2018-06-19**

**New**

* Added [Refund process support](http://docs.beyondshop.cloud/#_refunds) for payment apps.

**2018-06-05**

**New**

* [Retrieve support access status](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/support-access-status)

**Update**

* Removed user details from the [Enable support access](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/enable-support-access) response.

* Removed support user rendering from [List users](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/enable-support-access) and [Show user details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/user-get) endpoints.

**2018-05-22**

**Update**

* Added `minimumOrderValue` property to [cart's payload](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-get).

**2018-04-10**

**New**

* [Replace single line item](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-replace-line-item)

**Update**

* Enhanced official apps to carry additional configuration data used for payment app creation.

**2018-03-29**

**New**

* [Enable support access](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/enable-support-access) 
* [Disable support access](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/enable-support-access)

**2018-03-13**

**New**

* Implemented Payment Gateway for [payment integrations](https://beyond.docs.stoplight.io/payment-solution/payment-solution).

