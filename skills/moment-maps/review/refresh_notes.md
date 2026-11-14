# Refresh notes: moment-maps

Refresh against the rebuilt 1087-paper pack, then the fix pass for Codex's refresh review (RR-01..14).

What changed in SKILL.md (346 -> 302 lines):
- Step 1 "Prepare the cube": thermometry branch keeping unsubtracted cubes (2024ApJ...964..190L); weighting
  now rests on the corpus-wide stats median (robust 0.5) with pack subset counts 14 / 18, no ranking; channel
  widths labelled examples, range 0.11-100 km/s.
- Step 3 opens with a spectral-coverage check (2021A&A...654A..37D, 2026A&A...710A.390O).
- Step 4 mask table: per-paper thresholds for the sigma-clip row; MAD row split into per-spaxel channel
  selection (2021A&A...654A..24B) versus moment-0 detection (2026A&A...706A.236M); line ratios need a common
  beam, grid and uv range (2022ApJ...929..100K, 2024ApJ...977...37N).
- Step 5: velocity-map thresholds rebuilt (35 papers); effective width units fixed; per-pixel Gaussian fit
  numbers for 2021ApJ...908..231M kept as card-backed.
- Step 7: theta_50 defined; resolved-size significance check (2024MNRAS.533.1143M, 2021ApJ...914...36I).
- Pitfalls: moment 2 now covers thermal, bulk and hyperfine broadening; new brightness-temperature pitfall
  (optical depth, LTE, beam filling).
- Software, sampler, ring-width, smoothing, window, weighting and channel-width detail moved to
  references/parameters.md.

parameters.md: rebuilt velocity-threshold table (35, counting method stated), moment-0 clip list (16),
smoothed-cube masks (11), weighting, channel widths, Keplerian laws, sampler settings, software table.
Bibliographic-only papers checked against cards and marked "(card)".
