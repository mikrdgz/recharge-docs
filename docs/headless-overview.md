# Headless Overview

ReCharge offers APIs and developer tools that let you bring subscription functionality to the site or ecommerce platform of your choice. Use our subscription engine anywhere and seamlessly incorporate ReCharge with the rest of your ecommerce tech stack. This article covers the components necessary to create a headless ReCharge integration.

> ### Note
> Significant custom development is required to headlessly integrate ReCharge.

## Products
Products are where ReCharge stores information about the type of subscriptions you offer. If you want to offer subscriptions for a product, you must create that product in the ReCharge product catalog.

You can also create products manually via the [Control Panel](https://support.rechargepayments.com/hc/en-us/articles/360008830873-Creating-subscription-rulesets), if preferred.

## Storefront

The storefront is the frontend component of your site where you display product information to customers. You can surface ReCharge product data via the [Products API Resource](https://developer.rechargepayments.com/#products). Using this resource you can build your own subscription widget and display information about subscription products as you wish.
The storefront provides the capabilities to present your customers with subscription options on your website.  

### Best Practice
We recommend using our CDN JavaScript frontend approach with BigCommerce. To get started, see [BigCommerce Overview](docs/bigcommerce-overview.md).
If you're building your own frontend, refer to the [Expected Frontend Functionality](fe-functionality.md) article to ensure your CSS elements 

## Customer Portal

The Customer Portal is where customers can interact with their subscriptions and alter them at their convenience. They can edit subscriptions, view purchase history, updating billing information and more.

### Best Practice
We recommend using our hosted [Customer Portal](https://support.rechargepayments.com/hc/en-us/articles/360008683274-Customer-portal-) to allow customers to manage their subscriptions. This tech stack is a fast solution to getting started with headless. Building your own customer account functionality is only necessary if you require a very custom build. We recommend waiting to build a custom Customer Portal until your subscription program is proven and you see sustained customer growth.

## Backend Data Processing
We provide webhooks you application can listen for when an event occurs in the ReCharge system. See [Webhooks Overview](docs/webhooks-overview.md).

## Checkout 
### Best Practice
We recommend handing off order data to the ReCharge [hosted checkout](https://support.rechargepayments.com/hc/en-us/articles/360008682954-Customizing-the-ReCharge-checkout) as it's proven at scale with high conversion. If you chose to create your own checkout flow, you're responsible for keeping customer information secure and [PCI Compliance](https://www.pcisecuritystandards.org/). Our checkout can be customized to match the look and feel of your storefront, and we integrate with many major tax and shipping apps. 




