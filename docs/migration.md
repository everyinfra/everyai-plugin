# EveryAI cleanup transition

> Production advertises source-bound cleanup alongside the existing `everyinfra_chat` compatibility
> tool. Always confirm both cleanup tools through live MCP discovery; availability does not prove a
> particular account is eligible, activated or end-to-end tested.

## What is changing

EveryAI currently processes supplied text through the general-purpose chat contract. The planned
direction moves cleanup of EveryData results to a separate, source-bound entitlement rather than
making general chat free or silently changing the meaning of `everyinfra_chat`.

The initial cleanup policy has been approved for implementation with these limits:

| Dimension | Planned contract | Not implied |
| --- | --- | --- |
| Eligibility | Direct account with at least CNY 500.00 in verified net settled recharge principal | Wallet balance, bonus credit, or an unverified redemption code is not eligibility evidence. |
| Activation | Explicit, one-time activation | Reading entitlement status does not start the period. |
| Trial | 30 days, at most 30,000 successful units | It is not permanent or unlimited access. |
| Daily use | At most 1,000 successful units per UTC day | Failed attempts do not become successful usage. |
| Submit rate | 5 execute attempts per minute per account | Multiple API keys do not multiply the limit. |
| Concurrency | At most 5 execution units per account | It is not evidence of available production capacity. |

Cleanup remains bound to an authorized, readable EveryData source and a server-declared recipe. It
does not accept arbitrary chat history, customer-defined system prompts, model selection, tools,
external URLs, or a free-form output schema.

## Live 15-operation surface

Production uses two MCP tools and 15 operations. Always re-read the live `tools/list` and schemas.

| Tool | Operations | Purpose |
| --- | --- | --- |
| `everyinfra_data_cleanup_read` | `get_entitlement`, `get_source`, `get_source_fields`, `list_recipes`, `preview`, `list_jobs`, `find_job`, `get_job`, `list_units`, `get_result`, `export` | Inspect eligibility and current policy, discover a source version and fields, preview fixed recipes, recover the original task, and read/export terminal results. |
| `everyinfra_data_cleanup_action` | `activate`, `submit`, `cancel`, `delete_result` | Explicitly start the included period, submit an idempotent task, request cancellation, or delete result content. |

At execution time, call `tools/list`, confirm both tool names are present, then read the returned
schemas. If they are absent, keep using `everyinfra_chat` only for ordinary user-supplied text and
report source-bound cleanup as unavailable. Do not create a guessed request from this table.

### Refresh recovery and field discovery

- `list_jobs` returns the current account's unexpired tasks with bounded cursor pagination.
- `find_job` uses the original submission idempotency key to find that same task after an unknown
  response or refresh. Preserve the key outside the URL and analytics. A 404 does not prove the
  interrupted request was never accepted, so do not automatically submit with a new key.
- `get_source_fields` returns bounded inferred field paths and types without example values. Use the
  returned source version and treat inference as selection help; actual recipe validity is decided
  by `preview`.

## Choose the correct path

| Request | Current behavior | After a public cleanup contract exists |
| --- | --- | --- |
| Transform text the user already supplied | Use `everyinfra_chat` when it remains present in the live schema and the operation is authorized. | Follow the published compatibility or retirement notice; cleanup is not automatically an equivalent replacement. |
| Clean an EveryData result | Discover the live cleanup tools or REST operations, verify entitlement and source version, preview, then submit only after authorization. Do not relabel general chat as the cleanup entitlement. | Follow the same source-bound contract and any dated compatibility notice. |
| Normalize data deterministically | Prefer ordinary code when it can produce the result without a model. | The same rule continues; model cleanup is not mandatory. |
| Verify a current claim | Use EverySearch or a research workflow. | Cleanup output still does not prove a current fact. |

Never invent cleanup tool names or payloads from this document. The live MCP `tools/list` and public
OpenAPI document are the runtime contract. If they do not advertise cleanup, stop with a clear
availability result instead of sending the source through general chat as a fallback.

## Migration sequence

1. Keep existing authorized `everyinfra_chat` calls working while the compatibility interface is
   still published; no retirement date is declared here.
2. Inventory which calls transform user-supplied text and which calls process EveryData results.
3. For source-bound requests, discover the public cleanup schema and preserve the server-issued
   source reference and version.
4. Use discovery, entitlement inspection, preview, explicit activation and idempotent submission in
   that order.
5. Treat an unknown submission result as the original operation to inspect. Do not change an
   idempotency key or fall back to chat to repeat work whose outcome is unknown.
6. Retire old integrations only after a dated notice and the announced compatibility period. The
   compatibility period and an account's cleanup trial are separate clocks.

## Delivery layers

- **Skill:** instructions that help an agent choose and execute the workflow; editing a Skill does
  not add a server capability.
- **MCP:** the live runtime tool connection and schemas; a cleanup claim requires the production
  server to advertise and execute it.
- **Plugin:** the installable package that can distribute Skills and MCP metadata; publishing or
  installing it does not prove the service is enabled for an account.

Return to the [EveryAI overview](../README.md) or [workflow](workflow.md).
