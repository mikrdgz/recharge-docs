# Storing and Managing the Product Catalog

ReCharge has its own catalog of products aside from your ecommerce platform or site. You will need to create products in ReCharge via your application and store their data asynchronously in order to process subscription orders alongside your non-ReCharge product catalog.

## Overview
This document provides guidance on how to maintain products in the ReCharge product catalog. The product catalog stores all the data related to a product including price, images, and variants (if applicable). For merchants using Shopify or BigCommerce the product catalog is maintained by ReCharge through direct integrations and no additional work is needed. 

The product catalog is used throughout the ReCharge application to provide product data for the:

- Product widget
- Checkout
- Merchant Portal
- Customer Portal

## How to Maintain Products

You will need to store 

### Using Middleware
A middleware is developed to consume product related webhooks from the ecommerce platform, transform the data, and make the related API calls to ReCharge.

### Maintaining Products in ReCharge 
For custom ecommerce platforms, an internal function/service is developed to directly make the related API calls to ReCharge. 