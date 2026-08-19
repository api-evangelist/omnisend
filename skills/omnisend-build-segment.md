---
name: omnisend-build-segment
description: Build and measure an Omnisend segment from contact and event conditions, working around the building state and the tightest rate limits in the API.
api: Omnisend Segments API
version: '2026-03-15'
base: https://api.omnisend.com/api
spec: openapi/omnisend-segments-api-openapi.yml
operations:
  - GET /segments
  - POST /segments
  - GET /segments/{segmentID}
  - PUT /segments/{segmentID}
  - DELETE /segments/{segmentID}
  - GET /segments/{segmentID}/statistics
scopes: [segments.read, segments.write]
---

# Build a segment

Headers: `Authorization: Omnisend-API-Key {key}` and `Omnisend-Version: 2026-03-15`.

## Rate limits are the binding constraint

| Operation | Limit |
|---|---|
| `POST /segments`, `PUT /segments/{segmentID}` | **15 / minute** |
| `GET`, `DELETE` | 100 / minute |

These are the strictest limits Omnisend publishes. Batch your segment authoring; do not loop.

## Structure

```
conditionGroups[]     # OR between groups
  conditions[]        # AND between conditions
    entity: contact | event
    junction: and | or          # combines filters WITHIN one condition
    filters[]
```

## Contact filters

Valid `property` values: `email`, `phoneNumber`, `firstName`, `lastName`, `gender`, `country`,
`state`, `city`, `address`, `postalCode`, `lastDetectedCity`, `lastDetectedCountry`,
`customerLifecycleStage`, `tags`, `consent`, `averageOrderValue`, `totalSpent`, `dateAdded`,
`subscriptionStatus`, `birthday`, `custom`.

- Use `tags` (plural), never `tag`.
- When `property` is `custom`, supply both `name` and `valueType` (`text` | `number` | `bool` | `date`).
- `birthday` takes `valueType` `date` or `text` (text enables month matching like `"-05-"`).

## Event filters

Required: `name`, `operator` (`has`/`hasNot`), `count` (`atLeast`/`equals`), `value`.
Optional: `origin`, `period`, nested `filters` on the payload, `junction`.

`origin` is usually optional — supply it only when the event exists under several origins; otherwise
the API returns an error listing the valid values.

Periods: relative (`inTheLast`, `notInTheLast` with `unit` + `value`) or absolute (`equals`,
`before`, `after`, `between` with ISO `YYYY-MM-DD`).

Use `[]` as an array wildcard in property paths, chainable:
`raw.fulfillments.[].line_items.[].title`.

A custom event and its properties must have been **sent at least once** before they can be filtered on.

## The building state

After a write the segment enters a `building` state. While building:
- `PUT /segments/{segmentID}` returns **409 Conflict**
- `DELETE /segments/{segmentID}` returns **409 Conflict**

Poll `GET /segments/{segmentID}` until it leaves that state before writing again.

## Measure it

`GET /segments/{segmentID}/statistics` returns the total number of matching contacts. Do this before
attaching the segment to a campaign — it is the only pre-send size check available.

## Pagination

`GET /segments` is cursor-paginated. Sort fields: `createdAt` (default) and `name` (lexicographic,
case-sensitive). Single-field sorting only. Sort parameters are needed only on the first request;
the cursor carries them. If you pass sort parameters alongside a cursor they must match the cursor.
Cursors can become invalid if the referenced segment is deleted.
