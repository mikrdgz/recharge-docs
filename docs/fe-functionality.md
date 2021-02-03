# Expected storefront functionality

This reference displays what the ReCharge subscription widget and its functionality should look like on a storefront. The ReCharge integration injects CSS elements onto the page.

## Product page
**Data displayed**
- Purchase options selector (Subscribe and one-time, sub only, prepaid)
- Subscription frequency with displayed text= Delivery
- Subscription discount
**Functionality**
Add-to-cart functionality for subscriptions

![product page frontend](assets/images/product-page-fe.png)

## Cart Pop-up after add-to-cart	
**Data displayed**
- Subscription frequency
- Product subscription discounted price
- Cart subtotal with discounted prices
**Functionality**
Subscription checkout button

![cart pop up](assets/images/cart-pop-up-fe.png)

## Cart preview
**Data displayed**
- Product subscription discounted price if sub and save discount is present

**Functionality**
- Subscription checkout button

![cart preview](assets/images/cart-preview-fe.png)

## Cart summary
**Data displayed**
- Subscription frequency by product (Only shows “Subscription” if no discount is present. Shows “Subscribe & Save” if discount is present.)
- Price: Product subscription discounted price
- Estimated Total: Product line items total with discounted prices
- Subtotal: Cart subtotal with discounted prices
- Estimated Tax: should be hidden
- Estimated Grand Total: Total based including sub and save discounts

**Functionality**
- Subscription checkout button

![view cart](assets/images/view-cart-fe.png)

## Cart summary (hidden fields)
- These fields are hidden for subscription products:
- Shipping
- Coupon Code
**Functionality**
- Subscription checkout button

![hidden fields](assets/images/hidden-fields-fe.png)

## Checkout subscription button
**Data displayed**
- If subscription items are present, redirect cart to Recharge checkout
- Call the Bigcommerce Cart API endpoint to get all cart contents and call local storage for subscription info before posting combined cart data to Recharge

![sub checkout 1](assets/images/sub-checkout-1.png)
<br>
![sub checkout 2](assets/images/sub-checkout-2.png)
<br>
![sub checkout 3](assets/images/sub-checkout-3.png)

## Customer portal
**Data displayed**
- Link to Recharge hosted customer portal if the customer has subscriptions
![manage subs](assets/images/manage-subs.png)