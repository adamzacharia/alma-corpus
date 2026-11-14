# Refresh notes: gas-mass-co-conversion

What the refresh to the 876-paper pack changed, and what the fix pass after Codex's refresh review changed.

Refresh (writer, partly cut off):
- Description and counts moved to the 876-paper pack; restored myradex, imfit and gildas from the new
  software aggregate.

Fix pass (2026-11-02):
- Counts: every count is now the number of distinct bibcodes in the printed Key-parameter and Assumption
  entries (700 each, 450 bibcodes combined) matched by regex. The method is written in parameters.md.
  Recounted: Galactic alpha_CO 46, X_CO 2e20 39, alpha_CO 0.8 46, 3.6 10, 6.5 2, r21 70, r31 38, r41 15,
  X_CI 3e-5 10, CO/H2 1e-4 23, helium 32, alpha_850 5.
- Evidence: every cited bibcode with no line in the rebuilt pack (about 44 in SKILL.md, about 85 in
  parameters.md) was checked against its card and marked "(card)". Eight unsupported attributions were
  removed and three were narrowed.
- Ranges refreshed: r21 split by regime, r31 to 1.0, r41 0.22-1 with r43 separate, r61/r71 comparison
  SLEDs kept apart from adopted values, [CI] Tex 25-31.8 K, CO/H2 including 1e-3 for ejecta.
- Science: the [CI] 1375.8 forms are labelled helium-inclusive M_mol with the H2-only route; the 13CO
  lower bound is now conditional; the dust RJ applicability checks were added; distance and magnification
  are in the error budget; the aperture noise scaling formula is written out; the aperture/mask choice is
  no longer a fixed 3-sigma rule.
- Layout: SKILL.md is now 294 lines (from 370); the long tables are in references/parameters.md.
