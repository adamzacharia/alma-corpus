# Refresh notes: dust-continuum-mass

Refresh (3,500-paper pack, 915 technique papers) plus the Codex refresh-review fix pass (2026-11-01).

What changed in the fix pass:
- Counts recomputed from the current pack by regex over the Key parameters and Assumptions lines (515 bibcodes),
  hand-checked: fixed 20 K 45 -> 47; mu 2.8 to 2.86 stays 23 (20 exact 2.8), H2-labelled subset 12 -> 13.
  Method and dropped false hits are written in references/parameters.md.
- Two attributions the pack only lists bibliographically were verified on the cards and marked "(card)":
  4594 +/- 2848 (2020ApJ...892..147S), 2 sigma limit (2024ApJ...963....1O), SciPy MBB fit (2020ApJ...890...76N).
- Science corrections: optical-depth step no longer says T_b > T_d means thick (slab cannot exceed f B(T_d));
  mu_H vs mu_H2 conversion stated explicitly; 1/T mass scaling restricted to RJ; gas-temperature substitution needs a
  coupling argument; dust-based gas phase coverage depends on calibration; L_850 shortcut limited to
  lambda_rest > 250 um; the printed 100 x 10^(Z-Zsun) flagged for verification; plain KS not called censor-aware.
- Ranges widened: disk kappa 1.1 to 3.5 cm2/g; debris T adds fixed 40/100 K; upper-limit significance presented as
  a skill default, not a census.
- 2025A&A...694A.295P SciPy use described as a P23 disk SED fit, not a modified blackbody.
- 2013ApJ...764L..14Z moved back out of the opacity bullet (first-round SR-04).
- Length: SKILL.md 328 -> 305 lines; software table, opacity-uncertainty examples and unstated-settings counts
  moved to references/parameters.md.
