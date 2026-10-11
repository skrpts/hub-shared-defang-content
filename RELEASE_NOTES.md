# Release Notes

## v1.0.4
GH#1011 — add the prompt this skill never had, for the same reason as the rest of the batch: its consumers declared `local.transform`, which needs no prompt, so the steps reached the LLM default with nothing to send.

Not mapped to the `defang` builtin, and the reason is countable: the builtin covers THREE of this skill's five documented behaviours — the URL, IP and email substitutions, which are pure string work. It does not wrap code-execution patterns in warning fences, and does not flag sensitive file paths. Substituting it would have silently dropped two advertised behaviours.

## v1.0.3
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.0.2
GH#657 Framing B — republish wave. Bundle now ships `dependencies: []` in its signed manifest (injected by `publish-skrpt.mjs` for `--shared` publishes), so the App's dep-referenced install pipeline (post-PR #47) accepts it on standalone update via Hub Update-all. No content changes.

## v1.0.1
GH#645 Row 3a — republish with `manifest.id` aligned to Hub catalog UUID. Pre-K-037 v1.0.0 bundle carried a local `manifest.id` that drifted from the catalog UUID. Row 5 (`0d9c9dbe`) reconciled the source file but not the signed bundle; v1.0.1 ships the corrected `manifest.id` so the batch-of-81 consumer migrations (GH#645 Row 3b) can pin this version and pass engine STEP 4d. No content changes.

## v1.0.0
Initial catalog release as independent shared object (GH#612 Wave 3).
