# Managing Products

## Overview
Products are the core of ReCharge subscriptions. Our product catalog is where we store information about a product's price, weight, variant, SKU etc. The product[Products Resource endpoint](https://developer.rechargepayments.com/#products) is where you will find information about the subscription rules for an item. ReCharge automatically syncs and maintains product data between Shopify and BigCommerce via our direct integrations. This section provides guidance on directly maintaining product data between your own external catalog and the ReCharge product catalog and Products resource.

## Maintaining products in ReCharge using middleware

ReCharge stores all important information about a product's subscription options on the product resource. If you want to offer a subcription for a product, **you must create that product in ReCharge's catalog before creating an entry for it in the Products resource**. 

In a headless environment, you are responsible for syncing your external product catalog data into ReCharge. The best way to do this is by taking advantage of webhooks available on your existing platform and building a middlware controller that can receive webhooks payloads and then make appropriate changes to your catalog in ReCharge.

## Maintaining products in ReCharge with a cron job
For custom ecommerce platforms or instances when your platform does not support webhooks, you will build an internal service that syncs your data with ours. This could be a cron job that runs at an interval to pull product data from your platform and syncs it to ReCharge's product catalog. The ideal outcome is your platform's product catalog is asynchronously tied to ReCharge's in near real-time. 

<!--!theme: warning -->

> ### Syncing products infrequently could cause unwanted results
> Customers may purchase or subscribe to outdated products if you do not push changes from your platform to ReCharge in a timely manner.

## Deleting products
There are several tasks the ReCharge platform performs automatically when store owners delete a product. If you're handling product deletions in your external app, consider the following:
- You will need to audit the [Subscriptions](https://developer.rechargepayments.com/#the-subscription-object) resource before deleting a product to ensure that the item isn't tied to active customer subscriptions. If the product you're deleting is part of a subscription, you should swap the item for another product, or cancel the customer's subscription. Migrate a different product to the cancelled subscription in case the customer chooses to reactivate.
- Audit upcoming [Orders](https://developer.rechargepayments.com/#orders) when deleting [Onetime](https://developer.rechargepayments.com/#onetimes) products to ensure none of the orders contain that item. You can swap the item or remove it from orders.

## Resources
- [Products API reference](https://developer.rechargepayments.com/#products)
- [ReCharge product catalog API examples](https://docs.google.com/document/d/1m2EV6Cq6ivEwr47NVGvxU4eVQWykqioJJlKKZ1WWOGo/edit)


