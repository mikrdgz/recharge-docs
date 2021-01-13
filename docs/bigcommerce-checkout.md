# BigCommerce Fast Checkout
The ReCharge hosted checkout is the fastest to launch and is proven at scale with high conversion. You can customize it to match your storefront. ReCharge also integrates with many major tax, shipping, and other providers. 

Out-of-the-box a BigCommerce store will direct customers to the Recharge hosted checkout page. The Recharge storefront JavaScript performs this redirect.

## Functionality 
* **Checkout button** - Our JavaScript will replace the BigCommerce checkout button to pass cart data to Recharge.
* **Cart** - Our storefront JavaScript adds product subscription information to cart. We use BigCommerce's [Cart API](https://developer.bigcommerce.com/api-reference/storefront/carts) to retrieve cart data, then call local storage for ReCharge subscription info and combine the two before `POST`ing combined data to ReCharge.
* **Checkout flow** - Carts will go to ReCharge checkout where we process both subscription and one-time only carts. Our checkout can be customized to match your storefront and we integrate with many major tax, shipping, and other providers.
* **Checkout handoff** - Product information such as pricing, quantity, sku, product weights, custom tax codes, subscription frequency are all handed off to ReCharge checkout page
* **Cart clearing** - after a checkout is completed on ReCharge, the cart is removed on BigCommerce so the customer returns to the BigCommerce storefront with an empty cart.
