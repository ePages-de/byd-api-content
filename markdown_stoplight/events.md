### Events

Events can be triggered when a customer executes a specific action in an ePages online shop.
This can be e.g. a customer opening a new page of a shop, or adding a product to the cart.
If you have implemented an event in your application, you will be informed about related actions and can react accordingly.
Furthermore, your app will receive information related to the event, such as the current page a user is on.

These events are available:

| Event                | Type                  | Description       |
|---|---|---|
| `pageview`       | string                | Is triggered when the customer opens or reloads a page. Informs about the path of the page.  |
| `product`        | immutable.js object   | Is triggered when the customer selects a product. Informs about the respective product.|
| `cart:add`        | immutable.js object   | Is triggered when the customer adds a product to the cart. Informs about the current state of the cart, e.g. included items. This event isn’t triggered if the customer makes changes in the cart itself, e.g. changing the amount of an item.|

#### Pageview event

In order to make use of this event, you need to add the following snippet to your code:

``` {.javascript}
if (window.eComEventTarget) {
  window.eComEventTarget.addEventListener('pageview', function (event) {
    console.log('pageview url:', event.detail.url)
  })
}
```

You’ll receive something like this:

``` {.bash}
pageview url: /i/about-us
```

#### Product event

In order to make use of this event, you need to add the following snippet to your code:

``` {.javascript}
if (window.eComEventTarget) {
  window.eComEventTarget.addEventListener('product', function (event) {
    console.log('product:', event.detail.product.toJS())
  })
}
```

You’ll receive something like this:

``` {.bash}
availabilityText: "Available"
available: true
basePrice: {refQuantity: {…}, refPrice: {…}, formatted: "1 m³ = £0,12", quantity: {…}}
conditionMicrodata: "ConditionNew"
customAttributes: null
deliveryPeriod: "2-3"
deliveryPeriodUnit: "DAYS"
description: null
energyLabel: null
energyLabelSourceFile: null
gtin: null
hasCrossSelling: false
hasStockLevel: true
hasVariations: false
href: "/p/homemade-cherry-jam"
image: null
isVariationMaster: false
isVariationProduct: false
isVisible: true
links: (2) [{…}, {…}]
lowestPrice: null
mainCategoryId: "5954B711-E377-2A90-C400-D5809AB3F62B"
manufacturer: null
manufacturerPrice: null
metaDescription: ""
name: "Homemade Cherry Jam"
onStock: true
outOfStock: false
price: {taxType: "NET", formatted: "£40,00", amount: 40, currency: "GBP"}
productDataSheet: null
productId: "5954B706-E701-F357-A52D-D5809AB3F606"
productVariationSelection: null
productVariationValues: null
sku: "1007"
slideshow: [{…}, {…}, {…}, {…}]
slug: "homemade-cherry-jam"
stockLevelClass: "little"
stockLevelMicrodata: "InStock"
title: "Homemade Cherry Jam"
variationMaster: null
variations: null
vatNote: "components.productComponent.priceExclusiveVat"
warnStock: false
```

#### Cart:add event

In order to make use of this event, you need to add the following snippet to your code:

``` {.javascript}
if (window.eComEventTarget) {
  window.eComEventTarget.addEventListener('cart:add', function (event) {
    console.log('new cart data:', event.detail.cart)
  })
}
```

You'll receive something like this:

``` {.bash}
billingAddress: null
canHaveCoupon: true
cartId: "5C06901F-150C-3D9B-B144-D509AB34875"
checkoutButtons: []
checkoutState: null
checkoutUrl: "/checkout"
coupon: null
couponCampaign: null
grandAmount: "£76,01"
grandAmountNote: "components.productComponent.priceExclusiveVat"
minimumOrderValue: null
mustAcceptTermsAndConditions: true
netAmount: "£76,01"
paymentLineItem: {lineItemPrice: {…}, paymentMethod: {…}}
pickupToken: "ZjM3M2Q2YmY4jkFjYWRlZTIzZTBlYzQwMDU4MjYzZjYwNDNhZGY0NWM1N2JiNjZhMGI0YWNlNWFkYzU4ZTQ3OF8xNTQzOTM5MjIx"
productLineItems: [{…}, {…}, {…}]
registerSessionUrl: ""
shippingAddress: null
shippingLineItem: {lineItemPrice: {…}, shippingMethod: {…}}
subAmount: "£76,01"
taxType: "NET"
taxes: [{…}]
totalNumberOfItems: 3
_links: null
```