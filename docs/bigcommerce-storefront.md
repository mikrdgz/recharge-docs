# BigCommerce Storefront

The Recharge frontend works in the following key ways:
* We leverage a CDN to serve content to your frontend that we then cache in browser local storage upon initial site load.
* Recharge provides - JavaScript Interfaces
* Additional details on storefront functionality is in the Common/Expected FE Functionality page

## Fast
This implementation is geared toward developers who want to quickly integrate ReCharge with BigCommerce and don't need any custom functionality.

Once you've installed the BigCommerce/ReCharge integration, you'll see the ReCharge subscription widget right out of the box.
![sub widget](assets/images/sub-widget.png)

ReCharge works with the [Cornerstone](https://support.bigcommerce.com/s/article/Cornerstone-Theme-Manual) theme out of the box. We are developing support for additional themes, however the widget may work with other themes. Confirm by making sure that your front end displays the functionality shown in the [Expected BigCommerce Frontend article](docs/bigcommerce-functionality.md).
If you do not see these ReCharge elements, you'll need to customize your storefront.

## Custom Storefront

See the *Developing a Custom Storefront* section for the technical components and steps to customize a BigCommerce storefront, or for themes not currently supported by ReCharge out of the box, while using ReCharge subscriptions.



