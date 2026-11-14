# Refresh notes: continuum-subtraction

What the refresh plus the Phase 6b fix pass changed:

- Counts: the earlier card-wide regex census (not checkable against the pack) is gone. All "my count" numbers are
  regex counts over the 220 papers whose processing fields the pack prints (702 of about 2750 parameter lines).
  Method and patterns are in references/parameters.md. Pack aggregates (software, 323 not-stated labels) unchanged.
- Corpus rate updated to 64% of 3498 cards (stats/README.md).
- Bibliography-only papers: each claim was checked against a verbatim quote in the paper's methods card and marked
  "(card)", or removed. Removed: 2020A&A...637A..84P 300 km/s, 2017A&A...602A..59C alpha=2, 2019A&A...632A..19T
  CLASS, 2021A&A...656A..46M 5.3-36.6%, 2019MNRAS.485.2092C Var(S/sigma), 2024A&A...689A.317G residual check,
  2024A&A...689A..85G 125 MHz, 2025NatAs...9.1476C cvel2, 2021A&A...655A..72S 52 MHz, 2015ApJ...801...82H
  "about half", 2020A&A...643A...2B 3 sigma_v, the AIPS label for 2017Icar..286..289L, and the
  2024MNRAS.527.9343L JCMT check (removed in round 1 as SR-10).
- Parameter tables: corpus ranges replaced by named examples; total vs half-width exclusion separated; STATCONT
  failure threshold separated from measured line-free fractions; 2021AJ....162...99F and 2025A&A...703A..15M
  windows labelled for what they are.
- Science: absorption guidance now keeps a continuum-bearing product rather than banning subtraction; new pitfalls
  on channel covariance, bandpass residuals for weak absorption, and continuum-model fidelity
  (2023NatAs...7.1048C); source-model subtraction is optional and needs validation.
- CASA: imcontsub example uses keywords.
- Length: SKILL.md 288 lines; long tables moved to references/parameters.md.
