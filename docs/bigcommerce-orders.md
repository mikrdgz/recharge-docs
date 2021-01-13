Completed orders on the Recharge hosted checkout will be submitted directly to your BigCommerce store via API. This will work out of the box through our Recharge+BigCommerce Order Adapter.

To get the out of the box Recharge functionality working, Purchase/Install Recharge for Big Commerce and perform General Configuration of Recharge.

Additional information is included below highlight how this works:
* Order submission - Order price, status, shipping method, payment method, contact info, and additional information are submitted as part of the order
  * Order status is submitted as order status 11 = Awaiting Fulfillment
  * Additional fields are optional on orders when Multi-Currency is enabled on the store 
* Customer creation - 
  * If customer does not exist (new email), a customer is created
  * If customer exists and if address does not exist, an address is created
  * If shipping and billing address on RC are different, two addresses are created for BC customer address book
* Marketing - Customers that have opted in to marketing/receiving newsletter are marked that they accept email marketing via a POST Customers/Subscribers call. On BC a Subscriber can existing without having a customer.
* Refunds - Currently a BC store owner would need to refund via Recharge for refund, and would need to also refund on BC via BC store admin portal if they want to keep systems in sync
  * Development in progress - Sync full, partial and line item refunds on RC to BC
* Cancellations -  Recharge updates the order in BC with the Cancelled status. But, the order is still paid (a refund would be necessary to get money back). Generally used to prevent fulfillment.