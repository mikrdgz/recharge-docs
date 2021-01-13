# BigCommerce Checkout
The ReCharge hosted checkout is the fastest to launch and is proven at scale with high conversion. Our checkout can be customized to match your storefront and we integrate with many major tax, shipping, and other providers. Waiting to consider building a customized Customer Portal until after the subscription program grows in size is the recommended path.

The out of the box functionality is to use the Recharge hosted checkout. The Recharge storefront javascript performs a redirect which takes users from the BigCommerce storefront to a Recharge checkout web page.

To get the out of the box Recharge functionality working, Purchase/Install Recharge for Big Commerce and perform General Configuration of Recharge.

Additional information is included below highlight how this works:
* Checkout button - our javascript files will replace the checkout button to pass the cart over to Recharge
  * Subscription information on items is added to cart via our storefront javascript (additional information here Common/Expected FE Functionality)
* Checkout flow - Carts will go to Recharge checkout where both subscription and one time only product carts can be processed. The Recharge hosted checkout is the fastest to launch and is proven at scale with high conversion. Our checkout can be customized to match your storefront and we integrate with many major tax, shipping, and other providers.
* Checkout handoff - pricing, quantity, sku, product weights, custom tax codes, subscription frequency are all handed off to Recharge checkout page
* Cart clearing - after a checkout is completed on Recharge, the cart is removed on BigCommerce so that when the customer returns to the BigCommerce storefront the cart contents are not still present
