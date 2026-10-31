# Omnisend

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

Omnisend is a Lithuanian-headquartered email and SMS marketing automation platform purpose-built for ecommerce, with first-class integrations into Shopify, BigCommerce, WooCommerce, Magento, Wix, Square Online, and other storefronts. The platform unifies automation workflows, campaign builders, segmentation, popups and forms, web push, product recommendations, A/B testing, and reporting to drive customer engagement and revenue. The REST API at version 2026-03-15 is served from https://api.omnisend.com/api and covers contacts, events and custom event metadata, products, product categories, segments, campaigns, automations, batches, email templates, email content, universal layouts, images, brands and analytics — 82 published operations across 15 OpenAPI 3.0.0 documents. Authentication is an API key on the Authorization header (Omnisend-API-Key {key}) or OAuth 2.0 authorization code with PKCE and 26 resource scopes; every request must also carry an Omnisend-Version header, and a retired version returns 410. Omnisend additionally operates two first-party hosted MCP servers at mcp.omnisend.com and is listed in Claude's Connector Directory.

**Areas:** Email Marketing · Marketing Automation · E-Commerce · SMS Marketing · Customer Engagement · Segmentation · Campaigns · Forms · Popups · Web Push · Automation Workflows · Analytics

## Omnisend on APIs.io

Everything profiled for Omnisend is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/omnisend/](https://apis.io/providers/omnisend/)** — or go straight to one of the APIs or properties below.

### APIs (16)

- [Omnisend Brands API](https://apis.io/apis/omnisend/omnisend-brands-api/) — The Brands API from Omnisend — 2 operation(s) for brands. Version 2026-03-15, harvested from Omnisend's published contract.
- [Omnisend Campaigns API](https://apis.io/apis/omnisend/omnisend-campaigns-api/) — The Campaigns API from Omnisend — 14 operation(s) for campaigns. Version 2026-03-15, harvested from Omnisend's published contract.
- [Omnisend Contacts API](https://apis.io/apis/omnisend/omnisend-contacts-api/) — The Contacts API from Omnisend — 7 operation(s) for contacts. Version 2026-03-15, harvested from Omnisend's published contract.
- [Omnisend Events API](https://apis.io/apis/omnisend/omnisend-events-api/) — The Events API from Omnisend — 1 operation(s) for events. Version 2026-03-15, harvested from Omnisend's published contract.
- [Omnisend Images API](https://apis.io/apis/omnisend/omnisend-images-api/) — The Images API from Omnisend — 5 operation(s) for images. Version 2026-03-15, harvested from Omnisend's published contract.
- [Omnisend Products API](https://apis.io/apis/omnisend/omnisend-products-api/) — The Products API from Omnisend — 5 operation(s) for products. Version 2026-03-15, harvested from Omnisend's published contract.
- [Omnisend Segments API](https://apis.io/apis/omnisend/omnisend-segments-api/) — The Segments API from Omnisend — 6 operation(s) for segments. Version 2026-03-15, harvested from Omnisend's published contract.
- [Omnisend Automations API](https://apis.io/apis/omnisend/omnisend-automations-api/) — The Automations API from Omnisend — 13 operation(s) for creating, enabling, copying and restructuring event-triggered automation workflows, including the…
- [Omnisend Event Metadata API](https://apis.io/apis/omnisend/omnisend-event-metadata-api/) — The Event Metadata API from Omnisend — 3 operation(s) for declaring, merging and querying brand-custom event schemas. The only Omnisend operations that…
- [Omnisend Batch API](https://apis.io/apis/omnisend/omnisend-batch-api/) — The Batch API from Omnisend — 3 operation(s) for batch.
- [Omnisend Email Content API](https://apis.io/apis/omnisend/omnisend-email-content-api/) — The Email Content API from Omnisend — 2 operation(s) for email content.
- [Omnisend Email Templates API](https://apis.io/apis/omnisend/omnisend-email-templates-api/) — The Email Templates API from Omnisend — 4 operation(s) for email templates.
- [Omnisend Email Universal Layouts API](https://apis.io/apis/omnisend/omnisend-email-universal-layouts-api/) — The Email Universal Layouts API from Omnisend — 2 operation(s) for email universal layouts.
- [Omnisend Product Categories API](https://apis.io/apis/omnisend/omnisend-product-categories-api/) — The Product Categories API from Omnisend — 2 operation(s) for product categories.
- [Omnisend Reports API](https://apis.io/apis/omnisend/omnisend-reports-api/) — The Reports API from Omnisend — 1 operation(s) for reports.
- [Omnisend Statistics API](https://apis.io/apis/omnisend/omnisend-statistics-api/) — The Statistics API from Omnisend — 1 operation(s) for statistics.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (13)

Multi-step workflows that chain operations into a business task.

- [Omnisend Copy and Send Campaign](https://apis.io/arazzos/omnisend/omnisend-copy-and-send-campaign-workflow/)
- [Omnisend Create and Send Campaign](https://apis.io/arazzos/omnisend/omnisend-create-and-send-campaign-workflow/)
- [Omnisend Create and Verify Product Category](https://apis.io/arazzos/omnisend/omnisend-create-and-verify-category-workflow/)
- [Omnisend Create and Verify Contact](https://apis.io/arazzos/omnisend/omnisend-create-and-verify-contact-workflow/)
- [Omnisend Create and Verify Product](https://apis.io/arazzos/omnisend/omnisend-create-and-verify-product-workflow/)
- [Omnisend Create Segment and Read Statistics](https://apis.io/arazzos/omnisend/omnisend-create-segment-and-stats-workflow/)
- [Omnisend Refresh Product Catalog Entry](https://apis.io/arazzos/omnisend/omnisend-replace-product-workflow/)
- [Omnisend Subscribe and Trigger Welcome](https://apis.io/arazzos/omnisend/omnisend-subscribe-and-welcome-workflow/)
- [Omnisend Create and Tag Contact](https://apis.io/arazzos/omnisend/omnisend-tag-contact-workflow/)
- [Omnisend Track Added-to-Cart Event](https://apis.io/arazzos/omnisend/omnisend-track-cart-event-workflow/)
- [Omnisend Track Placed Order Event](https://apis.io/arazzos/omnisend/omnisend-track-order-event-workflow/)
- [Omnisend Update Product Category](https://apis.io/arazzos/omnisend/omnisend-update-category-workflow/)
- [Omnisend Upsert a Contact](https://apis.io/arazzos/omnisend/omnisend-upsert-contact-workflow/)

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Omnisend Webhooks](https://apis.io/asyncapis/omnisend/omnisend-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [omnisend-mcp.yml](https://apis.io/servers/omnisend/omnisend-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Omnisend Agentic Access](https://apis.io/agentic-access/omnisend/omnisend-agentic-access/)

#### JSON Schema (2)

The data models the API reads and writes.

- [Omnisend Contact](https://apis.io/schemas/omnisend/omnisend-contact/)
- [Omnisend Customer Event](https://apis.io/schemas/omnisend/omnisend-event/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Omnisend Context](https://apis.io/jsonld/omnisend/omnisend-context/)

#### Collections (17)

Postman and Open Collection request collections.

- [Omnisend REST API](https://apis.io/collections/omnisend/open-omnisend/)
- [Analytics API](https://apis.io/collections/omnisend/open-omnisend-analytics-api/)
- [Automations API](https://apis.io/collections/omnisend/open-omnisend-automations-api/)
- [Batches API](https://apis.io/collections/omnisend/open-omnisend-batches-api/)
- [Brands API](https://apis.io/collections/omnisend/open-omnisend-brands-api/)
- [Campaigns API](https://apis.io/collections/omnisend/open-omnisend-campaigns-api/)
- [Contacts API](https://apis.io/collections/omnisend/open-omnisend-contacts-api/)
- [Email Content API](https://apis.io/collections/omnisend/open-omnisend-emailcontent-api/)
- [Email Templates API](https://apis.io/collections/omnisend/open-omnisend-emailtemplates-api/)
- [Email Universal Layouts API](https://apis.io/collections/omnisend/open-omnisend-emailuniversallayouts-api/)
- [Event Metadata API](https://apis.io/collections/omnisend/open-omnisend-event-metadata-api/)
- [Events API](https://apis.io/collections/omnisend/open-omnisend-events-api/)
- [Images API](https://apis.io/collections/omnisend/open-omnisend-images-api/)
- [Product Categories API](https://apis.io/collections/omnisend/open-omnisend-productcategories-api/)
- [Products API](https://apis.io/collections/omnisend/open-omnisend-products-api/)
- [Segments API](https://apis.io/collections/omnisend/open-omnisend-segments-api/)
- [Omnisend REST API](https://apis.io/collections/omnisend/postman-omnisend/)

#### Overlays (31)

OpenAPI overlays, including conversational phrasing for each operation.

- [Omnisend Analytics Api Overlay](https://apis.io/overlays/omnisend/omnisend-analytics-api-overlay/)
- [Omnisend Automations Api Overlay](https://apis.io/overlays/omnisend/omnisend-automations-api-overlay/)
- [Omnisend Automations Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-automations-api-phrasing-overlay/)
- [Omnisend Batch Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-batch-api-phrasing-overlay/)
- [Omnisend Batches Api Overlay](https://apis.io/overlays/omnisend/omnisend-batches-api-overlay/)
- [Omnisend Brands Api Overlay](https://apis.io/overlays/omnisend/omnisend-brands-api-overlay/)
- [Omnisend Brands Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-brands-api-phrasing-overlay/)
- [Omnisend Campaigns Api Overlay](https://apis.io/overlays/omnisend/omnisend-campaigns-api-overlay/)
- [Omnisend Campaigns Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-campaigns-api-phrasing-overlay/)
- [Omnisend Contacts Api Overlay](https://apis.io/overlays/omnisend/omnisend-contacts-api-overlay/)
- [Omnisend Contacts Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-contacts-api-phrasing-overlay/)
- [Omnisend Email Content Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-email-content-api-phrasing-overlay/)
- [Omnisend Email Templates Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-email-templates-api-phrasing-overlay/)
- [Omnisend Email Universal Layouts Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-email-universal-layouts-api-phrasing-overlay/)
- [Omnisend Emailcontent Api Overlay](https://apis.io/overlays/omnisend/omnisend-emailcontent-api-overlay/)
- [Omnisend Emailtemplates Api Overlay](https://apis.io/overlays/omnisend/omnisend-emailtemplates-api-overlay/)
- [Omnisend Emailuniversallayouts Api Overlay](https://apis.io/overlays/omnisend/omnisend-emailuniversallayouts-api-overlay/)
- [Omnisend Event Metadata Api Overlay](https://apis.io/overlays/omnisend/omnisend-event-metadata-api-overlay/)
- [Omnisend Event Metadata Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-event-metadata-api-phrasing-overlay/)
- [Omnisend Events Api Overlay](https://apis.io/overlays/omnisend/omnisend-events-api-overlay/)
- [Omnisend Events Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-events-api-phrasing-overlay/)
- [Omnisend Images Api Overlay](https://apis.io/overlays/omnisend/omnisend-images-api-overlay/)
- [Omnisend Images Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-images-api-phrasing-overlay/)
- [Omnisend Product Categories Api Phrasing Overlay](https://apis.io/overlays/omnisend/omnisend-product-categories-api-phrasing-overlay/)
- [Omnisend Productcategories Api Overlay](https://apis.io/overlays/omnisend/omnisend-productcategories-api-overlay/)
- …and 6 more published on APIs.io

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Omnisend — jsonschema rules](https://apis.io/rules/omnisend/omnisend-jsonschema-spectral-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Omnisend Authentication](https://apis.io/security/omnisend/omnisend-authentication/)
- [Omnisend Domain Security](https://apis.io/security/omnisend/omnisend-domain-security/)
- [Omnisend Vulnerability Disclosure](https://apis.io/security/omnisend/omnisend-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Omnisend Scopes](https://apis.io/scopes/omnisend/omnisend-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Omnisend Plans Pricing](https://apis.io/plans/omnisend/omnisend-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Omnisend Rate Limits](https://apis.io/rate-limits/omnisend/omnisend-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Omnisend Finops](https://apis.io/finops/omnisend/omnisend-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.omnisend.com)
- [Documentation](https://api-docs.omnisend.com)
- [Getting started](https://api-docs.omnisend.com/docs/getting-started)
- [API reference](https://api-docs.omnisend.com/reference/overview)
- [Pricing](https://www.omnisend.com/pricing)
- [Sign up](https://app.omnisend.com/signup)
- [Support](https://support.omnisend.com)
- [Changelog](https://www.omnisend.com/changelog/)
- [Blog](https://www.omnisend.com/blog)
- [Terms of service](https://www.omnisend.com/terms)
- [Privacy policy](https://www.omnisend.com/privacy)
- [GitHub](https://github.com/omnisend)
- [Status](https://status.omnisend.com)

## API Evangelist rating

**Kin Score 73.0** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 68.6 |
| Contract governance | 28.0 |
| Operational transparency | 97.4 |
| Developer ergonomics | 49.4 |
| Access clarity | 77.6 |

**Agent readiness 58.2** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 40.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/omnisend/](https://apis.io/providers/omnisend/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Omnisend: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/omnisend/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
