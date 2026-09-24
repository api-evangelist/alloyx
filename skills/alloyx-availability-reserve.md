---
name: alloyx-availability-reserve
description: Reserve a time slot by querying availability, holding the slot, and optionally releasing it.
api: openapi/_original/usp-rest.json
operations:
- queryAvailability
- holdSlot
- releaseSlot
generated: '2026-09-24'
method: generated
generator: extract-docs-artifacts.py skills (local)
source: openapi/_original/usp-rest.json ; every operationId checked against the contract
---

# alloyx-availability-reserve

Reserve a time slot by querying availability, holding the slot, and optionally releasing it.

## Steps

1. 1. Call `queryAvailability` with the required request body fields as defined in the contract.
2. 2. Call `holdSlot` with the fields returned from the query to create a hold, using the `Authorization` header for authentication.
3. 3. If needed, call `releaseSlot` with the path parameter `hold_id` to free the held slot, also providing the `Authorization` header.

## Rules

- Authentication: Include the `Authorization` header with a valid API key or OAuth2 bearer token as defined by the provider's auth schemes.
- Idempotency: The `holdSlot` operation should be called only once per desired reservation; repeated calls may create multiple holds.
