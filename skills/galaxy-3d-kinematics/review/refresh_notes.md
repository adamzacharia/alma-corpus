# Refresh notes: galaxy-3d-kinematics

Pack: 341 papers (2013-2026), rebuilt against the 3,500-paper corpus.

What the refresh plus fix pass changed:
- Software counts rebuilt from the new aggregate, spelling variants merged and shown (3DBarolo 123, KinMS 81,
  emcee 34, kinemetry 21, GalPak3D 17). Unit: matched-step mentions, not papers.
- "Not stated" counts updated to the exact new labels (casa version 19, etc.), not summed across phrasings.
- Ring-width beam rules recounted with membership (20 papers, overlapping stage groups); ranges updated
  (CO 0.0138"-2"; dispersion starts 10-300 and 30-150 km/s).
- Gas scale-height count corrected (2019A&A...632A..33A 317 pc is stellar).
- Regularisation attribution fixed (2022MNRAS.516.4066L uses ring means, not Bezier).
- Virial estimators split back into separate rows (812L..23S, 493.4294B, 654A..37D, 987L..37W).
- New checks: line coverage and blends, spectral resolution vs channel spacing, tracer equivalence (eDIG,
  ionized vs molecular dispersions), near side before inflow/outflow, residual fluxes as lower limits,
  either route for lensed sources.
- Claims for papers listed only bibliographically in the new pack were checked against their cards and marked
  "(card)" (2025MNRAS.536.3757A, 2024ApJ...968....9W, 2025NatAs...9.1553F, 2015ApJ...812L..23S,
  2020MNRAS.493.4294B, 2024A&A...690A.169L, 2016ApJ...820L..39N, 2013ApJ...770L..27F, 2020ApJ...889..162L).
- Ranking language ("most common", "usual") replaced with example wording where the pack gives no denominator.
- SKILL.md 476 -> 313 lines; detail moved to references/parameters.md (mask table, staged fits, memberships,
  pressure-support and M_dyn conversion tables).
