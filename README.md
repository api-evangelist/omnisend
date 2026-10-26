# Omnisend (omnisend)

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

Omnisend is a Lithuanian-headquartered email and SMS marketing automation platform purpose-built for ecommerce, with first-class integrations into Shopify, BigCommerce, WooCommerce, Magento, Wix, Square Online, and other storefronts. The platform unifies automation workflows, campaign builders, segmentation, popups and forms, web push, product recommendations, A/B testing, and reporting to drive customer engagement and revenue. Omnisend's REST API exposes contacts, events, products, product categories, segments, campaigns, batches, email templates, email content, universal layouts, images, brands, and analytics reports. Authentication uses an API key passed via the `X-API-KEY` header, or OAuth 2.0 authorization-code flow with resource-scoped permissions for app-based integrations on the Omnisend App Market.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/omnisend/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/omnisend/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- Email Marketing
- Marketing Automation
- Ecommerce
- SMS Marketing
- Customer Engagement
- Segmentation
- Campaigns
- Forms
- Popups
- Web Push

## Timestamps

- **Created:** 2026-05-11
- **Modified:** 2026-05-25

## APIs

### Omnisend REST API

Omnisend's REST API for ecommerce email and SMS marketing automation. Manage contacts, events, products, product categories, segments, campaigns, batches, email templates, email content, email universal layouts, images, brands, and analytics reports. Authentication uses `X-API-KEY` header or OAuth 2.0 with resource-scoped permissions (`contacts.read`, `contacts.write`, `events.write`, `products.read`, `products.write`, `campaigns.read`, `campaigns.write`, `segments.read`, `segments.write`, `email-templates.read`, `email-templates.write`, `images.read`, `images.write`, `brands.read`, `brands.write`, `analytics.read`). Cursor-based pagination across list endpoints.

- **Human URL:** [https://api-docs.omnisend.com/reference/overview](https://api-docs.omnisend.com/reference/overview)
- **Base URL:** `https://api.omnisend.com/v5`

#### Tags

- Email Marketing
- Contacts
- Campaigns
- Ecommerce
- Events
- Segments
- Products
- Templates
- Analytics

#### Properties

- [Documentation](https://api-docs.omnisend.com/)
- [API Reference](https://api-docs.omnisend.com/reference/overview)
- [Authentication](https://api-docs.omnisend.com/reference/authentication)
- [O Auth](https://api-docs.omnisend.com/reference/oauth)
- [Postman](https://www.postman.com/omnisend-api/workspace/omnisend/overview) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [L L Ms Txt](https://api-docs.omnisend.com/llms.txt)
- [OpenAPI](openapi/omnisend-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/omnisend.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/omnisend.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/omnisend-contact-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/omnisend-event-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/omnisend-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [Website](https://www.omnisend.com)
- [Portal](https://www.omnisend.com)
- [Documentation](https://api-docs.omnisend.com)
- [API Reference](https://api-docs.omnisend.com/reference/overview)
- [Getting Started](https://api-docs.omnisend.com/docs/getting-started)
- [Authentication](https://api-docs.omnisend.com/reference/authentication)
- [O Auth](https://api-docs.omnisend.com/reference/oauth)
- [Changelog](https://api-docs.omnisend.com/changelog)
- [L L Ms Txt](https://api-docs.omnisend.com/llms.txt)
- [Pricing](https://www.omnisend.com/pricing)
- [Plans](plans/omnisend-plans-pricing.yml)
- [Rate Limits](rate-limits/omnisend-rate-limits.yml)
- [Fin Ops](finops/omnisend-finops.yml)
- [Sign Up](https://app.omnisend.com/signup)
- [Login](https://app.omnisend.com/login)
- [Support](https://support.omnisend.com)
- [Help Center](https://support.omnisend.com/en/articles/1061798-omnisend-api-documentation)
- [Contact Support](https://www.omnisend.com/contact-us/support)
- [Status Page](https://status.omnisend.com)
- [Blog](https://www.omnisend.com/blog)
- [GitHub Organization](https://github.com/omnisend)
- [LinkedIn](https://www.linkedin.com/company/omnisend)
- [Privacy Policy](https://www.omnisend.com/privacy)
- [Terms of Service](https://www.omnisend.com/terms)
- [SDK](https://github.com/omnisend/php-sdk)
- [Plugin](https://github.com/omnisend/wp-omnisend)
- [Plugin](https://github.com/omnisend/magento2-plugin)
- [Plugin](https://www.omnisend.com/integrations/woocommerce)
- [Plugin](https://www.omnisend.com/integrations/shopify)
- [Plugin](https://www.omnisend.com/integrations/bigcommerce)
- [Integrations](https://www.omnisend.com/integrations)
- [App Market](https://www.omnisend.com/app-market)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
**URL:** https://apievangelist.com
