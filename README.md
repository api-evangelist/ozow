# Ozow (ozow)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
