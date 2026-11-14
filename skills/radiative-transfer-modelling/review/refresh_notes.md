# Refresh notes: radiative-transfer-modelling

Refresh against the 3,500-paper pack (656 papers, 2012-2026), then the Phase 6b fix pass for Codex's
refresh review (18 RR findings: 17 FIXED, 1 PARTLY).

What changed:
- Counts recomputed from the current pack: -3.5 slope 45, LTE 68, non-LTE 22, CO 1e-4 about 21,
  gas-to-dust 100 59, freeze-out 13, walkers 22, mu 15, CMB 15 (distinct papers, my regex over the
  truncated Key parameters and Assumptions aggregates). Software counts copied from the aggregate.
- Fitting aggregate recounted as 40 phrasings / 43 occurrences with an explicit first-match rule.
- Ranges updated: grain sizes (0.001-20.5 um a_min; a_max to a fixed 10 cm), gamma 0-2, H100 5-15 au,
  beta 1.0-1.2, temperature index 0.2-0.75, walkers 16-500, radial turbulence 11 to 1 km/s.
- Abundances: number vs. mass ratios separated; n_H = n(H) + 2 n(H2) fixed; CO/H2 range 5e-5 to 2e-4.
- mu = 14 reported as adopted, with composition caveat.
- New content: background/CMB field, chemistry and thermometer caveats, hyperfine and line-overlap checks.
- Bibliography-only citations checked against methods cards and marked "(card)"; one unsupported opacity
  row (2018MNRAS.474.4347C) rewritten to what its card says.
- Photon numbers labelled as examples; per-task budgets from 2024NatAs...8.1148U restored from its card.
- SKILL.md shortened from 418 to about 305 lines; long tables moved to references/parameters.md.
