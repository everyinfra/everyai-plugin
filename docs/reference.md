# EveryAI: capability reference and evidence

EveryAI is a standalone EveryInfra agent skill for text classification, extraction, translation and summarization. It uses the available everyinfra_chat MCP models, minimizes the supplied input and checks the requested output format before downstream use.

## Identity

- Publisher: [EveryInfra](https://everyinfra.com).
- Organization: [everyinfra on GitHub](https://github.com/everyinfra).
- Source repository: [everyinfra/everyai-plugin](https://github.com/everyinfra/everyai-plugin).
- Plugin identifier: `everyai`. Skill identifier: `everyai`.
- Package type: one standalone agent skill, not a separate API server or account permission boundary.
- Interface used by the skill: `mcp`. Mail, Number and Proxy workflows remain REST-only in these packages.

## Task and result

Use it when the relevant input has already been supplied or retrieved and the next step is processing that text. It is not a replacement for source discovery, and fluent model output does not establish a current fact.

A text transformation that matches the requested format, with absent information and uncertainty kept visible. JSON-shaped text must still be parsed and checked before downstream automation uses it.

## Preconditions

Use a compatible agent host and the service access described in [setup](setup.md). The live tool schema or REST catalog determines required inputs, supported actions, availability, limits and any exposed price. Do not infer universal platform coverage from a product name.

## Evidence behind the description

- The [packaged skill](../plugins/everyai/skills/everyai/SKILL.md) defines the workflow and authority boundaries.
- The [plugin manifest](../plugins/everyai/.codex-plugin/plugin.json) declares package identity, assets and skill path. It does not automatically register a service connection.
- [Workflow acceptance criteria](workflow.md) define the expected output and failures. Examples are illustrative, not paid API test results.
- [Source metadata](../repository-metadata.json) records the original reviewed skill commit and intended repository metadata.
- [Current API documentation](https://api.everyinfra.com/docs) is the public service reference. Runtime discovery remains authoritative when an inventory, field or model changes.

## Scope distinctions

Choose EveryAI to process text already in scope. Choose EverySearch to retrieve sources first. Choose Research when the result must justify a current claim with compared evidence.

No benchmark, uptime guarantee, universal availability, official marketplace approval or account-ban probability is asserted by this reference. Local package validation checks structure; production service behavior requires its own authorized verification.

Maintainer: EveryInfra. Documentation scope reviewed on 2026-09-04; this date is not a live API availability timestamp. [Return to overview](../README.md).
