# Yallabid-Paypal-API

Users can connect to Yallabid paypal payments by providing their **Paypal Account Email.** instead of Connect Bank.


## PayPal Payment API
Use the following route to create a PayPal payment intent. Provide the amount and currency in the request body. If the payment intent is created successfully, the buyer will be redirected to a PayPal checkout webpage to approve the purchase.
If the payment is approved successfully, the request will be captured by the Yallabid api server to finalize the checkout.
```
POST
http://http://95.111.225.252/api/paypal/createIntent
{
  amount: "100.00",
  currency: "USD"
}
```
The payment funds reside in the Yallabid Admin's PayPal account, not the user's PayPal account yet.
> Please note that in PayPal, users' payment accounts are not managed by the Yallabid platform like Stripe Connect. However, in Stripe Connect, users' Stripe accounts are managed by Yallabid.



## PayPal Payout API
If a user wishes to withdraw from their wallet, he should send a withdraw request. To approve this request, Yallabid should payout to the user's PayPal account using his PayPal email.
Use the following route to start a payout to your users:
```
POST
http://http://95.111.225.252/api/paypal/payout
{
  email: <user-paypal-email>
  amount: "100.00",
  currency: "USD"
}
```


