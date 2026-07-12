# Xendit (xendit)

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
