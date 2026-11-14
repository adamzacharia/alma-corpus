# Refresh notes: spectral-index (refresh + Phase 6b fix)

Pack: rebuilt 640-paper `spectral-index` pack (3,500-paper corpus). Fix pass settled Codex refresh review RR-01..18
(see refresh_reconciliation.md).

What changed
- Fixed-beta census rebuilt from scratch: 196 single-value adoptions (was a mixed 82 / 195), with the parsing method,
  exclusions, multi-value papers and priors listed. Six bibcodes with no beta line in the current pack dropped.
- Measured-value table: rows for papers the pack lists only by title kept only where the card is verbatim, marked
  "(card)"; alpha Cen dropped; model assumptions (HD 107146 beta 0.4, NGC 3627 -0.85) separated from measurements;
  AB Aur and rho Oph W EME added.
- Counts recomputed from pack lines and labelled with method: per-band calibration (10% in 17), free-free -0.1 (11),
  synchrotron fiducial (20, separate from explored ranges), S/N cuts (12), common beam (9 + 3 card), matched uv (3),
  robust (3), MTMFS (4 used, 1 noisy), temperatures (10), DSHARP p = 3.5 (4).
- Science: background (CMB) condition for the Planck correction and tau; AME/EME check; stellar-flux subtraction for
  debris belts; integrated vs peak-intensity indices kept apart.
- Removed: 2020ApJ...892...66M joint T-beta experiment (not in pack).
- Layout: software census and long ledgers moved to references/parameters.md; SKILL.md 346 -> 312 lines.

Weak spots
- Bin labels for beta groups (disks vs galaxies) are my reading of the pack lines, not a pack field.
- 2018ApJ...852..122H's MTMFS band is not stated in the pack.
- Fomalhaut alpha_mm sign remains unresolved in the pack.
