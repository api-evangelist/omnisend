---
name: omnisend-sync-contact
description: Create or update an Omnisend contact and apply tags, using the 2026-03-15 contract.
api: Omnisend Contacts API
version: '2026-03-15'
base: https://api.omnisend.com/api
spec: openapi/omnisend-contacts-api-openapi.yml
operations:
  - POST /contacts
  - GET /contacts
  - GET /contacts/{id}
  - PATCH /contacts
  - PATCH /contacts/{id}
  - POST /contacts/tags
scopes: [contacts.read, contacts.write]
---

# Sync a contact into Omnisend

Every request needs two headers, not one:

```
Authorization: Omnisend-API-Key {key}     # or: Authorization: Bearer {oauth-token}
Omnisend-Version: 2026-03-15
```

Omitting `Omnisend-Version` fails. Naming a retired version returns **410 Gone**, not a warning.

## 1. Upsert the contact

`POST /contacts` is an upsert keyed on the email identifier.

```
POST https://api.omnisend.com/api/contacts
{
  "identifiers": [
    { "type": "email", "id": "hello@example.com",
      "channels": { "email": { "status": "subscribed", "statusDate": "2026-08-13T10:07:28Z" } } }
  ]
}
```

- **201 Created** — a new contact.
- **200 OK** — an existing contact was updated.

Branch on the status code; the body shape is the same.

## 2. Update an existing contact

Two paths, because a contact has no single primary key:

- `PATCH /contacts` — match by email address in the body.
- `PATCH /contacts/{id}` — match by the Omnisend contact id.

Use `PATCH` for partial updates. Omnisend documents `PUT` as full replacement and does not offer it on contacts.

## 3. Tag in bulk

`POST /contacts/tags` (add) and `DELETE /contacts/tags` (remove) select contacts by any combination of
`contactIDs`, `emails`, `phones` or `segmentID`. At least one selector is required. Selectors are
**additive** — the union is tagged, and a contact matched twice is tagged once. Emails and phones with
no match are silently ignored.

Both are rate limited to **60 requests/minute** (the general limit is 400) and are **asynchronous** —
the tag may not be visible on the next read.

## 4. List with filters

`GET /contacts` supports `email`, `phone`, `status`, `segmentID`, `tag`, `updatedAtFrom`, plus
`limit` (max 250, default 100), `after`/`before`, `sort` and `direction`.

Two filter rules the API enforces with **400**:
- `tag` and `status` cannot be combined.
- `updatedAtFrom` cannot be combined with `email`, `phone`, `status`, `segmentID` or `tag`.

Unknown query parameters also return 400 — Omnisend rejects rather than ignores them.

## Paginate

Read `paging.cursors.after` and pass it back as `?after=`. Stop when `paging.hasMore` is false or the
cursor is null. Do not send `after` and `before` together. Do not change filters mid-pagination — that
returns 400.

## Retry rules

**There is no idempotency key on this API.** `POST /contacts` is safe to replay only because it is an
upsert on email. Nothing else here is. On a 429, read `retryAfter` (seconds) from the RFC 9457 body —
there is no `Retry-After` header and no rate-limit headers at all. On a 5xx or 524, quote the
`instance` trace id (`urn:omnisend:request:{uuid}`) to support and check
https://app.omnisend.com/integrations/api-access-logs.
