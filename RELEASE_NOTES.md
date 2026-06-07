# Release Notes

## v1.0.1
GH#645 Row 3a — republish with `manifest.id` aligned to Hub catalogue UUID. Pre-K-037 v1.0.0 bundle carried a local `manifest.id` that drifted from the catalogue UUID. Row 5 (`0d9c9dbe`) reconciled the source file but not the signed bundle; v1.0.1 ships the corrected `manifest.id` so the batch-of-81 consumer migrations (GH#645 Row 3b) can pin this version and pass engine STEP 4d. No content changes.

## v1.0.0
Initial catalogue release as independent shared object (GH#612 Wave 3).
