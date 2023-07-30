# Yallabid Paypal API

Users can connect to Yallabid paypal payments by providing their **Paypal Account Email.** instead of Connect Bank.

ask the users to provide their **Paypal Account Emails.**


## PayPal Payment API
To charge wallet use the following route to create a PayPal payment intent. Provide the amount and currency in the request body.
If the payment intent is created successfully, an approval link will be returned and can be used for the user to complete checkout.
```
POST
http://http://95.111.225.252/api/paypal/createIntent
body: {
  amount: "100.00",
  currency: "USD"
}
```

example response:
```
{
    "status": true,
    "approveLink": "https://www.sandbox.paypal.com/checkoutnow?token=8UU954209S672521W",
    "token": "8UU954209S672521W"
}
```

## PayPal Capture Payment API
To successfully approve wallet charge, the user must first complete checkout.
use the following route, to approve the payment

```
POST
http://http://95.111.225.252/api/paypal/captureIntent/<token>
```

example response:
```
{
    "status": true,
    "amount": 85.794
}
```
use the response **amount** to update/increase the user wallet.

> The payment funds reside in the Yallabid Admin's PayPal account, not the user's PayPal account yet.
> (Limitation): Please note that in PayPal, users' payment accounts are not managed by the Yallabid platform. However, in Stripe Connect, users' Stripe accounts are managed by Yallabid.



## PayPal Payout API
If users want to withdraw from their wallet, use the following route to start a payout to your users:
```
POST
http://http://95.111.225.252/api/paypal/payout/<user-id>
body: {
  email: <user-paypal-email>
  amount: "100.00",
  currency: "USD"
}
```
update/decrease the user's wallet using route /withdraw/requests

