---
name: ask-expert
description: Ask one PickMyBrain expert by name (id, slug, or display name) in that persona's own voice.
---

# Ask one expert by name

Use the MCP tool **`ask_expert`** when the reader wants **one persona's answer**
in **that expert's own voice** — not a multi-expert synthesis.

## When to use

- «Ask Naval …»
- «What would Buffett say about …?»
- «Talk to &lt;expert name&gt; about …»

Match on **id**, **slug**, **display name**, or **short name**. Do **not** match
on tagline or topic alone — that is what **`ask_experts`** is for.

## Rules

1. **One question → one tool call.** Do not retry the same question in a loop.
2. **Attribute answers to the named expert.** Quote them; do not present their
   voice as your own.
3. Each call **writes that expert's thread** and **spends the daily budget**.
4. Pass `conversation_id` to continue the **same persona thread**.

## Ambiguous or missing names

- **`NotFound`** (no model call): tell the reader no expert matched; suggest
  checking spelling or browsing their catalog.
- **`Ambiguous`** (no model call): list `structuredContent.candidates` and ask
  the reader to pick the full name or `id`, then call again with that name.
- Do **not** guess when several experts match.

## Thread boundaries

- A `conversation_id` from **`ask_experts`** (global thread) **cannot** continue
  in `ask_expert`. Omit `conversation_id` to start a new persona thread.
- If the tool says the thread belongs to another persona, omit `conversation_id`
  or use the correct expert's thread.
