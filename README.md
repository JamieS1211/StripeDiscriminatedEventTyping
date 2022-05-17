# Stripe discriminated event typing

This project is a workaround for [the lack of typing for Stripe webhook events](https://github.com/stripe/stripe-node/issues/758).

## Usage

Copy `StripeDiscriminatedEvents.d.ts` into your project, then use it like this:

```ts
const event = stripe.webhooks.constructEvent(rawBody, sig, webhookSecret) as Stripe.DiscriminatedEvent;

if (event.type === 'payment_intent.succeeded') {
  const paymentIntent = event.data.object;
  // paymentIntent has type Stripe.PaymentIntent; no casting required
}
// et cetera
```
