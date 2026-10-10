# EveryAI plugin

Run bounded text classification, extraction, translation and summarization with EveryAI. Discover available models and validate the requested output format.

This package contains only `everyai`. It is a skills-only plugin: configure the approved EveryInfra service connection in the host before using it. It does not install other skills, register a new MCP server or broaden API permissions.

Text processing, including cleaning and labeling collected data, goes through the AI API
(`everyinfra_chat` or OpenAI-compatible REST), free for accounts that have topped up. The former
data cleanup tools were retired on 2026-10-09.

A text transformation that matches the requested format, with absent information and uncertainty kept visible. JSON-shaped text must still be parsed and checked before downstream automation uses it.

- Models and parameters depend on the live schema; no fixed model inventory or quality benchmark is promised here.
- Do not send secrets or unrelated private data as context.
- MCP and the OpenAI-compatible REST interface have different setup paths; installing this skill does not create an API credential.

Repository documentation and installation guidance accompany the source checkout. Current API documentation: https://api.everyinfra.com/docs
