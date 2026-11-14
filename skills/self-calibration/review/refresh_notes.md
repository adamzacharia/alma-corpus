# Refresh notes: self-calibration

Refresh (2026-10, 896-paper pack) plus fix pass after Codex refresh review (RR-01..RR-14).

What changed:
- Counts redone over the rebuilt pack's key-parameter section (lines 154-856, 330 self-cal lines):
  phase-only 106, amplitude terms 101, transfer to line data 50, kept off line data 3.
- `minsnr`/`minblperant` rows relabelled as examples with an inclusion rule; 2021ApJ...906..111T added.
- Final phase-only solint range extended to 240 s (2018MNRAS.481L..40S).
- Amplitude rounds whose mode the card does not give are now `amp`, not `ap`
  (2015ApJ...814...22E, 2016A&A...593A..61M, 2017A&A...600A..72F, 2017A&A...605A..21C).
- Claims from papers the pack lists only bibliographically were checked in their cards and tagged "(card)".
- CASA `gaintype='T'` described correctly (one polarization-independent gain per antenna; `G` for
  per-polarization gains). The old "per polarization with T" wording is gone.
- `combine` normalised to executable `'scan,spw'`; mosaic `'field'` combination made conditional, with
  per-pointing solves as the alternative.
- `startmodel` separated from saving model visibilities for `gaincal`.
- Removed the "peak rises modestly" expectation; added the non-Gaussian residual warning for transient
  injection tests (2022A&A...666A..39M).
- 2026A&A...712A.244H sequence marked ambiguous; mode-sequence row now illustrative, not a bound.
- Length: SKILL.md 324 -> 300 lines. Improvements table and tool-by-tool software table moved to
  `references/parameters.md`.
