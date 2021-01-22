# Overview

The Recharge integration with BigCommerce works out-of-the-box and only requires you to configure general store settings. However, you have the option to to customize the Storefront, Checkout and Customer Portal if desired. With Recharge's architecture you can start with an out-of-the-box solution (most start here), move to a highly flexible hybrid solution (many move here), and if desired build a custom solution (some merchants require this).

## How to Build
For BigCommerce implementations we recommend using the out-of-the-box solution to get started. If you have an unsupported storefront theme you'll need to customize the integration. 

## Use Cases

There are several key reasons to customize a ReCharge/BigCommerce implementation:

* You're using a theme ReCharge currently does not support.
* You want a custom user interface for ReCharge functionality on your product page.
* Matching the look and feel of an existing branded user experience.


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

4. Ensure that the following settings are also configured in ReCharge:
- Tax
- Shipping
- Payments
- Products
- Checkout Settings
- Customer Portal Settings


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
* Refund synchronization from Recharge to BigCommerce
* Refund synchronization from BigCommerce to Recharge

## Resources
- [ReCharge Setup](https://support.rechargepayments.com/hc/en-us/categories/360000413333-Installation-and-Getting-Started)
- [Creating a BigCommerce API account](https://support.bigcommerce.com/s/article/Store-API-Accounts)
- [BigCommerce Stencil frontend documentation](https://developer.bigcommerce.com/stencil-docs)