---
name: ask-experts
description: Fan out one question to every expert in the caller's PickMyBrain catalog and return a neutral synthesis with attributed quotes.
---

# Ask the experts

Use the MCP tool **`ask_experts`** when the reader wants a **neutral synthesis**
across **every expert they can see** — not one persona's voice.

## When to use

- «What do my experts think about …?»
- «Compare perspectives on …»
- «Ask everyone …»
- Broad research where attribution to multiple named experts matters

## When **not** to use

- The reader named **one** expert → use **`ask_expert`** instead.
- The tool is **missing** from `tools/list` → global search is off for this
  account; explain that and offer **`ask_expert`** for a single persona.

## Rules

1. **One question → one tool call.** Do not call `ask_experts` again with the
   same question in a loop.
2. **Ask the reader before fanning out again** on a follow-up that is really the
   same question rephrased.
3. **Quote and name experts** in your reply. Use `structuredContent.experts_cited`
   for names; do not paraphrase their words as your own.
4. Each call **writes the caller's global thread** and **spends their daily
   budget**. Say so if they might not expect a write or a cost.
5. Pass `conversation_id` from a prior `ask_experts` result to continue the
   **same global thread**. A global thread **cannot** continue in `ask_expert`.

## After the tool returns

- Present the synthesis from `content` (text).
- If `grounding_state` is not grounded, say so plainly.
- If a clarifying question is present, ask the reader before calling again.
