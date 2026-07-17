# Ozow (ozow)

Ozow (formerly i-Pay) is a South African fintech providing an instant EFT / "Pay by Bank" payment gateway. Merchants create a server-side payment request, redirect the customer to the Ozow secure bank-selection flow, and reconcile via a server-to-server notification. The REST API is ZAR-only (CountryCode ZA), authenticated with an ApiKey header and a SHA512 HashCheck built from a merchant PrivateKey.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/ozow/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/ozow/refs/heads/main/apis.yml)

## Tags

- Payments
- Instant EFT
- Pay by Bank
- Fintech
- South Africa

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## APIs

### Ozow Payments API

Creates an instant EFT payment request (POST /postpaymentrequest) and returns a redirect URL to the Ozow secure bank-selection page. ZAR-only, ApiKey header plus SHA512 HashCheck over the field set with the merchant PrivateKey.

- **Human URL:** [https://hub.ozow.com/docs](https://hub.ozow.com/docs)
- **Base URL:** `https://api.ozow.com`

#### Tags

- Payments
- Instant EFT
- Pay by Bank

#### Properties

- [Documentation](https://hub.ozow.com/docs)
- [API Reference](https://ozow.com/integrations)
- [OpenAPI](openapi/ozow-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ozow.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Ozow Transactions API

Query transaction status by Ozow transaction id (GET /GetTransaction) or by merchant reference (GET /GetTransactionByReference). Returns an array of transaction objects for reconciliation.

- **Human URL:** [https://hub.ozow.com/docs](https://hub.ozow.com/docs)
- **Base URL:** `https://api.ozow.com`

#### Tags

- Transactions
- Reconciliation
- Status

#### Properties

- [Documentation](https://hub.ozow.com/docs)
- [OpenAPI](openapi/ozow-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ozow.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Ozow Bank List API

Returns the list of supported banks (GET /GetBanks) for merchants that render their own bank-selection UI ahead of redirecting to the Ozow flow.

- **Human URL:** [https://hub.ozow.com/docs](https://hub.ozow.com/docs)
- **Base URL:** `https://api.ozow.com`

#### Tags

- Banks
- Bank Selection

#### Properties

- [Documentation](https://hub.ozow.com/docs)
- [OpenAPI](openapi/ozow-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ozow.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Ozow Refunds API

Refunds previously completed EFT payments from the merchant Ozow float (POST /PostRefundRequest). Uses a bearer token from the Ozow token service plus a HashCheck; Ozow notifies the merchant NotifyUrl on completion or failure.

- **Human URL:** [https://hub.ozow.com/docs](https://hub.ozow.com/docs)
- **Base URL:** `https://api.ozow.com`

#### Tags

- Refunds
- Payouts

#### Properties

- [Documentation](https://hub.ozow.com/docs)
- [OpenAPI](openapi/ozow-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ozow.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

## Common Properties

- [Agentic Access](agentic-access/ozow-agentic-access.yml)
- [Trust Center](security/ozow-trust-center.yml)
- [Vulnerability Disclosure](security/ozow-vulnerability-disclosure.yml)
- [Domain Security](security/ozow-domain-security.yml)
- [Authentication](authentication/ozow-authentication.yml)
- [LinkedIn](https://za.linkedin.com/company/ozowsecurepayments)
- [Website](https://ozow.com/)
- [Documentation](https://hub.ozow.com/docs)
- [Plans](plans/ozow-plans-pricing.yml)
- [Rate Limits](rate-limits/ozow-rate-limits.yml)
- [Fin Ops](finops/ozow-finops.yml)
- [Blog](https://ozow.com/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
