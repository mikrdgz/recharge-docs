# Overview

The Recharge integration with BigCommerce works out-of-the-box and only requires you to configure general store settings. However, you have the option to to customize the Storefront, Checkout and Customer Portal if desired. 

## Prerequisites
You should configure your ReCharge store settings before using the BigCommerce integration. See [Other Settings](https://support.rechargepayments.com/hc/en-us/categories/360000578494-Other-Settings) in the Help Center for details.

Ensure that the following settings are configured in ReCharge:
- Tax
- Shipping
- Payments
- Products
- Checkout Settings
- Customer Portal Settings

## Installing the BigCommerce integration

1. Create a V2/V3 [BigCommerce API Token](https://support.bigcommerce.com/s/article/Store-API-Accounts#creating) and select the following scope permissions:

|Scope|Permission|
|-|-|
|Content|Modify|
|Checkout Content|Modify|
|Customers|Modify|
|Customer Login|Login|
|Information and Settings|Read Only|
|Marketing|Modify|
|Orders|Modify|
|Orders Transactions|None|
|Create Payments|None|
|Get Payment Methods|None|
|Products|Modify|
|Themes|Modify|
|Carts|Modify|
|Checkouts|Modify|
|Sites and Routes|Read Only|
|Channel Settings|None|
|Channel Listings|None|
|Storefront API Tokens|Manage|
|Storefront API Customer Impersonation Tokens|Manage|

2. [Contact ReCharge](https://support.rechargepayments.com/hc/en-us/requests/new) to get your ReCharge store connected with your BigCommerce store.

3. You should configure [tax settings in BigCommerce](https://support.bigcommerce.com/s/article/Managing-Currencies#display-v-transactional) to reflect the prices you want to show on ReCharge subscription products.

4. Install ReCharge CDN script provided in the [BigCommerce Script Manager](https://support.bigcommerce.com/s/article/Using-Script-Manager)


## Limitations
The following features are either unsupported or have limited functionality:
* Discounts and coupons are only redeemable during checkout and recurring orders if created within ReCharge
* [BigCommerce modifiers](https://support.bigcommerce.com/s/article/Product-Options-v3#smo) and customer input values
* Different frequency of same product
* Certain BigCommerce themes
* Inventory management
* High volume stores that are not on a [BigCommerce Enterprise plan](https://support.bigcommerce.com/s/article/Pricing) (due to potential rate limit concerns). Those with multiple apps are particularly at risk of going over these limits.
* BigCommerce payment processors PayPal, AmazonPay and GooglePay. Payment displays in the cart and precedes the checkout handoff. Set up these [payment processors in ReCharge](https://support.rechargepayments.com/hc/en-us/articles/360008683494-Payment-processors).
* Displaying prices inclusive/exclusive of tax differently on product and cart pages
* Synchronized cancellations and order statuses across Recharge to BigCommerce
* Custom required order fields on [Customer address record](https://support.bigcommerce.com/s/article/Editing-Form-Fields#address-fields)
* Refund synchronization from ReCharge to BigCommerce
* Refund synchronization from BigCommerce to Recharge

## Resources
- [ReCharge Setup](https://support.rechargepayments.com/hc/en-us/categories/360000413333-Installation-and-Getting-Started)
- [Creating a BigCommerce API account](https://support.bigcommerce.com/s/article/Store-API-Accounts)
- [BigCommerce Stencil frontend documentation](https://developer.bigcommerce.com/stencil-docs)