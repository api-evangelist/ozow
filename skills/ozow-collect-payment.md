---
name: Collect an instant EFT payment and confirm it
description: Create an Ozow instant-EFT payment request, redirect the customer to the secure bank-selection flow, then confirm the outcome server-side before fulfilment.
api: openapi/ozow-openapi.yml
operations:
  - postPaymentRequest
  - getTransactionByReference
---

# Collect an instant EFT payment (Ozow)

Money-movement flow. Payment initiation should run under human-in-the-loop per
`agentic-access/ozow-agentic-access.yml`. ZAR-only (CountryCode `ZA`,
CurrencyCode `ZAR`).

## Auth
- Send the `ApiKey` header (merchant key from dash.ozow.com).
- Compute the `HashCheck`: concatenate the fields in documented order
  (SiteCode, CountryCode, CurrencyCode, Amount, TransactionReference,
  BankReference, CancelUrl, ErrorUrl, SuccessUrl, NotifyUrl, IsTest), append the
  merchant `PrivateKey`, lower-case, take the SHA512 hex digest. See
  `conventions/ozow-conventions.yml`.

## Steps
1. Generate a unique `TransactionReference` (enforce your own dedup — Ozow has no
   Idempotency-Key). Set `IsTest=true` while testing.
2. Call `postPaymentRequest` (POST `/postpaymentrequest`) with the payment
   fields + `HashCheck`. Read `url` from the response and redirect the customer
   there.
3. Wait for the server-to-server POST to your `NotifyUrl`. Verify its HashCheck
   before trusting it (never trust the browser SuccessUrl redirect alone).
4. Confirm with `getTransactionByReference` (GET `/GetTransactionByReference`)
   using your `TransactionReference`. Fulfil only when `status` is `Complete`
   and `amount` matches.

## Error handling
- A `400` usually means a HashCheck mismatch — re-check field order/PrivateKey.
- Non-terminal statuses (`Pending`, `PendingInvestigation`) mean do not fulfil
  yet; poll or await the notification. See `errors/ozow-decline-codes.yml`.
