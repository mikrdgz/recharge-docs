# API Integration Overview

ReCharge offers APIs that let you use subscription functionality with your existing ecommerce tech stack, or platform of your choice. Using our robust APIs you can seamlessly display ReCharge subscription options on any frontend. This article covers the high-level concepts necessary to create a headless ReCharge integration.

> ### Note
> Significant custom development is required to integrate ReCharge using an API-first approach.

## Products
ReCharge has its own catalog of products. You will need to create products in ReCharge via your application and sync their data asynchronously with that of your own product catalog in order to process subscription orders. ReCharge stores information about the type of subscriptions you offer on the products resource. If you want to offer subscriptions for a product, you must create that product in the ReCharge product catalog.

## Storefront

The storefront is the frontend component of your site where you display product and subscription information to customers. Using ReCharge's CRUD APIs, you can build your own subscription widget and display information about subscription products as you wish.
The storefront provides the capabilities to present your customers with subscription options on your website.  

You can surface subscription information about your product catalog via the [Products API Resource](https://developer.rechargepayments.com/#products). Using this resource to pull data, you can build your own subscription widget and display information about subscriptions.

## Checkout 
The Checkout component of your ReCharge integration is how you will process orders and charge customers for their recurring subscriptions. ReCharge offers three approaches to checkout: 

1. ReCharge hosts a fully [PCI-compliant](https://www.pcisecuritystandards.org/) checkout environment. 
2. ReCharge's [Checkouts API](docs/checkouts.md) lets you create your own checkout environment for shoppers.
3. You can own the checkout process and sync subscription information back to ReCharge after you've processed a checkout via an external system.

## Backend Processing
Once an order is processed via ReCharge, you will need to sync this data so that it is simultaneously reflected in your external system. We provide webhooks your application can listen for when an event occurs in the ReCharge system. See [Webhooks Overview](docs/webhooks-overview.md). Your application can then take action based on the data contained in our webhooks service payload.

## Customer Portal

The Customer Portal is where customers interact with their subscriptions and alter them at their convenience. They can edit subscriptions frequency, view purchase history, updating billing information and more.

## Resources
- [ReCharge Full API Reference](https://developer.rechargepayments.com/)
- [ReCharge Hosted Checkout](https://support.rechargepayments.com/hc/en-us/articles/360008682954-Customizing-the-ReCharge-checkout)
- [ReCharge Customer Portal](https://support.rechargepayments.com/hc/en-us/articles/360008683274-Customer-portal-)
