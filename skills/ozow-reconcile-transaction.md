---
name: Reconcile a transaction by reference or id
description: Look up the current status of an Ozow transaction by merchant reference or Ozow transaction id for reconciliation, without moving money.
api: openapi/ozow-openapi.yml
operations:
  - getTransaction
  - getTransactionByReference
---

# Reconcile an Ozow transaction

Read-only. Safe for autonomous agent use (`connected`/`read` in
`agentic-access/ozow-agentic-access.yml`).

## Auth
Send the `ApiKey` header. Read queries take `siteCode` plus the lookup key.

## Steps
1. If you hold the Ozow GUID, call `getTransaction` (GET `/GetTransaction`) with
   `siteCode` + `transactionId`.
2. If you only have the merchant reference, call `getTransactionByReference`
   (GET `/GetTransactionByReference`) with `siteCode` + `transactionReference`.
3. Both return a JSON **array** of matching transactions (empty array = no
   match, not a 404). Inspect `status`, `statusMessage`, `amount`, `paymentDate`.

## Notes
- Reconcile idempotently on `transactionReference`; there is no pagination.
- Map `status` values via `errors/ozow-decline-codes.yml`
  (Complete / Cancelled / Error / Abandoned / PendingInvestigation).
