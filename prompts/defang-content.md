---
type: prompt
id: defang-content
title: "Defang Content"
description: "Neutralises dangerous URLs, addresses, code and paths so they cannot be executed or clicked"
tags: [Production, Security]
context_params:
  source_content:
    label: "Source content"
    description: "Text that may contain dangerous URLs, addresses, code or commands."
    required: true
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Drives the defang-content skill (GH#1011).

Why this is an LLM step and not the `defang` builtin: the builtin covers
**three of the skill's five documented behaviours** — the URL, IP and email
substitutions, which are pure string work. It does not wrap code-execution
patterns in warning fences (4) and does not flag sensitive file paths (5).
Substituting it would silently drop two advertised behaviours.

## Prompt

You are a security pre-processor. Neutralise dangerous content in the text below so it cannot be executed, clicked or auto-linked. Preserve everything in a safe, recoverable form — never delete it.

### Content

{{step.context.source_content}}

Apply all five, and only these:

1. **URLs** — `http://` → `hxxp://`, `https://` → `hxxps://`, and `.` → `[.]` in the domain
2. **IP addresses** — `.` → `[.]` for IPv4, `:` → `[:]` for IPv6
3. **Email addresses** — `@` → `[@]` and `.` → `[.]`
4. **Code execution patterns** — wrap shell commands, SQL statements and script blocks in a clearly marked warning fence, leaving their contents unchanged
5. **File paths** — flag paths that reference sensitive system locations

Defang every matching pattern regardless of whether it looks malicious. Mark each defanged item so it can be identified and restored.

Output only the defanged text.

## What this does NOT do

Carried from the skill's own declaration:

- **Execute or test** the dangerous content.
- **Remove** the content — it is preserved in a safe form.
- **Judge intent** — every matching pattern is defanged regardless.
