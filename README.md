# Omnisend (omnisend)

Omnisend is a Lithuanian-headquartered email and SMS marketing automation platform purpose-built for ecommerce, with first-class integrations into Shopify, BigCommerce, WooCommerce, Magento, Wix, Square Online, and other storefronts. The platform unifies automation workflows, campaign builders, segmentation, popups and forms, web push, product recommendations, A/B testing, and reporting to drive customer engagement and revenue. The REST API exposes contacts, events, products, product categories, segments, campaigns, batches, email templates, email content, universal layouts, images, brands, and analytics reports — authenticated with `X-API-KEY` or OAuth 2.0 with resource-scoped permissions for App Market integrations.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/omnisend/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

- Email Marketing, Marketing Automation, Ecommerce, SMS Marketing, Customer Engagement, Segmentation, Campaigns, Forms, Popups, Web Push

## Timestamps

- **Created:** 2026-05-11
- **Modified:** 2026-05-25

## APIs

### Omnisend REST API

Omnisend's REST API for ecommerce email and SMS marketing automation. Manage contacts, events, products, product categories, segments, campaigns, batches, email templates, email content, email universal layouts, images, brands, and analytics reports. `X-API-KEY` header authentication for server-to-server; OAuth 2.0 authorization-code flow for App Market apps. Cursor-based pagination across list endpoints.

**Human URL:** [https://api-docs.omnisend.com/reference/overview](https://api-docs.omnisend.com/reference/overview)

**Base URL:** `https://api.omnisend.com/v5`

- [Documentation](https://api-docs.omnisend.com/)
- [API Reference](https://api-docs.omnisend.com/reference/overview)
- [Authentication](https://api-docs.omnisend.com/reference/authentication)
- [OAuth](https://api-docs.omnisend.com/reference/oauth)
- [Postman Workspace](https://www.postman.com/omnisend-api/workspace/omnisend/overview)
- [llms.txt](https://api-docs.omnisend.com/llms.txt)
- [OpenAPI](openapi/omnisend-openapi.yml)
- [JSON Schema — Contact](json-schema/omnisend-contact-schema.json)
- [JSON Schema — Event](json-schema/omnisend-event-schema.json)
- [JSON-LD context](json-ld/omnisend-context.jsonld)
- [Naftiko Capability — Contacts](capabilities/contacts.yaml)
- [Naftiko Capability — Events](capabilities/events.yaml)
- [Naftiko Capability — Products](capabilities/products.yaml)
- [Naftiko Capability — Product Categories](capabilities/product-categories.yaml)
- [Naftiko Capability — Segments](capabilities/segments.yaml)
- [Naftiko Capability — Campaigns](capabilities/campaigns.yaml)
- [Naftiko Capability — Batches](capabilities/batches.yaml)
- [Naftiko Capability — Email Templates](capabilities/email-templates.yaml)
- [Naftiko Capability — Analytics Reports](capabilities/analytics-reports.yaml)

## Authentication

| Method | Detail |
|---|---|
| API Key | `X-API-KEY: <your_key>` HTTP header. Account-scoped. |
| OAuth 2.0 | Authorization-code flow for Omnisend App Market apps with resource-scoped permissions. |

### Common OAuth Scopes

`contacts.read`, `contacts.write`, `events.write`, `products.read`, `products.write`, `campaigns.read`, `campaigns.write`, `segments.read`, `segments.write`, `email-templates.read`, `email-templates.write`, `images.read`, `images.write`, `brands.read`, `brands.write`, `analytics.read`.

## Pricing

| Plan | Starting Price | Contacts | Emails / month | Notes |
|---|---|---|---|---|
| Free | $0 | 250 | 500 | 500 web push notifications |
| Standard | $11.20/mo | 500 | 6,000 | Unlimited web push, no Omnisend branding |
| Pro | $41.30/mo | 2,500 | Unlimited | SMS included (from $0.007/SMS), AI personalization |
| Enterprise | Contact Sales | 150,000+ | Unlimited | Custom SLA and dedicated account manager |

3-month prepay yields ~30% off Standard and Pro. SMS pricing varies by destination country and volume — see [omnisend.com/sms-pricing](https://www.omnisend.com/sms-pricing).

See [`plans/omnisend-plans-pricing.yml`](plans/omnisend-plans-pricing.yml) for the reconciled API Commons Plans definition.

## Rate Limits

The Omnisend REST API uses a fixed-window limiter. Most resources share a generous default budget; `segments` has tighter per-method caps; `batches` is capped at 100 actions per batch. Throttled responses return HTTP `429`. See [`rate-limits/omnisend-rate-limits.yml`](rate-limits/omnisend-rate-limits.yml) for the full breakdown.

## FinOps

Token-style metering on subscription tier (active contacts) plus usage-metered SMS, dedicated IP, and overages. See [`finops/omnisend-finops.yml`](finops/omnisend-finops.yml) for the FOCUS-aligned definition including meters, discount models, and unit economics (cost-per-contact, cost-per-email, revenue-per-email).

## SDKs, Plugins, and Integrations

| Type | Resource |
|---|---|
| SDK | [PHP SDK (omnisend/php-sdk)](https://github.com/omnisend/php-sdk) — official PHP v3 wrapper |
| Plugin | [WordPress (omnisend/wp-omnisend)](https://github.com/omnisend/wp-omnisend) |
| Plugin | [WordPress + SureCart](https://github.com/omnisend/wp-omnisend-surecart) |
| Plugin | [WordPress + Contact Form 7](https://github.com/omnisend/wp-omnisend-contact-form-7) |
| Plugin | [WordPress + Gravity Forms](https://github.com/omnisend/wp-omnisend-gravity-forms) |
| Plugin | [WordPress + Ninja Forms](https://github.com/omnisend/wp-omnisend-ninja-forms) |
| Plugin | [WordPress + Formidable Forms](https://github.com/omnisend/wp-omnisend-formidable-forms) |
| Plugin | [WordPress + Paid Memberships Pro](https://github.com/omnisend/wp-omnisend-paid-memberships-pro) |
| Plugin | [WordPress + LifterLMS](https://github.com/omnisend/wp-omnisend-lifterlms) |
| Plugin | [Magento 2 (omnisend/magento2-plugin)](https://github.com/omnisend/magento2-plugin) |
| Integration | [Shopify](https://www.omnisend.com/integrations/shopify) |
| Integration | [BigCommerce](https://www.omnisend.com/integrations/bigcommerce) |
| Integration | [WooCommerce](https://www.omnisend.com/integrations/woocommerce) |
| Catalog | [Omnisend App Market](https://www.omnisend.com/app-market) — 130+ integrations |

## Common Resources

- [Website](https://www.omnisend.com)
- [Documentation](https://api-docs.omnisend.com)
- [API Reference](https://api-docs.omnisend.com/reference/overview)
- [Changelog](https://api-docs.omnisend.com/changelog)
- [Status Page](https://status.omnisend.com)
- [Support](https://support.omnisend.com)
- [Sign Up](https://app.omnisend.com/signup)
- [Login](https://app.omnisend.com/login)
- [Blog](https://www.omnisend.com/blog)
- [GitHub Organization](https://github.com/omnisend)
- [LinkedIn](https://www.linkedin.com/company/omnisend)
- [Privacy Policy](https://www.omnisend.com/privacy)
- [Terms of Service](https://www.omnisend.com/terms)

## Maintainers

- Kin Lane — kin@apievangelist.com — [apievangelist.com](https://apievangelist.com)
