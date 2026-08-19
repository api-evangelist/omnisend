---
name: omnisend-automation-webhook
description: Create an Omnisend automation that POSTs a webhook to an external system when a contact hits a workflow step — Omnisend's only outbound webhook mechanism.
api: Omnisend Automations API
version: '2026-03-15'
base: https://api.omnisend.com/api
spec: openapi/omnisend-automations-api-openapi.yml
operations:
  - POST /automations
  - GET /automations/{id}
  - PATCH /automations/{id}
  - PUT /automations/{id}/blocks
  - POST /automations/{id}/enable
  - POST /automations/{id}/disable
  - POST /automations/{id}/copy
  - DELETE /automations/{id}
scopes: [automations.read, automations.write]
---

# Send a webhook from an automation

Omnisend has **no webhook subscription API**. You do not register an endpoint and pick events. Instead
you create an automation whose trigger is an event and whose action block is `sendWebhook`. That is
the entire outbound mechanism.

Prerequisites: `automations.write` scope, a **paid plan** (automation webhooks are not on the free
plan), and an HTTPS receiver.

## 1. Create the workflow, disabled

```
POST https://api.omnisend.com/api/automations
Authorization: Omnisend-API-Key {key}
Omnisend-Version: 2026-03-15

{
  "name": "New Subscriber Webhook",
  "trigger": { "condition": { "event": "subscribed to marketing" } },
  "blocks": [
    { "temporaryID": "wait-5m", "type": "delay",
      "delay": { "mode": "duration", "duration": { "amount": 5, "units": "m" } } },
    { "temporaryID": "webhook-notify", "type": "action",
      "action": { "type": "sendWebhook", "sendWebhook": {
        "callbackUrl": "https://example.com/webhooks/omnisend",
        "headers": [ { "key": "X-Webhook-Secret", "value": "my-shared-secret" } ],
        "body": "{\"contactEmail\": \"[[contact.email]]\", \"event\": \"subscribed\"}"
      } } }
  ]
}
```

The response returns the automation **disabled**, with server-assigned block `id`s replacing each
`temporaryID`.

### callbackUrl rules the API enforces
HTTPS only. IP literals, non-443 ports, non-FQDN hosts and internal/private addresses are all
rejected.

### body rules
Must be valid JSON as a string. Personalization tags are substituted:
`[[contact.email]]`, `[[contact.first_name]]`, `[[event.raw.<property>]]`.

### trigger rules
`trigger.condition.event` must be a valid event for the brand. Some events (e.g. `placed order`)
require an `origin` naming the source platform.

## 2. Verify

`GET /automations/{id}` and inspect the `blocks` array for the resolved webhook block.

## 3. Enable

`POST /automations/{id}/enable`. Optional body `enrollExisting` also enrolls contacts who already
qualify; omitted or false means only new trigger events enrol.

## 4. Change it later — disable first

**An enabled automation cannot be patched or restructured.** `PATCH /automations/{id}` and
`PUT /automations/{id}/blocks` return 409 while enabled. The sequence is:

1. `POST /automations/{id}/disable` — with `contactsInWorkflow` controlling whether in-flight contacts
   `keep` progressing or are removed.
2. Make the change.
3. `POST /automations/{id}/enable`.

`PUT /automations/{id}/blocks` **replaces the whole tree**: blocks with `id` are updated in place,
blocks with `temporaryID` are created, and any existing block you leave out is **deleted**. Read the
current tree first.

## Copy and delete

`POST /automations/{id}/copy` always creates the copy **disabled**, named `Copy of: …` unless you
supply a name. `DELETE /automations/{id}` is documented as **idempotent** — deleting a non-existent
automation returns success. It is the only idempotent write in this API.

## Receiving end

Omnisend does **not sign** the callback. There is no HMAC header, no timestamp and no published
verification procedure — a shared secret in a custom header is the only integrity control offered,
and no retry or delivery guarantee is documented. Treat the receiver as unauthenticated: verify the
shared secret, make your handler idempotent yourself, and do not trust payload contents.
