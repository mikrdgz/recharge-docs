# Storing and Managing the Product Catalog
## Overview
ReCharge has its own catalog of products aside from your ecommerce platform or site. You will need to create products in ReCharge via your application and store their data asynchronously in order to process subscription orders alongside your non-ReCharge product catalog.

This document provides guidance on how to maintain products in the ReCharge product catalog. The product catalog stores all the data related to a product including price, images, and variants (if applicable). For merchants using Shopify or BigCommerce the product catalog is maintained by ReCharge through direct integrations and no additional work is needed. 

The product catalog is used throughout the ReCharge application to provide product data for the:

- Product widget
- Checkout
- Merchant Portal
- Customer Portal

## Using Middleware
You cannot make API calls to the ReCharge API via the storefront. You will need to build and maintain your own middlware to write to ReCharge's APIs and to fetch data from them.  

## How to Maintain Products

If you integrate ReCharge into Shopify or BigCommerce, ReCharge can sync the product catalog from those platforms automatically.  In a headless environment, you are responsible for syncing your catalog data into the ReCharge platform.  All products that can be purchased or subscribed-to (including one-time products) must be created in the ReCharge product catalog.  

Your middleware should consume product-related webhooks from the ecommerce platform or site, transform the data, and make the related API calls to ReCharge.

## Resources
[Products Reference](https://developer.rechargepayments.com/#products)


