# Expected Front End Functionality

This reference displays what the ReCharge subscription widget should look like on a frontend. The ReCharge integration injects CSS elements onto various pages within a site.

## Frontend functionality
|Group|Frontend page/element|Image|Data displayed|Functionality|
|-|-|-|-|-|
|Product|Product page|![product page frontend](assets/images/product-page-fe.png)| - Purchase options selector (Subscribe and one-time, sub only, prepaid) <br> - Subscription frequency with displayed text= Delivery <br> - Subscription discount|Add-to-cart functionality for subscriptions|
|Cart|Cart pop-up after add-to-cart|![cart pop up](assets/images/cart-pop-up-fe.png)|- Subscription frequency<br>- Product subscription discounted price<br>- Cart subtotal with discounted prices|Subscription checkout button|
|Cart|Cart preview (top right corner)|![cart preview](assets/images/cart-preview-fe.png)|Product subscription discounted price if sub and save discount is present|Subscription checkout button|
|Cart|View cart summary|![view cart](assets/images/view-cart-fe.png)|- Subscription frequency by product <br>* Only show “Subscription” if no discount is present. Show “Subscribe & Save” if discount is present <br>- Price: Product subscription discounted price<br>- Estimated Total - Product line items total with discounted prices <br>- Subtotal: Cart subtotal with discounted prices<br>- Estimated Tax: should be hidden<br>Estimated Grand Total: Total based including sub and save discounts|Subscription checkout button|
|Cart|View cart summary (hidden fields)|![hidden fields](assets/images/hidden-fields-fe.png)|- Hidden fields from cart compared with only one time products (OTPs):<br>* Shipping<br>* Coupon Code|Subscription checkout button|
|Checkout|Subscription checkout button|![sub checkout 1](assets/images/sub-checkout-1.png)![sub checkout 2](assets/images/sub-checkout-2.png)![sub checkout 3](assets/images/sub-checkout-3.png)|- If subscription items are present, redirect cart to Recharge checkout<br>- Call the Bigcommerce Cart API endpoint to get all cart contents and call local storage for subscription info before posting combined cart data to Recharge
|Customer Portal|Account > Manage Subscriptions|![manage subs](assets/images/manage-subs.png)||Link to Recharge hosted customer portal if the customer has subscriptions|
