### Change Log

This change log covers significant updates and changes to the Beyond REST API.

**2019-01-15**

**New**

Allow user creation without specifying a password.

Add new endpoint [Create variation product](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/products-create-with-variations).

**Update**

Add field `captureWorkflow` to payment method definitions.

**2018-12-18**

**Update**

Add optional field `dependentLocality` to billing and shipping address properties.

Add payment status for prepayment-style payments (e.g. OVERPAID, UNDERPAID). Allow passing the actual amount paid to the [Set payment status with amount](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payments/set-payment-status-with-amount) endpoint (first implementation step).

**2018-11-20**

**New**

Add new endpoints to handle payment methods:
* [Create a payment method from a payment method definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/create-payment-method)
* [Delete a payment method from a payment method definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/delete-payment-method)

**Update**

Add field `paymentNote` to payments.

[Create payment](http://docs.beyondshop.cloud/#_payment_flow) provides an `errorUri` to the payment app.

**2018-11-12**

Add new endpoint [Delete Shipping Address](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-remove-shipping-address).

**2018-11-07**

**New**

Add new endpoint [Delete Payment Method Definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/delete-payment-method-definition).

**Update**

Include possibility to add a payment note upon [creation of a payment](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-create-payment).

**2018-10-30**

**Update**

Rework [Product Attribute Definitions](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/product-attribute-definitions/product-attribute-definitions-list) and [Product Attributes](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/product-attributes-list) to reduce complexity by simplifying object structure.

**2018-10-29**

**New**

Add new endpoints to handle Payment Method Definitions:
* [List Payment Method Definitions](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/list-payment-method-definition)
* [Create Payment Method Definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/create-payment-method-definition)
* [Get Payment Method Definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/get-payment-method-definition)
* [Update Payment Method Definition](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-method-definitions/update-payment-method-definition)

**2018-10-18**

**Update**

Change several paths on [payment signup](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/payment-signup/merchant-account) to comply with a name change grom {paymentIntegration} to {paymentMethodDefinition}.

**2018-09-11**

**Update**

Simplify [creation of product images](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/product-images-create).

**2018-08-28**

**New**

Change [shop resource's body](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-shop-get) by
re-working its structure and content.

Add [shop attributes resource](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-shop-attribute-create), which allows clients to store arbitrary information.

Add [legal resource](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-legal-get).

Add [open](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-shop-open) and
[close](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/shop/merchant-shop-close) shop endpoints.

Add manufacturer suggested retail price, represented with the product
attribute [manufacturerPrice](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/products/product-get).

**2018-08-14**

**Update**

Change [cart details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-create) by adding `mustAcceptTermsAndConditions` property in the payload.

Change [Create order from cart](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-order) endpoint by adding `termsAndConditionsExplicitlyAccepted` property in the payload.

**2018-07-17**

**New**

Add [Change username](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/user-change-username) and [Trigger
email address change](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/change-email-request) user endpoints.

**2018-06-19**

**New**

Add [Refund process support](https://beyond.docs.stoplight.io/payment-solution/payment-solution#refunds) for payment apps.

**2018-06-05**

**New**

Add [Retrieve support access status](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/support-access-status)
endpoint.

**Update**

Change [Enable support access](#resources-enable-support-access) endpoint by removing user details from the response.

Change [List users](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/enable-support-access) and [Show user
details](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/user-get) endpoints by removing support user
rendering.

**2018-05-22**

**Update**

Change [cart's payload](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-get) endpoint by adding `minimumOrderValue` property.

**2018-04-10**

**New**

Add [Replace single line item](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/carts/cart-replace-line-item)
endpoint.

**Update**

Enhance official apps to carry additional configuration data used for
[payment app creation](#resources-official-apps-create).

**2018-03-29**

**New**

Add [Enable support access](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/enable-support-access) and
[Disable support access](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/users/enable-support-access) user endpoints.

**2018-03-13**

**New**

Implement Payment Gateway for [payment
integrations](https://beyond.docs.stoplight.io/payment-solution/payment-solution).

