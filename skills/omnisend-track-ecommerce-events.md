---
name: omnisend-track-ecommerce-events
description: Send customer events into Omnisend to trigger automations, and declare custom event schemas before segmenting on them.
api: Omnisend Events API + Event Metadata API
version: '2026-03-15'
base: https://api.omnisend.com/api
spec: openapi/omnisend-events-api-openapi.yml
operations:
  - POST /events
  - POST /event-metadata
  - PUT /event-metadata
  - POST /event-metadata/query
scopes: [events.write, events.read]
---

# Track customer events

Headers: `Authorization: Omnisend-API-Key {key}` and `Omnisend-Version: 2026-03-15`.

## Predefined ecommerce events

Omnisend documents a fixed set that drives its prebuilt automations:

`added product to cart`, `started checkout`, `placed order`, `paid for order`, `ordered product`,
`order refunded`, `order fulfilled`, `order canceled`, `viewed product`, `viewed page`,
`subscribed to marketing`, `opened message`, `clicked message`, `marked message as spam`.

An event is identified by **name + origin**. Where a name exists under multiple origins (for example
`placed order` under `shopify`), `origin` becomes required.

## 1. Send an event

`POST /events` — 400 requests/minute, scope `events.write`.

## 2. Declare a custom event before you segment on it

A brand-custom event must be declared, with at least one top-level property, before its properties
can be used in a segment filter. Operations here are the only ones in the whole Omnisend contract
that carry an `operationId`:

- `post_event_metadata` — `POST /event-metadata`. Creates a schema. Identity is `name` + `origin`;
  `displayName` and at least one top-level property are required. Optional metadata fields must be
  **omitted, not sent as null**. Every node comes back flagged `explicitlyDefined`.
- `put_event_metadata` — `PUT /event-metadata`. Merges. Only supplied fields apply; omitted metadata
  and omitted properties are preserved and no property is deleted. **The type of an already
  explicitly-defined property cannot change.**
- `post_event_metadata_query` — `POST /event-metadata/query`. Reads back metadata for a category
  (`automations`, `events`, `segments`), optionally filtered by `events` (exact, case-sensitive) and
  `origins`. Set `includeProperties: true` for the nested property tree; set
  `excludeCustomEvents: true` for a predictable response size over standard events only.

Events a category exposes depend on the requested `Omnisend-Version`; a date between releases
resolves to the nearest earlier supported version. Brand-custom events are not version-scoped.

`PUT /event-metadata` can return **503** with "The event metadata was modified concurrently; retry
the request" — that is optimistic-concurrency loss and retry is safe there.

## 3. Browser-side tracking

For client-side events, load the snippet and push onto the queue:

```html
<script type="text/javascript">
  window.omnisend = window.omnisend || [];
  omnisend.push(["brandID", "<YOUR_BRAND_ID>"]);
  omnisend.push(["track", "$pageViewed"]);
</script>
```

`omnisend.identifyContact({ email, phone })` ties the browser session to a contact (phone in E.164).
`omnisend.push(["track", "<eventName>", { ..., callbacks: { onSuccess, onError } }])` sends an event.

## Backfilling history — read this before you run it

Omnisend's own documentation warns: **before sending a batch of events, confirm no automation is
configured that would message customers from the imported data.** Historic imports will otherwise
fire live sends to real people.

There is **no idempotency key** on this API, so a retried or replayed event ingest duplicates. Use
`POST /batches` (max 100 actions, asynchronous — poll `GET /batches/{batchID}`) for bulk, disable the
relevant automations first, and re-enable afterwards.
