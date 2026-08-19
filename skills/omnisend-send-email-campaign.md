---
name: omnisend-send-email-campaign
description: Create, preview, and send an Omnisend email campaign, respecting its draft-only state machine.
api: Omnisend Campaigns API
version: '2026-03-15'
base: https://api.omnisend.com/api
spec: openapi/omnisend-campaigns-api-openapi.yml
operations:
  - POST /campaigns
  - GET /campaigns/{id}
  - PATCH /campaigns/{id}
  - POST /campaigns/{id}/test-email
  - POST /campaigns/{id}/send
  - POST /campaigns/{id}/copy
  - POST /campaigns/{id}/cancel
  - PUT /campaigns/{id}/utm
scopes: [campaigns.read, campaigns.write]
---

# Send an email campaign

Headers on every call:

```
Authorization: Omnisend-API-Key {key}
Omnisend-Version: 2026-03-15
```

## The state machine is the whole job

`draft → scheduled → started → sent`, with `paused`, `stopped` and `canceled` branches.
**Only a `draft` can be updated or sent.** Every other transition attempt returns **409 Conflict**.

## 1. Create the draft

`POST /campaigns` returns a campaign in `draft`.

## 2. Set UTM tags (optional, draft only)

`PUT /campaigns/{id}/utm` replaces the tag set. Send a `tags` object for a regular campaign, a
`variants` object for an A/B campaign. The campaign must still be a draft.

## 3. Preview before sending

`POST /campaigns/{id}/test-email` renders the draft and emails it to up to **5** recipients using the
saved subject, sender and content. Email campaigns only. This is the safe rehearsal step — use it.

## 4. Send

`POST /campaigns/{id}/send` submits the draft. Behaviour follows the campaign's sending strategy:
immediate, or queued for a scheduled time with optional timezone optimisation.

**A campaign cannot be sent twice.** To send again, `POST /campaigns/{id}/copy` — which creates a new
draft prefixed `Copy of: ` with its own id — and send the copy.

## 5. Cancel

`POST /campaigns/{id}/cancel` is valid from `scheduled` or `paused` (any channel), or `started`
(email only). Anything else returns 409. For a started campaign cancellation is **best-effort**:
messages already in flight may still be delivered.

## A/B tests

`POST /campaigns/{id}/ab-test/stop` (valid while `started`), `.../ab-test/resume` (valid while
`stopped`), and `.../ab-test/winner` to pick a variant manually and route it into the send pipeline
immediately. Calling these on a campaign that is not an A/B test returns **422**, not 409.

## Boosters

A booster is a campaign whose `boosterSettings.campaignID` points at a parent. The parent must be a
regular email campaign in `draft` or `sent` — `scheduled` and `started` parents return 409. One
booster per parent. For a draft parent supply `boosterSettings.delay` (max 240 hours) rather than
`sendingSettings`; the booster is scheduled automatically when the parent sends.

## Errors that will actually happen

- **402 Payment Required** — the brand's plan or balance does not permit sending. Seen on send and test-email.
- **409** — wrong status for the transition. Re-read `GET /campaigns/{id}` and branch on `status`.
- **422** — right status, wrong kind of campaign (channel unsupported, no verified sender email, not an A/B parent).
- **429** — 400/minute per brand. Read `retryAfter` from the body; there is no header.

There is no idempotency key. A retried `POST /campaigns/{id}/send` is not safe — confirm state with
`GET /campaigns/{id}` before retrying anything.
