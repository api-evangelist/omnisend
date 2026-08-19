---
name: omnisend-sync-product-catalog
description: Sync a product catalog and its categories into Omnisend, in bulk, for product recommendations and abandonment automations.
api: Omnisend Products API + Product Categories API + Batches API
version: '2026-03-15'
base: https://api.omnisend.com/api
spec: openapi/omnisend-products-api-openapi.yml
operations:
  - GET /products
  - POST /products
  - GET /products/{productID}
  - PUT /products/{productID}
  - DELETE /products/{productID}
  - GET /product-categories
  - POST /product-categories
  - PATCH /product-categories/{categoryID}
  - DELETE /product-categories/{categoryID}
  - POST /batches
  - GET /batches/{batchID}
  - GET /batches/{batchID}/items
scopes: [products.read, products.write]
---

# Sync a product catalog

Headers: `Authorization: Omnisend-API-Key {key}` and `Omnisend-Version: 2026-03-15`.

## Order matters

Create **categories first**, then products that reference them by `categoryID`. A product also
carries an `imageID` referencing an image uploaded through the Images API.

## Single-item operations

| Purpose | Call |
|---|---|
| List | `GET /products` — cursor paginated, `limit` max 250 |
| Create | `POST /products` |
| Read | `GET /products/{productID}` |
| Replace | `PUT /products/{productID}` — full replacement, not partial |
| Delete | `DELETE /products/{productID}` |

Categories mirror this except that update is `PATCH /product-categories/{categoryID}` (partial),
not `PUT`. Omnisend documents the distinction deliberately: PATCH for partial, PUT for replace.

All of these are 400 requests/minute per brand.

## Bulk — use batches for anything above a few dozen items

```
POST https://api.omnisend.com/api/batches
```

- Up to **100 actions per batch**.
- `POST` batch operations create; `PUT` batch operations update.
- Required scopes depend on the payload type (`products.write` here).
- Creation is **asynchronous**. Poll `GET /batches/{batchID}` for status and
  `GET /batches/{batchID}/items` for per-item outcomes.

Omnisend recommends batches explicitly as the way to avoid hitting rate limits.

## Retry rules

There is no idempotency key. `PUT /products/{productID}` is naturally replay-safe because it is a
full replacement against a caller-supplied id — prefer it over `POST /products` when re-running a
sync. `POST /batches` is **not** replay-safe: a retried batch will duplicate its create actions.
Record the returned `batchID` before retrying anything.

On 429 read `retryAfter` (seconds) from the RFC 9457 body; Omnisend publishes no rate-limit headers.

## Images

`POST /images` uploads by public URL; `POST /images/upload` uploads a file. JPEG, PNG, GIF, WebP,
max 5 MB. Non-image types return **415**.
