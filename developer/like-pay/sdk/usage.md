---
description: >-
  Generate a one time QR code for receiving LIKE payment, suitable for
  eshop/etc.
---

# Usage

## Note: This library is still under active development and is not suitable for production use yet

## Browser integration guide

Include like-pay sdk in your website's &lt;head&gt;:

```
 <script src="https://static.like.co/sdk/like-pay-0.0.1.js"></script>
```

Define where you want the LIKE pay QR code to show up by making a &lt;div&gt; , say `#likepay`.

{% code title="index.html" %}
```bash
<head>
  <script src="https://static.like.co/sdk/like-pay-0.0.1.js"></script>
</head>
<body>
  <div id="likepay"></div>
</body>
```
{% endcode %}

In your javascript, call `likePay.createPaymentQRCode()`, parameters are `DOM selector`,  `your liker ID` and `LIKE amount to be recevied`

{% code title="index.js" %}
```bash
likePay.createPaymentQRCode('#likepay', 'ckxpress', 1)
  .then((tx) => {
    /* returns after tx complete, shows tx completion */
    console.log(tx);
    return tx;
  })
```
{% endcode %}

`createPaymentQRCode()` returns a promise, if the user have completed the payment flow in their Liker Land app, the promise will resolve with tx information.

