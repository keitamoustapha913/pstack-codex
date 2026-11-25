---
name: make-bot-ui
description: >-
  Use when building a custom UI (page, dashboard, buttons) that should wake a
  Grok Bot over a webhook, when the user must provide a webhook sender key, or
  when exposing that UI on Tailscale.
---

**Codex host:** Read `../poteto-mode/references/codex-compatibility.md` relative to this SKILL.md before executing. Its host mappings govern all downstream instructions and resources; retain the original workflow.
# How to make a bot UI

**Codex limitation:** This is the original Cursor/Grok webhook routine workflow, kept for reference. Do not execute the legacy routine/secret tools or use a Grok model. Only proceed with an explicitly authorized Codex/OpenAI-compatible webhook and secret mechanism that has been verified in the active runtime; adapt the host-specific steps to that mechanism. If unavailable, report this workflow as blocked. Never expose a sender key or bind a server externally without authorization.

Build a page the user clicks. A server on this computer POSTs JSON to a webhook routine. The bot wakes with that JSON. Keep the sender key on the server. Do not put the sender key in the browser, in chat, or in this skill.

Read `references/upstream-webhook-workflow.md` for the original workflow and its output/security contract. Translate its steps only after identifying a supported, explicitly authorized OpenAI-compatible webhook trigger, secret storage, and hosting surface. Keep secrets server-side, treat incoming payloads as untrusted data, verify a harmless payload, and do not expose the service to other machines without approval. If the host cannot support those steps, report the blocker rather than inventing a tool, invoking a disallowed model, or claiming a routine was created.
