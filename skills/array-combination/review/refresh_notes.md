# Refresh notes: array-combination

Refresh against the 3,500-paper pack (714 papers), plus the fix pass on Codex's refresh review.

- Description and corpus size: 714 papers, 2013-2026.
- Counts recomputed from current key-parameter lines with stated regex/hand methods (references/parameters.md):
  79 ALMA TP lines (55 feather, 3 of them model-then-feather, 13 method not stated), ~137 12m+7m lines,
  29 non-ALMA single-dish lines (18 feather), weighting split by line/continuum/unspecified (56 papers).
- Claims whose papers the pack lists only by title were checked against methods cards; kept only when the card
  quotes them verbatim, marked "(card)". Removed or narrowed: the paraphrased 2016PASJ...68...88K quote,
  "<~30% north" (2020ApJ...903...94M), the PHANGS PB order, 2026ApJ..1003...68Y regridding claims, and the
  2015ApJ...803...60S, 2015ApJ...804...37L and 2019ApJ...874...89C uses.
- New guidance: single-dish coverage check (Step 1), units by method (Jy/beam for feather, Jy/pixel for MACF),
  K-to-Jy conventions, continuum line-free ranges per dataset frame, deconvolved SD map before
  pseudo-visibilities, matched apertures and curves of growth for flux recovery.
- Weights now separate multipliers from resulting ratios; 2026ApJ..1005...94N added.
- Self-calibration patterns re-sorted by what each card or pack line states.
- Recommendation rests on 2023PASP..135c4501P with its stated limitations; feather vs MACF is a test to run.
- 2020ApJ...894...72S flagged as a PB recipe that fits neither branch.
- SKILL.md trimmed to 284 lines; long tables moved to references/parameters.md.
