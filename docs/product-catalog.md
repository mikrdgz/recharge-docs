# Product Catalog
The [product catalog](https://docs.google.com/document/d/1m2EV6Cq6ivEwr47NVGvxU4eVQWykqioJJlKKZ1WWOGo/edit) endpoint is where data about each item in your external catalog is stored within ReCharge's system. With our direct integrations, ReCharge automatically pulls information such as price, variant, weight SKU etc. into our product catalog at the time a user creates subscription rules for a product in the Merchant Portal.

In the ReCharge API, product subscription rules are tied to items by creating a [Products resource](products.md) entry. You **must** create a product catalog entry for an item first before you can add subscription rules via a Products resource entry.

## Uses

The product catalog is used throughout the ReCharge application to provide product data for the following areas:

- Product widget
- Checkout
- Merchant Portal
- Customer Portal

> ### Note about /catalog/ endpoint
> The `/catalog/` endpoint is currently in beta. If you encounter an issue while using this resource, please contact ReCharge.