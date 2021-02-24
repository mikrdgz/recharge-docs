# API Integration Overview

ReCharge offers APIs that let you use subscription functionality with your existing ecommerce tech stack, or platform of your choice. Using our robust APIs you can seamlessly display ReCharge subscription options on any frontend. 

> ### Note
> Significant custom development is required to integrate ReCharge using an API-first approach.

## Products
ReCharge has its own catalog of products. You will need to create products in ReCharge via your application and sync their data asynchronously with that of your own product catalog in order to process subscription orders. ReCharge stores information about the type of subscriptions you offer on the products resource. If you want to offer subscriptions for a product, you must create that product in the ReCharge product catalog.

## Storefront

 Using ReCharge's frontend JavaScript SDK, you can build your own subscription widget and display information about subscription products as you wish.

## Checkout 
The Checkout component of your ReCharge integration is how you will process a customers initial recurring subscription purchase. ReCharge offers three approaches to checkout: 

1. ReCharge hosts a fully [PCI-compliant](https://www.pcisecuritystandards.org/) checkout environment. 
2. ReCharge's [Checkouts API](checkouts.md) lets you create your own checkout environment for customers.
3. You can own the checkout process and sync subscription information back to ReCharge after you've processed a checkout via an external system.

## Backend Processing
Once an order is processed via ReCharge, you will need to sync this data so that it is simultaneously reflected in your external system. We provide webhooks your application can listen for when an event occurs in the ReCharge system. See [Webhooks Overview](webhooks-overview.md). Your application can then take action based on the data contained in our webhooks service payload.

## Merchant and Customer Portals

The ReCharge Merchant Portal lets you configure your ReCharge store's settings and manually edit customers, subcription products and more.

The [Customer Portal](https://support.rechargepayments.com/hc/en-us/articles/360008683274-Customer-portal-) is where customers interact with their ReCharge subscriptions and alter them at their convenience. They can edit subscriptions frequency, view purchase history, updating billing information and more.
