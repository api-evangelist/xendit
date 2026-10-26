# Xendit (xendit)

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

Xendit is a payments infrastructure provider for Southeast Asia, giving businesses in Indonesia, the Philippines, and the wider region a single REST API to accept payments, disburse funds, and manage money movement. The unified Payments API accepts virtual accounts, e-wallets (OVO, DANA, GoPay, ShopeePay, GCash, GrabPay, Maya), QR (QRIS / QR Ph), cards, direct debit, and retail outlets through Payment Requests and Payment Tokens; complementary APIs cover hosted Invoices, Payouts / disbursements, Balance, Transactions, Customers, and Refunds.

## Access Model

Access is **self-serve**. Register for a Xendit dashboard account and you immediately get **test-mode** secret API keys to simulate payments; **live-mode** keys unlock after business verification and move real money. There is no waitlist or partner-gate for basic API access.

- **Base URL:** `https://api.xendit.co`
- **Authentication:** HTTP Basic — your secret API key is the **username**, the password is left **empty** (the client Base64-encodes `SECRET_KEY:`). See [authentication/xendit-authentication.yml](authentication/xendit-authentication.yml).
- **Versioning:** the v3 Payments API (`/v3/payment_requests`, `/v3/payment_tokens`) requires an `api-version` header (`2024-11-11`); Customers accepts dates such as `2020-10-31`.
- **Async model:** Xendit uses **outbound webhooks / callbacks** (HTTPS POST to a merchant-configured URL) for payment, refund, payout, session, report, and account events. There is **no public WebSocket API** — see [review.yml](review.yml).

Pricing is usage-based (per transaction), not subscription tiers. Rates vary by country and channel; the [plans](plans/xendit-plans-pricing.yml) and [finops](finops/xendit-finops.yml) files carry representative Indonesia (IDR) and Philippines (PHP) figures and are marked `reconciled: false`.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/xendit/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/xendit/refs/heads/main/apis.yml)

## Tags

- Payments
- Fintech
- Payment Gateway
- Southeast Asia
- Indonesia
- Philippines
- Disbursements
- E-Wallet
- Virtual Accounts
- Cards
- Financial Infrastructure

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### Xendit Payment Requests API

The unified Payments API surface. Create, retrieve, and cancel payment requests that charge end users across every Xendit channel — virtual accounts, e-wallets, QR (QRIS / QR Ph), cards, direct debit, and retail outlets. Requires the `api-version` header (2024-11-11).

- **Human URL:** [https://docs.xendit.co/apidocs/create-payment-request](https://docs.xendit.co/apidocs/create-payment-request)
- **Base URL:** `https://api.xendit.co`

#### Tags

- Payments
- Payment Requests
- Virtual Accounts
- E-Wallet
- Cards

#### Properties

- [Documentation](https://docs.xendit.co/apidocs/introduction)
- [API Reference](https://docs.xendit.co/apidocs/create-payment-request)
- [OpenAPI](openapi/xendit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/xendit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/xendit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Xendit Payment Tokens API

Save an end user's payment method as a reusable payment token for future and recurring transactions, then reference it from a payment request. Part of the v3 Payments API and gated by the `api-version` header (2024-11-11).

- **Human URL:** [https://docs.xendit.co/apidocs/create-payment-token](https://docs.xendit.co/apidocs/create-payment-token)
- **Base URL:** `https://api.xendit.co`

#### Tags

- Payment Methods
- Tokens
- Recurring

#### Properties

- [API Reference](https://docs.xendit.co/apidocs/create-payment-token)
- [OpenAPI](openapi/xendit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/xendit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/xendit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Xendit Invoices API

Create Xendit-hosted invoices / payment links that present every enabled payment channel on a single checkout page. Create an invoice, retrieve it, list invoices, and expire an outstanding invoice.

- **Human URL:** [https://docs.xendit.co/apidocs/payment-link](https://docs.xendit.co/apidocs/payment-link)
- **Base URL:** `https://api.xendit.co`

#### Tags

- Invoices
- Payment Links
- Checkout

#### Properties

- [Documentation](https://docs.xendit.co/apidocs/payment-link)
- [OpenAPI](openapi/xendit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/xendit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/xendit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Xendit Payouts API

Disburse funds to bank accounts and e-wallets across the region. Create a payout, retrieve it by ID, and cancel a pending payout. The v3 Payouts API supersedes the legacy Disbursement product.

- **Human URL:** [https://docs.xendit.co/apidocs/payouts-introduction](https://docs.xendit.co/apidocs/payouts-introduction)
- **Base URL:** `https://api.xendit.co`

#### Tags

- Payouts
- Disbursements
- Transfers

#### Properties

- [Documentation](https://docs.xendit.co/apidocs/payouts-introduction)
- [API Reference](https://docs.xendit.co/apidocs/create-payout-v3)
- [OpenAPI](openapi/xendit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/xendit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/xendit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Xendit Balance API

Retrieve your Xendit account balance for a given account type (CASH or HOLDING) and currency, optionally at a point in time. Supports the multi-currency balances Xendit holds across the region.

- **Human URL:** [https://docs.xendit.co/apidocs/get-balance](https://docs.xendit.co/apidocs/get-balance)
- **Base URL:** `https://api.xendit.co`

#### Tags

- Balance
- Wallet

#### Properties

- [API Reference](https://docs.xendit.co/apidocs/get-balance)
- [OpenAPI](openapi/xendit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/xendit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/xendit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Xendit Transactions API

List the money-movement transactions on your account with rich filters (type, status, channel, currency, amount, created/updated date ranges) and cursor pagination, and retrieve a single transaction by ID.

- **Human URL:** [https://docs.xendit.co/apidocs/list-transactions](https://docs.xendit.co/apidocs/list-transactions)
- **Base URL:** `https://api.xendit.co`

#### Tags

- Transactions
- Ledger
- Reporting

#### Properties

- [API Reference](https://docs.xendit.co/apidocs/list-transactions)
- [OpenAPI](openapi/xendit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/xendit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/xendit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Xendit Customers API

Create and manage customer records — individual or business — that can be attached to payment requests, payment tokens, and payouts. Create a customer, list customers by reference, retrieve one, and update it.

- **Human URL:** [https://docs.xendit.co/apidocs/create-customer-request](https://docs.xendit.co/apidocs/create-customer-request)
- **Base URL:** `https://api.xendit.co`

#### Tags

- Customers
- KYC

#### Properties

- [API Reference](https://docs.xendit.co/apidocs/create-customer-request)
- [OpenAPI](openapi/xendit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/xendit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/xendit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Xendit Refunds API

Initiate a full or partial refund against a successful payment request and retrieve refund status. Refund webhooks notify your systems as the refund settles.

- **Human URL:** [https://docs.xendit.co/apidocs/refund-payment-request](https://docs.xendit.co/apidocs/refund-payment-request)
- **Base URL:** `https://api.xendit.co`

#### Tags

- Refunds
- Payments

#### Properties

- [API Reference](https://docs.xendit.co/apidocs/refund-payment-request)
- [OpenAPI](openapi/xendit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/xendit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/xendit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Domain Security](security/xendit-domain-security.yml)
- [Authentication](authentication/xendit-authentication.yml)
- [GitHub Organization](https://github.com/xendit)
- [LinkedIn](https://www.linkedin.com/company/xendit)
- [Website](https://www.xendit.co)
- [Documentation](https://docs.xendit.co)
- [Plans](plans/xendit-plans-pricing.yml)
- [Rate Limits](rate-limits/xendit-rate-limits.yml)
- [Fin Ops](finops/xendit-finops.yml)
- [Blog](https://www.xendit.co/en/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
