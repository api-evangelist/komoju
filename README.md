# KOMOJU (komoju)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

KOMOJU is a Japan-focused global payment gateway operated by Degica that lets web and e-commerce merchants accept a wide range of local and international payment methods through a single RESTful JSON API. It is especially strong on Japan-specific methods - convenience-store (konbini) cash payments, PayPay and other QR / e-money wallets, bank transfer, and Pay-easy (ATM) - alongside credit cards, Apple Pay, carrier billing, and cross-border wallets such as Alipay and WeChat Pay. Merchants integrate via a Hosted Page, Hosted Fields, or direct API.

## Access Model

KOMOJU is a **commercial payment gateway that requires a merchant account** - there is no fully anonymous public sandbox. Once you have an account you get **two key pairs, one for test and one for live**, each with a **secret key** and a **publishable key**:

- **Secret key** - full access to all API resources; keep it server-side only.
- **Publishable key** - safe to expose client-side; limited to creating tokens and paying for sessions.

All requests use **HTTP Basic Authentication**: send your API key as the username and leave the password **empty** (for example `curl -u secret_key: "https://komoju.com/api/v1/payments"`). The **test key pair** lets you exercise the full API against test payment methods before going live. No monthly or setup fees - KOMOJU charges per transaction.

**Base URL:** `https://komoju.com/api/v1`

POST requests support idempotency via the `X-KOMOJU-IDEMPOTENCY` header, and the API version can be pinned with `X-KOMOJU-API-VERSION`.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/komoju/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/komoju/refs/heads/main/apis.yml)

## Tags

- Payments
- Payment Gateway
- Japan
- Konbini
- Cards
- PayPay
- Bank Transfer
- E-Money
- Checkout
- Fintech

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### KOMOJU Payments API

Create, capture, refund, cancel, update, and list payments across cards, konbini, bank transfer, Pay-easy, and e-money wallets. Supports two-step capture (authorize then capture) and manual refund requests for non-refundable methods like konbini.

- **Human URL:** [https://doc.komoju.com/reference/payments](https://doc.komoju.com/reference/payments)
- **Base URL:** `https://komoju.com/api/v1`

#### Tags

- Payments
- Refunds
- Konbini

#### Properties

- [Documentation](https://doc.komoju.com/docs/creating-payments-directly)
- [API Reference](https://doc.komoju.com/reference/payments)
- [OpenAPI](openapi/komoju-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/komoju.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/komoju.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### KOMOJU Sessions API

Hosted checkout sessions that collect payment or customer details on a KOMOJU-hosted page. Create, show, cancel, and pay for sessions in payment, customer, or customer_payment mode.

- **Human URL:** [https://doc.komoju.com/reference/sessions](https://doc.komoju.com/reference/sessions)
- **Base URL:** `https://komoju.com/api/v1`

#### Tags

- Checkout
- Hosted Page
- Sessions

#### Properties

- [Documentation](https://doc.komoju.com/docs/hosted-page-integration-guide)
- [API Reference](https://doc.komoju.com/reference/sessions)
- [OpenAPI](openapi/komoju-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### KOMOJU Tokens API

Tokenize payment details so sensitive card data never touches your server. Create short-term tokens and 3D Secure secure tokens, and retrieve secure token status for later use as payment details.

- **Human URL:** [https://doc.komoju.com/reference/tokens](https://doc.komoju.com/reference/tokens)
- **Base URL:** `https://komoju.com/api/v1`

#### Tags

- Tokenization
- 3D Secure
- Cards

#### Properties

- [Documentation](https://doc.komoju.com/docs/tokenizing-payment-details)
- [API Reference](https://doc.komoju.com/reference/tokens)
- [OpenAPI](openapi/komoju-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### KOMOJU Customers API

Create, retrieve, update, list, and delete customers with securely stored payment details. A saved customer ID can be charged directly in place of raw payment details for delayed billing and repeat purchases.

- **Human URL:** [https://doc.komoju.com/reference/createcustomer](https://doc.komoju.com/reference/createcustomer)
- **Base URL:** `https://komoju.com/api/v1`

#### Tags

- Customers
- Saved Cards
- Recurring

#### Properties

- [Documentation](https://doc.komoju.com/docs/long-term-tokens)
- [API Reference](https://doc.komoju.com/reference/createcustomer)
- [OpenAPI](openapi/komoju-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### KOMOJU Subscriptions API

Recurring payments charged against a saved customer on a weekly, monthly, or yearly period. Create, show, list, and delete subscriptions; subscriptions are immutable once created.

- **Human URL:** [https://doc.komoju.com/reference/subscriptions](https://doc.komoju.com/reference/subscriptions)
- **Base URL:** `https://komoju.com/api/v1`

#### Tags

- Subscriptions
- Recurring Payments
- Billing

#### Properties

- [API Reference](https://doc.komoju.com/reference/subscriptions)
- [OpenAPI](openapi/komoju-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### KOMOJU Payment Methods API

Lists the payment methods available to the authenticated merchant for a given amount and currency - credit_card, konbini, bank_transfer, pay_easy, paypay, merpay, au_pay, rakutenpay, linepay, alipay, wechatpay, and paidy - plus konbini barcode retrieval for compatible payments.

- **Human URL:** [https://doc.komoju.com/reference/listpaymentmethods](https://doc.komoju.com/reference/listpaymentmethods)
- **Base URL:** `https://komoju.com/api/v1`

#### Tags

- Payment Methods
- Konbini
- E-Money

#### Properties

- [Documentation](https://doc.komoju.com/supported-payment-methods)
- [API Reference](https://doc.komoju.com/reference/listpaymentmethods)
- [OpenAPI](openapi/komoju-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### KOMOJU Events API

Query the webhook events KOMOJU emits (payment.authorized, payment.captured, payment.refunded, payment.failed, payment.marked.as.fraud, and more). Webhooks are delivered as signed HTTP POSTs verified via an X-Komoju-Signature HMAC header.

- **Human URL:** [https://doc.komoju.com/reference/listevents](https://doc.komoju.com/reference/listevents)
- **Base URL:** `https://komoju.com/api/v1`

#### Tags

- Webhooks
- Events
- Notifications

#### Properties

- [Documentation](https://doc.komoju.com/docs/webhooks)
- [API Reference](https://doc.komoju.com/reference/listevents)
- [OpenAPI](openapi/komoju-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Domain Security](security/komoju-domain-security.yml)
- [Authentication](authentication/komoju-authentication.yml)
- [GitHub Organization](https://github.com/komoju)
- [LinkedIn](https://www.linkedin.com/company/komoju)
- [Website](https://en.komoju.com)
- [Documentation](https://doc.komoju.com)
- [Plans](plans/komoju-plans-pricing.yml)
- [Rate Limits](rate-limits/komoju-rate-limits.yml)
- [Fin Ops](finops/komoju-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
