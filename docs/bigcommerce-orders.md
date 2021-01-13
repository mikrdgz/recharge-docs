# BigCommerce Orders

ReCharge submits orders from our hosted checkout to BigCommerce via API. We've built an adapter that ensures this works seamlessly out of the box.

* **Order submission** - Order price, status, shipping method, payment method, contact info, and additional information are submitted as part of the order
* **Order status** - Orders are submitted as BigCommerce order status type [Awaiting Fulfillment](https://support.bigcommerce.com/s/article/Order-Statuses)
* Additional fields are optional on orders when [Multi-Currency](https://support.bigcommerce.com/s/article/Managing-Currencies#mc) is enabled on the store 
* **Customer creation** - 
  * If customer does not exist (new email), ReCharge creates a customer on BigCommerce
  * If customer exists and if an address does not exist, we create an address
  * If shipping and billing addresses on ReCharge are different, two addresses are created within the BigCommerce customer's address book
* **Marketing** - Customers that have opted in to marketing/receiving a store newsletter are marked as acceptingmarketing via a POST Customers/Subscribers call. On BigCommerce a Subscriber can exist without being attached to a customer account.
* Refunds - Currently a BC store owner would need to refund via Recharge for refund, and would need to also refund on BC via BC store admin portal if they want to keep systems in sync
  * Development in progress - Sync full, partial and line item refunds on RC to BC
* Cancellations -  Recharge updates the order in BC with the Cancelled status. But, the order is still paid (a refund would be necessary to get money back). Generally used to prevent fulfillment.