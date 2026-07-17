---
name: Refund a completed EFT payment
description: Refund a previously completed Ozow EFT payment from the merchant float, using a bearer token and HashCheck, and confirm the refund outcome.
api: openapi/ozow-openapi.yml
operations:
  - postRefundRequest
  - getTransaction
---

# Refund a completed Ozow payment

Money-movement flow. Requires human-in-the-loop per
`agentic-access/ozow-agentic-access.yml`.

## Auth
Refunds do NOT use the `ApiKey` header. Obtain a reusable **bearer token** from
the Ozow token service and send it as `Authorization: Bearer <token>`, plus a
per-request `HashCheck`. See `authentication/ozow-authentication.yml`.

## Steps
1. Confirm the original payment is refundable: call `getTransaction`
   (GET `/GetTransaction`) and verify `status` is `Complete`.
2. Compute the refund `HashCheck` over the refund field set + `PrivateKey`
   (lower-cased SHA512).
3. Call `postRefundRequest` (POST `/PostRefundRequest`) with `SiteCode`,
   `TransactionId`, `Amount`, `RefundReference`, `NotifyUrl`, `HashCheck`.
4. Ozow POSTs the refund outcome to your `NotifyUrl` — verify its HashCheck and
   reconcile on `RefundReference`.

## Error handling
- A `400` means validation failure, expired/missing bearer token, or HashCheck
  mismatch. See `errors/ozow-problem-types.yml`.
- Ensure sufficient merchant float; partial vs full refund is set via `Amount`.
