# Review task: an ALMA agent skill against its evidence pack

You are reviewing a skill file (SKILL.md, plus an optional parameters table) that another model wrote from the
EVIDENCE PACK below. The pack is built from methods cards of published ALMA papers; every quote in it was
mechanically verified against the paper text. The skill will be given to research agents that analyse ALMA data,
so wrong defaults or misattributed practice cause real errors. You have no file access: everything you need is in
this message.

Check, in this order:

1. **Attribution.** Every number, range, default, software attribution and "papers do X" claim that cites
   bibcodes: does the pack support it for those bibcodes? Flag claims the pack contradicts, claims cited to a paper
   whose pack entry says something else, and counts that do not match the pack aggregates.
2. **Unsupported practice.** Statements presented as literature practice with no support in the pack. (General
   background marked as general practice is fine if it is correct.)
3. **Scientific correctness.** Wrong formulas, wrong units, wrong CASA task/parameter names or semantics, unsafe
   advice, or a recommendation that contradicts the evidence.
4. **Omissions.** Important pitfalls, assumptions or validation checks that are clearly present in the pack (for
   example in "Limitations the authors admit" or "Settings cards flag as needed but not stated") but missing from
   the skill.
5. **Usability.** Anything an agent would misread or could not act on.

Output format (Markdown, nothing else):

```
# Codex review: <slug>
VERDICT: CLEAN | FIX
## Findings
- SR-01 | high|medium|low | <attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- SR-02 | ...
## Notes
<at most 5 lines: overall quality, anything the writer should know>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (polarization-magnetic-fields) ===
---
name: alma-polarization-magnetic-fields
description: "Calibrate, image and interpret ALMA full-polarization data: Stokes I/Q/U/V imaging, debiased polarized intensity, fraction and angle maps, deciding between magnetic grain alignment, radiative alignment and dust self-scattering, plane-of-sky field morphology, DCF and structure-function field strengths, Zeeman and Goldreich-Kylafis line polarization, and Faraday rotation of compact synchrotron sources. Use when a user has or wants ALMA polarization data, asks about B-field maps, polarization vectors, DCF, grain alignment vs scattering in disks, Stokes V or rotation measures. Built from 109 ALMA papers (2013-2026), about 55 of them on-topic polarimetry."
---

# Dust polarization, line polarization and magnetic fields

ALMA measures linear polarization (Stokes Q, U) and, less reliably, circular polarization (Stokes V). Papers use it
for three different things: the plane-of-sky magnetic field direction (dust E-vectors rotated by 90 deg), grain size
(self-scattering in disks), and field strength (DCF from angle dispersion, or Zeeman splitting in lines). Two
mistakes matter most: rotating vectors by 90 deg before showing the emission comes from magnetically aligned,
optically thin dust, and trusting polarization fractions from filtered, low-S/N or off-axis interferometer maps.

Counts are from the evidence pack (`skills/packs/polarization-magnetic-fields.md`). The pack was tagged by regex,
so many of its 109 papers are off-topic. By my count of the pack's paper list, about 55 are ALMA polarimetry papers:
17 on protostellar envelopes, cores and clumps, 13 on protoplanetary disks, 8 on line or maser polarization, 14
on compact synchrotron sources (AGN, GRBs, Sgr A*, calibrators) and 2 on galaxies. I left out near-IR scattered-light
polarimetry (for example 2020MNRAS.492.1531M, 2018A&A...620A..75K), star-formation-law papers that only set
B = 0 (2018MNRAS.477.4380S, 2019MNRAS.487.4305S) and papers matched on unrelated words. Aggregate counts (software,
"not stated" settings) cover all 109 papers and are labelled as pack aggregates.

## When to use

- Dust continuum polarization in Class 0/I envelopes, cores and massive clumps, to map the plane-of-sky field
  (2018ApJ...859..165S, 2019ApJ...879...25K, 2020ApJ...893...54Y, 2019A&A...626A..36D, 2025ApJ...992..103Z).
- Protoplanetary disk polarization, to tell scattering from alignment and constrain maximum grain size
  (2016ApJ...831L..12K, 2017ApJ...851...55S, 2018ApJ...860...82H, 2018ApJ...864...81O, 2025ApJ...990..183U).
- Field strength estimates: DCF or structure function on dust or line angles (2019ApJ...884...48C,
  2020ApJ...896..157H, 2024A&A...686A.274V), or Zeeman limits from CN or SiO masers (2021ApJ...908..141H,
  2019A&A...624L...7V, 2017A&A...603A..92V).
- Molecular line polarization (Goldreich-Kylafis, radiative alignment, masers) in evolved-star envelopes and jets
  (2024A&A...686A.274V, 2018NatCo...9.4636L).
- Linear polarization and rotation measure of compact synchrotron sources: AGN cores and jets, GRB afterglows,
  Sgr A* (2024ApJ...975..103P, 2019ApJ...878L..26L, 2018ApJ...868..101B, 2019MNRAS.489..470G).
- Ordered fields in external or high-z galaxies (2020ApJ...893...33L, 2023Natur.621..483G).

## When not to use

- **Only XX and YY were recorded (no cross-hands).** Full Stokes imaging is impossible. Papers instead fit the
  XX/YY ratio against parallactic angle (2016A&A...593A..44L, Stokes U then undetermined), use dual differential
  polarimetry (2016A&A...593A..61M), or report |Q/I| = (XX-YY)/2I as a lower limit (2020ApJ...891...80M).
- **You need a field strength from unresolved dust polarization.** 2023Natur.621..483G states the strength cannot
  be reliably estimated from their z=2.6 dust data; report orientation and ordered fraction only.
- **You need circular polarization from older-cycle data.** Stokes V was unreliable in Cycle 3
  (2019MNRAS.489..470G) and not assured in Cycle 5 (2020ApJ...896..157H); 2018ApJ...864...81O ignored V because it
  was not characterized. For extended lines, V is dominated by beam effects (2024A&A...686A.274V).
- **One wavelength and a disk.** A single band cannot separate scattering from alignment (2018ApJ...864...81O).
  Get a second band or treat the mechanism as unknown.
- **Near-IR polarized scattered light** (SPHERE, NaCo) is a different technique; this skill covers ALMA mm/submm.

## Steps

1. **Polarization calibration.** Goal: remove leakage (D-terms), cross-hand delay and XY phase. Papers use the
   ALMA polarization calibration scripts (2024A&A...686A.274V, 2023Natur.621..483G) or rerun them by hand in CASA:
   `gaincal` without a polarization model, `qufromgain` for the calibrator Q/U, `gaincal` with `gaintype='KCROSS'`
   and `'XYf+QU'`, `xyamb`, then `polcal` for D-terms (2016ApJ...824..132N, 2020ApJ...895...64L,
   2024ApJ...975..103P). Leakage needs wide parallactic-angle coverage of the polarization calibrator, about 90 deg
   in 2019ApJ...878L..26L. 2020ApJ...895...64L repeated the whole calibration with a second reference antenna of a
   different architecture.
2. **Self-calibrate on Stokes I and apply to all correlations.** Phase-only rounds are typical: four rounds
   (2020A&A...644A..11L), two rounds with solint 'inf' then 'int' (2024A&A...686A.274V), final solint 90 s
   (2019ApJ...884...48C). 2024A&A...686A.274V also corrected an amplitude re-normalisation problem first.
3. **Image Stokes I, Q, U (and V).** `tclean` with `stokes='IQUV'`. Briggs robust 0.5 is the most common choice
   (my count of the pack's key-parameter lines: 14 on-topic papers, e.g. 2018ApJ...864...81O, 2020ApJ...893...54Y,
   2025ApJ...992..103Z). For multi-band comparisons, image every band on a common uv range (27-1310 klambda in
   2018A&A...616A..56A; "same uv distance" in 2025NatAs...9..526O) and smooth to a common beam. Other settings seen:
   multiscale 0, 0.3, 0.9 arcsec (2016ApJ...831L..12K); `nterms=2`, cell 0.2", robust 1 (2024ApJ...975..103P);
   threshold 10 uJy (2023Natur.621..483G). 2018ApJ...859..165S primary-beam corrected all four Stokes maps;
   2020A&A...644A..11L skipped primary-beam correction for its statistics.
4. **Derive debiased polarized intensity, fraction and angle.** Standard: PI = sqrt(Q^2 + U^2 - sigma_PI^2),
   P = PI/I, chi = 0.5 arctan(U/Q) (2020ApJ...893...54Y, 2018ApJ...859..165S, 2025NatAs...9..526O,
   2024A&A...686A.274V). Use a two-argument arctangent (atan2, 2019ApJ...884L..58U). Tools: CASA `immath` modes
   `POLI`/`POLA` (2024ApJ...975..103P), MIRIAD `impol` (2020ApJ...899..152H). At low S/N on point sources, debias by
   Monte Carlo over Q, U (1e5 draws, 2019ApJ...878L..26L). Angle error: sigma_chi = 28.65 deg x sigma_P/P
   (2025ApJ...992..103Z), equivalently Delta(PA) = Delta P / 2P (2020ApJ...896..157H). Keep only pixels above a
   PI threshold (see table), sample about Nyquist (0.1" pixels, 2020ApJ...893...54Y; 4 pixels per beam,
   2020A&A...644A..11L), and stay inside the inner third of the primary beam (2019A&A...626A..36D,
   2020A&A...640A.111A, 2018ApJ...861...91H).
5. **Decide the polarization mechanism before rotating.** Candidates: magnetic alignment, radiative (k-RAT)
   alignment, self-scattering. Tests papers use:
   - Wavelength dependence: fraction 7.9, 5.3, 3.5% in Bands 3, 6, 7 (2018A&A...616A..56A); orientations at 0.87
     and 1.3 mm differ by 5 +- 4 deg with fraction 1.7x higher at 1.3 mm (2020ApJ...893...54Y); pattern changes with
     wavelength in HL Tau (2017ApJ...851...55S).
   - Morphology: vectors versus disk minor axis (2018ApJ...859..165S), vector flips explained by scattering
     (2016ApJ...831L..12K), offset between angle and radial direction versus azimuth for radiative alignment
     (2018ApJ...864...81O, 2019MNRAS.483.2371Y).
   - Optical depth: peak brightness temperature 30 K against dust temperature 67 K (2020ApJ...893...54Y); spectral
     index with beta = alpha - 2 only under thin Rayleigh-Jeans assumptions (2018A&A...616A..56A).
   - Forward models: RADMC-3D self-scattering (2016ApJ...831L..12K, 2024ApJ...963..134Y), aligned Mie grains
     (2020A&A...634L..15G), scattering-efficiency prior P ~ 0.02 P90 omega (2025ApJ...990..183U).
   Rotate by 90 deg only when emission is from aligned grains and optically thin (2020ApJ...893...54Y,
   2019ApJ...879..101L, 2020A&A...640A.111A).
6. **Analyse field morphology.** Compare B segments with outflow axes or core orientation and test against random
   (histograms and K-S tests, 2025ApJ...992..103Z, 2020A&A...640A.111A). Compare with models through synthetic
   observations: DustPol + `simobserve`/`simanalyze` over a grid of k = B_p/B_phi (2018A&A...616A..56A), non-ideal
   MHD + SPARX + CASA simulator, scored by the fraction of segments within 30 deg (2020ApJ...893...54Y), toroidal
   torus field with CLUMPY/HYPERCAT (2020ApJ...893...33L), chi-square fit of |B_r|:|B_phi|:|B_z|
   (2025NatAs...9..526O), analytic hourglass matched by eye (2018ApJ...859..165S). For population statistics use
   the angle dispersion function S and P (n = 8 neighbours, lag about half a beam, 2020A&A...644A..11L).
7. **Estimate field strength (optional, order of magnitude).**
   - DCF (general practice): B_pos = xi sqrt(4 pi rho) sigma_v / sigma_phi, with xi = 0.5 (2020ApJ...896..157H) and
     sigma_phi in radians. Variant B0 ~ sqrt(8 pi rho) sigma_v / alpha with alpha from a dispersion/structure
     function fit (2020ApJ...893...33L).
   - sigma_phi: remove the ordered field first, by subtracting a 0.5"-smoothed angle map (2020ApJ...896..157H) or
     smoothing Q, U with a 3x larger beam (2019ApJ...879...25K, from its card); or take the EVPA standard deviation over regions
     with at least 10 independent Nyquist points (2019ApJ...884...48C), or the circular-mean variance
     (2019A&A...626A..36D).
   - Structure function fits (Hildebrand/Houde/Koch style) give B_t/B_0 and the number of turbulent cells:
     0.061 +- 0.001 and N ~ 1.2 within ~2" (2024A&A...686A.274V); 0.062 +- 0.025 (2020ApJ...893...33L).
   - sigma_v from a dense-gas line (H13CO+, 2019ApJ...884...48C; 13CS ~0.8 km/s, 2017ApJ...847...92H) and n from
     dust mass or an assumed density (1e6 cm^-3, 2020ApJ...896..157H). Total field 4B/pi (2020ApJ...896..157H).
8. **Zeeman and line polarization (if lines).** Fit V = C1 I + C2 dI/dnu + 0.5 Z B dI/dnu to unblended hyperfine
   parts after a Keplerian velocity shift with `gofish` (CN 2-1, 2021ApJ...908..141H). SiO masers: V proportional to
   dI/dnu with z ~ 1500 s^-1 G^-1 (2017A&A...603A..92V) or g Omega/2pi = 230 Hz/G (2020ApJ...896..157H). Linear
   line polarization modelled with PORTAL on LIME output (2024A&A...686A.274V) or a G-K code with LAMDA rates
   (2020ApJ...899..152H).
9. **Compact synchrotron sources.** Fit Q and U with position and beam fixed from Stokes I (`imfit`,
   2019ApJ...878L..26L, 2020ApJ...895...64L). For rotation measure, image each SPW at matched resolution and fit
   EVPA versus lambda^2 linearly (CASA `rmfit`, 3-sigma polarized threshold, 2024ApJ...975..103P).

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Briggs robust (Stokes IQU) | 0.5 | -2 to 2, natural | 0.5: 14; 1: 3; natural: 3; 0, 2, -0.5, -2: 1 each (my count, key-parameter lines) | 2018ApJ...864...81O; 2017ApJ...851...55S (1); 2020ApJ...893...33L (natural); 2018ApJ...861...91H (-2) |
| PI detection threshold | 3 sigma_PI | 3-5 sigma | 3: 9; 4: 3; 5: 2 (my count) | 2020ApJ...893...54Y, 2023Natur.621..483G (3); 2018ApJ...859..165S, 2020ApJ...896..157H (4); 2018A&A...616A..56A, 2024A&A...686A.274V (5) |
| Debiasing | sqrt(Q^2+U^2-sigma^2) | MC (1e5 draws); none if >3 sigma | 5+ | 2020ApJ...893...54Y; 2019ApJ...878L..26L; 2016ApJ...831L..12K |
| Polarization fraction floor | 0.1% MDP | 0.03% systematic; 0.1% 1-sigma | 3 | 2020ApJ...893...33L; 2023Natur.621..483G; 2018ApJ...859..165S |
| Usable field | inner 1/3 of primary beam | on-axis <=20", off-axis 20-60" checked | 4 | 2019A&A...626A..36D; 2020A&A...640A.111A; 2024ApJ...975..103P |
| D-term level | ~1% per antenna | repeat solutions agree within 0.5% | 2 | 2019ApJ...878L..26L; 2016ApJ...824..132N |
| Residual calibrator polarization | ~0.1% | <0.02% stability on phase calibrator | 2 | 2020ApJ...895...64L; 2019ApJ...884L..58U |
| Parallactic angle coverage | ~90 deg | | 1 | 2019ApJ...878L..26L |
| Absolute EVPA accuracy | 0.4 deg | | 1 | 2016ApJ...824..132N |
| Angle error | 28.65 deg sigma_P/P | <~9 deg at S/N>3; <7 deg at S/N>=4 | 3 | 2025ApJ...992..103Z; 2020ApJ...893...54Y; 2020ApJ...896..157H |
| Self-cal (Stokes I) | phase-only, 2-4 rounds | solint inf/int to 90 s | 4 | 2020A&A...644A..11L; 2024A&A...686A.274V; 2019ApJ...884...48C |
| DCF correction xi | 0.5 | | 1 in pack lines (2019A&A...626A..36D card also uses 0.5) | 2020ApJ...896..157H |
| DCF sigma_phi | 4-10 deg | 5 +- 2 deg; 0.38 rad; 30 +- 20 deg | 5 | 2020ApJ...896..157H; 2019ApJ...879...25K (10 deg, card); 2020ApJ...893...33L; 2018MNRAS.477.2760M; 2018NatCo...9.4636L |
| DCF density | 1e6 cm^-3 | n_H2 >~ 2e6; whole-torus median (upper limit) | 3 | 2020ApJ...896..157H; 2018NatCo...9.4636L; 2020ApJ...893...33L |
| Self-scattering a_max | ~100-150 um | 61-150 um | 4 | 2018ApJ...860...82H (61); 2016ApJ...831L..12K (150); 2024ApJ...963..134Y (140); 2019MNRAS.482L..29D (~100) |
| Model-data agreement | within 30 deg | mean residual 20-23 deg | 2 | 2020ApJ...893...54Y; 2018A&A...616A..56A |
| RM fit | linear chi vs lambda^2 over 4 SPWs | | 1 | 2024ApJ...975..103P |

Longer tables and per-paper values are in `references/parameters.md`.

## Software

From the pack aggregates (all 109 papers, so some counts include off-topic uses):

| Tool | Use | Count |
|---|---|---|
| CASA (`gaincal` KCROSS/XYf+QU, `qufromgain`, `xyamb`, `polcal`, `tclean`, `immath` POLI/POLA, `imfit`, `rmfit`) | calibration, Stokes imaging, PI/angle maps, point-source and RM fits | casa 62, tclean 3, gaincal 2, imfit/casa imfit 3, polcal 1, qufromgain 1, xyamb 1 |
| MIRIAD (`impol`, `imfit`, `gpcal options=qusolve`, `imdiff`) | debiasing, Gaussian fits, CARMA leakage, XX/YY comparisons | 6 (+ imdiff 1) |
| RADMC-3D | self-scattering and alignment radiative transfer | 6 |
| MCFOST | disk radiative transfer (mostly in near-IR papers) | 3 |
| gofish | Keplerian shifting before Zeeman fits | 2 |
| emcee | MCMC with polarization priors | 2 |
| UVMultiFit | visibility fits of compact sources | 2 |
| CASA simobserve/simanalyze | synthetic observations of B-field models | 2 |
| ARTIST DustPol, SPARX, PORTAL + LIME 1.9.5, G-K code (Yang & Lai 2010) | polarized RT for dust and lines | 1 each |
| lenstronomy | source-plane field for lensed galaxies | 1 |
| MrBeam (with ehtim, pygmo) | closure-trace polarimetric imaging | 2 |

## Pitfalls

- **Interferometric filtering inflates fractions.** Stokes I and Q/U resolve out differently (2016ApJ...831L..12K);
  missing CO flux overestimates line fractions by 2-3x (2024A&A...686A.274V); missing short baselines inflate P
  (2020ApJ...896..157H, 2020ApJ...899..152H, 2020A&A...644A..11L); 30-70% flux loss in 2019A&A...626A..36D.
- **Mechanism ambiguity.** One band cannot separate scattering from alignment, and optically thick regions hide
  midplane grains (2018ApJ...864...81O). Polarization may come from aligned grains rather than scattering, which
  makes derived fragmentation velocities very uncertain (2025ApJ...990...59Y). Polarization toward an embedded disk
  may be affected by self-scattering (2019ApJ...879..101L).
- **DCF is order of magnitude.** Authors say so (2019A&A...626A..36D, 2019ApJ...879...25K); outflows and collapse
  degrade it (2019ApJ...879...25K); validity uncertain (2018MNRAS.477.2760M); sigma_v extrapolated by a Kolmogorov
  law (2019ApJ...884...48C); a whole-region mean density gives only an upper limit (2020ApJ...893...33L); a
  structure-function result is a lower limit if the field is not frozen in (2024A&A...686A.274V).
- **Instrumental systematics mimic signal.** A 0.27 +- 0.04% GRB afterglow detection (2019ApJ...884L..58U) became
  a 3-sigma upper limit of 0.30% after independent recalibration with a systematic term from the gain calibrator
  (2020ApJ...895...64L), which left the origin of the time-varying systematics uninvestigated. Stokes V detections may be spurious (2017ApJ...851...55S).
- **Off-axis and dynamic range.** Sources outside the inner third of the primary beam are unreliable
  (2018ApJ...861...91H); Stokes I dynamic range limits P interpretation (2020ApJ...892..152H, 2016ApJ...824..132N).
- **Rotation measure traps.** Phase wraps and low-polarization calibration errors make the largest RMs suspect
  (2018ApJ...868..101B); poor parallactic coverage in Bands 7/8 and EVPA variability can mimic RM
  (2019A&A...621A..18M); emission at different wavelengths may come from different regions (2024ApJ...975..103P).
- **Zeeman stacking.** Stacking red and mirrored blue sides cancels a vertical field (2021ApJ...908..141H).
- **Small samples and non-simultaneity.** Random versus preferred orientations cannot be separated with few cores
  (2020A&A...640A.111A, 2025ApJ...992..103Z); non-simultaneous multi-band data block joint fits
  (2019MNRAS.489..470G, 2019ApJ...884L..58U).
- **Models are rarely unique.** By-eye matches (2018ApJ...859..165S), non-unique models (2017ApJ...851...55S),
  reduced chi-square ~9-16 (2025NatAs...9..526O).
- **What cards flag as not stated** (pack aggregate): CASA version (12), self-cal solution intervals (5, plus
  related variants), polarization debiasing method (2), polarization calibration details (several single entries).
  Report these explicitly.

## Verification checks

What papers did:
- Compare the polarization calibrator's fraction and angle with the ALMA Calibrator Source Catalogue
  (2018A&A...616A..56A) or monitoring programs (2020ApJ...899..152H).
- Check D-terms (~1%) and XX/YY gain ratio (within ~2% of unity, 2019ApJ...878L..26L); residual calibrator
  polarization after calibration (~0.1%, 2020ApJ...895...64L); on- and off-axis leakage below the analysis
  threshold (2024ApJ...975..103P); repeated D-term solutions on a second calibrator (2016ApJ...824..132N).
- Monte Carlo D-term and XY-phase errors to test a Stokes V result (2017A&A...603A..92V).
- Split the data: by sideband, by execution, by base-band, by antenna type, by reference antenna
  (2020ApJ...895...64L, 2019ApJ...878L..26L, 2016A&A...593A..44L).
- Stokes V rms close to thermal noise (2016ApJ...831L..12K).
- Smooth new data to an older beam and check fractions and angles agree (2018ApJ...864...81O,
  2018ApJ...859..165S).
- Neighbouring channels show the same structure, arguing against missing-flux artefacts (2024A&A...686A.274V);
  other channels give field strengths within 30% (2024A&A...686A.274V).
- Simulate the lens and convolution to show they do not rotate angles or change P (2023Natur.621..483G).
- Compare DCF strength with independent masers or scaling laws (2020ApJ...896..157H, 2020ApJ...893...33L).

What a careful referee adds:
- State the mechanism test that justifies the 90 deg rotation, with optical depth at the polarized positions.
- Quote sigma_I, sigma_Q, sigma_U, the debiasing formula, the threshold and the systematic floor (0.1%).
- Show the fraction is not driven by filtering: give the maximum recoverable scale and, if possible, compare with
  single-dish polarimetry.
- For DCF, give the ordered-field removal method, the number of independent beams, density and sigma_v sources, and
  the correction factor; quote at least a factor-of-2 uncertainty.

## Source cards

Full list: `references/sources.md`. Most informative for this skill:

- 2016ApJ...824..132N: step-by-step CASA polarization calibration and EVPA accuracy on 3C 286
- 2020ApJ...895...64L: independent recalibration, systematic error budget, upper limit
- 2019ApJ...878L..26L: leakage checks, fixed-position Q/U fits, Monte Carlo debiasing
- 2024ApJ...975..103P: Stokes imaging per SPW, leakage limits, `rmfit` rotation measure
- 2020ApJ...893...54Y: debiasing, two-band comparison, optical-depth check, MHD model scoring
- 2018A&A...616A..56A: three-band fractions, common uv range, DustPol model grid
- 2018ApJ...864...81O: radiative alignment test, resolution comparison, limits of one band
- 2016ApJ...831L..12K: self-scattering with RADMC-3D, filtering caveat
- 2017ApJ...851...55S: wavelength transition of the polarization pattern in HL Tau
- 2018ApJ...860...82H: scattering-derived a_max in IM Lup
- 2025NatAs...9..526O: 3D field components from multi-band disk polarization
- 2018ApJ...859..165S: thresholds, disk minor-axis test, hourglass model
- 2019A&A...626A..36D: DCF and structure function in a high-mass region, order-of-magnitude caveat
- 2019ApJ...884...48C: DCF variants and dispersion estimator
- 2020ApJ...896..157H: DCF on SiO line angles, Zeeman test of Stokes V
- 2020A&A...644A..11L: statistics of S and P across Class 0 cores
- 2025ApJ...992..103Z: relative orientation of fields across scales
- 2021ApJ...908..141H: CN Zeeman fitting with `gofish`
- 2024A&A...686A.274V: line polarization, PORTAL modelling, structure function
- 2020ApJ...893...33L: dust polarization and field strength in an AGN torus
- 2023Natur.621..483G: dust polarization in a lensed z=2.6 galaxy

=== references/parameters.md ===
# Per-paper parameters: polarization and magnetic fields

All values are from the evidence pack (`skills/packs/polarization-magnetic-fields.md`), key-parameter, assumption
and excerpt lines. Entries marked "card" come from the paper's methods card.

## Calibration and imaging

| Paper | Setting |
|---|---|
| 2016ApJ...824..132N | `gaincal` KCROSS and XYf+QU, `qufromgain`, `polcal` D-terms on J1337-1257; repeat with 3C 279 agrees within 0.5% (typically 0.1-0.3%); absolute EVPA accuracy 0.4 deg |
| 2020ApJ...895...64L | Tsys/WVR, bandpass, `qufromgain`, XYf+QU, `xyamb`, `polcal`; reference antenna DV06 then DA64; cross-hand delay from the strongest-polarization scan; robust 0.0; residual calibrator polarization ~0.1%; extra 1-sigma systematic ~0.09% of Stokes I |
| 2019ApJ...878L..26L | leakage calibrator with ~90 deg parallactic coverage; D-terms ~1%; XX/YY gain ratio within ~2% of unity; Q/U fitted with Stokes I position and beam fixed; 1e5 Monte Carlo draws for P |
| 2024ApJ...975..103P | `polcal` D-terms; `tclean` nterms=2, cell 0.2", robust 1; `immath` POLI/POLA; `imfit` elliptical Gaussians; `rmfit` with 6 mJy/beam (3 x rms) threshold, no systematics included |
| 2024A&A...686A.274V | ALMA polarization scripts after re-normalisation fix; CASA 5.7.2; phase self-cal solint 'inf' then 'int'; robust 0.5; >5 sigma_P detections |
| 2023Natur.621..483G | pipeline plus polarization script; clean threshold 10 uJy; P/sigma_P >= 3; 0.1% MDP added in quadrature |
| 2020ApJ...893...33L | natural weighting; MDP 0.1%, systematic 0.03%; vectors at P/sigma_P >= 3 |
| 2018A&A...616A..56A | common uv range 27-1310 klambda for Bands 3, 6, 7; vectors at PI S/N = 5 |
| 2018ApJ...864...81O | robust 0.5; sigma_PI = 2.9e-5 Jy/beam; fraction only above 3 sigma_PI; mean angle error ~2.5 deg |
| 2016ApJ...831L..12K | robust 0.5; multiscale 0, 0.3, 0.9"; Stokes V rms 25.2 uJy near thermal; sigma_PI = 42.8 uJy/beam |
| 2018ApJ...859..165S | PB-corrected I, Q, U, V; PI/sigma > 4; sigma_PI ~ sigma_Q ~ sigma_U; 0.1% 1-sigma fraction uncertainty |
| 2020ApJ...893...54Y | robust +0.5; 0.1" pixels; I and PI S/N > 3; orientation errors <~9 deg |
| 2025ApJ...992..103Z | robust 0.5; 3 sigma cutoff on Q and U; sigma_PA = 28.65 deg sigma_p/I_p |
| 2019A&A...626A..36D | S/N > 4; inner third of primary beam; sigma_psi from circular-mean variance |
| 2020A&A...640A.111A | robust 0.5, Hogbom; inner third of primary beam; 52 cores, 29 with polarization |
| 2020A&A...644A..11L | robust 1; four phase-only self-cal rounds; 4 pixels per beam; S with n = 8 neighbours and lag ~half a beam; no PB correction for statistics |
| 2019ApJ...884...48C | robust 0.5; final self-cal solint 90 s |
| 2020ApJ...892..152H | robust 2.0, 0.5, -0.5; 4 self-cal rounds |
| 2018ApJ...861...91H | robust -2 for the high-resolution VLA 1623 image; sources outside inner third of PB flagged unreliable |
| 2017A&A...603A..92V | lines robust 0.5, continuum robust -0.5; Monte Carlo of 1000 random D-term sets for Stokes V |
| 2019ApJ...884L..58U | per-SPW Stokes maps; phase-calibrator polarization stable to <0.02%; angle by atan2 |
| 2020ApJ...899..152H (CARMA) | MIRIAD `xyauto` for R-L phase, `gpcal options=qusolve` for leakage, `impol` debiasing |

## Mechanism and grain-size modelling

| Paper | Setting |
|---|---|
| 2018A&A...616A..56A | beta = alpha - 2 (thin, Rayleigh-Jeans); radiative alignment fit i = 48 deg, PA = 138 deg (+-15); DustPol at 343 GHz, i = 55 deg, k grid, best k = 3, mean residual 23.4 deg (sigma 7.5) |
| 2018ApJ...864...81O | 0.87 mm field as proxy for 140 um radiation; i = 27 deg, PA = 341 deg; pixels above 10 sigma |
| 2016ApJ...831L..12K | RADMC-3D, compact spherical grains, slope -3.5, a_max 150 um (range ~40-300 um), T 36 K, i 27 deg |
| 2018ApJ...860...82H | MRN a^-3.5, a_min 0.25 um, ice/organics/silicates 62/30/8%; a_max 61 um best, 50 and 70 um tested |
| 2024ApJ...963..134Y | a_max 140 um, a_min 0.1 um; 1.6e8 photons; only self-scattering |
| 2019MNRAS.482L..29D | natural weighting; scattering only, multiple scattering included; a_max ~100 um |
| 2019MNRAS.483.2371Y | radiative alignment test in Band 3; p0 = 2%, i = 46.72 deg; thin disk, radial radiation flux |
| 2020A&A...634L..15G | perfect alignment of compact astrosilicate grains; b/a = 1.1 or 0.9 |
| 2025ApJ...990..183U | scattering polarization ~ C P90 omega with C ~ 0.02, used as an MCMC prior (emcee) |
| 2024NatAs...8.1148U | 1e9 photon packages for ALMA polarization models |
| 2020ApJ...893...54Y | optical-depth check: peak T_b 30 K vs T_dust 67 K; models scored by segments within 30 deg |

## Field strength

| Paper | Inputs and result |
|---|---|
| 2020ApJ...896..157H | DCF on SiO v=0 J=2-1 angles after subtracting a 0.5"-smoothed angle map; delta phi = 4 deg, Delta V ~ 10 km/s, n = 1e6 cm^-3, correction 0.5; B_pos 23 mG, total ~30 mG (4B/pi) |
| 2020ApJ...893...33L | B0 ~ sqrt(8 pi rho) sigma_v / alpha; sigma_v = 10 km/s, alpha = 5 +- 2 deg, rho = 1.4e-22 g cm^-3; B = 0.67 mG (upper limit); B_t/B_0 = 0.062 +- 0.025 |
| 2024A&A...686A.274V | structure function (Koch et al. 2010) within ~2"; delta ~300 au, Delta' ~500 au, W1 ~40 au, N ~1.2; B_t/B_0 = 0.061 +- 0.001; ~19 mG at 250 au; lower limit if field not frozen in |
| 2019ApJ...884...48C | DCF and two variants; EVPA standard deviation; >= 10 independent Nyquist points per region; sigma_v from H13CO+ with Kolmogorov extrapolation (n = 0.36) |
| 2019A&A...626A..36D | DCF and structure function; order-of-magnitude only; xi = 0.5 (card) |
| 2019ApJ...879...25K | DCF called very rough; F = 91 mJy, D = 300 pc, kappa = 0.01 cm^2/g, T_d = 30 K; trans-sonic sigma assumed |
| 2018NatCo...9.4636L | Delta v_los ~15 km/s; Delta phi ~30 +- 20 deg; n_H2 >~ 2e6 cm^-3 |
| 2018MNRAS.477.2760M | sigma_theta ~0.38 rad; v_turb 0.1-1 km/s |
| 2017ApJ...847...92H | sigma_v ~0.8 km/s from 13CS |
| 2020ApJ...899...55A | sigma_phi ~ sigma_psi, M_A ~ sigma_psi |

## Zeeman and line polarization

| Paper | Inputs and result |
|---|---|
| 2021ApJ...908..141H | CN 2-1, robust 0.5, 0.25 km/s channels; `gofish` Kepler shift (i = 35.3 deg, 126 pc, 1.25 Msun); V = C1 I + C2 dI/dnu + 0.5 B Z dI/dnu on unblended parts; 3-sigma limits 5.0 and 4.2 mG |
| 2019A&A...624L...7V | CN in TW Hya; robust 0.5; low inclination so sensitive mainly to B_z |
| 2017A&A...603A..92V | SiO masers: z ~ 1500 s^-1 G^-1; B cos(theta) ~2.4 G; grain-alignment lower limit B > 13 mG |
| 2020ApJ...896..157H | g Omega/2pi = 230 Hz/G; implied ~10 G judged implausible |
| 2024A&A...686A.274V | PORTAL on LIME; turbulent velocity 1 km/s; extended-line Stokes V dominated by beam effects |
| 2020ApJ...899..152H | G-K model, uniform field and velocity gradient slab; predicted m_l ~3% matches CO in R Crt |

## Compact synchrotron sources

| Paper | Inputs and result |
|---|---|
| 2024ApJ...975..103P | RM from linear EVPA vs lambda^2 over four SPWs; core RM (4.5 +- 0.4)e4 rad m^-2; core fraction 0.88 +- 0.08% |
| 2019MNRAS.489..470G | 2D Gaussian fits on natural-weighted maps; 3 sigma detections; log-normal fraction A = 0.86, mu = 2.05, sigma = 0.97; median 2.2 +- 0.6% at 97.5 GHz |
| 2016A&A...593A..44L | XX/YY ratio vs parallactic angle, Q offset fitted; Sgr A* ~14 +- 1.2% at PA 158 +- 3 deg (Stokes U undetermined) |
| 2016A&A...593A..61M | dual differential polarimetry; differential RM can be biased by up to ~30% |
| 2018ApJ...868..101B | baselines < 50 klambda rejected; largest RMs suspect from phase wraps |
| 2019A&A...621A..18M | poor parallactic coverage in Bands 7/8 limits RM; EVPA variability can mimic RM |

=== EVIDENCE PACK (polarization-magnetic-fields) ===
# Evidence pack: Dust polarization and magnetic field strength (`polarization-magnetic-fields`)

Scope: polarization maps, B-field morphology, DCF strengths, scattering vs alignment

Built from 109 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2013-2026.
Matcher (regex over analysis steps): `polari[sz]|stokes|magnetic field|davis|chandrasekhar|\bdcf\b|grain alignment|self[- ]scattering`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- star_formation: 38
- protoplanetary_disks: 38
- agn_and_quasars: 21
- milky_way_ism: 16
- stellar_physics: 8
- high_z_galaxies: 7
- astrochemistry: 5
- transients: 5
- instrumentation: 5
- nearby_galaxies: 4
- evolved_stars: 4
- galaxy_clusters_and_sz: 3
- debris_disks: 2
- solar_system: 2
- exoplanets: 2

### Software named in the matched steps
- casa: 62
- miriad: 6
- radmc-3d: 6
- python: 4
- tclean: 3
- mcfost: 3
- emcee: 2
- gofish: 2
- casa imfit: 2
- gaincal: 2
- uvmultifit: 2
- casa clean: 2
- mrbeam: 2
- iraf: 2
- casa simobserve/simanalyze: 1
- artist dustpol: 1
- sparx: 1
- emcp: 1
- aips jmfit: 1
- makeplots (t. davis): 1
- clumpy: 1
- hypercat: 1
- imfit: 1
- xyamb: 1
- polcal: 1
- qufromgain: 1
- miriad imdiff: 1
- impbcor: 1
- applycal: 1
- casa 5.7.2: 1
- portal: 1
- lime 1.9.5: 1
- lenstronomy: 1
- casa simobserve: 1
- cadre: 1
- lamda: 1
- g-k code of yang & lai 2010: 1
- ps4c: 1
- camb: 1
- ace: 1

### Fitting methods (most common phrasings)
- free inclination and PA; best fit VLA 5a: i=48 deg, PA=138 deg: 1
- grid in k from 1 to infinity; best k=3 by mean residual deltaPA: 1
- Modified prior p1*p2: 1
- log-normal with A=0.86, mu=2.05, sigma=0.97: 1
- Linear fit of EVPA vs lambda^2: 1
- Least-squares-type fit; per-channel rms from region outside disk as uncertainties: 1
- 2D Gaussian components: 1
- Gaussian profile fits: 1
- Multi-Gaussian chi^2 minimization, adding Gaussians as needed: 1
- V proportional to dI/dν fit: 1
- Point source fit with position fixed to Stokes I: 1
- Least-squares (bootstrap shown in figures); priors not stated: 1
- Maximum likelihood factor minimizing XX-YY image difference: 1
- least-squares minimization: 1
- structure function fit; ratio 0.061 ± 0.001: 1
- Grid of chi_B values, no sampler: 1
- Not fitted; chi2_SED/N used for comparison only: 1
- imfit; errors from range of deconvolved parameters: 1
- by eye, no formal fit: 1
- chi-square minimization: 1
- Particle swarm over regularization weights; objectives chi2 of closure traces plus R_ms, R_hw, R_ptv: 1
- Gaussian fit to DCF: 1
- Power law F ∝ ν^α: 1
- heuristic optimisation in SciPy: 1
- Visual comparison of model and observed cuts and histogram (no formal fit stated): 1
- emcee MCMC; chi2 with covariance C = sigma^2 delta + s_f^2 M_i M_j; two rounds (s_f=0 then nonzero): 1
- Grid search minimizing NMSE (no sampler): 1
- Slopes estimated qualitatively: 1
- Elliptical Gaussian: 1
- hyperfine fitting of N2H+ spectra: 1

### Validation checks used
- calibrator polarization compared to ALMA Calibrator Catalogue: 1
- caveats on optical depth and RJ departure discussed: 1
- residual deltaPA histogram: 1
- consistency with sense of rotation from molecular line maps: 1
- Ratio ~1 outside the flip region indicates no depolarization: 1
- Model compared with observed vectors: 1
- Compared to pebble flux estimates in the literature: 1
- Compared with Tucci2012 and D05-based predictions: 1
- Optical depth check via peak brightness temperature 30 K vs dust temperature 67 K: 1
- Histogram of angle differences; fraction of model segments within 30 deg of observations: 1
- Calibrator checks show on- and off-axis leakage below 6 mJy/beam: 1
- RM errors in core radially symmetric; core shift negligible: 1
- Cross-check with stacking of red and mirrored blue unblended lines (no detection): 1
- astrometric error budget delta_tot: 1
- same estimate at 100 and 300 AU gives similar results: 1
- XX/YY gain ratio within ≈2% of unity; D-terms ≈1%: 1
- Checked via gain calibrator polarization stability, secondary peaks, separate base-bands, and independent ALMA reduction: 1
- PA consistent with 1.4 GHz after Faraday correction: 1
- vectors shown for P/sigma_P >= 3: 1
- independent aperture measurement at 0.12" east: 1
- compare synthetic degree and PA profile along PA 105 deg with observations: 1
- compared with B scaled from 0.4 pc via B∝r^-2 (~0.14 mG at 8 pc): 1
- Monte Carlo test of D-term and X-Y phase errors on Stokes V: 1
- Compared with Band 7/9 convolved to Band 5 beam and spectral index: 1
- Compared Q,U with Urata et al.; sidebands differ by 32 uJy in Q: 1
- Residual polarization of calibrator ≈0.1%: 1
- Checked DA-only, DV-only, DA-DV subsets and with/without PM antennas; consistent across spws: 1
- Residuals consistent with thermal noise; CI emission XX/YY ~1 away from absorption: 1
- Compared with true model in simulations and CASA Guide for 3C 286: 1
- Compared before/after re-normalisation spectra; compared flux with ACA and JCMT: 1
- Stokes V found dominated by beam effects for extended lines: 1
- Consistency between neighbouring channels used to argue against missing-flux artefacts: 1
- Qualitative comparison of predicted and observed polarisation morphology and fractions: 1
- Other velocity channels give field within 30%: 1
- MDP of 0.1 per cent added in quadrature to uncertainties: 1
- Lens and convolution do not rotate or change P; noise adds ~10 deg uncertainty: 1
- Compared calibrator EVPAs with MOJAVE/VLBA-BU/POLAMI; leakage rank correlation with archival data: 1
- Compared predicted m_l with observed CO polarization: 1
- Compared PS4C counts with DZ16 estimates: 1
- Compare to SED, ALMA profile, scattered light and polarisation: 1

### Key parameters and settings (bibcode: value)
- 2018A&A...616A..56A: vectors drawn at S/N=5 in polarized intensity
- 2018A&A...616A..56A: field inclination 55 deg; k free
- 2018ApJ...864...81O: robust = 0.5
- 2018ApJ...864...81O: sigma_PI = 2.9e-5 Jy/beam
- 2018ApJ...864...81O: Pixels above 10 sigma; gradients from the pixel with maximum F_nu r^-2
- 2025ApJ...990..183U: Polarization degree approx C P90 omega with C ~ 0.02; applied to entire disk
- 2025ApJ...990..183U: alpha_vert = 1e-4 (also 1e-3 and 1e-5 tested)
- 2020ApJ...893...54Y: robust = +0.5
- 2020ApJ...893...54Y: pixel 0.1'', S/N>3, orientation uncertainty <~9 deg
- 2020ApJ...893...54Y: misalignment 15 deg; cosmic-ray ionization 1e-16 s^-1 (misaligned) vs 5e-17 (aligned); stop at 0.1 Msun
- 2024ApJ...975..103P: nterms=2, cell 0.2", robust=1
- 2024ApJ...975..103P: polarized threshold 6 mJy/beam (3 x rms); no systematics in RMFIT
- 2021ApJ...908..141H: robust = 0.5; 0.25 km/s channels
- 2021ApJ...908..141H: Only low-frequency part of line 5 and high-frequency part of line 7 used because of blending
- 2025A&A...695A.149K: robust 0.5, restoring beam 65x45 mas PA -50
- 2018MNRAS.477.4380S: b = 0.4, beta_mag -> infinity, eps_ff = 0.015
- 2019ApJ...878L..26L: flux scale from power-law fit to calibrator catalog flux at 91.5 and 103.5 GHz
- 2019ApJ...878L..26L: Gamma_ej ≈15, Pi_0 ~0.6 (beta~0), t_dec ≈ T90 = 116 s
- 2018ApJ...865...13T: 1.5 sigma mask threshold
- 2020ApJ...893...33L: minimum detectable polarization 0.1%, systematic 0.03%
- 2020ApJ...893...33L: i=75 deg, theta=110 deg, p0=0.1, full resolution 1.2 mas, 14.4 Mpc
- 2020ApJ...893...33L: sigma_v=10 km/s, alpha=5+-2 deg
- 2017A&A...603A..92V: line robust 0.5; continuum robust -0.5
- 2017A&A...603A..92V: maser linewidth ~1 km/s; z≈1500 s^-1 G^-1
- 2017A&A...603A..92V: a=0.1 micron, s=0.5, Td=Tg=100 K, n_g≈9e9 cm^-3
- 2020ApJ...895...64L: robust 0.0
- 2020ApJ...895...64L: cross-hand delays from scan 61 on polarization calibrator
- 2016A&A...593A..44L: constant polarization PA assumed; Q offset delta fitted
- 2016A&A...593A..44L: 2.5 km/s velocity channels; CI 12m data tapered at 1.5"
- 2024Ap&SS.369...18M: robust = 0.5, Stokes I
- 2024A&A...686A.274V: solint 'inf' then 'int'
- 2024A&A...686A.274V: detection threshold >5 sigma_P
- 2024A&A...686A.274V: V_lsr CW Leo = -26.5 km/s
- 2024A&A...686A.274V: CW Leo dipole inclined 45 deg, PA 125 deg
- 2024A&A...686A.274V: turbulent velocity 1 km/s; gas mean particle mass 2.35 AMU
- 2024A&A...686A.274V: delta~300 au, Delta'~500 au, W1~40 au, N~1.2
- 2023Natur.621..483G: clean threshold 10 uJy
- 2023Natur.621..483G: 801x801 grid, 0.01'' pixel; pwv 0.6 mm; antenna configuration 2 (Cycle 8)
- 2020ApJ...899..152H: gpcal with options=qusolve
- 2018ApJ...858...85P: 5 to 15 bins; Poisson errors at 68% confidence
- 2018ApJ...858...85P: r=0.05, Planck best fit cosmology
- 2015A&A...581A..97S: Belt at 40 au, width 5 au, e_max=0.03, SW50 reference, material M1
- 2024PSJ.....5..230D: snapshot duration <5.5 min; pixel 3 mas
- 2020A&A...638L..14C: 14.86 K/Jy conversion; 10 min chunks; baseline fitted 1372-1376 MHz
- 2018ApJ...859..165S: P/sigma>4; sigma_PI ~ sigma_Q ~ sigma_U; 0.1% fraction uncertainty
- 2018ApJ...859..165S: A=10, theta=54 deg, nu0=60, r0=40 au, peak density ~6e10 cm-3
- 2016ApJ...831L..12K: robust 0.5; scales 0, 0.3, 0.9 arcsec
- 2016ApJ...831L..12K: Sigma0max 0.6, Sigma0min 0.008 g cm^-2; rc 170 au; rw 27 au; theta_d 30 deg; phi_d 60 deg; T 36 K; inclination 27 deg; PA 71 deg
- 2020ApJ...896..157H: angle error Delta(PA)=DeltaP/2P; vectors plotted for S/N>=4 (errors <7 deg)
- 2020ApJ...896..157H: delta phi = 4 deg; Delta V ~ 10 km/s; n(H2)=1e6 cm-3
- 2020ApJ...896..157H: g Omega/2pi=230 Hz/G
- 2024A&A...689A.299M: 10 s averaging; spectral window 227.1 GHz
- 2020MNRAS.492.1531M: central r < 4 px masked
- 2020MNRAS.492.1531M: a=0.34'', PA 18.1 deg, i 49.1 deg
- 2025ApJ...992..103Z: Briggs robust 0.5
- 2025ApJ...992..103Z: 3 sigma cutoff
- 2019MNRAS.487.4305S: KDM eps_ff=0.015; SFK eps_ff=0.0045, b=0.4, beta_mag to infinity
- 2019ApJ...884L..58U: P0 = 1%, 0.5%, 10%
- 2020A&A...636A..62K: DCF time steps 12 d (weekly) and 33 d (monthly)
- 2020A&A...636A..62K: 10% flux accuracy; position error ~1/10 beam; polarization threshold 9 sigma
- 2018A&A...620A..75K: dust condensation radius 1.5 or 2.5 R*IR; Al abundance 2.8e-6 rel. to H; star blackbody 2500 K; free parameters f and grain size
- 2014A&A...568A..40G: Contrast drop factor >~6 between 0.65'' and 0.3''
- 2019A&A...626A..36D: polarisation analysis above S/N of 4; analysis within inner third of primary beam
- 2019A&A...626A..36D: sigma_psi from circular-mean variance over selected pixels in POLI images
- 2017ApJ...851...55S: robust=1
- 2017ApJ...851...55S: instrumental P error 0.1%
- 2017ApJ...851...55S: intrinsic polarization 1%, grain size 30 um
- 2026ApJ..1003..215F: alpha=1e-4; Stokes 0.002-0.2; dust-to-gas 0.01; grid 504x1170; planets 0.5-2 M_iso; h/r 0.05, 0.06, 0.07
- 2026ApJ..1003..215F: alpha=1e-4, Stokes 0.01, surface density slope 1, flaring index 0.25, stellar mass ±3%
- 2020A&A...644A..11L: robust = 1, four phase-only selfcal rounds
- 2020A&A...644A..11L: n = 8 neighbours, 4 pixels per beam, lag about half a beam
- 2020A&A...644A..11L: grains 62.5% silicate/37.5% graphite, MRN, a_min 2 nm, a_max 10 um, aspect ratio 0.5, G0=1, 400 pc, 80 au beam
- 2025A&A...695A.233R: acceptable reduced chi-square < 2
- 2020A&A...634L..15G: log-normal sigma=0.1; MRN-like a^-3.5; b/a=1.1 or 0.9; G0=100
- 2024A&A...682A..56Z: Carbon sublimation at 300 K (also 500 K) with 50% and 80% organics tested
- 2014AJ....147..141H: sigma_v ~4 km/s (mean 2nd moment), M=2e5 Msun, R=2.8 pc, T=20 K
- 2018NatCo...9.4636L: robust = 2; resolution ~0.2"
- 2018NatCo...9.4636L: blue −22 to 8 km/s; red 11 to 42 km/s
- 2018NatCo...9.4636L: Δv_los ~ 15 km/s; Δφ ~ 30° ± 20°; n_H2 ≳ 2.0e6 cm^-3
- 2018ApJ...860...82H: robust = 0.5; shortest solint 10 s
- 2018ApJ...860...82H: a_max = 61 um best; 50 and 70 um tested
- 2025ApJ...984L..19Y: 8 free parameters; 5000 steps, 24 walkers; median from last 4200 steps
- 2020A&A...640A.111A: robust 0.5, Hogbom
- 2020A&A...640A.111A: within one-third of primary beam; 52 cores, 29 with polarization
- 2020ApJ...895L..46L: h/r = 0.07, alpha = 1e-3 and 1e-4
- 2025ApJ...990...59Y: Grid: Mdot 1e-5 to 1e-3 (20 log steps), r_disk 150-200 au, v_frag 0.1-30 m/s (30 log steps)
- 2019ApJ...879...25K: robust = 0.5
- 2019ApJ...879...25K: F = 91 mJy, D = 300 pc, kappa = 0.01 cm2/g, Td = 30 K
- 2019MNRAS.482L..29D: natural weighting
- 2019MNRAS.482L..29D: L*=28 Lsun, scale height 10 au at 100 au, DHS max void fraction 0.8, a_max ~100 um
- 2024ApJ...963..134Y: spherical grid 300x128x128 in r, theta, phi; r 1-300 au log; 1.6e8 photons
- 2024ApJ...963..134Y: a_max=140 um, a_min=0.1 um, Sigma_0=1 g/cm2, rc=61 au, rw=10 au, phic=109 deg, phiw=30 deg, T60=60 K
- 2018ApJ...868..101B: baselines <50 kλ rejected
- 2020ApJ...892..152H: robust = 2.0, 0.5, -0.5; 4 self-cal rounds
- 2025ApJ...990...80K: 3x3 pixel (36") smoothing kernel
- 2018MNRAS.477.2760M: sigma_theta ~0.38 rad; v_turb 0.1-1 km/s
- 2019A&A...624L...7V: robust 0.5
- 2024ApJ...971..129C: rho_m=1.675 g/cm3, Q>2 for stability
- 2017AJ....153....7Y: Profile fit L=A exp(-r^B/C^2) over 15 to 140 pixels
- 2024NatAs...8.1148U: 1e7 photon packages (continuum), 1e9 (ALMA polarization), 1e11 (NIR)
- 2018ApJ...855...92C: 5 sigma mask
- 2018A&A...619A.161C: grain size ~3 x lambda
- 2019ApJ...884...48C: robust 0.5; final self-cal solint 90 s
- 2019ApJ...884...48C: n=0.36; at least 10 independent (Nyquist) points per region; delta phi as std of EVPA
- 2019MNRAS.483.2371Y: p0 = 2%, i = 46.72 deg
- 2017ApJ...847...92H: sigma(v)~0.8 km/s from unpublished 13CS ALMA data
- 2019ApJ...879..101L: robust = 0.5; C18O channels 0.2 km/s
- 2018ApJ...861...91H: robust = -2 for high-resolution VLA 1623 image
- 2019ApJ...886L...4Z: c12=3.2e6, k=40
- 2018ApJ...854...56L: robust 0.5, beam ~0.12 arcsec
- 2017MNRAS.464L..31H: T=13 K, sigma_3D~0.7 km/s, L=0.35 pc


### Assumptions (bibcode: value)
- 2018A&A...616A..56A: optically thin, Rayleigh-Jeans
- 2018A&A...616A..56A: Shu et al. 2007 viscously accreting disk with advected, twisted field
- 2018ApJ...864...81O: Stokes V ignored
- 2018ApJ...864...81O: 0.87 mm radiation field used as proxy for 140 um field; inclination 27 deg, PA 341 deg
- 2025ApJ...990..183U: Smooth gas disk from 13C17O-based profile; dust-to-gas 0.01; rho_m = 1.675 g cm^-3; Q=1.4; M*=2.1 Msun
- 2019MNRAS.489..470G: Sources point-like; no Stokes V debiasing
- 2019MNRAS.489..470G: Debiasing term lowers P by ~0.01%, negligible
- 2019MNRAS.489..470G: Same distribution applied to all sub-populations
- 2020ApJ...893...54Y: Polarization orientations rotated by 90 deg to infer B-field if emission from aligned grains and optically thin
- 2020ApJ...893...54Y: Barotropic approximation
- 2024ApJ...975..103P: Single screen, chi = chi0 + RM lambda^2, same opacity at all wavelengths; linear fit due to limited frequency coverage
- 2021ApJ...908..141H: Inclination, position angle, distance, stellar mass fixed (i=35.3 deg, 126 pc, 1.25 Msun)
- 2021ApJ...908..141H: Fit uncertainties taken as 1 sigma; 3 sigma used for upper limits
- 2025A&A...695A.149K: 3C84 unpolarized for leakage; 3C286 PA 33 deg
- 2025A&A...695A.149K: field perpendicular to linear polarization vector for sigma components
- 2015ApJ...812...27A: R_curv ~ scale height H; B ∝ rho^(2/3); steady state; gas pressure ignored
- 2018MNRAS.477.4380S: Magnetic fields neglected
- 2019ApJ...878L..26L: Newtonian RS with g≈3, k=2
- 2019ApJ...885L..10L: Polarisation similar to that at 24 GHz
- 2020ApJ...893...33L: toroidal field with constant strength B0(r)=const; homogeneous grain alignment; optically thin; extinction curve R_V=5.5 (WD2001)
- 2020ApJ...893...33L: median volume mass density 1.4e-22 g/cm3 of whole torus (from LR2018)
- 2017A&A...603A..92V: Zeeman origin of circular polarization; field reversals at Vlsr~15 and 30 km/s
- 2017A&A...603A..92V: gas-to-dust ratio 100
- 2020ApJ...895...64L: Stokes V of polarization calibrator negligible
- 2020ApJ...895...64L: Gain calibrator intrinsic polarization constant over observations; systematic is Gaussian
- 2020ApJ...895...64L: β≈-0.43 from Urata et al.
- 2016A&A...593A..44L: Non-variable source; Stokes U not determined (no XY/YX)
- 2016A&A...593A..44L: Foreground CI absorber has negligible Tex and identical tau for X and Y
- 2016A&A...593A..61M: Short baselines so parallactic angle is same for all antennas; for 3C 286, constant gain amplitude ratio and Ceres unpolarized
- 2014ApJ...783L..13P: T=35 K, gas-to-dust 100, kappa=10 cm^2/g at 450 um for mass
- 2014ApJ...783L..13P: a=1 mm, rho_s=1 g/cm3, Sigma=10 g/cm2, St~1e-2; gas T=50 K for sound speed
- 2024A&A...686A.274V: Spherically symmetric envelope expanding at constant velocity; amorphous carbon opacities (CW Leo), silicate (R Leo); gas-to-dust 300 (CW Leo), 167 (R Leo)
- 2024A&A...686A.274V: Field frozen into gas, isotropic incompressible turbulence from transverse Alfven waves; result a lower limit if not frozen
- 2023Natur.621..483G: Constant polarization fraction of unity/1% and constant B orientation in source plane; continuum matches CO morphology
- 2020ApJ...899..152H: Uniform magnetic field and velocity gradient in constant-density slab
- 2018ApJ...858...85P: Polarization angle uniformly distributed; C_B ≈ C_E ≈ C_U ≈ C_Q
- 2015A&A...581A..97S: Inclination 89.5 deg; Mie spheres; wind speed 400 km/s; stellar mass 0.5 Msun
- 2020ApJ...891...80M: Stokes U unconstrained so |Q/I| is a lower limit
- 2018ApJ...859..165S: inclination from cos i = b/a
- 2018ApJ...859..165S: T = 20 K, kappa = 0.024 cm2/g at 1.3 mm, d = Ophiuchus distance
- 2016ApJ...831L..12K: compact spherical grains, size slope -3.5
- 2025NatAs...9..526O: inclination 27 deg, PA 161 deg; same p_max in both layers for dual model
- 2016ApJ...824..132N: Absolute EVPA error 0.4 deg from 2 deg misalignment over 29 antennas
- 2020ApJ...896..157H: density 1e6 cm-3 from maser pumping; correction factor 0.5; total field 4B/pi
- 2020ApJ...896..157H: uniform field for all velocity components
- 2024A&A...689A.299M: Negligible circular polarization
- 2013ApJ...779...96T: 0.5<m_A<2 range, f_g=1, alpha_vir,cl=1, phi_geom=1
- 2019MNRAS.487.4305S: Zero magnetic field in SFK
- 2019ApJ...884L..58U: Tangled magnetic field in random cells
- 2018A&A...620A..75K: Suh (2016) amorphous Al2O3 optical constants; gas density from CO model
- 2019ApJ...872..121U: X(H13CO+)=6e-11, X(C34S)=4.87e-10, distance 8.5 kpc, mu=2.35e-57 Msun, no external pressure or magnetic field
- 2019PASP..131g5003G: Stokes V = 0 and negligible second-order D-terms
- 2019A&A...626A..36D: polarisation dominated by magnetic alignment, not scattering
- 2019A&A...626A..36D: MM3 velocity dispersion assumed equal to MM4
- 2017ApJ...851...55S: Oblate grains with shortest axes aligned radially
- 2026ApJ..1003..215F: Stellar mass 1 Msun; scale-free; fixed planet orbit
- 2017MNRAS.469L.123O: turbulent field produces random polarization orientation; turbulent region size 4 kpc
- 2025A&A...695A.233R: gamma_j=10, phi=0.01 rad, viewing angle 0.1 rad, equipartition, m=1, n=2, alpha=-0.5
- 2020A&A...634L..15G: Perfect alignment, homogeneous compact astrosilicate grains
- 2019ApJ...878L..25H: Negligible depolarization between source and observer for point source at mm wavelengths
- 2018NatCo...9.4636L: ρ = 1.4 n_H2 m_H2
- 2018ApJ...860...82H: MRN n(a) ∝ a^-3.5, a_min = 0.25 um; spherical grains of ice 62%, organics 30%, silicates 8%; Sigma_c = 0.25 g cm^-2 at 100 au, H_c = 3 au, gamma = 1.0
- 2025ApJ...984L..19Y: T_mid = T100 (r/100 au)^-0.5; grain size index -3.5; amin 1e-5 cm; DSHARP opacities
- 2019A&A...621A..18M: SW image unpolarized so p_d is NE polarization
- 2020A&A...640A.111A: Grain alignment by radiative alignment torques; polarization perpendicular to B
- 2026ApJ..1002L..28Y: SIS profiles, circular orbits, ln Lambda=0.93 (galaxies) and ~6 (BHs)
- 2020ApJ...895L..46L: gas-to-dust ratio 100; gamma = 0.1; max particle size 0.1 mm
- 2014ApJ...791..108F: isothermal cylinder; ignores magnetic fields and external pressure
- 2019ApJ...879...25K: Grains aligned with magnetic fields; optical depth tau~0.2 at peak for T=30 K
- 2019ApJ...879...25K: Gas-to-dust ratio 100; trans-sonic non-thermal velocity ~0.3 km/s at 30 K; cylinder geometry
- 2019MNRAS.482L..29D: spherical grains, scattering only source of polarisation, multiple scattering included
- 2024ApJ...963..134Y: Dust composition giving n=2.3, k=0.023; T=T60 (r/60 au)^-0.5; only self-scattering
- 2025A&A...699A..62J: outflow velocity taken as escape velocity
- 2021AJ....161..238W: mu = 2.3; material density 1.8 g/cm3
- 2018MNRAS.477.2760M: Polarization not from self-scattering
- 2018MNRAS.477.2760M: Free-fall density profile; v_turb 0.1 to 1 km/s
- 2019A&A...624L...7V: Low inclination so sensitive mostly to vertical field B_z
- 2024ApJ...971..129C: Sigma_g/Sigma_d=100 for Q profile
- 2019A&A...622A.196K: ALMA polarized flux originates from the VLBI core; no RM >~1e8 rad/m^2
- 2020ApJ...904L..24S: eta=1, Vs=3900 km/s
- 2020ApJ...899...55A: sigma_phi ~ sigma_psi, M_A ~ sigma_psi
- 2017ApJ...842L...9H: Isothermal, ideal MHD; scaled with cs = 0.2 km/s, nH = 1000 cm^-3
- 2017ApJ...842L...9H: Field perpendicular to measured polarization; Stokes I traces column density structure
- 2018A&A...619A.161C: rho_pc = 1 g/cm3, St near unity
- 2019ApJ...884...48C: Dust grains aligned with B; EVPA dispersion due to non-thermal motions; spherical geometry for density
- 2019MNRAS.483.2371Y: Optically and geometrically thin disk; radiation flux radial; Stokes I from high-resolution Band 3 image
- 2017ApJ...847...92H: B perpendicular to polarization orientation
- 2016ApJ...820...54K: model uncertainty ±50%
- 2019ApJ...879..101L: B-field perpendicular to polarization when envelope optically thin
- 2018ApJ...869L..47Z: GI limit with Toomre Q=1 caps gas surface density; preferred alpha=1e-3 and DSD1
- 2016ApJ...833..209O: uniform density sphere; magnetic fields neglected
- 2019ApJ...886L...4Z: All emission in these regions is synchrotron (upper limit)


### Limitations the authors admit
- 2018A&A...616A..56A: Residuals likely from binary-induced field twisting not in the model; optical depth affects grain size estimate
- 2018ApJ...864...81O: Northern peaks optically thick, so midplane grain size is unmeasurable
- 2018ApJ...864...81O: Single wavelength cannot separate scattering from alignment
- 2025ApJ...990..183U: Preference for amorphous-carbon-rich dust within 40 au arises partly from priors and high optical depth, not conclusive
- 2025ApJ...990..183U: Filling factor assumed constant across the size distribution; smooth gas disk assumed
- 2019MNRAS.489..470G: ALMA and ATCA not simultaneous so no joint fit; small sample prevents firm conclusions
- 2019MNRAS.489..470G: Stokes V unreliable in Cycle 3
- 2020ApJ...893...54Y: Simulations are axisymmetric, barotropic, with constant polarization efficiency; they do not reproduce N-S asymmetry or the intensity morphology; the misaligned run used a different cosmic-ray rate
- 2024ApJ...975..103P: 1.3 mm and 3.5 mm emission may not arise from same location; limited resolution hinders HST-1 vs inner jet attribution
- 2021ApJ...908..141H: Stacking destroys signal from a vertical field; lines 5-7 remain blended
- 2025A&A...695A.149K: Better angular and spectral resolution needed to confirm Zeeman triplets
- 2025A&A...695A.149K: CH3CN optically thick, so temperatures overestimated
- 2015ApJ...812...27A: Inclination poorly constrained by the disk model; mass estimates are uncertain by optical depth, temperature, abundance
- 2015ApJ...812...27A: PV mean-position method underestimates break radius at limited resolution
- 2018MNRAS.477.4380S: Dust parameters cannot be simultaneously constrained; clump conditions assumed equal to galaxy-wide
- 2018MNRAS.477.4380S: Magnetic fields unavailable and neglected
- 2019ApJ...878L..26L: Systematic uncertainties from RS dynamics approximations and stochastic random walk; forward-shock parameters degenerate since nu_a not located
- 2018ApJ...865...13T: X_CO uncertainty may overestimate mass by a factor of a few
- 2018ApJ...865...13T: Projection effects: motions in plane of sky unknown
- 2019ApJ...885L..10L: Systematics associated with phasing cycles in active-phasing scans
- 2020ApJ...893...33L: B-field strength is an upper limit because median density of the whole torus was used; axisymmetric model cannot explain asymmetry
- 2017A&A...603A..92V: Higher resolution needed to map field structure
- 2020ApJ...895...64L: Origin of time-varying systematics (e.g. XY phase) not investigated; second-order corrections beyond scope
- 2016A&A...593A..44L: Absolute flux uncertain (~20%) because Titan scans were largely flagged; single epoch only.
- 2016A&A...593A..61M: Differential RM imaging with polarized fiducial element can be biased by up to ~30%.
- 2014ApJ...783L..13P: Emission may be partly optically thick so asymmetries may not trace mass; masses are lower limits.
- 2024Ap&SS.369...18M: Cannot draw conclusions on continuum morphology
- 2024A&A...686A.274V: Spatial filtering resolves out much CO flux, overestimating polarisation fractions by factor 2-3.
- 2024A&A...686A.274V: Circular polarisation of extended lines dominated by beam effects; no test of anisotropic resonant scattering.
- 2023Natur.621..483G: Lack sensitivity and resolution to map B-field at ~100 pc scales; field strength cannot be reliably estimated from dust polarization
- 2020ApJ...899..152H: Observations are sensitivity-limited; interferometric filtering may overestimate m_l
- 2018ApJ...858...85P: Planck detections may be biased upward toward high fractional polarization; forecasts limited to ≤150 GHz, excluding dusty galaxies
- 2015A&A...581A..97S: Axisymmetric discs only; models not unique
- 2024PSJ.....5..230D: High-dielectric region seen only at limb due to incomplete rotational coverage; shape mismatch could mimic it
- 2024PSJ.....5..230D: Thermal inertia retrieval requires accurate shape model
- 2020A&A...638L..14C: rms does not decrease as 1/sqrt(t), possibly pointing jitter or weak interference in commissioning
- 2020A&A...637A...7M: Non-simultaneous XD and XH observations and time variability; high uncertainties
- 2020A&A...637A...7M: Assumed covering factor of 1
- 2018ApJ...859..165S: Model is simple, axisymmetric, excludes rotation, matched by eye; short spacings missing to trace hourglass
- 2016ApJ...831L..12K: High southwest polarization fraction may be due to interferometric filtering
- 2025NatAs...9..526O: Reduced chi-square much greater than 1; more detailed observations and refined models needed
- 2016ApJ...824..132N: Only three VLBI points, non-simultaneous, C2 may be optically thick; Stokes I dynamic-range limited
- 2020ApJ...896..157H: ALMA Stokes V calibration not guaranteed in Cycle 5
- 2020ApJ...896..157H: Fractional polarization may be overestimated because short baselines lack
- 2024A&A...689A.299M: Assumes vanishing circular polarization; MO-PSO does not reproduce multimodality; primary-beam polarization not treated
- 2020MNRAS.492.1531M: Grain size distribution may be biased to small sizes; dust mass and optical depth uncertain
- 2025ApJ...992..103Z: G14 RO distribution cannot be distinguished from random due to small numbers; G28 and I18360 excluded
- 2013ApJ...779...96T: Mass uncertain by a factor of about 2; core size definition arbitrary; kinematic distance to F uncertain
- 2019MNRAS.487.4305S: Large systematic uncertainties; magnetic field strength unknown; need larger sample
- 2019ApJ...884L..58U: Non-simultaneous multi-wavelength polarimetry limits conclusions
- 2016ApJ...829L..23B: Short-spacing problem makes Mach number anti-correlated with pressure normalization
- 2016ApJ...829L..23B: Pre-shock temperature unconstrained in Chandra data
- 2020A&A...636A..62K: Photon index uncertainties too large for quantitative analysis
- 2018A&A...620A..75K: Spherical model gives reduced chi2 ~4.0; a non-spherical model is needed
- 2018A&A...620A..75K: Beam-shift effect in ZIMPOL data not corrected; Clump γ polarization likely overestimated
- 2023NatAs...7...80U: PA difference between radio and optical only ~90% significant
- 2019ApJ...872..121U: Abundance uncertainty up to a factor of 2 affects masses
- 2019PASP..131g5003G: Not applying Tsys leaves a source-dependent amplitude offset; flux uncertainty up to 10-20% in some sources
- 2014A&A...568A..40G: Low ALMA angular resolution prevents strong conclusions from spatial coincidence
- 2024ApJ...970...56P: VLA bands observed sequentially, not simultaneously, so no instantaneous spectrum.
- 2019A&A...626A..36D: DCF/SF values are order-of-magnitude; flux loss 30-70% from missing short spacings
- 2019A&A...626A..36D: Mass and column density errors could be factors of 5-10
- 2017ApJ...851...55S: Stokes V detection may be spurious and not discussed
- 2017ApJ...851...55S: Model is not unique and does not match all details
- 2017MNRAS.469L.123O: Low SNR in the ridge limits constraint on polarization; edge gradients in spectral index maps
- 2020A&A...644A..11L: Significant uncertainty in reliability of Pfrac due to filtering and different scales
- 2020A&A...644A..11L: Simulations do not reproduce the observed morphologies, and massive ones are axisymmetric and unturbulent
- 2025A&A...695A.233R: Sparse uv-coverage causes large systematic uncertainties on core size and flux
- 2020A&A...634L..15G: Only homogeneous compact weakly elongated grains; no fluffy aggregates or self-scattering
- 2024A&A...682A..56Z: Disk model lacks the east-west asymmetry of the observed source, so outskirts are overpredicted
- 2014AJ....147..141H: Interferometer-only data resolves out structure larger than 9.1"
- 2019ApJ...878...73Y: Three candidates may contain false detections
- 2019ApJ...878L..25H: Large reduced chi^2 in SED fits possibly due to differing epochs; significant variability at 242 GHz
- 2018MNRAS.475.3004S: Mass is subject to large systematic uncertainty from the assumed Galactic XCO.
- 2018NatCo...9.4636L: Polarization cannot be mapped reliably beyond ~3"; redshifted component not detected; field ambiguity (poloidal vs toroidal) unresolved
- 2018ApJ...860...82H: Cannot draw firm quantitative conclusions about dust settling since the optical depth across the polarized region is uncertain
- 2025ApJ...984L..19Y: CO/H2 ratio uncertain; absolute gas surface density scales as X_CO^-0.5
- 2025ApJ...984L..19Y: Dust opacity model uncertainty affects gas-to-dust ratio; limited spatial resolution
- 2019A&A...621A..18M: Poor parallactic angle coverage in Bands 7/8 limits RM precision; EVPA variability could mimic RM
- 2020A&A...640A.111A: Sample size does not allow discriminating 50-70 deg, random, or bimodal populations
- 2026ApJ..1002L..28Y: T_dust and beta assumed; multi-band FIR needed
- 2026ApJ..1002L..28Y: Pair fraction is a lower limit because the survey is incomplete
- 2020ApJ...895L..46L: Two-Gaussian model underestimates the shortest baselines; D2 is tentative; plateau width poorly measured
- 2025ApJ...990...59Y: Polarization may arise from aligned grains rather than self-scattering, making v_frag highly uncertain
- 2014ApJ...791..108F: Mass uncertain by at least a factor of two from opacity; distance conflict; no magnetic or external pressure
- 2019PASJ...71L...3F: Low-frequency spectra for 2017 are unavailable; earlier periastron spectra used instead
- 2019ApJ...879...25K: DCF very rough; no observed non-thermal linewidth; central mass uncertain
- 2019MNRAS.482L..29D: Ring widths unresolved so optical depth only a lower limit; absolute flux calibration may offset alpha by 0.3
- 2024ApJ...963..134Y: True nature of moderate settling cannot be determined; alpha limited by gas column uncertainty
- 2018ApJ...868..101B: Largest fitted RMs are suspect due to phase wrap, poor fits and calibration errors at low polarization
- 2020ApJ...892..152H: Stokes I is dynamic-range limited, which limits interpretation of polarization fraction
- 2025A&A...699A..62J: Detailed SED modeling is needed to constrain the magnetic field
- 2021AJ....161..238W: Midplane thermal emission not vertically resolved; smooth tapered density model too simple
- 2025ApJ...990...80K: Protostellar mass not included in core mass, so gravity may be underestimated
- 2018MNRAS.477.2760M: Model comparison is only qualitative; DCF validity uncertain; interferometric filtering of large scales
- 2019A&A...624L...7V: Continuum polarisation low S/N and no other wavelengths, so nature is beyond scope
- 2024ApJ...971..129C: Only two bands constrain four parameters; priors needed; porosity unconstrained
- 2019A&A...622A.196K: Absolute flux density at 86 GHz uncertain by ~30%.
- 2024ApJ...972...74M: Unpolarized optical emission in 3C 273 and 3C 454.3 prevents definitive conclusions
- 2020ApJ...899...55A: Statistically limited sample; Lupus III result marginal
- 2017ApJ...842L...9H: Trends in P vs I are weak and could be geometrical; simulations lack outflows, disks, non-ideal MHD
- 2024NatAs...8.1148U: Dust composition uncertain; MRI/wind accretion not modeled; model underestimates intensity beyond 200 au
- 2018ApJ...855...92C: Cannot definitively state the cause of the polarization hole
- 2018A&A...619A.161C: Emission only marginally optically thin so masses are lower limits; large uncertainties in opacity and gas surface density
- 2018A&A...619A.161C: Spectral index decrease may be due to optical thickness rather than grain growth
- 2026ApJ..1001..124M: Arc may be optically thick at 0.9 mm; vortex origin not unique; need longer-wavelength and gas kinematics
- 2019ApJ...884...48C: Dust temperature poorly constrained; higher core temperatures would lower masses and raise alpha_total
- 2019ApJ...884...48C: Velocity dispersion extrapolated via an assumed Kolmogorov law
- 2017ApJ...847...92H: Large uncertainties in energetics inputs
- 2016ApJ...820...54K: Disk model is not a unique solution
- 2019ApJ...879..101L: Polarization toward disk unresolved and possibly affected by self-scattering; deeper observations needed; secondary source unconfirmed; collapse model simplistic
- 2018ApJ...869L..47Z: Gap profiles fitted at fixed 1000 orbits; dust feedback ignored
- 2018ApJ...869L..47Z: Occurrence rates are upper limits since gaps may not be planetary
- 2018ApJ...861...91H: VLA 1623 sources lie outside the inner 1/3 of the primary beam where polarimetry is considered reliable.
- 2018ApJ...861...91H: CB disk size may be a lower limit due to maximum recoverable scale.
- 2016ApJ...833..209O: Extended filament emission resolved out; cannot rule out deeply embedded low-mass protostars; core sizes assumed compact
- 2019A&A...624A...7V: Model is a compromise and working model, not best fit; J1852 modeling degenerate
- 2019ApJ...886L...4Z: Opening angle and inclination weakly constrained by the model
- 2019ApJ...886L...4Z: Detailed non-LTE H30alpha modeling not done
- 2018MNRAS.474.5105B: Data not flux calibrated

### Settings cards flag as needed but not stated
- casa version: 12
- self-calibration solution intervals: 5
- casa version and pipeline version: 3
- self-calibration solution intervals and number of iterations: 3
- line-free channel ranges for continuum: 3
- image size and cell size: 3
- source coordinates: 3
- casa version and whether the pipeline or manual calibration was used: 3
- self-calibration solution intervals and number of rounds: 2
- flagging details: 2
- line-free channels used for uvcontsub and fit order: 2
- flux scale uncertainty: 2
- self-calibration solution intervals and reference antenna: 2
- pipeline version: 2
- polarization debiasing method: 2
- whether self-calibration was applied: 2
- casa version and calibration procedure: 2
- casa version and whether alma pipeline or manual calibration was used: 1
- tclean parameters (weighting/robust, deconvolver, cell, image size, masks, niter, threshold): 1
- polarization calibration details (leakage solutions, calibration of polarization angle): 1
- dustpol input parameters (density, temperature, grain properties, disk size): 1
- how model maps were compared (pixel selection, error on pa): 1
- how the bands 3 and 7 spectral index maps were aligned and noise-clipped: 1
- number of tclean iterations, cleaning threshold, masks, cell and image size: 1
- continuum channel selection (line-free channels): 1
- flux calibrator and flux-scale uncertainty: 1
- how polarization calibration was applied in detail: 1
- smoothing kernel details for resolution comparison: 1
- debiasing formula details and the inner-disk gaussian fitting setup: 1
- imaging details: cell size, image size, deconvolver, masking, niter/threshold: 1
- azimuthal averaging details: deprojection geometry (inclination, pa), radial bin width, radial rang…: 1
- exact reprocessing steps for the 0.45, 0.87, 1.3 and 7.9 mm images: 1
- dust material density and optical constants details per material (partly cited only): 1
- details of the pebble accretion calculation setup (seed planet radial locations): 1
- treatment of the stokes number and gas profile at the gaps: 1
- number/size of stokes images and cell size: 1
- whether tclean/clean parameters, niter, thresholds, masks were used: 1
- exact way polarization leakage and angle calibration were solved (casa tasks): 1
- spectral windows combined for the gaussian fits and per-sub-band fitting procedure: 1
- how redshifts were assigned and the galactic rm values used: 1

## Paper excerpts (40 of 109, chosen for detail and spread over fields/years)

### 2018A&A...616A..56A: Magnetic field in a young circumbinary disk (2018; star_formation, protoplanetary_disks; observational_alma_primary)
- question: Which mechanism (self-scattering, radiative alignment, or magnetic alignment) produces the multi-band polarization in the BHB07-11 circumbinary disk?
- step 1: Image Stokes I, Q, U in common uv range
  - method: cleaned maps with common uv range 27-1310 klambda, primary beam corrected [2.1 ALMA: "we produced cleaned maps using a *uv* range that is common for all bands, from 27 to 1310 k$\lambda$"]
  - software: CASA
  - parameter: vectors drawn at S/N=5 in polarized intensity [2.1 ALMA: "we adopt a signal-to-noise ratio of 5 in polarized intensity for all bands in order to produce vector maps"]
  - validation: calibrator polarization compared to ALMA Calibrator Catalogue [2.1 ALMA: "The mean polarization fraction of $2.4$% is consistent with earlier measurements of this object according to the ALMA Calibrator Source Catalogue."]
- step 2: Derive spectral index and beta
  - method: Smooth Band 3 and 7 Stokes I to common beam, compute alpha from flux difference, beta = alpha - 2 [4 Spectral properties: "We computed the dust opacity index $\beta$ assuming an optically thin and Rayleigh-Jeans regime for the disk edge ($\beta = \alpha - 2$)"]
  - assumption: optically thin, Rayleigh-Jeans [4 Spectral properties: "assuming an optically thin and Rayleigh-Jeans regime for the disk edge"]
  - validation: caveats on optical depth and RJ departure discussed [4 Spectral properties: "An accurate estimation of maximum grain size is affected by departures from the Rayleigh-Jeans regime and changes in optical depth through the disk."]
- step 3: Test radiative alignment model
  - method: synthetic polarization maps for VLA 5a, 5b, and 1/d^2 combination; inclination and PA free; compare mean deltaPA [7.1 Alignment with radiation field: "We used the disk inclination and position angle in the plane-of-sky as free parameters."]
  - fitting: free inclination and PA; best fit VLA 5a: i=48 deg, PA=138 deg [7.1 Alignment with radiation field: "from which a disk inclination of 48$^\circ$ and position angle of 138$^\circ$ were derived (fit error of $\pm 15\ensuremath{^\circ}$)"]
  - validation: residual deltaPA histogram [7.1 Alignment with radiation field: "The histogram in Fig. [7](#fig:rf) shows the distribution of residuals ($\delta$PA)"]
- step 4: Fit magnetic field model
  - method: DustPol models of Shu07 disk at 343 GHz, i=52 deg, rotated 138 deg, varying k=Bp/Bphi, processed with simobserve/simanalyze with Band 7 configuration; compared to 90-deg rotated PA [7.2 Alignment with magnetic field: "We ran DustPol assuming a frequency of 343 GHz as in Band 7 observations."]
  - software: ARTIST DustPol, CASA simobserve/simanalyze
  - parameter: field inclination 55 deg; k free [7.2 Alignment with magnetic field: "we adopted $i=55$$^\circ$ and considered $k$ as a free parameter"]
  - assumption: Shu et al. 2007 viscously accreting disk with advected, twisted field [7.2 Alignment with magnetic field: "we assumed the model by (cite: Shu07) of a viscously accreting disk surrounding a low-mass protostar"]
  - fitting: grid in k from 1 to infinity; best k=3 by mean residual deltaPA [7.2 Alignment with magnetic field: "The best fit is represented by the $k=3$ case, with mean residual $\delta$PA$= 23.4\ensuremath{^\circ}$"]
  - validation: consistency with sense of rotation from molecular line maps [7.2 Alignment with magnetic field: "Our results are consistent with the rotation seen in our molecular line maps"]
- result: Mean polarization fraction Band 3 = 7.9 ± 0.8 % [3 Polarization properties: "the mean polarization fraction is 7.9$\pm$0.8, 5.3$\pm$0.3 and 3.5$\pm$0.1% for bands 3, 6 and 7, respectively"]
- result: Mean polarization fraction Band 6 = 5.3 ± 0.3 % [3 Polarization properties: "the mean polarization fraction is 7.9$\pm$0.8, 5.3$\pm$0.3 and 3.5$\pm$0.1% for bands 3, 6 and 7, respectively"]
- result: Mean polarization fraction Band 7 = 3.5 ± 0.1 % [3 Polarization properties: "the mean polarization fraction is 7.9$\pm$0.8, 5.3$\pm$0.3 and 3.5$\pm$0.1% for bands 3, 6 and 7, respectively"]
- result: Mean spectral index Band 3-7 = 3.01 ± 0.02 dimensionless [4 Spectral properties: "The spectral index has a mean value of $3.01 \pm 0.02$ with a minimum $2.67 \pm 0.01$ near the center of the disk."]
- result: Mean dust opacity index beta = ~1.0 ± not stated dimensionless [4 Spectral properties: "found $\langle\beta\rangle \sim 1.0$"]
- result: Best magnetic model mean residual deltaPA (k=3) = 23.4 ± sigma = 7.5 deg deg [7.2 Alignment with magnetic field: "The best fit is represented by the $k=3$ case, with mean residual $\delta$PA$= 23.4\ensuremath{^\circ}$ and standard deviation $\sigma=7.5\ensuremath{^\circ}$."]
- result: Radiative alignment (VLA 5a) mean deltaPA = 20.2 ± sigma = 6.9 deg deg [7.1 Alignment with radiation field: "with mean $\delta$PA$= 20.2\ensuremath{^\circ}$ and $\sigma = 6.9\ensuremath{^\circ}$"]
- limitation (authors): Residuals likely from binary-induced field twisting not in the model; optical depth affects grain size estimate [abstract: "The residual is likely due to the internal twisting of the magnetic field due to the binary system dynamics, which is not considered in our model."]
- not stated (card): CASA version and whether ALMA pipeline or manual calibration was used; tclean parameters (weighting/robust, deconvolver, cell, image size, masks, niter, threshold); polarization calibration details (leakage solutions, calibration of polarization angle); DustPol input parameters (density, temperature, grain properties, disk size); how model maps were compared (pixel selection, error on PA); how th…

### 2018ApJ...864...81O: Two Different Grain Size Distributions within the Protoplanetary Disk around HD 142527 Revealed by ALMA Polarization Observation (2018; protoplanetary_disks; observational_alma_primary)
- question: Which polarization mechanism (magnetic grain alignment, radiative grain alignment, or self-scattering) produces the 0.87 mm polarized emission in different regions of the HD 142527 disk, and what does that imply for grain sizes
- step 1: Calibrate and image Stokes I, Q, U
  - method: CASA calibration, phase+amp self-cal, tclean of combined Cycle 3+4 data [2 Observations: "All images were reconstructed using the CASA task tCLEAN, with Briggs weighting with a robust parameter of 0.5 by combining these data."]
  - software: CASA, tclean
  - parameter: robust = 0.5 [2 Observations: "Briggs weighting with a robust parameter of 0.5"]
- step 2: Derive polarized intensity, angle and fraction
  - method: PI=sqrt(Q^2+U^2), debiased; polarization angle errors from CASA guide; fraction only above 3 sigma_PI [2 Observations: "The polarization fraction ($P_{\rm frac}=PI/I$) is derived only where the detection is above the threshold 3$\sigma_{\rm PI}$."]
  - software: CASA
  - parameter: sigma_PI = 2.9e-5 Jy/beam [2 Observations: "$\sigma_{\rm PI}=2.9\times10^{-5}$ Jy beam$^{-1}$"]
  - assumption: Stokes V ignored [2 Observations: "we ignore the Stokes *V* component in this study because it has not been well characterized for ALMA"]
- step 3: Compare with previous lower-resolution data
  - method: Smooth Q, U, I of new data to the previous beam and compare polarization-fraction ratios [3.2 Dependence on Spatial Resolution: "Then, we calculate the ratio of the polarization fraction for our high resolution data to that for the previous data."]
  - validation: Ratio ~1 outside the flip region indicates no depolarization [3.2 Dependence on Spatial Resolution: "In the whole region excepting for the part where the flip is found, the ratio is almost unity"]
- step 4: Test polarization vector morphology against the mechanisms
  - method: Offset between polarization angle and projected radial direction versus PA; model of radiative alignment from continuum intensity gradient rotated by 90 deg [4.1 Morphology of Polarization Vectors: "we calculate the offset angle between the polarization angle and the position angle measured from the central star."]
  - parameter: Pixels above 10 sigma; gradients from the pixel with maximum F_nu r^-2 [4.1 Morphology of Polarization Vectors: "First, we find the pixel where $F_{\nu}\times r^{-2}$ is a maximum within the image."]
  - assumption: 0.87 mm radiation field used as proxy for 140 um field; inclination 27 deg, PA 341 deg [4.1 Morphology of Polarization Vectors: "we regard the radiation field of 0.87 mm as the radiation field of $140$ $\mu$m for simplicity."]
  - validation: Model compared with observed vectors [4.1 Morphology of Polarization Vectors: "the model does not match the observed polarization vectors."]
- result: Total continuum flux = 3.0 ± not stated Jy [3.1 New High Spatial Resolution Data: "The total flux is derived to be 3.0 Jy"]
- result: Polarization fraction in southern minimum-intensity region = ~15 ± not stated % [3.1 New High Spatial Resolution Data: "A high polarization fraction of $\sim15$% is found in the minimum intensity region"]
- result: Upper limit on polarization fraction at stellar position = ~2.0 ± not stated % [3.1 New High Spatial Resolution Data: "We calculate the upper limit of the polarization fraction to be $\sim2.0$%"]
- result: Inner disk peak intensity = 4.4 ± not stated mJy/beam [3.1 New High Spatial Resolution Data: "with a peak intensity of 4.4 mJy beam$^{-1}$"]
- result: Mean polarization angle error = ~2.5 ± not stated deg [2 Observations: "The 1$\sigma$ error of the polarization angle is derived to be $\sim2.5^\circ$ on average."]
- result: Northeast to southwest intensity contrast (robust=-2 image) = 22:1 ± not stated dimensionless [High Spatial Resolution Image and Spira…: "The contrast in the intensity reaches a ratio of $22:1$ between the northeast peak and the southwest minimum"]
- limitation (authors): Northern peaks optically thick, so midplane grain size is unmeasurable [abstract: "The grain size near the middle plane in the northern region cannot be measured because the emission at 0.87 mm is optically thick."]
- limitation (authors): Single wavelength cannot separate scattering from alignment [4.5 Future Prospects: "In the future, we distinguish the polarization caused by scattering from that caused by grain alignment by observing multiple millimeter wavelengths"]
- not stated (card): Number of tclean iterations, cleaning threshold, masks, cell and image size; Self-calibration solution intervals and number of rounds; Continuum channel selection (line-free channels); Flux calibrator and flux-scale uncertainty; How polarization calibration was applied in detail; Smoothing kernel details for resolution comparison; Debiasing formula details and the inner-disk Gaussian fitting setup

### 2025ApJ...990..183U: Multiwavelength Dust Characterization of the HL Tau Disk and Implications for Planet Formation (2025; protoplanetary_disks; observational_alma_primary)
- question: What are the dust properties (temperature, surface density, maximum grain size, composition, filling factor, size distribution) of the HL Tau disk, and what do they imply for planet formation via pebble accretion?
- step 5: Add polarization-based prior
  - method: Add prior p2 = 0.5{1+tanh[(P90*omega_eff(345GHz)-0.15)/0.1]} on polarization efficiency and rerun full fit [4.3 Scattering Polarization: "we perform the MCMC analysis with an additional prior based on the polarization efficiency at 0.87 mm"]
  - software: emcee
  - parameter: Polarization degree approx C P90 omega with C ~ 0.02; applied to entire disk [4.3 Scattering Polarization: "it can be roughly approximated as $C P_{90} \omega^{\rm eff}_{\nu}$ with $C \sim 0.02$ (cite: Kataoka+16)"]
  - fitting: Modified prior p1*p2 [4.3 Scattering Polarization: "the modified prior is given by $p_{1}p_{2}$."]
- step 6: Derive pebble flux, accretion rate and pebble lifetime
  - method: Compute Stokes number, radial drift, pebble flux 2 pi r v_r Sigma_d, pebble accretion efficiency (Liu & Ormel 2018) for 3 Earth-mass seed from MCMC posteriors [6.4 Planet formation in the HL Tau disk: "The radial pebble flux is calculated as"]
  - parameter: alpha_vert = 1e-4 (also 1e-3 and 1e-5 tested) [6.4 Planet formation in the HL Tau disk: "We assume $\alpha_{\rm vert}=10^{-4}$."]
  - assumption: Smooth gas disk from 13C17O-based profile; dust-to-gas 0.01; rho_m = 1.675 g cm^-3; Q=1.4; M*=2.1 Msun [4.1 Full fitting: "where $\rho_{\rm m}=1.675~{\rm g~cm^{-3}}$ is the dust material density."]
  - validation: Compared to pebble flux estimates in the literature [5.4 Planet formation in the HL Tau disk: "These values are consistent with the pebble fluxes of our organics-rich dust model at $>40$ au where the derived dust properties are not significantly affected by high optical thickness."]
- result: Preferred filling factor with polarization prior = 0.03 to 0.3 ± not stated dimensionless [4.3 Scattering Polarization: "The filling factor is preferred to be in the range $0.03 \lesssim f_{\rm fill} \lesssim 0.3$"]
- result: Maximum dust size beyond 40 au with polarization prior = ~100 ± not stated micron [4.3 Scattering Polarization: "At $r \gtrsim 40$ au, the maximum dust size is likely $\sim100$ ${\rm \mu m}$"]
- result: Radial pebble flux beyond 40 au (porous organics-rich) = up to 1e3 ± not stated M_earth/Myr [6.4 Planet formation in the HL Tau disk: "where it can be as high as $10^{3}M_{\oplus}~{\rm Myr^{-1}}$"]
- limitation (authors): Preference for amorphous-carbon-rich dust within 40 au arises partly from priors and high optical depth, not conclusive [4.1 Full fitting: "the preference for amorphous-carbon-rich dust arises from prior selection rather than intrinsic composition."]
- limitation (authors): Filling factor assumed constant across the size distribution; smooth gas disk assumed [5.2 Dust porosity in the HL Tau disk: "Although this study assumes that the filling factor is constant across the dust size distribution, filling factor may, in reality, depend on dust size."]
- not stated (card): CASA version and pipeline version; Imaging details: cell size, image size, deconvolver, masking, niter/threshold; Azimuthal averaging details: deprojection geometry (inclination, PA), radial bin width, radial range fitted; Exact reprocessing steps for the 0.45, 0.87, 1.3 and 7.9 mm images; Dust material density and optical constants details per material (partly cited only); Details of the pebble …

### 2019MNRAS.489..470G: ALMA Band 3 polarimetric follow-up of a complete sample of faint PACO sources (2019; agn_and_quasars; observational_alma_primary)
- question: What are the total intensity and linear polarization properties at 97.5 GHz of a complete sample of 32 faint PACO radio sources, and how do they extend the spectra, polarization fractions, RMs and polarized source counts to mm wavelengths?
- step 1: Extract Stokes I, Q, U flux densities
  - method: 2D Gaussian fit of naturally weighted maps; central peak if Q/U fit fails [3 Data reduction: "Whenever the fit fails because the source is too faint to be detected in Stokes $Q$ and $U$, we consider the central peak in the image."]
  - software: CASA
  - assumption: Sources point-like; no Stokes V debiasing [3 Data reduction: "Since almost all the objects are point-like"]
- step 2: Derive P, polarization angle and fraction
  - method: P = sqrt(Q^2+U^2), Pi = 100 P/I, 3 sigma detection limit [3 Data reduction: "the linearly polarized emission, $P$, can be safely estimated from the Stokes parameters $Q$ and $U$ only"]
  - assumption: Debiasing term lowers P by ~0.01%, negligible [3 Data reduction: "the debiasing term $\sigma_V$ lowers the estimated value of the polarized flux density by $\sim 0.01\%$"]
- step 3: Polarization fraction distribution
  - method: Bootstrap with 1000 resamplings, Gaussian per detection, uniform for upper limits, log-normal fit [4.2 Linear polarization fraction: "Then, we generated $1000$ simulated data sets by resampling with repetitions the distributions of percentage polarization fractions of each source."]
  - fitting: log-normal with A=0.86, mu=2.05, sigma=0.97 [4.2 Linear polarization fraction: "with $A=0.86$, $\mu=2.05$ and $\sigma=0.97$."]
- step 5: Polarized source counts at 95 GHz
  - method: Convolve C2Ex total intensity counts with log-normal polarization fraction distribution [5 Source Counts: "We started from the C2Ex model for total intensity source counts, $n(S)$, by (cite: Tucci2011) and used the approach of (cite: Tucci2012)"]
  - assumption: Same distribution applied to all sub-populations [5 Source Counts: "the distribution of eq. ([\[eq:lognorm\]](#eq:lognorm)) was applied to all sub-populations"]
  - validation: Compared with Tucci2012 and D05-based predictions [5 Source Counts: "there is a very remarkable agreement between our current data and the model predictions by (cite: Tucci2012)"]
- result: Polarization detection rate at 3 sigma = 97 ± not stated percent [2 ALMA Observations: "3\,\sigma$ detection rate of $97\%$ (only one non-detection)"]
- result: Median polarization fraction at 97.5 GHz = 2.2 ± 0.6 percent [4.2 Linear polarization fraction: "The median polarization fraction measured by ALMA for the full sample is $2.2\pm 0.6\%$"]
- result: Log-normal parameters of polarization fraction distribution = A=0.86, mu=2.05, sigma=0.97 ± not stated dimensionless [4.2 Linear polarization fraction: "with $A=0.86$, $\mu=2.05$ and $\sigma=0.97$."]
- limitation (authors): ALMA and ATCA not simultaneous so no joint fit; small sample prevents firm conclusions [4.1 Spectral behaviour: "Therefore we have not attempted a joint fit of ALMA and ATCA data"]
- limitation (authors): Stokes V unreliable in Cycle 3 [3 Data reduction: "Stokes V images obtained were not reliable"]
- not stated (card): Number/size of Stokes images and cell size; Whether tclean/clean parameters, niter, thresholds, masks were used; Exact way polarization leakage and angle calibration were solved (CASA tasks); Spectral windows combined for the Gaussian fits and per-sub-band fitting procedure; How redshifts were assigned and the Galactic RM values used; Total intensity source count error computation details and C2E…

### 2020ApJ...893...54Y: Transition from Ordered Pinched to Warped Magnetic Field on a 100 au Scale in the Class 0 Protostar B335 (2020; star_formation; observational_alma_primary)
- question: How does the magnetic field structure in the Class 0 protostar B335 behave on a 100 au scale, and is it consistent with MHD simulations with aligned or misaligned magnetic field and rotational axis?
- step 1: Image Stokes IQU and build polarization maps
  - method: Briggs-weighted tclean imaging of calibrated, phase-self-calibrated data; debiased polarized intensity [Observations: "we debiased the polarized intensity ($I_{\rm p}$) with $I_{\rm p} = \sqrt{Q^2 + U^2 - {\sigma_{Q,U}}^2}$"]
  - software: CASA
  - parameter: robust = +0.5 [Observations: "with a robust parameter of +0.5"]
- step 2: Extract polarization detections
  - method: Bin to 0.1'' pixels; keep detections with Stokes I and Ip S/N > 3 [Observations: "The polarization detections are extracted when the signal-to-noise ratios (S/N) of both Stokes *I* and $I_{\rm p}$ are larger than three"]
  - software: CASA
  - parameter: pixel 0.1'', S/N>3, orientation uncertainty <~9 deg [Observations: "the expected uncertainties in the polarization orientations are $\lesssim$9$^\circ$"]
- step 3: Compare 0.87 and 1.3 mm polarization
  - method: Convolve to 1.3 mm beam, extract with same criteria, compare orientations and percentages at same positions [Results: "Then we compared the polarization orientations and percentages at 0.87 mm and 1.3 mm at the same positions."]
  - software: CASA
  - assumption: Polarization orientations rotated by 90 deg to infer B-field if emission from aligned grains and optically thin [Origins of the polarized continuum emis…: "the magnetic field structures in B335 can be inferred by rotating the observed polarization orientations by 90$^\circ$"]
  - validation: Optical depth check via peak brightness temperature 30 K vs dust temperature 67 K [Results: "The peak brightness temperature is measured to be 30 K"]
- step 4: Simulate aligned and misaligned collapsing cores and compare with observations
  - method: Non-ideal MHD simulations, SPARX radiative transfer with constant polarization efficiency, CASA simulator; compare B-field orientations in central 100 au [Simulation with the aligned magnetic fi…: "on the assumption of a constant polarization efficiency meaning that the polarized intensity is simply proportional to the column density"]
  - software: SPARX, CASA
  - parameter: misalignment 15 deg; cosmic-ray ionization 1e-16 s^-1 (misaligned) vs 5e-17 (aligned); stop at 0.1 Msun [Simulation with the misaligned magnetic…: "the cosmic-ray ionization rate was increased to be $1\times10^{-16}$ s$^{-1}$"]
  - assumption: Barotropic approximation [Comparison between the aligned and misa…: "Our simulations were performed with the barotropic approximation"]
  - validation: Histogram of angle differences; fraction of model segments within 30 deg of observations [Comparison between the aligned and misa…: "The number of the model segments with their orientations consistent with the observations within 30$\ensuremath{^\circ}$ increases by 50%"]
- result: Beam = 0.19 x 0.17 ± not stated arcsec [Observations: "The achieved synthesized beam is $0.19\ensuremath{''} \times 0.17\ensuremath{''}$."]
- result: Peak brightness temperature = 30 ± not stated K [Results: "The peak brightness temperature is measured to be 30 K"]
- result: Mean difference in B-field orientation between 0.87 and 1.3 mm = 5 ± std 4 deg [Results: "The mean difference in the orientations at the two wavelengths is 5$\ensuremath{^\circ}$ with a standard deviation of 4$\ensuremath{^\circ}$."]
- result: Polarization percentage ratio 1.3 mm / 0.87 mm = 1.7 ± not stated dimensionless [Results: "On average, the polarization percentages at 1.3 mm are a factor of 1.7 higher."]
- result: Increase in model segments within 30 deg of observations with misalignment = 50 ± not stated percent [Comparison between the aligned and misa…: "The number of the model segments with their orientations consistent with the observations within 30$\ensuremath{^\circ}$ increases by 50%"]
- limitation (authors): Simulations are axisymmetric, barotropic, with constant polarization efficiency; they do not reproduce N-S asymmetry or the intensity morphology; the misaligned run used a different cosmic-ray rate [Comparison between the aligned and misa…: "This change in the intensity distribution is not fully consistent with the observations."]
- not stated (card): Clean thresholds, masks, niter, image size for tclean; Self-calibration solution intervals and number of iterations; Which executions used which calibrators and flux scale uncertainty; Details of the 1.3 mm archival data (project codes, beam); Simulation code name, resolution and numerical setup of the MHD runs; SPARX and CASA simulator parameters for synthetic observations; Exact method of compu…

### 2024ApJ...975..103P: The Faraday Rotation Measure of the M87 Jet at 3.5 mm with ALMA (2024; agn_and_quasars; observational_alma_primary)
- question: What is the Faraday rotation measure of the M87 core and jet at 3.5 mm, and what does it imply about the origin of the Faraday screen and the magnetic field structure of the jet?
- step 1: Calibrate data including polarization
  - method: Standard CASA calibration plus polarization calibration: gaincal XYf+QU on 3C279, polcal for D-terms [2 Observation and data reduction: "Finally, we solved for the instrumental polarization determining the leakage terms (or D-terms) for all antennas with the task `polcal`."]
  - software: CASA
  - validation: Calibrator checks show on- and off-axis leakage below 6 mJy/beam [2 Observation and data reduction: "both on-axis ($\rm \leq 20\ensuremath{''}$) and off-axis ($\rm 20\sim 60\ensuremath{''}$) polarization leakages are below the threshold of our polarization analysis"]
- step 2: Image Stokes I,Q,U,V and make polarization images
  - method: tclean per subband; immath POLI for polarized intensity, POLA for EVPA [2 Observation and data reduction: "To obtain the image of linear polarized intensity, the CASA task `IMMATH` was used with the `POLI` mode."]
  - software: CASA
  - parameter: nterms=2, cell 0.2", robust=1 [2 Observation and data reduction: "we set `NTERMS=2`, `CELL= 0.2`$\ensuremath{''}$, and a Briggs weighting with `Robust=1`"]
- step 3: Measure core and knot polarization properties
  - method: IMFIT with elliptical Gaussians; EVPA errors propagated plus systematics [2 Observation and data reduction: "We used the `IMFIT` task to measure the polarized properties of the M87 core and the jet knots assuming elliptical Gaussian components."]
  - software: CASA
- step 4: Derive RM image
  - method: Match SPW resolutions by taper/restoring beam, then RMFIT on the four SPW images with polarized threshold 6 mJy/beam (3 sigma); linear fit of EVPA vs lambda^2 [2 Observation and data reduction: "we applied the `RMFIT` task to the individual SPW images to make a Faraday RM image and the associated error map with a polarized threshold of $\rm 6\ mJy\ beam^{-1}$"]
  - software: CASA
  - parameter: polarized threshold 6 mJy/beam (3 x rms); no systematics in RMFIT [2 Observation and data reduction: "No systematic errors were included in `RMFIT`."]
  - assumption: Single screen, chi = chi0 + RM lambda^2, same opacity at all wavelengths; linear fit due to limited frequency coverage [1 Introduction: "We can derive the RM by measuring the observed EVPA of the target at multiple wavelengths assuming that the opacity is the same at these wavelengths."]
  - fitting: Linear fit of EVPA vs lambda^2 [3 Results: "we adopted a linear fitting to estimate the RM for both the core and the sampled position in the jet knots"]
  - validation: RM errors in core radially symmetric; core shift negligible [3 Results: "because the distribution of RM errors in the core is radially symmetric"]
- result: Core RM at centroid = 4.5e4 ± 0.4e4 rad m^-2 [abstract: "the rotation measure (RM) of the M87 core is $\rm (4.5\pm 0.4)\times10^{4}\ rad\ m^{-2}$"]
- result: Core fractional polarization = 0.88 ± 0.08 % [3 Results: "The lowest fractional polarization is found in the core at a level of only $\rm (0.88\pm 0.08)\%$."]
- result: Average core RM within 1" radius = 4.9e4 ± 0.9e4 rad m^-2 [3 Results: "is $\rm (4.9\pm0.9)\times10^{4}\ rad\ m^{-2}$"]
- result: RM at knot B centroid = -0.03e4 ± 0.07e4 rad m^-2 [3 Results: "$(-0.03\pm 0.07)\times10^4\rm~rad\ m^{-2}$ at the centroid of knot B"]
- result: Peak polarized flux density at knot B = 36.7 ± 1.8 mJy/beam [3 Results: "with a peak flux density of $\rm 36.7\pm1.8 \ mJy\ beam^{-1}$"]
- result: Stokes I core peak = 1.407 ± 0.006 Jy/beam [3 Results: "a peak brightness of $\rm 1.407\pm0.006 \ Jy\ beam^{-1}$"]
- limitation (authors): 1.3 mm and 3.5 mm emission may not arise from same location; limited resolution hinders HST-1 vs inner jet attribution [4.1 Faraday rotation measure at the core: "We caution that the 1.3 mm and 3.5 mm emissions may not arise from the same location"]
- not stated (card): tclean niter, threshold, image size, spw/channel setup; Which phased-array/ALMA products were used and how phasing affected calibration; Details of the orthogonal distance regression (data points, weighting); Exact RMFIT settings (e.g. n pi ambiguity handling); Distance to M87 / physical scale conversion

### 2021ApJ...908..141H: ALMA CN Zeeman Observations of AS 209: Limits on Magnetic Field Strength and Magnetically Driven Accretion Rate (2021; protoplanetary_disks; observational_alma_primary)
- question: Can CN 2-1 Zeeman splitting observations of AS 209 constrain the line-of-sight magnetic field strength (toroidal and vertical) and the magnetically driven accretion rate?
- step 1: Image Stokes I,Q,U,V cubes and continuum
  - method: Briggs-weighted cleaning with robust 0.5; continuum subtraction; 0.25 km/s channels; phase-only self-cal on continuum I [Observations: "The data were cleaned using Briggs weighting with a robust parameter of 0.5 to create image cubes and continuum images for all four Stokes parameters."]
  - software: CASA
  - parameter: robust = 0.5; 0.25 km/s channels [Observations: "The image cubes were created with a spectral resolution of 0.25 km/s."]
- step 2: Correct for Keplerian rotation
  - method: Shift velocities in Stokes I and V cubes by expected Keplerian velocity per pixel to common centroid [Line circular polarization: "we used the package `gofish` (cite: 2019JOSS....4.1632T) to shift the velocities in the Stokes $I$ and Stokes $V$ cubes by the amounts appropriate to correct for Keplerian motion."]
  - software: gofish
  - assumption: Inclination, position angle, distance, stellar mass fixed (i=35.3 deg, 126 pc, 1.25 Msun) [Line circular polarization: "Based on the disk’s inclination angle, position angle, distance, and stellar mass, `gofish` calculates the expected Keplerian velocity for each pixel in the image cube."]
- step 3: Fit Stokes V profiles for B_LOS (red and blue sides)
  - method: Fit V_j = C1 I_j + C2 dI_j/dnu + 0.5 B Z_j dI_j/dnu to unblended line portions of the Kepler-corrected red and blue side spectra [Line circular polarization: "This technique fits the observed Stokes $V$ profile of each hyperfine component to the expression"]
  - software: gofish
  - parameter: Only low-frequency part of line 5 and high-frequency part of line 7 used because of blending [Line circular polarization: "We therefore used only the lower-frequency portion of the Kepler-corrected line 5 data and the higher-frequency portion of the Kepler-corrected line 7 data"]
  - assumption: Fit uncertainties taken as 1 sigma; 3 sigma used for upper limits [Discussion: "we have calculated 3-$\sigma$ upper limits on the net toroidal and vertical magnetic field strengths."]
  - fitting: Least-squares-type fit; per-channel rms from region outside disk as uncertainties [Line circular polarization: "we calculated the per-channel rms in a region outside the disk from spectral line cubes whose velocities had been Kepler-corrected in `gofish`."]
  - validation: Cross-check with stacking of red and mirrored blue unblended lines (no detection) [Line circular polarization: "stacking the lines in this way did not lead to a detection of circularly polarized emission."]
- result: Continuum Stokes I total flux = 215.0 ± 1.8 mJy [Results: "the disk has a peak flux of 127.4 mJy/beam and a total intensity of 215.0 $\pm$ 1.8 mJy."]
- result: Integrated CN intensity lines 5-7 = 3.874 ± 0.015 Jy km/s [Results: "is 3.874 $\pm$ 0.015 Jy km/s"]
- result: B_LOS limit, redshifted side = 5.0 ± not stated mG [Line circular polarization: "the limit on the net line-of-sight magnetic field strength is 5.0 mG on the redshifted side of the disk and 4.2 mG on the blueshifted side"]
- result: B_LOS limit, blueshifted side = 4.2 ± not stated mG [Line circular polarization: "the limit on the net line-of-sight magnetic field strength is 5.0 mG on the redshifted side of the disk and 4.2 mG on the blueshifted side"]
- limitation (authors): Stacking destroys signal from a vertical field; lines 5-7 remain blended [Line circular polarization: "this method of stacking would destroy any Stokes $V$ signal from a vertical magnetic field"]
- not stated (card): Line-free channels for continuum subtraction; Image size, cell size, masks, clean threshold; Details of initial calibration/pipeline version and flux calibrator; Disk position angle and centre used in gofish Kepler correction; Regions/radii used for averaging and for rms estimation; Details of the mass accretion rate derivation and disk model (discussion text is truncated); Line weights w_I and w…

### 2025A&A...695A.149K: Physical conditions around high-mass young star-forming objects via simultaneous observations of excited OH and methanol masers (2025; star_formation, astrochemistry, milky_way_ism; multi_facility_alma_minor)
- question: What physical conditions (temperature, density, magnetic field) around high-mass young stellar objects can be derived from simultaneous e-MERLIN imaging of 6.035 GHz excited OH and 6.668 GHz methanol masers?
- step 1: calibrate and image e-MERLIN cubes
  - method: eMCP pipeline for wide band; CASA narrow-band calibration, self-cal on bright channel, full-polarization cubes [Observations, data reduction, and metho…: "We applied the solutions to all narrow channels and made spectral image cubes for each target (in full polarization, for ex-OH)."]
  - software: CASA, eMCP
  - parameter: robust 0.5, restoring beam 65x45 mas PA -50 [Observations, data reduction, and metho…: "we used an intermediate weighting (robust 0.5) and a standard restoring beam of 65 mas$\times$45 mas at a PA of $-$50$^\circ$"]
  - assumption: 3C84 unpolarized for leakage; 3C286 PA 33 deg [Observations, data reduction, and metho…: "using 3C84, assumed to be unpolarized"]
- step 2: measure maser spots
  - method: 2D Gaussian fits in Stokes I, then Q, U, LHCP, RHCP at same positions; keep spots >2 sigma in at least two consecutive channels [Observations, data reduction, and metho…: "we took only those spots with a total intensity above 2$\sigma$ that appear in at least two consecutive channels"]
  - software: AIPS JMFIT
  - fitting: 2D Gaussian components [Observations, data reduction, and metho…: "We used the JMFIT procedure in AIPS (cite: greisen2003) to fit 2D Gaussian components"]
  - validation: astrometric error budget delta_tot [Observations, data reduction, and metho…: "The total astrometric accuracy is $\delta_{\mathrm{tot}}=(\delta_1^2+\delta_2^2+\delta_3^2+\delta_4^2)^{0.5}$."]
- step 4: derive magnetic field and polarization
  - method: Gaussian fits to RHCP/LHCP spectra give Zeeman splitting, B_los from 0.056 km/s/mG; m_l, m_c, chi_l from Stokes [Results: "Using the formula $\Delta V_{\mathrm{Z}}/B=$0.056 from (cite: baudry1997), we calculated the magnetic field along the line of sight"]
  - assumption: field perpendicular to linear polarization vector for sigma components [Results: "The orientation of the magnetic field, $\Phi_{\mathrm{B}}$, is perpendicular to the linear polarization vector for $\sigma$ components."]
  - fitting: Gaussian profile fits [Results: "the parameters of the fit Gaussian profile to the spectrum; the peak amplitude ($S_{\mathrm {fit}}$), the full width at half maximum of the profile ($FWHM_{\mathrm {fit}}$), and the peak velocity ($V_{\mathrm {fit}}$)"]
- result: Line-of-sight magnetic field range = 0.2 to 10.6 ± not stated mG [4.3.1 Zeeman pairs: "The calculated magnetic field along the line of sight is from 0.2 mG up to 10.6 mG, with mean and median values of 4.8 mG and 5.2 mG, respectively."]
- result: Number of Zeeman pairs = 37 in eight sources ± not stated count [4.3.1 Zeeman pairs: "In total, we have identified 37 Zeeman pairs in eight HMYSOs"]
- result: Zeeman triplet candidates = 8 (21%) ± not stated count [4.3.3 Zeeman triplets: "we find that in eight cases (21%)"]
- result: Gas density from B_los = 0.1 to 378e6 ± not stated cm^-3 [4.3.1 Zeeman pairs: "derived gas densities ($n_\mathrm{H_2}$) in the range from 0.1 to 378$\times$10$^6$ cm$^{-3}$"]
- limitation (authors): Better angular and spectral resolution needed to confirm Zeeman triplets [4.3.3 Zeeman triplets: "However, better angular and spectral resolution is needed to confirm that."]
- limitation (authors): CH3CN optically thick, so temperatures overestimated [Methyl cyanide: "all of our estimated temperatures are overestimated, and our column densities are underestimated"]
- not stated (card): ALMA calibration/imaging details (pipeline version, beam, cube setup) for the archival Band 6 data; Which ALMA project covers which source and lines; Aperture/ellipse definitions for CH3CN spectra per source; Outflow position angle determination from ALMA data; Procedure for gas density from Bayandina et al. (2014); Spot-selection thresholds beyond 2 sigma in two channels and KS test details

### 2015ApJ...812...27A: ALMA Observations of the Transition from Infall Motion to Keplerian Rotation around the Late-phase Protostar TMC-1A (2015; star_formation, protoplanetary_disks; observational_alma_primary)
- question: How does infall motion in the envelope of the Class I protostar TMC-1A transition to Keplerian rotation in the disk, and what does this imply for Keplerian disk formation?
- step 5: Estimate magnetic field required for slow infall
  - method: Order-of-magnitude radial equation of motion with magnetic pressure and tension at 200 AU [5.3 Magnetic Pressure and Tension: "The magnetic flux density required to make the infall velocity as small as $0.3 V_{\rm ff}$ is estimated from the equation of motion"]
  - assumption: R_curv ~ scale height H; B ∝ rho^(2/3); steady state; gas pressure ignored [5.3 Magnetic Pressure and Tension: "We also assume $B\propto \rho ^{2/3}$"]
  - validation: same estimate at 100 and 300 AU gives similar results [5.3 Magnetic Pressure and Tension: "The same estimations are also done at radii of 100 AU and 300 AU, providing results similar to that at 200 AU."]
- result: Magnetic field for slow infall = ~2 ± not stated mG [5.3 Magnetic Pressure and Tension: "the magnetic flux density required for $V_{r}=0.3V_{\rm ff}$ is estimated to be $B\sim 2$ mG"]
- limitation (authors): Inclination poorly constrained by the disk model; mass estimates are uncertain by optical depth, temperature, abundance [4.3 Rotating Disk Models: "it is difficult to give a constraint on the inclination angle in this model fitting"]
- limitation (authors): PV mean-position method underestimates break radius at limited resolution [4.2 Rotation Profile: "may systematically underestimate $R_{b}$ when the spatial resolution is not high enough"]
- not stated (card): MCMC details for disk model fit (sampler, priors, steps, convergence); CASA version and calibration pipeline/script version; CLEAN iterations/threshold, cell and image size; Line-free channel ranges for continuum; Exact flux-correction handling beyond the 0.85 factor; Mask definitions and uncertainty computation for mean positions; Disk code is from Ohashi et al. 2014, not available here; Continu…

### 2018MNRAS.477.4380S: Testing star formation laws in a starburst galaxy at redshift 3 resolved with ALMA (2018; high_z_galaxies, star_formation; archival_reuse)
- question: Do existing star formation laws (KS, KDM12, SFK15) reproduce the SFR surface density of the brightest clump in lensed starburst SDP 81, and what is the role of turbulence?
- step 5: Compare observed SFR with KS, KDM12, SFK15 predictions
  - method: Evaluate relations with MC (100,000 samples) and compare PDFs; reduced chi2 scatter vs local regions [6 Comparison of observed SFR surface de…: "These PDFs were calculated using Monte Carlo simulations with a sample size of 100,000"]
  - parameter: b = 0.4, beta_mag -> infinity, eps_ff = 0.015 [6 Comparison of observed SFR surface de…: "We use a mixed driving mode with $b=0.4$"]
  - assumption: Magnetic fields neglected [6 Comparison of observed SFR surface de…: "we neglect magnetic fields and set $\beta_{\mathrm{mag}}\to \infty$"]
- result: Sigma_SFR KS = 52 ± 17 Msun/yr/kpc^2 [abstract: "$\Sigma_{\mathrm{SFR,KS}} = 52\pm17"]
- result: Sigma_SFR KDM12 = 106 ± 37 Msun/yr/kpc^2 [abstract: "$\Sigma_{\mathrm{SFR,KDM}} = 106\pm37"]
- result: Sigma_SFR SFK15 = 491 ± +139/-194 Msun/yr/kpc^2 [abstract: "$\Sigma_{\mathrm{SFR,SFK}} = 491^{+139"]
- result: Reduced chi2 scatter (KS, KDM12, SFK15) = 50.1, 7.27, 1.25 ± not stated dimensionless [6 Comparison of observed SFR surface de…: "$\chi^2_{\mathrm{red}} = 50.1$ and $7.27$ for the KS and KDM12 relations, respectively"]
- limitation (authors): Dust parameters cannot be simultaneously constrained; clump conditions assumed equal to galaxy-wide [3 Measurement of the Star Formation Rate: "the available ALMA observations are insufficient to simultaneously constrain the dust parameters"]
- limitation (authors): Magnetic fields unavailable and neglected [6 Comparison of observed SFR surface de…: "We do not have any estimates of magnetic field strength in this galaxy"]
- not stated (card): Source-plane reconstructed maps (S15) are not provided; need the lens model and the S15 reconstruction procedure; Clump A pixel mask and the kernel sizes used for background subtraction; Flux values for clump A in each band; Derivation of the Toomre freefall time inputs for KDM12/SFK15 (galaxy-scale parameters); Number of MC iterations for SED fit and the fitting code details; Data used for compa…

### 2019ApJ...878L..26L: ALMA Detection of a Linearly Polarized Reverse Shock in GRB 190114C (2019; transients; observational_alma_primary)
- question: Is the mm-band afterglow of GRB 190114C linearly polarized, and what does its polarization and temporal evolution imply about the reverse shock and jet magnetic field structure?
- step 1: Polarization calibration of ALMA data
  - method: Standard CASA full-polarization calibration using J0423-012 for leakage with ≈90° parallactic angle coverage [2.3.1 ALMA Data analysis: "We used these solutions to estimate the intrinsic Stokes parameters of the polarization calibrator, followed by the cross-hand delays, the XY-phase offset, and the calibrator’s intrinsic polarization."]
  - software: CASA
  - parameter: flux scale from power-law fit to calibrator catalog flux at 91.5 and 103.5 GHz [2.3.1 ALMA Data analysis: "to which we fit a power law model to fix the flux density scale for each channel"]
  - validation: XX/YY gain ratio within ≈2% of unity; D-terms ≈1% [2.3.1 ALMA Data analysis: "The leakage (D-terms) were found to be at the $\approx1\%$ level for individual antennas, as expected for the ALMA 12m array (cite: nnp+16)."]
- step 2: Measure Stokes I light curve and Q, U
  - method: Split source data by scan, imfit in image plane for Stokes I; Q and U measured with position and beam fixed from Stokes I image, per run [2.3.2 Measurement of polarization: "measured by fixing the position and beam parameters using the Stokes $I$ image"]
  - software: CASA imfit
- step 3: Derive P, chi, Pi with debiasing
  - method: Monte Carlo with 10^5 realizations from Q and U measurements, including Stokes I uncertainty for Pi [2.3.2 Measurement of polarization: "We generate $10^5$ random realizations from the individual $Q$ and $U$ measurements and calculate $P=\sqrt{Q^2+U^2}$"]
  - validation: Checked via gain calibrator polarization stability, secondary peaks, separate base-bands, and independent ALMA reduction [2.3.2 Measurement of polarization: "All three sets of images yield results consistent within measurement uncertainty."]
- step 5: Constrain magnetic field coherence angle
  - method: Random-walk of N incoherent patches with N~(Gamma_ej theta_B)^-2; Pi ~ Pi_0 Gamma_ej theta_B [5 Discussion: "The observed polarization is a random walk of $N$ steps in the $QU$ plane, with $\Pi \sim \Pi_0/\sqrt{N} \sim \Pi_0\Gamma_{\rm ej}\theta_B$"]
  - parameter: Gamma_ej ≈15, Pi_0 ~0.6 (beta~0), t_dec ≈ T90 = 116 s [5 Discussion: "Taking $\ensuremath{t_{\rm dec}}\approx T_{90}=116$ s from *Fermi*/GBM[^9]"]
  - assumption: Newtonian RS with g≈3, k=2 [5 Discussion: "For $g\approx3$ and $k=2$, we have"]
- result: Fractional linear polarization, first epoch = 0.87 ± 0.13 % [Table 3: "| 0.114 | 89.5 | 14.6 | 32.0 | 15.3 | 96.3 | 14.6 | 9.8 | 4.6 | 0.87 | 0.13 |"]
- result: Fractional linear polarization, last epoch = 0.60 ± 0.19 % [Table 3: "| 0.202 | 1.84 | 14.5 | -41.1 | 14.6 | 43.7 | 14.0 | -43.7 | 11.7 | 0.60 | 0.19 |"]
- result: Polarization position angle, first to last = 10 to -44 ± ±5 to ±12 deg [abstract: "evolving in polarization position angle from $(10\pm5)^\circ$ to $(-44\pm12)^\circ$"]
- result: Circular polarization limit = <0.3 (statistical); systematic ≈0.6 ± 3 sigma % [2.3.2 Measurement of polarization: "corresponding to a formal $3\sigma$ limit on circular polarization of $\Pi_{\rm V} < 0.3\%$ (statistical only)"]
- result: Magnetic coherence angle theta_B = ≈1e-3 ± ≈15% statistical radian [5 Discussion: "The uncertainty on this estimate from the signal-to-noise of the measurement of $\Pi$ is $\approx15\%$"]
- limitation (authors): Systematic uncertainties from RS dynamics approximations and stochastic random walk; forward-shock parameters degenerate since nu_a not located [5 Discussion: "larger systematic uncertainties arise from the approximations used in the RS dynamics as well as the stochastic nature of the 2D random walk."]
- not stated (card): tclean parameters (weighting, robust, cell, image size, masking) for the Stokes images; CASA version; Whether archive pipeline products or manual calibration were used as the base; Time-binning of scans for the Stokes I light curve; Forward-shock model fitting method and priors; how parameters were chosen; Flagging details; Polarization calibrator solution settings (solints)

### 2018ApJ...865...13T: A Galaxy-scale Fountain of Cold Molecular Gas Pumped by a Black Hole (2018; galaxy_clusters_and_sz, nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: Are the warm ionized and cold molecular gas in the Abell 2597 BCG cospatial and comoving, and does their kinematics reflect inflow, jet-driven outflow and bubble uplift (a galaxy-scale fountain) as predicted by chaotic cold accretion/preci…
- step 2: Make moment maps and two-Gaussian maps
  - method: Masked moments: smooth cube spatially (beam FWHM) and spectrally, mask at 1.5 sigma, compute moments on unsmoothed cube; two-Gaussian fits along lines of sight [2.1 ALMA CO(2-1) Observations: "enabling creation of a three dimensional mask that selects all pixels above a 1.5$\sigma$ flux threshold."]
  - software: makeplots (T. Davis), Python
  - parameter: 1.5 sigma mask threshold [2.1 ALMA CO(2-1) Observations: "selects all pixels above a 1.5$\sigma$ flux threshold"]
  - fitting: Multi-Gaussian chi^2 minimization, adding Gaussians as needed [3.4.2 Cold gas motions induced by the r…: "These fits iteratively fit (and, if necessary, add) Gaussians to the extracted spectra using a simple $\chi^2$ minimization technique."]
- result: FWHM of broad southern-jet component = 342 ± 8 km/s [3.4.2: "FWHM of $342\pm8$ km s($\sigma=145\pm3$ km s)"]
- result: Gas mass in southern-jet region = 6.4e8 ± 0.4e8 Msun [3.4.2: "molecular gas mass of $\left(6.4\pm 0.4\right) \times 10^8$"]
- limitation (authors): X_CO uncertainty may overestimate mass by a factor of a few [3.3: "we may be overestimating the total mass by a factor of a few"]
- limitation (authors): Projection effects: motions in plane of sky unknown [3.4: "unless most gas motions are contained in the plane of the sky"]
- not stated (card): CLEAN cell size, image size, niter/threshold, and masking; Line-free channels used for UVCONTSUB and fit order; Self-calibration solution intervals and number of iterations; Spectral resampling/regridding details for velocity frame; Exact smoothing kernel widths in the masked-moment code beyond FWHM=beam; Polygon aperture definitions for spectra; Flux scale uncertainty; Pipeline vs manual calibra…

### 2019ApJ...885L..10L: Detection of Pulses from the Vela Pulsar at Millimeter Wavelengths with Phased ALMA (2019; stellar_physics, instrumentation; observational_alma_primary)
- question: Can phased ALMA detect, time and search for pulsars at 3 mm, and what are the flux density and polarization of the Vela pulsar at 85-101 GHz?
- step 5: polarisation calibration
  - method: Use 24 GHz profile as polarisation template; fit differential gain and phase [3.3.3 Polarization properties: "we can use the data by (cite: kjlb11) as a polarisation template and perform a system calibration"]
  - assumption: Polarisation similar to that at 24 GHz [3.3.3 Polarization properties: "Assuming that the observed polarisation characteristics are similar to those observed at 24 GHz"]
  - validation: PA consistent with 1.4 GHz after Faraday correction [3.3.3 Polarization properties: "the position angle is perfectly consistent with the 1.4 GHz data (after correcting for Faraday rotation)"]
- result: Linear polarisation degree = ~20 ± not stated % [3.3.3 Polarization properties: "the degree of linear polarisation ($\sim 20\%$) is lower than at 24 GHz"]
- limitation (authors): Systematics associated with phasing cycles in active-phasing scans [4 Discussion: "we noticed significant systematics in the time series which are associated with the phasing cycles."]
- not stated (card): Vela ephemeris used for folding; Folding parameters and number of profile bins; Template profile used for TOA; PRESTO search parameters; Polarisation calibration fitting details; Interferometric imaging settings; Phasing solution details

### 2020ApJ...893...33L: ALMA Polarimetry Measures Magnetically Aligned Dust Grains in the Torus of NGC 1068 (2020; agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: Is the 860 micron polarization in the torus of NGC 1068 from magnetically aligned dust grains, and what does it say about the torus and its magnetic field?
- step 1: Image Stokes I, Q, U
  - method: tclean with natural weighting, continuum from 8 GHz bandwidth [Observations and data Reduction: "The dust continuum and polarization images were estimated using the Common Astronomy Software Applications (cite: mcmullin2007) with the task TCLEAN with a natural weighting parameter."]
  - software: CASA
- step 2: Compute polarization degree and PA
  - method: P = sqrt(Q^2+U^2), PA = 0.5 arctan(U/Q), debiased [Observations and data Reduction: "The degree of polarization was corrected by bias."]
  - software: CASA
  - parameter: minimum detectable polarization 0.1%, systematic 0.03% [Observations and data Reduction: "ALMA provides a systematic uncertainty in linear polarization of 0.03%, which corresponds to a minimum detectible polarization of 0.1%."]
  - validation: vectors shown for P/sigma_P >= 3 [3 Results: "Each polarization vector shows the E-vector with a statistically independent measurement of $P/\sigma_{P} \ge 3$."]
- step 3: Torus profile along the equatorial axis
  - method: Co-add Stokes IQU in bins of 25x83 mas along PA 105 deg within 12x5 pc region, then debias [3.1 The Total and Polarized Flux of the…: "we co-added the Stokes IQU at each location along the equatorial axis within bins of $25$ mas $\times$ $83$ mas ($1.5 \times 4.8$ pc)"]
  - validation: independent aperture measurement at 0.12" east [3.1 The Total and Polarized Flux of the…: "To obtain an independent polarization measurement of the East region of the torus, we estimate the polarization within a $0.07\ensuremath{''} \times 0.06\ensuremath{''}$"]
- step 5: Synthetic polarimetric observations of toroidal B-field
  - method: CLUMPY/HYPERCAT cloud distribution as column density, Stokes equations with toroidal field, convolve with ALMA beam via CASA [4.2 Synthetic observations: "We obtain the synthetic Stokes IQU observations using CASA v5.4"]
  - software: CASA, HYPERCAT, CLUMPY
  - parameter: i=75 deg, theta=110 deg, p0=0.1, full resolution 1.2 mas, 14.4 Mpc [4.1 Model definition: "we adopt a $p_{0} = 0.1$ (cite: FP2000)"]
  - assumption: toroidal field with constant strength B0(r)=const; homogeneous grain alignment; optically thin; extinction curve R_V=5.5 (WD2001) [4.1 Model definition: "We assume a magnetic field distribution with a constant strength as a function of the radial distance to the center, $B_{0}(r) = const.$"]
  - validation: compare synthetic degree and PA profile along PA 105 deg with observations [4.2 Synthetic observations: "we compute the profiles of the Stokes I, degree and polarized flux as a function of the radius at a PA of $105^{\circ}$ using the synthetic observations"]
- step 6: Magnetic field strength and turbulence
  - method: Hildebrand 2009 angular dispersion ratio and modified DCF: B0 ~ sqrt(8 pi rho) sigma_v/alpha [5.3 The magnetic field strength of the …: "$$\begin{equation} B_{o} \simeq \sqrt{8\pi\rho} \frac{\sigma_{v}}{\alpha} \end{equation}$$"]
  - parameter: sigma_v=10 km/s, alpha=5+-2 deg [5.3 The magnetic field strength of the …: "We take a velocity dispersion of $\sigma_{V} = 10$ km s$^{-1}$."]
  - assumption: median volume mass density 1.4e-22 g/cm3 of whole torus (from LR2018) [5.3 The magnetic field strength of the …: "yield a median volume mass density of $(1.4^{+1.43}_{-0.62}) \times 10^{-22}$ g cm$^{-3}$"]
  - validation: compared with B scaled from 0.4 pc via B∝r^-2 (~0.14 mG at 8 pc) [5.3 The magnetic field strength of the …: "we estimate a magnetic field strength at 8 pc of $\sim0.14$ mG, which is in agreement within the uncertainties of our measurements"]
- result: Peak torus polarization (east) = 3.7 ± 0.5 % [3.1 The Total and Polarized Flux of the…: "we measure a statistically significant polarized peak of $3.7\pm0.5$% in three consecutive bins"]
- result: Aperture polarization degree at 0.12" east = 2.2 ± 0.3 % [3.1 The Total and Polarized Flux of the…: "The degree and PA of polarization were measured to be $2.2\pm0.3$% and $19\pm2^{\circ}$, respectively."]
- result: Aperture E-vector PA = 19 ± 2 deg [3.1 The Total and Polarized Flux of the…: "$2.2\pm0.3$% and $19\pm2^{\circ}$"]
- result: Turbulent-to-ordered field ratio = 0.062 ± 0.025 dimensionless [5.3 The magnetic field strength of the …: "$\langle B^{2}_{t}\rangle^{1/2} / B_{o} = 0.062\pm0.025$"]
- result: Large-scale B-field strength (east torus, 3-8 pc) = 0.67 ± +0.94/-0.31 mG [5.3 The magnetic field strength of the …: "We estimate a magnetic field strength of $B = 0.67_{-0.31}^{+0.94}$ mG"]
- result: Model torus constraints = i>65 deg, sigma=33-50 deg, q<<1, Y>=17 ± not stated mixed [4.4 Exploration of torus model paramete…: "the torus 1) is highly inclined, $i>65^{\circ}$, 2) has intermediate angular widths $\sigma = 33-50^{\circ}$"]
- limitation (authors): B-field strength is an upper limit because median density of the whole torus was used; axisymmetric model cannot explain asymmetry [5.3 The magnetic field strength of the …: "Thus, we estimate an upper-limit of the large-scale magnetic field strength in the eastern size of the torus."]
- not stated (card): Number of clean iterations, threshold, masks, and cell/image size in tclean; Polarization calibration and self-calibration procedure and CASA version for data reduction; Continuum channel selection excluding the CN line; Debiasing method for polarization; Parameters of HYPERCAT image generation (not yet published) and the bin position/aperture definitions; Method for calculating the angular dispe…

### 2017A&A...603A..92V: Magnetically aligned dust and SiO maser polarisation in the envelope of the red supergiant VY Canis Majoris (2017; evolved_stars, stellar_physics; archival_reuse)
- question: What do the linear and circular polarization of SiO lines and of the dust continuum from VY CMa reveal about the magnetic field and dust alignment in its envelope?
- step 1: Calibrate and image full-Stokes data
  - method: Standard ALMA calibration plus polarization calibration, self-cal on SiO maser, imaging in Stokes I,Q,U,V [Observations and data reduction: "We then reimaged all the spws at full spectral resolution and both the continuum and lines at full polarization, producing data cubes in Stokes I, Q, U, and V."]
  - software: CASA
  - parameter: line robust 0.5; continuum robust -0.5 [Observations and data reduction: "The continuum was imaged using a robust gridding weighting parameter of $-0.5$"]
  - validation: Monte Carlo test of D-term and X-Y phase errors on Stokes V [Appendix: "we have generated one thousand sets of random D-terms for all the ALMA antennas, together with random X-Y phases for the reference antenna."]
- step 2: Measure continuum fluxes and polarization
  - method: Deconvolve star and clump C; derive fractional polarization and EVPA [Dust continuum: "Deconvolving the two components, we measure a total flux of $36\pm3$ mJy for the star and $94\pm9$ mJy for clump C."]
  - validation: Compared with Band 7/9 convolved to Band 5 beam and spectral index [Dust continuum: "the distribution appears identical when the ALMA Band 7 and Band 9 observations (OG+15) are convolved with the Band 5 beam."]
- step 3: Extract SiO spectra and polarization
  - method: Spectra of Stokes I, linear fraction, EVPA and V at the peak intensity [SiO emission: "Their spectra, in Stokes I, linear polarization fraction, EVPA, and Stokes V, are shown in Figs."]
- step 4: Derive maser magnetic field from circular polarization
  - method: Zeeman: B ≈1.3 Pc cosθ, and fit V = z B cosθ dI/dν [SiO maser polarization: "Our fit shown in Fig. [2](#line1)(right) then yields a magnetic field strength of $B\cos{\theta}\sim2.4$ G."]
  - parameter: maser linewidth ~1 km/s; z≈1500 s^-1 G^-1 [SiO maser polarization: "Here, the proportionality term $z=g\Omega\approx1500$ s$^{-1}$ \[Gauss\]$^{-1}$."]
  - assumption: Zeeman origin of circular polarization; field reversals at Vlsr~15 and 30 km/s [SiO maser polarization: "if one assumes a magnetic field reversal at $V_{\rm lsr}\sim15$ and $30$ km s$^{-1}$"]
  - fitting: V proportional to dI/dν fit [Discussion, SiO maser polarization: "Assuming a general Zeeman splitting origin, the circular polarization spectrum $V$ is expected to be proportional to the derivative of the total intensity $I$, with a proportionality coefficient that depends on the magnetic field strength."]
- step 5: Lower limit of field for grain alignment
  - method: Compare Larmor timescale with gas-dust timescale (Hoang & Lazarian 2009) [Dust polarization of clump C: "For the dust alignment to be efficient, we find $B>13$ mG (or less if clump C is indeed severely depleted in gas)."]
  - parameter: a=0.1 micron, s=0.5, Td=Tg=100 K, n_g≈9e9 cm^-3 [Dust polarization of clump C: "we find $n_g\approx 9\times10^9$ cm$^{-3}$."]
  - assumption: gas-to-dust ratio 100 [Dust polarization of clump C: "assuming a gas-to-dust ratio of $100$"]
- result: Clump C flux at 178 GHz = 94 ± 9 mJy [Dust continuum: "$94\pm9$ mJy for clump C"]
- result: Star flux at 178 GHz = 36 ± 3 mJy [Dust continuum: "we measure a total flux of $36\pm3$ mJy for the star"]
- result: Continuum EVPA = 8 ± 4 deg [Dust continuum: "The average (non-rotated) electric vector position angle (EVPA) is $8\pm4^\circ$ (East of North)"]
- result: Maximum continuum fractional polarization = ~3 ± not stated % [Dust continuum: "The maximum fractional polarization is $\sim3\%$."]
- result: Max linear polarization 29SiO v=1 = 28.6 ± not stated % [Table 2: "| 170.328$^{b}$ | $J=4-3, v=1$ | 1779 | $2.484\times | 7.4 | 28.6 | 0.9 |"]
- result: Magnetic field from circular polarization, B/cosθ = 0.85 ± not stated G [SiO maser polarization: "We thus find $B/\cos{\theta} \approx 0.85$ G."]
- result: B cosθ from dI/dν fit = ~2.4 ± not stated G [SiO maser polarization: "$B\cos{\theta}\sim2.4$ G"]
- result: Minimum field for dust alignment in clump C = >13 ± not stated mG [Dust polarization of clump C: "we find $B>13$ mG"]
- result: Clump C dust mass = >1.2e-3 ± not stated Msun [Conclusions: "the estimated clump C dust mass is $>1.2\times10^{-3}$ M$_\odot$"]
- limitation (authors): Higher resolution needed to map field structure [Magnetic field morphology: "it is not possible to produce a more detailed map of the magnetic field with the current data."]
- not stated (card): Exact CASA tasks and parameters for imaging (cell size, image size, masks, deconvolver, niter); Line-free channel ranges for continuum; Reference antenna and self-calibration solution intervals; Method of two-component deconvolution for clump C and star fluxes; Aperture used for the extended SiO v=0 spectra; Debiasing of polarized intensity and thresholds

### 2020ApJ...895...64L: Radio Linear Polarization of GRB Afterglows: Instrumental Systematics in ALMA Observations of GRB 171205A (2020; transients; archival_reuse)
- question: Is the linear polarization of the GRB 171205A radio afterglow claimed by Urata et al. detected, or is it an ALMA instrumental systematic?
- step 1: Regenerate QA2 data and test stability
  - method: Run archive calibration scripts, image Stokes IQUV, fit point source with imfit, split by sideband and by SB execution [2.1 QA2 calibration: "we used the CASA (cite: mws+07) calibration scripts, associated with the data set and also available from the ALMA archive, to regenerate the calibrated Quality Assurance 2 (QA2) measurement set."]
  - software: CASA, imfit
  - parameter: robust 0.0 [2.1 QA2 calibration: "using a robust parameter of 0.0"]
  - fitting: Point source fit with position fixed to Stokes I [2.1 QA2 calibration: "Fitting for the linearly polarized flux density with the position fixed to that derived from the Stokes $I$ image"]
  - validation: Compared Q,U with Urata et al.; sidebands differ by 32 uJy in Q [2.1 QA2 calibration: "we find that the Stokes $Q$ measurements differ between the two sidebands by $32~\mu$Jy"]
- step 2: Independent polarization calibration
  - method: Tsys/wvr, bandpass, qufromgain, XYf+QU in gaincal, xyamb, polcal for D-terms, repeated with two reference antennas [2.2 Detailed data analysis: "We use DV06 as reference antenna, and validate our calibration by repeating the entire analysis separately using a nearby antenna with a different architecture, DA64."]
  - software: CASA, qufromgain, xyamb, gaincal, polcal
  - parameter: cross-hand delays from scan 61 on polarization calibrator [2.2 Detailed data analysis: "we use scan 61 on the polarization calibrator as the scan with the strongest polarization signal"]
  - assumption: Stokes V of polarization calibrator negligible [2.4 Polarization measurements: "Standard polarization calibration assumes negligible $V$ in the polarization calibrator."]
  - validation: Residual polarization of calibrator ≈0.1% [2.2 Detailed data analysis: "the final residual polarization, determined by running `qufromgain` on the calibrated calibrator data, is $\approx0.1\%$"]
- step 4: Quantify systematic uncertainty and upper limit
  - method: Use gain calibrator polarization variation across SB executions; range of three Gaussian draws gives 1σ systematic, combined with statistical error; Rician bias [2.5 Systematic calibration uncertainty: "Thus, we estimate an additional $1\sigma$ systematic calibration uncertainty of $\approx0.16\%/1.69\approx0.09\%$ for these observations."]
  - assumption: Gain calibrator intrinsic polarization constant over observations; systematic is Gaussian [2.5 Systematic calibration uncertainty: "assume that the calibrator’s intrinsic polarization is constant with time over our observations"]
- step 5: Interpret limit with jet magnetic field models
  - method: Compare with Granot & Taylor 2005 toroidal models and patch-coherence estimate [4.2 Constraints on magnetic field geome…: "The low degree of polarization disfavors models of polarization produced by toroidal magnetic fields in GRB jets."]
  - assumption: β≈-0.43 from Urata et al. [4.2 Constraints on magnetic field geome…: "for $\beta\approx-0.43$ (cite: uth+19)"]
- result: 3σ upper limit on linearly polarized intensity = 97.2 ± not stated uJy [abstract: "We derive a 3$\sigma$ upper limit on the linearly polarized intensity of $P<97.2~\mu$Jy"]
- result: 3σ upper limit on fractional linear polarization = <0.30 ± not stated % [abstract: "$\Pi_{\rm L}<0.30\%$"]
- result: Additional 1σ systematic calibration uncertainty = 0.09 ± not stated % of Stokes I [2.5 Systematic calibration uncertainty: "$\approx0.16\%/1.69\approx0.09\%$"]
- result: Combined-data linear polarized flux (undebiased) = 41.7 ± ±32.4 uJy [2.5 Systematic calibration uncertainty: "This yields a linear polarization measurement of $41.7\pm32.4~\mu$Jy (undebiased)"]
- result: Magnetic patch scale limit = 4e-3 Gamma^-1 ± not stated rad [4.2 Constraints on magnetic field geome…: "$\theta_{\rm B}\lesssim \Pi_{\rm L,lim}\Gamma^{-1}\Pi_{\rm max}^{-1}\approx4\times10^{-3}\Gamma^{-1}$ rad"]
- result: mm spectral index = -0.51 ± ±0.04 dimensionless [4.2 Constraints on magnetic field geome…: "for which we calculate $\beta_{\rm mm}=-0.51\pm0.04$"]
- limitation (authors): Origin of time-varying systematics (e.g. XY phase) not investigated; second-order corrections beyond scope [2.4 Polarization measurements: "investigating this requires second-order calibration corrections, which are beyond the scope of this work."]
- not stated (card): Number of clean iterations, threshold and masks for tclean; Exact flagging selections beyond DV22 and the specific spectral window; Targeted source coordinates; Spectral windows' channelization; Whether the reduction scripts and CASA version for the manual reduction match 5.6.1

### 2016A&A...593A..44L: The 492 GHz emission of Sgr A* constrained by ALMA (2016; milky_way_ism, agn_and_quasars; observational_alma_primary)
- question: Characterize the polarized continuum emission of Sgr A* at ~492 GHz (intensity, polarization position angle, polarization percentage) and compare with lower-frequency observations.
- step 3: Fit polarization percentage and position angle
  - method: Least-squares fit of XX/YY ratio vs parallactic angle with Q/I - delta = P cos(2(Psi - eta - phi)); Evector 0 deg [3 Results: "Evector of ALMA is 0$^{\circ}$ for the frequency band we observed."]
  - parameter: constant polarization PA assumed; Q offset delta fitted [3.1 Continuum data: "From a least square fit to constant polarization position angle"]
  - assumption: Non-variable source; Stokes U not determined (no XY/YX) [4 Discussion: "we are not able to determine Stokes U."]
  - fitting: Least-squares (bootstrap shown in figures); priors not stated [Results, Continuum data: "From a least square fit to constant polarization position angle, the measured XX to YY intensity ratios for Sgr A\* are consistent with the polarization percentage of $\sim$14%$\pm$1.2%"]
  - validation: Checked DA-only, DV-only, DA-DV subsets and with/without PM antennas; consistent across spws [3.1 Continuum data: "We obtained identical measurements from these three subsets."]
- step 4: Gauge spurious polarization using CI line and Titan
  - method: Miriad imdiff to find XX/YY multiplicative factor in CI images over a box region, per scan and per 2.5 km/s channel; compare with continuum ratio and absorption [3.2 Spectral line data: "We used the Miriad task `imdiff` to systematically estimate the multiplicative factor that minimizes the difference between the XX and YY synthesized images of CI"]
  - software: Miriad imdiff
  - parameter: 2.5 km/s velocity channels; CI 12m data tapered at 1.5" [3.2 Spectral line data: "for every 2.5 km s$^{-1}$ wide velocity channels"]
  - assumption: Foreground CI absorber has negligible Tex and identical tau for X and Y [3.2 Spectral line data: "it is safe to assume that $T_{ex}$ is negligible, and the gas optical depth $\tau$ is identical for the orthogonal linear polarizations X and Y."]
  - fitting: Maximum likelihood factor minimizing XX-YY image difference [Results, Spectral line data: "estimate the multiplicative factor that minimizes the difference between the XX and YY synthesized images of CI in a maximum likelihood sense"]
  - validation: Residuals consistent with thermal noise; CI emission XX/YY ~1 away from absorption [3.2 Spectral line data: "we found that $R(\nu, t)$, and its time integration, are consistent with thermal noise."]
- result: Sgr A* polarization percentage (lower limit) = 14 ± 1.2 % [3.1 Continuum data: "consistent with the polarization percentage of $\sim$14%$\pm$1.2% and a position angle of $\sim$158$^{\circ}$$\pm$3$^{\circ}$"]
- result: Sgr A* polarization position angle = 158 ± 3 deg [3.1 Continuum data: "a position angle of $\sim$158$^{\circ}$$\pm$3$^{\circ}$"]
- result: J1744-3116 Stokes I = 252 ± not stated mJy [3.1 Continuum data: "can be fitted to Stokes I = 252 mJy"]
- result: J1744-3116 polarization percentage = 7.9 ± 0.9 % [3.1 Continuum data: "with 7.9%$\pm$0.9% polarization in position angle P.A. = 14.1$^{\circ}$$\pm$4.2$^{\circ}$"]
- result: J1744-3116 polarization PA = 14.1 ± 4.2 deg [3.1 Continuum data: "P.A. = 14.1$^{\circ}$$\pm$4.2$^{\circ}$"]
- result: J1744-3116 normalized Q offset delta = -0.02 ± 0.02 dimensionless [3.1 Continuum data: "$\delta$=$-$0.02$\pm$0.02"]
- result: Peak CI absorption XX/YY ratio near vlsr~20 km/s = ~1.3 ± not stated dimensionless [3.2 Spectral line data: "The local peak value of $F_{XX}^{CI}(\nu)$ / $F_{YY}^{CI}(\nu)$ is $\sim$1.3 (or 0.11 in logarithm)."]
- result: Std of CI XX/YY away from 20 km/s = 0.043 ± not stated dimensionless [3.2 Spectral line data: "is 0.043."]
- result: Titan XX/YY continuum difference = ~3 ± not stated % [3.2 Spectral line data: "The continuum emission from Titan shows a $\sim$3% intensity difference between the XX and the YY correlations."]
- limitation (authors): Absolute flux uncertain (~20%) because Titan scans were largely flagged; single epoch only. [2 Observations and Data Reduction: "The scans on Titan were largely flagged due to interference from spectral lines."]
- not stated (card): Line-free channel ranges used for uvcontsub; Polynomial order of uvcontsub fit; Flagging details; Model flux/shape used in demos for self-calibration; How the bootstrap errors in the XX/YY fits were computed; Image size and cell size; Titan flux model used for flux scaling

### 2016A&A...593A..61M: Dual differential polarimetry. A technique to recover polarimetric information from dual-polarization observations (2016; instrumentation, agn_and_quasars; technical_calibration_or_instrument)
- question: Can polarimetric information of resolved sources be recovered from dual-polarization (XX, YY only) interferometric data using Earth-rotation synthesis of the parallactic angle?
- step 1: Deconvolve Stokes I
  - method: CLEAN deconvolution of full dataset without polarization calibration [Implementation of differential polarime…: "we deconvolved the source structures (applying the CLEAN algorithm) using the complete set of observations"]
  - software: CASA
- step 3: Compute Rpol and fit sinusoid vs parallactic angle
  - method: Compute Rpol per pixel relative to fiducial source element and fit Rpol = pdif cos(2(phi-alpha-psi)) [Extended polarized emission: "we computed $R^\psi_{pol}$ pixel by pixel for each parallactic angle and fit the results at each pixel to the model given in Eq."]
  - assumption: Short baselines so parallactic angle is same for all antennas; for 3C 286, constant gain amplitude ratio and Ceres unpolarized [4 Test with ALMA Science Verification d…: "if we assume that the overall ratio of gain amplitudes in the array does not change significantly throughout the observations"]
  - fitting: least-squares minimization [Case 1. Perfect amplitude calibration: "we can recover the $p$ and $\phi$ distribution by means of a least-squares minimization"]
  - validation: Compared with true model in simulations and CASA Guide for 3C 286 [Extended polarized emission: "demonstrating the reliability of our differential polarization method"]
- result: 3C 286 fractional polarization = 0.189 ± 0.001 dimensionless [4 Test with ALMA Science Verification d…: "Our best-fit fractional polarization is $p = 0.189 \pm 0.001$"]
- result: 3C 286 polarization angle = 37.04 ± 0.12 deg [4 Test with ALMA Science Verification d…: "we obtain a source polarization angle of $\phi = 37.04 \pm 0.12$ deg."]
- result: PKS 1830-211 RM, 10 April 2012 (reanalysis) = 2.0e6 ± 1.0e6 rad/m^2 [Reanalysis of Martí-Vidal et al. (2015): "$(2.0\pm1.0)\times10^6$ rad/m$^2$ and $(3.7\pm0.5)\times10^6$ rad/m$^2$ (observer’s frame)"]
- result: PKS 1830-211 RM, 23 May 2012 (reanalysis) = 3.7e6 ± 0.5e6 rad/m^2 [Reanalysis of Martí-Vidal et al. (2015): "$(2.0\pm1.0)\times10^6$ rad/m$^2$ and $(3.7\pm0.5)\times10^6$ rad/m$^2$ (observer’s frame)"]
- limitation (authors): Differential RM imaging with polarized fiducial element can be biased by up to ~30%. [Bias in the $RM$ differential imaging: "the bias can be as large as $\sim30$%, even with wide fractional bandwidths"]
- not stated (card): CLEAN parameters (niter, threshold, masks) for simulations and 3C 286; Scan/time binning used to define constant parallactic angle; Noise levels in simulations; In-house modified simobserve not available; Details of the fit initial values and uncertainties for the PKS 1830-211 reanalysis; Corrected feed angles and spectral windows/epochs used in reanalysis

### 2014ApJ...783L..13P: Large-scale Asymmetries in the Transitional Disks of SAO 206462 and SR 21 (2014; protoplanetary_disks; observational_alma_primary)
- question: What is the large-scale structure of the dust emission in the transitional disks of SAO 206462 and SR 21, and are the asymmetries consistent with vortex-like features?
- step 4: Derive vortex mass and turbulence
  - method: Convert vortex flux to mass; use vortex aspect ratio and Stokes number to infer turbulent velocity [Discussion: "The vortex aspect ratio derived for SAO 206462 and SR 21 would then require turbulent velocities of about $90\:\textrm{m~s}^{-1}$ and $68\:\textrm{m~s}^{-1}$ respectively"]
  - assumption: T=35 K, gas-to-dust 100, kappa=10 cm^2/g at 450 um for mass [Discussion: "assuming a temperature of $T=35K$, a gas-to-dust ratio of 100, and a dust opacity of $\kappa_{\nu}=10\:\textrm{cm}^{2}\:\textrm{g}^{-1}$ at $450\:\mu$m"]
  - assumption: a=1 mm, rho_s=1 g/cm3, Sigma=10 g/cm2, St~1e-2; gas T=50 K for sound speed [Discussion: "Dust grains with size $a=1$ mm and internal density $\rho_s=1$ g cm$^{-3}$, embedded in a disk with a surface density of $\Sigma=10$ g cm$^{-2}$"]
- result: Vortex mass = ~2 ± not stated M_Jup [Discussion: "The flux density in the asymmetry corresponds to a mass (dust+gas) of $\sim2\:M_{\textrm{Jup}}$ for both SAO 206462 and SR 21"]
- result: Required turbulent velocity = 90 (SAO 206462), 68 (SR 21) ± not stated m/s [Discussion: "turbulent velocities of about $90\:\textrm{m~s}^{-1}$ and $68\:\textrm{m~s}^{-1}$ respectively"]
- limitation (authors): Emission may be partly optically thick so asymmetries may not trace mass; masses are lower limits. [Discussion: "These are lower limits on the vortex mass, given the uncertainty in optical depth at this wavelength."]
- not stated (card): CASA version; Self-calibration solution intervals and reference antenna; Cell size, image size, deconvolver and masking; MCMC walkers, steps, burn-in, priors and parameter bounds; Flux calibrator model for Titan and flux uncertainty; How the moment maps were made (channel range, clip); Continuum channel selection / line-free channels

### 2024Ap&SS.369...18M: Multi-wavelength observation of MAXI J1348─630 during the outburst in 2019 (2024; stellar_physics; observational_alma_primary)
- question: What are the broadband spectral properties of MAXI J1348–630 and its radio/X-ray luminosity correlation during the decay phase of the January 2019 outburst?
- step 1: Calibrate and image ALMA continuum
  - method: Pipeline calibration, flux scaling with setjy, extra flagging, mstransform split, tclean continuum imaging, self-calibration, primary beam correction [2.1 ALMA observation: "After the initial data calibration, we used the task `MSTRANSFORM` to split the corrected target data set with all available rest frequencies."]
  - software: CASA, tclean, gaincal, applycal, impbcor
  - parameter: robust = 0.5, Stokes I [2.1 ALMA observation: "we created the continuum image of MAXI J1348–630 using task `TCLEAN` with Stokes-I and robust parameter 0.5."]
- limitation (authors): Cannot draw conclusions on continuum morphology [3.1 Continuum image of MAXI J1348–630 u…: "So, we cannot draw any conclusions about the continuum morphology of MAXI J1348–630."]
- not stated (card): Image size, cell size, number of clean iterations, threshold and masking; Self-calibration solution intervals, number of rounds, and solution type; Spectral windows used for each band's continuum and line-free channels; Method for the molecular line search and column density upper limits (software, excitation temperature, line width); Band 6 frequency range is misprinted in Table 1; Whether the p…

### 2024A&A...686A.274V: Molecular line polarisation from the circumstellar envelopes of asymptotic giant branch stars (2024; evolved_stars, stellar_physics; observational_alma_primary)
- question: What is the large-scale magnetic field morphology and strength in AGB circumstellar envelopes, as traced by non-maser molecular line polarisation (GK effect and radiative alignment) in CW Leo and R Leo?
- step 1: Calibrate and self-calibrate
  - method: ALMA polarisation calibration scripts after re-normalisation correction; two rounds phase-only self-cal on continuum [2 Observations and data reduction: "Calibration was done using the ALMA polarisation calibration scripts (cite: Nagai16)."]
  - software: CASA 5.7.2
  - parameter: solint 'inf' then 'int' [2 Observations and data reduction: "Two rounds of phase-only self-calibration, (with solution intervals "inf" and "int") were done on the continuum."]
  - validation: Compared before/after re-normalisation spectra; compared flux with ACA and JCMT [2 Observations and data reduction: "A comparison between the results before and after re-normalisation indeed revealed significant differences in the total intensity spectra."]
- step 2: Make Stokes cubes and debiased polarisation maps
  - method: uvcontsub, Briggs robust 0.5 imaging of I,Q,U,V; P_l = sqrt(Q^2+U^2-sigma_P^2) with sigma_P mean of sigma_Q and sigma_U [2 Observations and data reduction: "Finally we produce debiased linear polarisation maps from the Stokes Q and U imaged using $P_l=\sqrt{Q^2+U^2-\sigma^2_P}$."]
  - software: CASA
  - parameter: detection threshold >5 sigma_P [3.1 Polarisation result overview: "We detect significant ($>5\sigma_P$) polarised emission towards the 338 GHz continuum of both CW Leo and R Leo"]
  - validation: Stokes V found dominated by beam effects for extended lines [2 Observations and data reduction: "find that these are, for the extended molecular lines, dominated by ALMA beam effects (cite: Hull20)."]
- step 3: Characterise polarisation morphology and radial profiles
  - method: Histograms of deviation from tangential direction; azimuthally averaged Stokes I, polarised flux and fraction in channel nearest stellar velocity [3.2 CW Leo: "we plot a histogram with the deviation from the tangential direction for all polarisation vectors in Fig. [6](#fig:angdist)(left)"]
  - parameter: V_lsr CW Leo = -26.5 km/s [3.2 CW Leo: "($V_{\rm lsr, CW Leo}=-26.5$ km s$^{-1}$)"]
  - validation: Consistency between neighbouring channels used to argue against missing-flux artefacts [3.2 CW Leo: "All lines show a good correspondence of polarisation structure between neighbouring channels"]
- step 4: Polarised radiative transfer modelling
  - method: PORTAL on converged LIME output with parameterised CSE (density, T, velocity, abundance profiles); compare radiative rates to magnetic precession rate; model radial alignment for CS/H13CN/SiS and dipole/toroidal B for CO of CW Leo, radial … [4 Polarised radiative transfer models: "The modelling of the line polarisation is performed with the PORTAL (POlarised Radiative Transfer Adapted to Lines) code (cite: Lankhaar20)."]
  - software: PORTAL, LIME 1.9.5
  - parameter: CW Leo dipole inclined 45 deg, PA 125 deg [4.2 CW Leo: "we assume it to be inclined at 45$^\circ$"]
  - parameter: turbulent velocity 1 km/s; gas mean particle mass 2.35 AMU [4.1 Circumstellar envelope models: "contained a contribution from a constant turbulent velocity of 1 km s$^{-1}$"]
  - assumption: Spherically symmetric envelope expanding at constant velocity; amorphous carbon opacities (CW Leo), silicate (R Leo); gas-to-dust 300 (CW Leo), 167 (R Leo) [4.1 Circumstellar envelope models: "In the case of C-rich CSEs, such as CW Leo, we adopted the opacities for amorphous carbon type of dust given by (cite: suh00)"]
  - validation: Qualitative comparison of predicted and observed polarisation morphology and fractions [4.3 R Leo: "The predicted polarisation morphology appears to be consistent with the observations."]
- step 5: Magnetic field strength via structure function analysis (CW Leo CO)
  - method: Structure function of CO J=3-2 polarisation angles in central channel, fit with Koch et al. 2010 equation within <~2''; B0 from turbulent-to-ordered ratio and Alfven velocity; correction N from Houde16 [5.3 Structure function: "The structure function can be fit using the equation from (cite: Koch10) within $\lesssim2$$''$"]
  - parameter: delta~300 au, Delta'~500 au, W1~40 au, N~1.2 [5.3 Structure function: "This yields $\delta\sim300$ au and $\Delta'\sim500$ au. The parameter $W_1\approx40$ au is the radius of the interferometric beam."]
  - assumption: Field frozen into gas, isotropic incompressible turbulence from transverse Alfven waves; result a lower limit if not frozen [5.3 Structure function: "the derived field strength should be considered a lower limit."]
  - fitting: structure function fit; ratio 0.061 ± 0.001 [5.3 Structure function: "$\frac{\langle B_t^2\rangle^{1/2}}{B_0} = 0.061\pm0.001$"]
  - validation: Other velocity channels give field within 30% [5.3 Structure function: "yield similar field strengths to within $30\%$"]
- result: Max continuum fractional polarisation CW Leo = 0.88 ± not stated % [3.1 Polarisation result overview: "The maximum fraction of continuum polarisation is $0.88\%$ for CW Leo and $0.17\%$ for R Leo."]
- result: Max continuum fractional polarisation R Leo = 0.17 ± not stated % [3.1 Polarisation result overview: "The maximum fraction of continuum polarisation is $0.88\%$ for CW Leo and $0.17\%$ for R Leo."]
- result: Peak fractional polarisation 12CO J=3-2 CW Leo = 1.18 ± not stated % [Table 1: "| $^{12}$CO $J=3-2$ | 17.89 | 1.18 |"]
- result: Peak fractional polarisation 12CO J=3-2 R Leo = 3.90 ± not stated % [Table 1: "| $^{12}$CO $J=3-2$ | 4.66 | 3.90 |"]
- result: Peak fractional polarisation SiO v=1 J=8-7 R Leo = 32.4 ± not stated % [Table 1: "| SiO $v=1,J=8-7$ | 12.68 | 32.4 |"]
- result: SiO v=1 circular polarisation fraction R Leo = 1.3 ± not stated % [3.3 R Leo: "This corresponds to a circular polarisation percentage of $P_v=1.3\%$."]
- result: Structure function ratio B_t/B0 CW Leo = 0.061 ± 0.001 dimensionless [5.3 Structure function: "$\frac{\langle B_t^2\rangle^{1/2}}{B_0} = 0.061\pm0.001$"]
- result: Plane-of-sky field CW Leo at ~250 au = ~19 ± not stated mG [Conclusions: "reveal a plane-of-the-sky magnetic field of $\sim19$ mG at $R=250$ au"]
- result: B(r) CW Leo, r=50-485 au = 107 x (50/r) ± not stated mG (r in au) [5.3 Structure function: "$B=107\times(50/r)$ mG between $r=50$ and $485$ au"]
- result: Number of turbulent cells N = ~1.2 ± not stated dimensionless [5.3 Structure function: "Hence, we find $N\sim1.2$."]
- result: SiO maser field strength R Leo from circular polarisation = 2-3 ± not stated G [3.3 R Leo: "this corresponds to a magnetic field of $B\sim2-3$ G in the SiO maser region"]
- result: Dust fractional polarisation R Leo / CW Leo (if dust-only) = ~0.6 / 3 ± not stated % [3.1 Polarisation result overview: "this means the dust fractional polarisation is $\sim0.6\%$."]
- limitation (authors): Spatial filtering resolves out much CO flux, overestimating polarisation fractions by factor 2-3. [2 Observations and data reduction: "this can lead to an overestimate of the polarisation fractions with a factor of $2-3$"]
- limitation (authors): Circular polarisation of extended lines dominated by beam effects; no test of anisotropic resonant scattering. [5.2 Anisotropic Resonant Scattering: "we cannot directly investigate anisotropic resonance scattering through a study of the circular polarisation."]
- not stated (card): Exact self-calibration solution interval values and spw/channel selection for continuum; Line-free channels used for uvcontsub and fit order; Image size, cell size, deconvolver, masking and clean threshold; Polarisation calibration script details and leakage solutions; Details of the amplitude re-normalisation correction; PORTAL/LIME setup: grid, number of photons, magnetic field strength used fo…

### 2023Natur.621..483G: Polarized thermal emission from dust in a galaxy at redshift 2.6 (2023; high_z_galaxies; observational_alma_primary)
- question: Is there a large-scale ordered magnetic field in a z=2.6 lensed starburst galaxy, as traced by polarized dust emission?
- step 1: Calibrate and image Stokes IQU
  - method: ALMA pipeline plus polarization calibration; tclean on all Stokes with common beam [Observations and data reduction: "The polarization calibration script derives and applies additional corrections for instrument-related polarization effects"]
  - software: CASA
  - parameter: clean threshold 10 uJy [Observations and data reduction: "Dirty images are cleaned to a stopping threshold of 10 $\mu$Jy"]
- step 2: Measure polarization fraction and B-field angle
  - method: Debiased P from mean Q,U,I for pixels with P/sigma_P>=3; chi_B = 0.5 arctan(U/Q)+pi/2; mean from independent beams [Measuring polarization: "for measurements with a polarized intensity signal to noise ratio $P/\sigma_{P} \ge 3$"]
  - validation: MDP of 0.1 per cent added in quadrature to uncertainties [Observations and data reduction: "all quoted uncertainties in this work have the minimum detectable polarization of 0.1 per cent added in quadrature"]
- step 3: Constrain source-plane B-field orientation via lens simulation
  - method: Lens source-plane Gaussian disk with constant chi_B and P=1%, lensed with SIE+shear, simulated with simobserve, cleaned like data; compare Stokes U detection [Constraining the B-field orientation: "We can constrain the orientation by rotating the *B*-field until the corresponding Stokes $U$ image shows a $3\sigma$ detection in the synthetic polarimetric observations."]
  - software: lenstronomy, CASA simobserve
  - parameter: 801x801 grid, 0.01'' pixel; pwv 0.6 mm; antenna configuration 2 (Cycle 8) [Lens modelling: "Using a grid of $801\times801$ pixels$^{2}$ with a scale of $0.01\mbox{$^{\prime\prime}$}$ pixel$^{-1}$"]
  - assumption: Constant polarization fraction of unity/1% and constant B orientation in source plane; continuum matches CO morphology [Lens modelling: "The *B*-field orientation in the source plane is assumed to be constant, $\chi_{B,{\rm sp}}$, with a constant polarization fraction of unity"]
  - fitting: Grid of chi_B values, no sampler [Methods, Constraining the B-field orien…: "With a polarization fraction of 1% we set a range of constant $\chi_{B,{\rm sp}}$ orientations in the source plane."]
  - validation: Lens and convolution do not rotate or change P; noise adds ~10 deg uncertainty [Constraining the B-field orientation: "We conclude that the lens model and convolution do not produce rotation or change in the polarization fraction from the source plane to the image plane."]
- result: Integrated flux density = 62 ± not stated mJy [main text: "We measure an image plane integrated flux density of $I=62$ mJy"]
- result: Integrated polarization fraction = 0.6 ± 0.1 % [main text: "integrated polarization fraction of $P=0.6\pm 0.1$%"]
- result: Mean polarization fraction = 0.6 ± 0.3 % [main text: "$\langle P \rangle = 0.6\pm0.3$%"]
- result: Source-plane B-field orientation = 5 ± +5/-10 deg east of north [main text: "orientated $\chi_{\rm B} =5^{+5}_{-10}$ degrees east of north"]
- limitation (authors): Lack sensitivity and resolution to map B-field at ~100 pc scales; field strength cannot be reliably estimated from dust polarization [main text: "We currently lack the sensitivity and resolution to map the configuration of the *B*-field strength at scales $\sim$100 pc"]
- not stated (card): Image size and cell size for tclean; Polarization calibration script details and polarization calibrator model; Self-calibration, if any; Pipeline version; Masking used in cleaning; Exact sensitivity-weighted selection of pixels for averages; Total on-source time

### 2020ApJ...899..152H: Mapping Circumstellar Magnetic Fields of Late-type Evolved Stars with the Goldreich-Kylafis Effect: CARMA Observations at λ1.3 mm of R Crt and R Leo (2020; evolved_stars; multi_facility_alma_minor)
- question: Can Goldreich-Kylafis linear polarization of thermal CO J=2-1 be detected with CARMA toward R Crt and R Leo, and is it consistent with G-K model predictions for the circumstellar magnetic field?
- step 1: Calibrate full-Stokes CARMA data
  - method: CADRE parallel-hand calibration, then R-L phase and D-term calibration [Data reduction: "The $\mathtt{MIRIAD}$ task $\mathtt{xyauto}$ solves for the R-L phase corrections for all the 10-m antennas using this method"]
  - software: CADRE, MIRIAD
  - parameter: gpcal with options=qusolve [Data reduction: "The $\mathbf{D}_{m}$ terms were solved for using the $\mathtt{MIRIAD}$ task $\mathtt{gpcal}$ with $\mathtt{options=qusolve}$."]
  - validation: Compared calibrator EVPAs with MOJAVE/VLBA-BU/POLAMI; leakage rank correlation with archival data [Polarization and calibration quality as…: "The resulting 14-day averaged EVPA for 3C279 thus obtained is $42.88^{\circ} \pm 10.83^{\circ}$"]
- step 2: Image and measure polarization
  - method: invert IQUV, debias P with impol, measure peak P, I, m_l, error-weighted EVPA [Data reduction: "The synthesized maps of linearly polarized intensity $P$ were de-biased (cite: wardle_kronberg_74) using $\mathtt{MIRIAD}$ task $\mathtt{impol}$"]
  - software: MIRIAD
- step 4: Predict G-K fractional polarization
  - method: Yang & Lai G-K code with mixed 1-D/2-D LVG geometry, optionally with anisotropic radiation from central star [Observed linear polarization and the G-…: "A mixed LVG velocity gradient geometry (Fig. [8](#fig:COpol_model_LVGs)(iii)) was adopted in the G-K modeling"]
  - software: G-K code of Yang & Lai 2010, LAMDA
  - assumption: Uniform magnetic field and velocity gradient in constant-density slab [G-K modeling: "The model used here considers an uniform magnetic field and uniform velocity gradient through the slab of material with constant thickness and density, as a first-order approximation."]
  - validation: Compared predicted m_l with observed CO polarization [Observed linear polarization and the G-…: "Our G-K model predicts $m_l \sim 3\%$ (Fig. [7](#fig:COpol_model)) which is consistent with our observational result for the CO emission toward R Crt."]
- result: CO J=2-1 peak fractional linear polarization, R Crt = 3.13 ± 7.2 sigma detection % [Table 3: "| R Crt | SiO (J=5-4, v=1) | 12.0 | 0.778 | 4.52 | 17.2 (17.3 $\sigma$) | $-15.4$ |"]
- result: CO J=2-1 peak fractional linear polarization, R Leo = 9.71 ± 6.1 sigma detection % [Table 3: "| R Leo | SiO (J=5-4, v=1) | -4.0 | 18.67 | 53.98 | 34.6 (317 $\sigma$) | $-1.1$ |"]
- result: CO mean EVPA R Crt = 7.6 ± ±1.0 ±10.8 deg [Table 5: "| R Crt | $\phi_{B} = 7.6^{\circ}\pm 1.0^{\circ}\pm 10.8^{\circ}$ | CO $(J=2-1)$ | CARMA | This work | \(a\) |"]
- result: CO mean EVPA R Leo = -77.7 ± ±1.7 ±11.6 deg [Table 5: "| R Leo | $\phi_{B} = -77.7^{\circ}\pm 1.7^{\circ}\pm 11.6^{\circ}$ | CO $(J=2-1)$ | CARMA | This work | \(1\) |"]
- result: SiO maser linear polarization R Crt / R Leo = 17.2 / 34.6 ± not stated % [SiO maser polarization: "We detect linear polarization in the $v=1,\ J=5-4$ SiO maser emission toward R Crt at $m_l \sim 17.2\%$ and R Leo at $m_l\sim 34.6\%$"]
- result: Continuum R Crt LSB = 14.9 ± 2.4 mJy/beam [Results: "We detect continuum emission toward R Crt of $14.9 \pm 2.4$ mJy/beam in the LSB continuum spectral window"]
- result: SiO circular polarization R Leo = 5.7 ± 40.3 sigma % [SiO maser polarization: "We detect peak fractional circular polarization $m_c \sim 5.7\%$ in the $v=1, J=5-4$ SiO maser line toward R Leo"]
- limitation (authors): Observations are sensitivity-limited; interferometric filtering may overestimate m_l [Conclusions: "These observations are profoundly sensitivity-limited compared to modern telescopes such as ALMA"]
- not stated (card): Magnetic field and G-K code input grids (optical depth range, geometry details) not tabulated; Exact Stokes I/P noise values per cube used for masking; Calibrator-specific flagging details; Image size and cell size

### 2018ApJ...858...85P: Forecasting the Contribution of Polarized Extragalactic Radio Sources in CMB Observations (2018; cosmology, agn_and_quasars; multi_facility_alma_minor)
- question: How does the fractional polarization of extragalactic radio sources depend on frequency (1.4-217 GHz), and how much do polarized ERS contaminate CMB B-mode observations of current and forthcoming experiments?
- step 1: derive polarization fraction distributions
  - method: Bootstrap resampling of catalogue fluxes, binned fractions, log-normal fit [Statistical properties of ERS polarizat…: "Finally, a log-normal distribution function [\[eq:lognorm\]](#eq:lognorm) is fitted from each dataset"]
  - parameter: 5 to 15 bins; Poisson errors at 68% confidence [Statistical properties of ERS polarizat…: "ranging from 5 to 15 bins depending on the number of data collected in each catalogue"]
- step 3: forecast ERS contamination for CMB experiments
  - method: Compute number counts and Poissonian power spectra with PS4C, compare with CAMB CMB and rescaled Galactic foregrounds [Forecasts for forthcoming CMB ground-ba…: "we assume their distribution in the sky to be Poissonian"]
  - software: PS4C, CAMB
  - parameter: r=0.05, Planck best fit cosmology [Forecasts for forthcoming CMB ground-ba…: "assuming the *Planck* best fit cosmological parameters (cite: 2016A&A...594A..13P) and a tensor to scalar ratio $r=0.05$"]
  - assumption: Polarization angle uniformly distributed; C_B ≈ C_E ≈ C_U ≈ C_Q [Forecasts for forthcoming CMB ground-ba…: "we can approximate $C_{\ell} ^B\simeq C_{\ell} ^E\simeq C_{\ell} ^U\simeq C_{\ell} ^Q$"]
  - validation: Compared PS4C counts with DZ16 estimates [PS4C with future space missions: "Comparison of surface densities of polarized ERSs brighter than $P_{4 \sigma}$ estimated by (cite: 2016arXiv160907263D)(DZ16) and by PS4C."]
- result: <Pi^2>^1/2 at 95 GHz (PACO-ALMA, flat spectrum) = 4.94 ± 1.32 % [Table bestfitlognorm: "| 95 | 32 | $1.09 \pm 0.21$ | $2.13 \pm 0.23$ | $0.97 \pm 0.09$ | $3.20 \pm 0.60$ | $2.07 \pm 0.24$ | $4.94 \pm 1.32$ | This work |"]
- result: Max polarized sources detected at 3 sigma by CMB-S3 LA (30 GHz) = 2329 ± not stated sources [PS4C with current and forthcoming CMB g…: "the maximum number of polarized sources detected above a $3\sigma$ level and using the large aperture telescope is $2329$"]
- limitation (authors): Planck detections may be biased upward toward high fractional polarization; forecasts limited to ≤150 GHz, excluding dusty galaxies [The Second Planck Catalogue of Compact …: "the statistics of ERS polarization can be biased upward"]
- not stated (card): ALMA 95 GHz data processing, calibration, project code and polarization measurements (deferred to Galluzzi et al. 2018); Number of bootstrap resamplings N_resamp and exact bin choices; Fit method for log-normal and linear fits

### 2015A&A...581A..97S: Collisional modelling of the AU Microscopii debris disc (2015; debris_disks; theory_or_simulation_compared_to_alma)
- question: What dust production, dust transport and planetesimal dynamics in the AU Mic debris disc are consistent with the SED, the ALMA 1.3 mm radial profile and scattered light data?
- step 2: Collisional modelling of outer disc
  - method: ACE simulations varying wind strength, material, e_max, belt width; fit SED vertical scaling by timestep; compare to scaled convolved 1.3 mm profile, scattered light and polarisation [4 Resolved outer disc: "we vary other initial disc parameters of this reference run in order to more tightly constrain the parameters and reveal degeneracies among them"]
  - software: ACE
  - parameter: Belt at 40 au, width 5 au, e_max=0.03, SW50 reference, material M1 [4.1 Stellar wind strength: "having the full width $\Delta r_\mathrm{PB}=5$ au. In all three runs, the maximum eccentricity of the planetesimals was set to $e_\text{max}=0.03$"]
  - assumption: Inclination 89.5 deg; Mie spheres; wind speed 400 km/s; stellar mass 0.5 Msun [4.1 Stellar wind strength: "we assumed a disc inclination of 89.5$^\circ$ from face-on (cite: Krist2005)"]
  - fitting: Not fitted; chi2_SED/N used for comparison only [4.1.1 Impact on thermal emission: "We stress that the models are not fitted to the data through variations of the initial disc parameters."]
  - validation: Compare to SED, ALMA profile, scattered light and polarisation [Resolved outer disc: "First, we seek to explain the available observational data on the resolved outer AU Mic disc, including the SED, the ALMA radial brightness profile, and scattered light measurements."]
- result: Max fraction of central emission from inner dust ring = 60 ± not stated % [7 Conclusions: "emits at most 60% of the observed central emission"]
- limitation (authors): Axisymmetric discs only; models not unique [7 Conclusions: "All the models presented here are not unique as a full exploration of the parameter space by collisional modelling is impossible."]
- not stated (card): CASA version, imaging task and weighting for the re-reduction; Calibration/flagging details and flux calibrator; Number of ACE grid points and size range of the grid; Fitting range and details of SAnD chi2 (error handling); Scaling factors applied to ALMA profile per model

### 2024PSJ.....5..230D: Surface Properties of the Kalliope─Linus System from ALMA and VLA Data (2024; solar_system; observational_alma_primary)
- question: What are the thermophysical and electrical (emissivity, dielectric) surface properties of Kalliope and Linus from mm-cm thermal emission, and what do they imply for metal content and the origin of the system?
- step 1: Image snapshots and self-calibrate
  - method: Group 3-5 scans into snapshots, iterative imaging and self-calibration in CASA, images in Stokes I and P [2.1 ALMA: "An iterative imaging and self-calibration procedure (cite: cornwell1999) was performed on the visibilities in each snapshot"]
  - software: CASA
  - parameter: snapshot duration <5.5 min; pixel 3 mas [2.1 ALMA: "The total duration of each snapshot never exceeded 5.5 minutes"]
- step 7: Polarization test
  - method: Bin polarization pixels by emission angle (40 bins) and compare with Fresnel-based simulated polarization [2.1 ALMA: "binned the results into 40 emission angle bins"]
- result: Polarization upper limit at 1.3 mm = 1 ± not stated % [4.1: "with an upper limit of 1% at 1.3 mm (Figure [4](#fig:polfrac)) and 2% at 9 mm"]
- limitation (authors): High-dielectric region seen only at limb due to incomplete rotational coverage; shape mismatch could mimic it [5.2: "This region of high dielectric constant is only observed when it is at Kalliope’s limb due to our incomplete rotational coverage."]
- limitation (authors): Thermal inertia retrieval requires accurate shape model [3.2.2.3 Shape model: "retrieving an accurate thermal inertia is only possible when a shape model exists that provides a good approximation to the observations"]
- not stated (card): CASA version and pipeline version; Exact tclean parameters (weighting, robust, deconvolver, masking, iterations) for ALMA snapshots; Self-calibration solution interval and reference antenna details; Snapshot grouping scan lists; Thermal inertia-dependent TPM code (Delbo 2015 implementation) not released; Flux scale adjustment details for VLA 3C 138 are personal communication; Radar-derived densit…

### 2020ApJ...891...80M: Properties of M Dwarf Flares at Millimeter Wavelengths (2020; stellar_physics, star_formation; archival_reuse)
- question: What are the properties and likely emission mechanism of millimeter flares from M dwarfs (AU Mic and Proxima Cen) detected by ALMA?
- step 3: Spectral index and linear polarization
  - method: Fit point sources separately to lower and upper sidebands; fit XX and YY separately to get |Q/I|=(XX-YY)/2I [3 Detection of a Millimeter Flare from …: "we fit point source models independently to the millimeter visibilities from the lower (213.5 and 216 GHz spectral windows) and upper (228.5 and 230.5 GHz spectral windows) sidebands."]
  - software: CASA
  - assumption: Stokes U unconstrained so |Q/I| is a lower limit [3 Detection of a Millimeter Flare from …: "We note that $|Q/I|$ is only a lower limit to the true linear polarization fraction"]
  - validation: Compared calibrator results with ALMA calibrator catalogue; quiescent parallactic-angle fit gives instrumental polarization ~1%; XX-YY difference image shows 4σ peak at flare [3 Detection of a Millimeter Flare from …: "At face value, these results suggest that the instrumental contribution to any measured polarization is at the $\sim1\%$ level for these observations."]
- result: AU Mic spectral index (A1) = -1.3 ± 0.4 (peak fit); 0.05 (Table 1) dimensionless [3 Detection of a Millimeter Flare from …: "yielding a spectral index of $\alpha = -1.3\pm0.4$"]
- result: |Q/I| at flare peak = 0.12 ± 0.04 dimensionless [3 Detection of a Millimeter Flare from …: "yields $|Q/I| = 0.12\pm0.04$"]
- result: Quiescent polarization percentage = 0.008 ± 0.004 dimensionless [3 Detection of a Millimeter Flare from …: "The best-fit polarization percentage is $0.008\pm0.004$"]
- not stated (card): Proxima Cen project code and data reduction details; Clean parameters (image size, cell size, niter, threshold); Initial point-source parameters and fit settings for uvmodelfit; Flare-peak time definition and how Gaussian fits were done for t1/2; Flare luminosity/spectral index error propagation; Details of the non-linear least squares polarization fit; How the delta from spectral index is conver…

### 2020A&A...638L..14C: The atomic gas of star-forming galaxies at z ∼ 0.05 as revealed by the Five-hundred-meter Aperture Spherical Radio Telescope (2020; nearby_galaxies; multi_facility_alma_minor)
- question: What is the atomic gas (HI) content and dynamics of four z~0.05 VALES star-forming galaxies observed with FAST, compared with their ALMA CO(1-0) data?
- step 1: Reduce and calibrate FAST ON-OFF spectra
  - method: Noise-diode calibration, inverse-variance weighted mean of ON and OFF spectra, ON-OFF, sinusoid+linear baseline fit, LSR correction, polarisations combined [6 Data reduction: "We subtract the baseline using model-fit based on a sinusoidal plus a linear function"]
  - parameter: 14.86 K/Jy conversion; 10 min chunks; baseline fitted 1372-1376 MHz [6 Data reduction: "The data is reduced in chunks of 10 min."]
  - validation: Compared with ALFALFA spectrum and checked two polarisations [6 Data reduction: "We do not find significant differences in polarisation"]
- result: rms at 1.7 km/s for 5 min ON (GAMA 214184) = 2.61 ± not stated mJy/beam [Table 1: "| HATLASJ083601.5+002617 | 214184 | 5 | 2.61 |"]
- limitation (authors): rms does not decrease as 1/sqrt(t), possibly pointing jitter or weak interference in commissioning [3 Results: "The rms declines with the on-target integration time, but not in the manner of $\propto 1/\sqrt{t}$"]
- not stated (card): ALMA CO(1-0) calibration and imaging details (all from earlier papers); Inclination values and HI radii used per galaxy; H2 mass conversion (alpha_CO) for baryon mass; Baseline fit and RFI flagging details; Distances used for HI mass

### 2020A&A...637A...7M: Detection of deuterated molecules, but not of lithium hydride, in the z = 0.89 absorber toward PKS 1830-211 (2020; astrochemistry, high_z_galaxies; observational_alma_primary)
- question: Are deuterated molecules (ND, NH2D, HDO) and lithium hydride detectable in the z=0.89 absorber toward PKS 1830-211, and what are their abundance ratios?
- step 1: Extract normalized spectra
  - method: Fit two point sources to visibilities with UVMULTIFIT; normalize Stokes I spectra to continuum and average the two executions [2 Observations: "The spectra, extracted from Stokes I data, were then normalized to the continuum level and averaged."]
  - software: CASA, UVMULTIFIT
  - validation: NE image spectra used as monitor to discard Galactic, atmospheric lines or bandpass ripples [2 Observations: "the spectra extracted from the NE image serve as a monitor to control the quality of the spectral bandpass"]
- limitation (authors): Non-simultaneous XD and XH observations and time variability; high uncertainties [Summary and conclusions: "Measurements of deuterium fractionation toward PKS 1830$-$211 could be improved by simultaneous observations of the XD and XH isotopologues"]
- limitation (authors): Assumed covering factor of 1 [3.1: "We further assume that the absorbing gas completely and uniformly covers the background continuum emission from the quasar"]
- not stated (card): Line-free channels and continuum normalization procedure; Gaussian fitting code and fitting/error method; Exact CASA version and bandpass/flux calibrator flux scale; Velocity-resolution/Hanning details per project; Details of the time-variation correction applied to final ratios; Phase center/coordinates of target; Exact RADEX input parameters beyond range

### 2018ApJ...859..165S: Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. I. VLA 1623 (2018; star_formation, protoplanetary_disks; observational_alma_primary)
- question: What are the dust polarization morphologies and mechanisms (scattering, magnetic or radiative grain alignment) in the inner disks and extended ring of the Class 0 system VLA 1623?
- step 2: Image Stokes I, Q, U, V
  - method: clean with primary beam correction; multi-scale interactive for I [2 Observations: "We perform one final, deep iteration of clean and a primary beam correction on each of the four Stokes maps"]
  - software: CASA clean
- step 3: Derive polarization maps
  - method: Debiased polarized intensity sqrt(Q^2+U^2-sigma^2), angle 0.5 atan(U/Q), fraction PI/I [3 Results: "we limit our analysis to only those data with $\mbox{$\mathcal{P}_I$}/\mbox{$\sigma_{\mathcal{P}I}$}>4$"]
  - parameter: P/sigma>4; sigma_PI ~ sigma_Q ~ sigma_U; 0.1% fraction uncertainty [3 Results: "We assume a 1 $\sigma$ polarization fraction uncertainty of 0.1%"]
- step 4: Fit Gaussians to inner disks
  - method: imfit Gaussian fits to Stokes I, deconvolved with beam; no background subtraction [4.1 The Inner Protostellar Disks: "We fit the disks using the *imfit* task in MIRIAD (cite: Sault95)."]
  - software: MIRIAD
  - assumption: inclination from cos i = b/a [4.1 The Inner Protostellar Disks: "assuming $\cos{i} = b/a$ (see Table [1](#disk_prop))"]
  - fitting: imfit; errors from range of deconvolved parameters [Polarization Morphology: The Inner Prot…: "with errors estimated by the largest absolute difference between the best-fit deconvolved parameters and the range of deconvolved parameters when considering the errors in the observed Gaussian fit from *imfit*."]
- step 5: Compare polarization to mechanisms
  - method: Compare e-vector angles to disk minor axes, spectral index (nterms=2) for optical depth, Stokes I gradient vs polarization angle for ring [5.2 Radiation Field Alignment: "Figure [11](#ang_diff) shows these relative angles for the ring only."]
  - software: CASA clean
  - validation: Smoothing ALMA data to CARMA resolution reproduces CARMA position angle [4.3 Comparison to Previous Polarization…: "From our smoothed data, we find a typical position angle of -57, which matches (cite: Hull14)."]
- step 6: Model hourglass magnetic field
  - method: Analytic flux-frozen oblate Plummer spheroid model, matched by eye to ring b-vectors; ring mass from 1.3 mm flux [5.1 Model Results: "We qualitatively match our model by eye to the observations."]
  - software: MIRIAD
  - parameter: A=10, theta=54 deg, nu0=60, r0=40 au, peak density ~6e10 cm-3 [5.1 Model Results: "We also adopt a ratio of peak density to background density of $\nu_0 = 60$"]
  - assumption: T = 20 K, kappa = 0.024 cm2/g at 1.3 mm, d = Ophiuchus distance [5.1 Model Results: "We assume $T = 20$ K and $\kappa = 0.024$ cm$^2$ g$^{-1}$ at 1.3 mm (cite: Andrews09)."]
  - fitting: by eye, no formal fit [Discussion: Model Results: "We qualitatively match our model by eye to the observations."]
  - validation: Good by-eye agreement in NW and SE quadrants; departures in NE and SW [5.1 Model Results: "There are noticeable departures in the north-east and south-west quadrants, however."]
- result: Stokes I flux VLA 1623-A = 141.8 ± 5.9 mJy [Table 1: "| flux (mJy) | $141.8 \pm 5.9$ | $127.3 \pm 1.9$ |"]
- result: Stokes I flux VLA 1623-B = 127.3 ± 1.9 mJy [Table 1: "| flux (mJy) | $141.8 \pm 5.9$ | $127.3 \pm 1.9$ |"]
- result: Median polarization fraction of inner disks = 1.7 ± not stated % [4.1 The Inner Protostellar Disks: "median polarization fractions of 1.7%"]
- result: Typical polarization fraction of ring = 2.4 ± not stated % [4.2 The Extended Dust Ring: "with a typical polarization fraction of 2.4%"]
- result: Ring 1.3 mm flux = 0.6 ± not stated Jy [5.1 Model Results: "we use this source-subtracted image to measure the 1.3 mm flux of the ring, $S_{1.3} = 0.6$ Jy"]
- result: Ring mass = 0.1 ± not stated Msun [5.1 Model Results: "we calculate a total mass for the ring $M = S_{1.3}d^2/B(T)\kappa = 0.1\ \mbox{M$_{\odot}$}$"]
- result: Column density at polarization transition = 5e24 ± not stated (lower limit) cm-2 [5.3 Dust Scattering: "the transition point corresponds to a column density of $\mbox{N(H$_2$)}\approx 5 \times 10^{24}$ cm$^{-2}$"]
- limitation (authors): Model is simple, axisymmetric, excludes rotation, matched by eye; short spacings missing to trace hourglass [5.1 Magnetic Field Alignment: "The model is only a first step toward a full description, which should include both disk rotation and the dense core environment."]
- not stated (card): Robust/weighting, cell size, image size, niter and threshold for clean; Multiscale scales used; Self-calibration solution intervals and reference antenna/spw; Spectral setup and continuum bandwidth; Line-free/continuum channel selection; Pixel-level masks for ring and disk region definitions beyond the 4 sigma contours with 'slight modification'; Flux of the calibrators and flux scale uncertainty…

### 2016ApJ...831L..12K: Submillimeter Polarization Observation of the Protoplanetary Disk around HD 142527 (2016; protoplanetary_disks; observational_alma_primary)
- question: Is the submillimeter polarization of the HD 142527 disk produced by grain alignment with magnetic fields or by dust self-scattering, and what does it imply for grain size?
- step 1: Image Stokes I,Q,U,V
  - method: Iterative CLEAN with self-calibration, multiscale, Briggs weighting [Observations: "We further perform the iterative CLEAN deconvolution imaging by using CASA with self-calibration to improve the image quality."]
  - software: CASA
  - parameter: robust 0.5; scales 0, 0.3, 0.9 arcsec [Observations: "multiscale option with scale parameters of 0, 0.3, and 0.9 arcsec"]
  - validation: Stokes V rms close to thermal noise [Observations: "The rms for the Stokes $V$ image is 25.2 $\mu$Jy, close to the thermal noise level of the integration time."]
- step 2: Derive polarized intensity and fraction
  - method: PI from integrated Q and U; polarization fraction = PI/I; restrict to >3 sigma_PI [Results: "The discussion in this Letter is concerning at the regions where the detection is larger than 3 $\sigma_{\rm PI}$"]
  - validation: positive polarization bias argued not to affect >3 sigma regions [Results: "thus the positive polarization bias does not affect the results"]
- step 3: Model self-scattering polarization
  - method: RADMC-3D radiative transfer of lopsided ring with amax 150 um, compared qualitatively with observations [Discussions: "We model the intensity with a simple model and perform radiative transfer calculations with RADMC-3D"]
  - software: RADMC-3D
  - parameter: Sigma0max 0.6, Sigma0min 0.008 g cm^-2; rc 170 au; rw 27 au; theta_d 30 deg; phi_d 60 deg; T 36 K; inclination 27 deg; PA 71 deg [Discussions: "$r_c = 170$ au, and $r_w=27$ au."]
  - assumption: compact spherical grains, size slope -3.5 [Discussions: "power-law size distribution with a power of $-3.5$ and the maximum grain size $150 {\rm~\mu m}$"]
  - validation: qualitative comparison of vector flip and PI/continuum peak offset [Comparison with the Observation: "The flip of the polarization vectors of the observations is naturally explained with the self-scattering model."]
- result: Polarization fraction at PI peak = 3.26 ± 0.02 % [Results: "The polarization fraction is $3.26 \pm0.02$ % at the peak of the polarized intensity"]
- result: Polarization fraction at continuum peak = 0.220 ± 0.010 % [Results: "as low as $0.220 \pm 0.010$ % at the peak of the continuum"]
- result: Peak polarization fraction (southwest) = 13.9 ± 0.6 % [Results: "a fraction of $13.9 \pm 0.6$ %"]
- result: Total polarized intensity = 1.75 ± not stated mJy [Results: "to be $1.75$ mJy with an rms of $\sigma_{\rm PI}=42.8 {\rm~\mu Jy~beam^{-1}}$"]
- result: Total polarization fraction = 0.207 ± not stated % [Results: "we derive the total polarization fraction to be $0.207$ %"]
- result: Maximum grain size = ~150 ± range ~40-300 um um [abstract: "this puts a constraint on the maximum grain size to be approximately 150 ${\rm \mu m}$"]
- limitation (authors): High southwest polarization fraction may be due to interferometric filtering [Grain alignment: "could be due to interferometric filtering effects, where the Stokes $I$ and the Stokes $Q$, $U$ maps are resolved out differently."]
- not stated (card): CASA version; number of self-calibration rounds and solution intervals; clean mask, threshold and image size/cell size; how Stokes Q/U/V imaging and polarization leakage calibration were done (deferred to Nagai16); distance to HD 142527; opacity table and RADMC-3D settings (photon number, grid, stellar parameters); polarization debiasing method

### 2025NatAs...9..526O: Observationally derived magnetic field strength and 3D components in the HD 142527 disk (2025; protoplanetary_disks; archival_reuse)
- question: Can multi-wavelength (Band 7, 6, 4, 3) dust polarization of the HD 142527 disk be used to derive the 3D magnetic field components and field strength?
- step 1: Make Stokes I, Q, U images
  - method: tclean with Briggs weighting after phase-only self-calibration [Imaging: "All images were generated with Briggs weighting."]
  - software: CASA, tclean
- step 2: Derive debiased PI, PF and polarization angles
  - method: PI=sqrt(Q^2+U^2-sigma^2); PF=PI/I; PA=0.5 arctan(U/Q), above 3 sigma_PI [Imaging: "We therefore debiased the PI image as ${\rm PI}=\sqrt{Q^2+U^2-\sigma_{\rm PI}^2}$"]
- step 3: Compare polarization across wavelengths
  - method: Images made with same uv range, 0.87 mm smoothed to match beam; compute Delta PA and PF ratios [Imaging of the differences: "the images of the polarization vector differences (Supplementary Figure 1) were generated using the same uv distance."]
- step 4: Fit B_r:B_phi:B_z (single and dual layer)
  - method: Chi-square fit of angular offset between observed B (polarization rotated 90 deg) and toroidal field vs position angle at 200+-50 au in the south [Single Layer Model: "We find that $|B_r |:|B_\phi |:|B_z | = 0.26:1:0.23$ best fits the observations from the chi-squared fit as shown in Figure 3."]
  - assumption: inclination 27 deg, PA 161 deg; same p_max in both layers for dual model [Results: "assuming the disk inclination and position angle of 27$^\circ$ and 161$^\circ$, respectively"]
  - fitting: chi-square minimization [Single Layer Model: "We find that $|B_r |:|B_\phi |:|B_z | = 0.26:1:0.23$ best fits the observations from the chi-squared fit as shown in Figure 3."]
  - validation: Compared with alternate ratio parameters; reduced chi2 ~9 (single) vs ~16 (dual) [Dual Layer Model: "The reduced chi-square value for the best-fit model is approximately 16, which is larger than that of the single layer model."]
- result: |B_r|:|B_phi|:|B_z| single layer = 0.26:1:0.23 ± not stated dimensionless [Single Layer Model: "$|B_r |:|B_\phi |:|B_z | = 0.26:1:0.23$ best fits the observations"]
- result: |B_r|:|B_phi|:|B_z| dual layer = 0.21:1:<0.1 ± not stated dimensionless [Dual Layer Model: "The best fit resulted in $|B_r |:|B_\phi |:|B_z | =0.21:1:<0.1$"]
- result: Reduced chi-square single / dual = 9 / 16 ± not stated dimensionless [Dual Layer Model: "(9 for the single layer model and 16 for the dual layer model)"]
- result: Delta PA 1.3mm-0.87mm in south = 3.9 ± 0.6 degrees [Imaging of the differences: "$\Delta {\rm PA_{1.3mm-0.87mm}}=3.9\pm0.6$ degrees"]
- limitation (authors): Reduced chi-square much greater than 1; more detailed observations and refined models needed [Dual Layer Model: "more detailed observations and refined models would be necessary to understand fine magnetic structure"]
- not stated (card): Archive Stokes I/Q/U imaging details: cell size, image size, masks, niter/threshold, deconvolver; Details of polarization calibration, calibrators and flux scale; Chi-square fit details: parameter grid, errors on Delta phi, spatial sampling, B_r, B_z sign conventions; Temperature profile and scale height details at 200 au beyond T=30 K; Supplementary Table 2 (imaging parameters) is missing from t…

### 2016ApJ...824..132N: ALMA Science Verification Data: Millimeter Continuum Polarimetry of the Bright Radio Quasar 3C 286 (2016; agn_and_quasars, instrumentation; observational_alma_primary)
- question: What are the millimeter (1.3 mm) total intensity and linear polarization properties of the quasar 3C 286, and how do they relate to the centimeter EVPA trend and core shift?
- step 1: Polarization calibration
  - method: Gain solution without polarization model, qufromgain for Q/U of calibrator, KCROSS and XYf+QU for cross-hand, then polcal for D-terms with J1337-1257 [2 Observation and Data Reduction: "The cross-hand delay and cross-hand phase differences relative to a reference antenna were calibrated using the CASA task `gaincal` with the modes `KCROSS` and `XYf+QU` respectively."]
  - software: CASA
  - validation: Repeated D-term calibration with 3C 279; agreement within 0.5% [A.1.2 Reproducibility of the Instrument…: "The differences between the two solutions is not greater than 0.5% and is typically 0.1–0.3% over the band"]
- step 3: Measure core and SW intensity and polarization
  - method: Peak intensities from I, Q, U images; polarization bias correction for the SW component [3 Results: "we should take into account the polarization bias (cite: Vaillancourt2006) for this component."]
  - software: CASA
  - assumption: Absolute EVPA error 0.4 deg from 2 deg misalignment over 29 antennas [2 Observation and Data Reduction: "Throughout this paper, we adopt $0.4^{\circ}$ for the absolute EVPA accuracy."]
  - validation: Agreement with Hull2015 and Agudo2012 EVPA [3 Results: "The obtained EVPA shows a good agreement with (cite: Hull2015) and (cite: Agudo2012)"]
- result: Core peak intensity I = 387.77 ± 0.05 mJy/beam [Table 1: "387.77$\pm$0.05 mJy"]
- result: Core polarized intensity = 64.81 ± 0.07 mJy/beam [Table 1: "64.81$\pm$0.07 mJy"]
- result: Core fractional polarization = 16.7 ± 0.2 % [3 Results: "The polarization percentage of the core is 16.7$\pm$0.2%"]
- result: Core EVPA = 38.6 ± 0.4 degrees [3 Results: "The EVPA of the core is $38.6\pm0.4$ degrees."]
- result: SW component peak intensity = 0.55 ± 0.05 mJy/beam [Table 1: "0.55$\pm$0.05 mJy"]
- limitation (authors): Only three VLBI points, non-simultaneous, C2 may be optically thick; Stokes I dynamic-range limited [4 Discussion: "Since we have only three data points, it is not possible to perform a fit"]
- not stated (card): Image size, cell size, and CLEAN iterations/threshold/masks; Which data were excluded in the first half of the observation; Flagged channels and antennas list; Beam size of final images; Fitting regions/method for core and SW flux and polarization; Details of core-shift power-law extrapolation and error propagation; Image parameters for VLBA reduction and super-resolution beam

### 2020ApJ...896..157H: Magnetic Field Structure of Orion Source I (2020; star_formation, astrochemistry; observational_alma_primary)
- question: What is the magnetic field structure in the bipolar outflow of Orion Source I, probed by polarization of SiO maser/thermal emission at 43 and 86 GHz?
- step 1: Image continuum and line cubes in full Stokes
  - method: Synthesis imaging with CASA and Miriad; 0.5 km/s channels for 28SiO v=0,1 and 1.0 km/s others; 2 km/s for display [2.1 ALMA: "Full-Stokes velocity channel maps were first made with the common velocity resolution of 0.5 km s$^{-1}$ for $^{28}$SiO $v$=0 and $v$=1 transitions"]
  - software: CASA, Miriad
- step 2: Derive debiased linear polarization and angles
  - method: P=sqrt(Q^2+U^2-sigma^2); line-averaged angles from Q,U over 30 km/s centered at 5 km/s; fractional polarization from P and I [2.1 ALMA: "the linearly polarized intensity images were debiased by subtracting the rms noise over the emission-free channels/regions in the images; $P=\sqrt{Q^{2}+U^{2}-\sigma^{2}}$."]
  - parameter: angle error Delta(PA)=DeltaP/2P; vectors plotted for S/N>=4 (errors <7 deg) [3.2.2 Linear polarization: "we plot the vectors with the signal-to-noise ratio of 4 or higher, and hence, the errors in the polarization angle, $\Delta{\rm (PA)}$ are smaller than 7 degrees."]
- step 4: Estimate field strength with DCF method
  - method: Davis-Chandrasekhar-Fermi on 28SiO v=0 J=2-1 angle residuals after subtracting 0.5 arcsec-smoothed angle map [4.2.4 Estimate of the magnetic field st…: "we convolved the SiO Stokes I, Q, and U images with an 0.5$''$ FWHM Gaussian, generated a low resolution polarization angle map from these data, then subtracted this image from the 0.1$''$ resolution image"]
  - parameter: delta phi = 4 deg; Delta V ~ 10 km/s; n(H2)=1e6 cm-3 [4.2.4 Estimate of the magnetic field st…: "Therefore, we adopt a somewhat smaller dispersion $\delta\phi$ = 4$^\circ$"]
  - assumption: density 1e6 cm-3 from maser pumping; correction factor 0.5; total field 4B/pi [4.2.4 Estimate of the magnetic field st…: "we adopt a density of $10^{6}$ cm$^{-3}$ in the $^{28}$SiO $v$=0 $J$=2-1 emission region in order to satisfy the maser pumping model"]
  - validation: compared with OH maser and scaling laws with density [4.2.4 Estimate of the magnetic field st…: "a magnetic field strength $\sim$30 mG is consistent with that estimated from OH maser observations (cite: Cohen2006)"]
- step 5: Test Zeeman interpretation of Stokes V
  - method: Fit V = b dI/dnu to Stokes V spectra at selected positions [4.2.5 Circular Polarization: "we were able to fit some of the velocity components in the Stokes V spectra to the Zeeman pattern"]
  - parameter: g Omega/2pi=230 Hz/G [4.2.5 Circular Polarization: "The magnitude of the Zeeman splitting, $g \Omega/2\pi$=230 Hz G$^{-1}$"]
  - assumption: uniform field for all velocity components [4.2.5 Circular Polarization: "Assuming uniform magnetic field strengths for all the velocity components"]
  - validation: implied fields of ~10 G implausible; opposite signs in J=1-0 and 2-1 [4.2.5 Circular Polarization: "Such large magnetic fields are implausible."]
- result: 96 GHz continuum integrated flux density of SrcI = 58 ± 6 mJy [Table 2: "Integrated Flux$^{a}$ | 10$\pm$1 mJy | 58$\pm$6 mJy"]
- result: DCF plane-of-sky field strength = 23 ± not stated mG [4.2.4 Estimate of the magnetic field st…: "gives a plane of sky magnetic field strength of 23 mG."]
- result: Total field strength = ~30 ± not stated mG [4.2.4 Estimate of the magnetic field st…: "An estimate for the total field strength is $4B_{\rm los}/\pi$ (cite: Crutcher2004), or $\sim$30 mG."]
- result: Fractional linear polarization 28SiO v=0 J=2-1 (average) = ~20-50 ± not stated percent [3.2.2 Linear polarization: "the fractional linear polarizations of the $^{28}$SiO $v$=0 $J$=1-0 and 2-1 lines are $\sim$50-70% and $\sim$20-50%, respectively."]
- result: Polarization angle residual dispersion adopted = 4 ± not stated degrees [4.2.4 Estimate of the magnetic field st…: "we adopt a somewhat smaller dispersion $\delta\phi$ = 4$^\circ$"]
- result: Peak 29SiO v=0 J=2-1 brightness temperature = 1.3e6 ± not stated K [3.3 29SiO v=0 J=2-1 line: "The peak brightness temperature of 1.3$\times$10$^{6}$ K at the LSR velocity of $-1$ km s$^{-1}$ indicates strong maser emission"]
- limitation (authors): ALMA Stokes V calibration not guaranteed in Cycle 5 [2.1 ALMA: "We note that circular polarization measurements were not assured in these ALMA cycle 5 observations."]
- limitation (authors): Fractional polarization may be overestimated because short baselines lack [3.2.2 Linear polarization: "fractional linear polarizations derived from our aperture synthesis images may be overestimated"]
- not stated (card): CASA version used for ALMA and VLA; tclean parameters (weighting/robust, cell, image size, deconvolver, masking, threshold); line-free channels for continuum; how Stokes V and polarization leakage were calibrated in CASA (tasks, solints); how the 5 sigma cutoff and moment velocity ranges were chosen exactly; pixel-level procedure for the Faraday rotation measure solution; how Zeeman fits to Stoke…

### 2024A&A...689A.299M: Prospects of directly using closure traces for imaging in very long baseline interferometry (2024; agn_and_quasars, instrumentation; multi_facility_alma_minor)
- question: Can closure traces (gain- and leakage-independent polarimetric closure quantities) be fitted directly to create polarimetric images in VLBI (EHT, ngEHT) and in a denser array such as ALMA?
- step 1: Prepare ALMA data
  - method: Download archive data, calibrate with ALMA pipeline, export to uvfits, time-average 10 s [Real Data Application: "The data were downloaded from the ALMA archive and calibrated with the ALMA pipeline script."]
  - software: MrBeam
  - parameter: 10 s averaging; spectral window 227.1 GHz [Real Data Application: "time-averaged the data by 10 seconds"]
  - assumption: Negligible circular polarization [Imaging Procedure: "We therefore restrict ourselves in this work to situations with negligibly small circular polarization at first instance."]
- step 2: Reconstruct polarization from closure traces
  - method: MO-PSO multiobjective imaging fitting closure traces, with ALMA pipeline product as initial guess [Real Data Application: "The pipeline product of ALMA was used as an initial guess. The reconstruction of the polarized structure from the closure traces, was then performed with the MO-PSO algorithm"]
  - software: MrBeam, ehtim, pygmo
  - fitting: Particle swarm over regularization weights; objectives chi2 of closure traces plus R_ms, R_hw, R_ptv [Description of the imaging algorithms: "by screening the regularization weights with a particle-swarm optimization algorithm, and solving the related weighted sum problem by fast gradient based minimization techniques."]
  - validation: Qualitative comparison with Albentosa2023 model-fitting results [Real Data Application: "The Stokes I reconstruction, as well as the EVPA structure looks very similar to the reconstructions presented in (cite: Albentosa2023), presenting an interesting cross-verification."]
- result: Runtime of ALMA MO-PSO reconstruction = roughly 30 minutes ± not stated minutes [Real Data Application: "The reconstruction was performed on a common notebook in roughly 30 minutes."]
- limitation (authors): Assumes vanishing circular polarization; MO-PSO does not reproduce multimodality; primary-beam polarization not treated [Conclusions: "As a remaining limitation, we rely on the assumption of vanishing circular polarization"]
- not stated (card): ALMA pipeline/CASA version; Which of the archive execution blocks/scans of 2016.1.01154.V were used and flagging; Number of pixels, field of view, and regularization/weight settings for the ALMA reconstruction; MO-PSO swarm size, iterations, and EVPA alignment details for the real-data run; Total intensity initial guess details for ALMA (pipeline image used); Quantitative metric comparing with Al…

### 2020MNRAS.492.1531M: NaCo polarimetric observations of Sz 91 transitional disc: a remarkable case of dust filtering (2020; protoplanetary_disks; multi_facility_alma_minor)
- question: What are the dust properties and cavity structure of the Sz 91 transitional disk in polarized near-IR light, what companions can be ruled out, and what does this imply for the origin of its large sub-mm cavity?
- step 1: Reduce polarimetric data
  - method: Double-difference Stokes Q,U, then Qphi/Uphi maps [2.1 H and Ks band Polarimetry: "corrected for instrumental polarization using the double-difference method as described in (cite: canovas2011) to produce the final Stokes Q and U images."]
  - software: custom scripts
  - parameter: central r < 4 px masked [2.1 H and Ks band Polarimetry: "The central r $<$ 4 px are dominated by noise, and therefore this region has been masked out"]
  - validation: flux consistent with 2MASS within 0.05 mag [2.1 H and Ks band Polarimetry: "the measured flux is consistent, within an error bar of 0.05 mag, with the published 2MASS photometry"]
- step 5: Polarized phase function
  - method: Adjacent 0.04'' apertures along an ellipse on Qphi image, north vs south [5.2 Polarized phase function: "The size of the aperture was fixed to 0.04$''$."]
  - parameter: a=0.34'', PA 18.1 deg, i 49.1 deg [5.2 Polarized phase function: "semi-major axis $a$ of 0.34$''$, position angle PA of 18.1$^\circ$ and inclination $i$ of 49.1$^\circ$"]
  - validation: compared with best fit model [5.2 Polarized phase function: "Our best model represents relatively well both functions"]
- result: PA minimizing N-S phase function peak offset = 9 ± not stated deg [Appendix: "We found that for a PA of 9$^\circ$ this difference is minimized."]
- limitation (authors): Grain size distribution may be biased to small sizes; dust mass and optical depth uncertain [3.2.3 Caveats of the modeling: "both the total dust mass and the optical depth reported here should be treated carefully"]
- not stated (card): ALMA calibration, imaging parameters and reduction of the 2015.1.01301.S Band 7 image are not given; MCFOST version and number of photon packets; Exact frame selection for H band; Number of principal components used per separation in PCA-ADI; Dust composition fractions beyond 'small amount of carbonaceous particles'

### 2025ApJ...992..103Z: Impact of Gravity on Changing Magnetic Field Orientations in a Sample of Massive Protostellar Clusters Observed with ALMA (2025; star_formation, milky_way_ism; observational_alma_primary)
- question: How do magnetic field orientations at 0.01 pc core scale and 10^3 au envelope scale relate in massive protostellar clumps, and what role does gravity play in changing them?
- step 1: Calibrate and image continuum Stokes I, Q, U
  - method: Calibration by ARC, phase self-cal on Stokes I, tclean of line-free continuum [2 Observations: "The fully calibrated visibilities were then imaged in CASA."]
  - software: CASA
  - parameter: Briggs robust 0.5 [2 Observations: "Briggs weighting of the visibilities with a robust parameter of 0.5"]
- step 2: Derive magnetic field position angles
  - method: theta = 0.5 arctan(U/Q), 3 sigma cutoff on Q and U, rotate by 90 deg [3.1: "The PAs of the magnetic field follow by rotating the electric field by $90^\circ$."]
  - parameter: 3 sigma cutoff [3.1: "Applying a threshold cutoff of 3$\sigma$, the rms of the noise level, to the Stokes $Q$ and $U$ emission"]
  - validation: PA uncertainty 28.65 deg sigma_p/I_p [3.1: "the $1 \sigma$ uncertainty in PA is given by $28.65^\circ \frac{\sigma_p}{I_p}$"]
- limitation (authors): G14 RO distribution cannot be distinguished from random due to small numbers; G28 and I18360 excluded [3.2: "the hypothesis that the RO distribution in G14 is randomly distributed cannot be ruled out due to small number statistics"]
- not stated (card): Number of self-calibration iterations/solints per target and which targets were self-calibrated; Line-free channel selection; Image sizes, cell sizes, clean thresholds and masks; CASA version; Flux calibration accuracy; Pixel sampling details and beams used for RO maps for each source; Exact mosaicking procedure; Whether the K-S comparison random distribution was simulated or analytic; Column den…

### 2013ApJ...779...96T: The Dynamics of Massive Starless Cores with ALMA (2013; star_formation, astrochemistry, milky_way_ism; observational_alma_primary)
- question: Are massive starless cores in IRDCs in virial and pressure equilibrium (Turbulent Core Accretion) or strongly sub-virial (Competitive Accretion)?
- step 4: Compare with virial predictions and magnetic field
  - method: Compute sigma_c,vir and R_c,vir from MT03; derive phi_B,vir, m_A,vir, B_c,vir and B_crit [3.4: "We then evaluate the ratio of the observed velocity dispersion derived from the $\rm N_2D^+$(3-2) spectrum to the prediction from virial equilibrium"]
  - assumption: 0.5<m_A<2 range, f_g=1, alpha_vir,cl=1, phi_geom=1 [1.3: "Finally, we assume that the clump is virialized with $\alpha_{\rm vir,cl}=1$."]
- result: Mean sigma_N2D+/sigma_c,vir,mm (6 cores) = 0.806 ± +0.158/-0.099 dimensionless [3.4: "$\sigma_{\rm N_2D^+}/\sigma_{\rm c,vir}\simeq 0.806^{0.964}_{0.707}$"]
- result: Mean R_c/R_c,vir,mm = 1.58 ± +0.50/-0.28 dimensionless [3.4: "$R_c/R_{\rm c,vir}\simeq 1.58^{2.08}_{1.30}$"]
- result: C1-S m_A,vir = 0.262 ± +0.186/-0.095 dimensionless [3.4: "$\phi_{\rm B,vir}=23.1$, corresponding to $m_{\rm A,vir}=0.262$ and $B_{\rm c,vir}=1050\:{\rm \mu G}$"]
- result: C1-S B_c,vir = 1050 ± +740/-517 microGauss [Table 3: "$1050^{1790}_{533}$"]
- limitation (authors): Mass uncertain by a factor of about 2; core size definition arbitrary; kinematic distance to F uncertain [3.3.2: "Note, that $M_{\rm c,mm}$ still has uncertainties of about a factor of 2"]
- not stated (card): CASA version and calibration/imaging details (weighting, cleaning, mask) not given; Line-free channels used for continuum; Hyperfine fitting code and priors not named; Exact moment-map and core-boundary extraction code

### 2019MNRAS.487.4305S: Testing star formation laws on spatially resolved regions in a z ≈ 4.3 starburst galaxy (2019; high_z_galaxies, star_formation; archival_reuse)
- question: Do the Kennicutt-Schmidt, KDM and SFK star formation relations predict the measured SFR surface density in resolved regions of the z~4.3 starburst AzTEC-1?
- step 5: Predict SFR surface density from KS, KDM, SFK relations and compare
  - method: Evaluate the three relations with measured parameters via Monte Carlo and compare PDFs with measured Sigma_SFR [4.3 Salim-Federrath-Kewley (SFK) Relati…: "The median of the PDF of $\Sigma_{\mathrm{SFR}}$ from the multi-freefall model is"]
  - parameter: KDM eps_ff=0.015; SFK eps_ff=0.0045, b=0.4, beta_mag to infinity [4.3 Salim-Federrath-Kewley (SFK) Relati…: "where $\epsilon_{\mathrm{ff}}=0.0045$, $b$ is the turbulent driving parameter (set to 0.4"]
  - assumption: Zero magnetic field in SFK [4.3 Salim-Federrath-Kewley (SFK) Relati…: "This means we assume that the magnetic field is zero."]
- result: Sigma_SFR,KS nucleus / clump = 105 / 62 ± 42 / 26 Msun/yr/kpc^2 [4.1 Kennicutt-Schmidt (KS) Relation: "$\Sigma^{\mathrm{nucleus}}_{\mathrm{SFR,KS}} = 105\pm42$ and $\Sigma^{\mathrm{sfclump}}_{\mathrm{SFR,KS}} = 62\pm26"]
- result: Sigma_SFR,KDM nucleus / clump = 134 / 106 ± 47 / 40 Msun/yr/kpc^2 [4.2 Krumholz-Dekel-McKee (KDM) Relation: "$\Sigma^{\mathrm{nucleus}}_{\mathrm{SFR,KDM}} = 134\pm47$ and $\Sigma^{\mathrm{sfclump}}_{\mathrm{SFR,KDM}} = 106\pm40"]
- result: Sigma_SFR,SFK nucleus / clump = 270 / 280 ± 145 / 147 Msun/yr/kpc^2 [4.3 Salim-Federrath-Kewley (SFK) Relati…: "$\Sigma^{\mathrm{nucleus}}_{\mathrm{SFR,SFK}} = 270\pm145$ and $\Sigma^{\mathrm{sfclump}}_{\mathrm{SFR,SFK}} = 280\pm147"]
- limitation (authors): Large systematic uncertainties; magnetic field strength unknown; need larger sample [4.4 Comparison of Star Formation Relati…: "Given the large systematic uncertainties that go in calculating the key ingredients, we require a large sample of diverse star-forming regions"]
- not stated (card): Calibration, CASA version and imaging parameters of the archival data (deferred to other papers); Exact Gaussian fitting procedure and regions/software for the 2D fit; Monte Carlo sample count and input distributions; f_H2 value in KDM; Which data products (cubes, moment maps) were used and how moment-1 maps were made; Line-free channels and continuum subtraction; 3DBarolo parameter details beyon…

### 2019ApJ...884L..58U: First Detection of Radio Linear Polarization in a Gamma-Ray Burst Afterglow (2019; transients; observational_alma_primary)
- question: Is the millimeter-band linear polarization of the GRB 171205A afterglow detectable, and does its low degree imply Faraday depolarization by non-accelerated electrons?
- step 1: Image Stokes I, Q, U
  - method: CLEAN with self-calibration on full band and per-SPW [ALMA: "we generated additional Stokes maps using the individual SPWs"]
  - software: CASA
  - validation: Phase calibrator polarization stability <0.02% [ALMA: "we confirm that the stability of linear polarization degree is $<0.02$%"]
- step 2: Derive polarization degree and position angle
  - method: P=100 sqrt(Q^2+U^2)/I; P.A.=1/2 arctan(U/Q) via atan2 [ALMA: "The $atan2$ function in the python math module which returns a numeric value between $-\pi$ and $\pi$, was used to calculate the polarization position angle."]
  - software: Python
- step 4: Test Faraday depolarization
  - method: Compare observed P with model P0 sin(tau/2)/(tau/2) for non-accelerated electron fraction f [Faraday depolarization effect: "the polarization degree is given by $P_0 \sin(\tilde{\tau}_V/2)/(\tilde{\tau}_V/2)$"]
  - parameter: P0 = 1%, 0.5%, 10% [Faraday depolarization effect: "For the case of $P_{0} = 0.5\%$ (Figure [3](#polspec)b), $1/f \sim 10$ is still required."]
  - assumption: Tangled magnetic field in random cells [Faraday depolarization effect: "the magnetic field in the shocked region has been assumed to be tangled on hydrodynamic scales"]
- result: Band 3 linear polarization degree (5.2 d) = 0.27 ± 0.04 % [Polarization: "yield a polarization degree of $0.27 \pm 0.04\%$ (including systematic error)."]
- result: Band 3 polarization position angle = -71.3 ± 3.3 deg [Table 1: "0.27$\pm$0.04 | $-$71.3$\pm$3.3"]
- result: Polarization upper limit at 11.2 d = <0.27 ± 3 sigma % [Polarization: "we measured the corresponding deep upper limit of the polarization degree ($<0.27\%$, 3$\sigma$ significance)"]
- result: Required 1/f for P0=1% = ~12 ± not stated dimensionless [Faraday depolarization effect: "$1/f \sim 12\;(E_{\rm iso}/2\times10^{50} {\rm erg})^{-5/4}"]
- limitation (authors): Non-simultaneous multi-wavelength polarimetry limits conclusions [Faraday depolarization effect: "Although the (semi-) simulataneous measurments in multiple wavelengths are required"]
- not stated (card): Weighting/robust, cell and image size; Mask used in CLEAN; Polarization calibration details and leakage handling; Target coordinates and ALMA array configuration; Fitting method for afterglow model and error treatment of P.A.; Time on source

## All papers in this technique

- 2013ApJ...779...96T (2013): The Dynamics of Massive Starless Cores with ALMA
- 2014A&A...568A..40G (2014): Shadows and cavities in protoplanetary disks: HD 163296, HD 141569A, and HD 150193A in polarized light
- 2014AJ....147..141H (2014): ALMA View of G0.253+0.016: Can Cloud-Cloud Collision form the Cloud?
- 2014ApJ...783L..13P (2014): Large-scale Asymmetries in the Transitional Disks of SAO 206462 and SR 21
- 2014ApJ...791..108F (2014): Distributed Low-mass Star Formation in the IRDC G34.43+00.24
- 2015A&A...581A..97S (2015): Collisional modelling of the AU Microscopii debris disc
- 2015ApJ...812...27A (2015): ALMA Observations of the Transition from Infall Motion to Keplerian Rotation around the Late-phase Protostar TMC-1A
- 2016A&A...593A..44L (2016): The 492 GHz emission of Sgr A* constrained by ALMA
- 2016A&A...593A..61M (2016): Dual differential polarimetry. A technique to recover polarimetric information from dual-polarization observations
- 2016ApJ...820...54K (2016): Grain Size Constraints on HL Tau with Polarization Signature
- 2016ApJ...824..132N (2016): ALMA Science Verification Data: Millimeter Continuum Polarimetry of the Bright Radio Quasar 3C 286
- 2016ApJ...829L..23B (2016): ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe
- 2016ApJ...831L..12K (2016): Submillimeter Polarization Observation of the Protoplanetary Disk around HD 142527
- 2016ApJ...833..209O (2016): Dense Core Properties in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA
- 2017A&A...599A.127F (2017): Radio emission and mass loss rate limits of four young solar-type stars
- 2017A&A...603A..92V (2017): Magnetically aligned dust and SiO maser polarisation in the envelope of the red supergiant VY Canis Majoris
- 2017AJ....153....7Y (2017): Near-infrared Imaging Polarimetry of Inner Region of GG Tau A Disk
- 2017ApJ...842L...9H (2017): Unveiling the Role of the Magnetic Field at the Smallest Scales of Star Formation
- 2017ApJ...847...92H (2017): ALMA Observations of Dust Polarization and Molecular Line Emission from the Class 0 Protostellar Source Serpens SMM1
- 2017ApJ...851...55S (2017): ALMA Reveals Transition of Polarization Pattern with Wavelength in HL Tau’s Disk
- 2017MNRAS.464L..31H (2017): Unveiling the early-stage anatomy of a protocluster hub with ALMA
- 2017MNRAS.469L.123O (2017): ALMA polarization observations of the particle accelerators in the hotspot of the radio galaxy 3C 445
- 2018A&A...616A..56A (2018): Magnetic field in a young circumbinary disk
- 2018A&A...619A.161C (2018): Evidence for a massive dust-trapping vortex connected to spirals. Multi-wavelength analysis of the HD 135344B protoplanetary disk
- 2018A&A...620A..75K (2018): High-resolution observations of gas and dust around Mira using ALMA and SPHERE/ZIMPOL
- 2018ApJ...854...56L (2018): ALMA Dust Polarization Observations of Two Young Edge-on Protostellar Disks
- 2018ApJ...855...92C (2018): ALMA’s Polarized View of 10 Protostars in the Perseus Molecular Cloud
- 2018ApJ...855L...2M (2018): Detection of a Millimeter Flare from Proxima Centauri
- 2018ApJ...858...85P (2018): Forecasting the Contribution of Polarized Extragalactic Radio Sources in CMB Observations
- 2018ApJ...859..165S (2018): Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. I. VLA 1623
- 2018ApJ...860...82H (2018): ALMA Observations of Polarization from Dust Scattering in the IM Lup Protoplanetary Disk
- 2018ApJ...861...91H (2018): ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527
- 2018ApJ...864...81O (2018): Two Different Grain Size Distributions within the Protoplanetary Disk around HD 142527 Revealed by ALMA Polarization Observation
- 2018ApJ...865...13T (2018): A Galaxy-scale Fountain of Cold Molecular Gas Pumped by a Black Hole
- 2018ApJ...866...87B (2018): The Extraordinary Outburst in the Massive Protostellar System NGC 6334I-MM1: Flaring of the Water Masers in a North-South Bipolar Outflow D…
- 2018ApJ...868..101B (2018): ALMA Polarimetry of Sgr A*: Probing the Accretion Flow from the Event Horizon to the Bondi Radius
- 2018ApJ...869L..47Z (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). VII. The Planet-Disk Interactions Interpretation
- 2018MNRAS.474.5105B (2018): HD 169142 in the eyes of ZIMPOL/SPHERE
- 2018MNRAS.475.3004S (2018): ALMA observation of the disruption of molecular gas in M87
- 2018MNRAS.477.2760M (2018): Magnetically regulated collapse in the B335 protostar? I. ALMA observations of the polarized dust emission
- 2018MNRAS.477.4380S (2018): Testing star formation laws in a starburst galaxy at redshift 3 resolved with ALMA
- 2018NatCo...9.4636L (2018): Unveiling a magnetized jet from a low-mass protostar
- 2019A&A...621A..18M (2019): Submillimeter polarization and variability of quasar PKS 1830-211
- 2019A&A...622A.196K (2019): Spatially resolved origin of millimeter-wave linear polarization in the nuclear region of 3C 84
- 2019A&A...624A...7V (2019): Spatial segregation of dust grains in transition disks. SPHERE observations of 2MASS J16083070-3828268 and RXJ1852.3-3700
- 2019A&A...624L...7V (2019): Stringent limits on the magnetic field strength in the disc of TW Hya. ALMA observations of CN polarisation
- 2019A&A...626A..36D (2019): ALMA reveals the magnetic field evolution in the high-mass star forming complex G9.62+0.19
- 2019ApJ...872..121U (2019): Molecular Cloud Cores in the Galactic Center 50 km s<SUP>-1</SUP> Molecular Cloud
- 2019ApJ...878...73Y (2019): ALMA 26 arcmin<SUP>2</SUP> Survey of GOODS-S at 1 mm (ASAGAO): Near-infrared-dark Faint ALMA Sources
- 2019ApJ...878L..25H (2019): ALMA Polarimetry of AT2018cow
- 2019ApJ...878L..26L (2019): ALMA Detection of a Linearly Polarized Reverse Shock in GRB 190114C
- 2019ApJ...879...25K (2019): Highly Ordered and Pinched Magnetic Fields in the Class 0 Protobinary System L1448 IRS 2
- 2019ApJ...879..101L (2019): A Pseudodisk Threaded with a Toroidal and Pinched Poloidal Magnetic Field Morphology in the HH 211 Protostellar System
- 2019ApJ...884...48C (2019): The Seven Most Massive Clumps in W43-Main as Seen by ALMA: Dynamical Equilibrium and Magnetic Fields
- 2019ApJ...884L..58U (2019): First Detection of Radio Linear Polarization in a Gamma-Ray Burst Afterglow
- 2019ApJ...885L..10L (2019): Detection of Pulses from the Vela Pulsar at Millimeter Wavelengths with Phased ALMA
- 2019ApJ...886L...4Z (2019): Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05
- 2019MNRAS.482L..29D (2019): Submillimetre dust polarization and opacity in the HD163296 protoplanetary ring system
- 2019MNRAS.483.2371Y (2019): Does HL Tau disc polarization in ALMA band 3 come from radiatively aligned grains?
- 2019MNRAS.487.4305S (2019): Testing star formation laws on spatially resolved regions in a z ≈ 4.3 starburst galaxy
- 2019MNRAS.489..470G (2019): ALMA Band 3 polarimetric follow-up of a complete sample of faint PACO sources
- 2019MNRAS.490.5300D (2019): Investigating the multiwavelength behaviour of the flat spectrum radio quasar CTA 102 during 2013-2017
- 2019NatAs...3.1109P (2019): Kinematic detection of a planet carving a gap in a protoplanetary disk
- 2019PASJ...71L...3F (2019): First detection of PSR B1259-63/LS 2883 in the millimeter and submillimeter wavelengths with ALMA
- 2019PASP..131g5003G (2019): Calibration of ALMA as a Phased Array. ALMA Observations During the 2017 VLBI Campaign
- 2020A&A...634L..15G (2020): Polarized emission by aligned grains in the Mie regime: Application to protoplanetary disks observed by ALMA
- 2020A&A...636A..62K (2020): Investigating the connection between γ-ray activity and the relativistic jet in 3C 273 during 2015-2019
- 2020A&A...637A...7M (2020): Detection of deuterated molecules, but not of lithium hydride, in the z = 0.89 absorber toward PKS 1830-211
- 2020A&A...638L..14C (2020): The atomic gas of star-forming galaxies at z ∼ 0.05 as revealed by the Five-hundred-meter Aperture Spherical Radio Telescope
- 2020A&A...640A.111A (2020): Outflows, cores, and magnetic field orientations in W43-MM1 as seen by ALMA
- 2020A&A...644A..11L (2020): A statistical analysis of dust polarization properties in ALMA observations of Class 0 protostellar cores
- 2020ApJ...891...80M (2020): Properties of M Dwarf Flares at Millimeter Wavelengths
- 2020ApJ...892..152H (2020): Understanding the Origin of the Magnetic Field Morphology in the Wide-binary Protostellar System BHR 71
- 2020ApJ...893...33L (2020): ALMA Polarimetry Measures Magnetically Aligned Dust Grains in the Torus of NGC 1068
- 2020ApJ...893...54Y (2020): Transition from Ordered Pinched to Warped Magnetic Field on a 100 au Scale in the Class 0 Protostar B335
- 2020ApJ...895...64L (2020): Radio Linear Polarization of GRB Afterglows: Instrumental Systematics in ALMA Observations of GRB 171205A
- 2020ApJ...895L..46L (2020): Hints of a Population of Solar System Analog Planets from ALMA
- 2020ApJ...896..157H (2020): Magnetic Field Structure of Orion Source I
- 2020ApJ...899...55A (2020): Search for Alignment of Disk Orientations in Nearby Star-forming Regions: Lupus, Taurus, Upper Scorpius, ρ Ophiuchi, and Orion
- 2020ApJ...899..152H (2020): Mapping Circumstellar Magnetic Fields of Late-type Evolved Stars with the Goldreich-Kylafis Effect: CARMA Observations at λ1.3 mm of R Crt …
- 2020ApJ...904L..24S (2020): ALMA CO Observations of the Gamma-Ray Supernova Remnant RX J1713.7-3946: Discovery of Shocked Molecular Cloudlets and Filaments at 0.01 pc …
- 2020MNRAS.492.1531M (2020): NaCo polarimetric observations of Sz 91 transitional disc: a remarkable case of dust filtering
- 2021AJ....161..238W (2021): The Anatomy of an Unusual Edge-on Protoplanetary Disk. I. Dust Settling in a Cold Disk
- 2021ApJ...908..141H (2021): ALMA CN Zeeman Observations of AS 209: Limits on Magnetic Field Strength and Magnetically Driven Accretion Rate
- 2023NatAs...7...80U (2023): Simultaneous radio and optical polarimetry of GRB 191221B afterglow
- 2023Natur.621..483G (2023): Polarized thermal emission from dust in a galaxy at redshift 2.6
- 2024A&A...682A..56Z (2024): Exploring the dust grain size and polarization mechanism in the hot and massive Class 0 disk IRAS 16293-2422 B
- 2024A&A...686A.274V (2024): Molecular line polarisation from the circumstellar envelopes of asymptotic giant branch stars
- 2024A&A...689A.299M (2024): Prospects of directly using closure traces for imaging in very long baseline interferometry
- 2024Ap&SS.369...18M (2024): Multi-wavelength observation of MAXI J1348─630 during the outburst in 2019
- 2024ApJ...963..134Y (2024): Turbulent Vortex with Moderate Dust Settling Probed by Scattering-induced Polarization in the IRS 48 System
- 2024ApJ...970...56P (2024): Radio Emission from the Magnetically Active M Dwarf UV Ceti from 1 to 105 GHz
- 2024ApJ...971..129C (2024): A Dust-trapping Ring in the Planet-hosting Disk of Elias 2-24
- 2024ApJ...972...74M (2024): Observations of Low and Intermediate Spectral Peak Blazars with the Imaging X-Ray Polarimetry Explorer
- 2024ApJ...975..103P (2024): The Faraday Rotation Measure of the M87 Jet at 3.5 mm with ALMA
- 2024NatAs...8.1148U (2024): Support for fragile porous dust in a gravitationally self-regulated disk around IM Lup
- 2024PSJ.....5..230D (2024): Surface Properties of the Kalliope─Linus System from ALMA and VLA Data
- 2025A&A...695A.149K (2025): Physical conditions around high-mass young star-forming objects via simultaneous observations of excited OH and methanol masers
- 2025A&A...695A.233R (2025): A multifrequency study of sub-parsec jets with the Event Horizon Telescope
- 2025A&A...699A..62J (2025): ALMA observation of an evolving magnetized corona in the radio-quiet changing-state active galactic nucleus NGC 1566
- 2025ApJ...984L..19Y (2025): exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings
- 2025ApJ...990...59Y (2025): The Impact of Silicate Grain Coagulation on Millimeter Emission from Massive Protostellar Disks
- 2025ApJ...990...80K (2025): Key Physical Parameters Influencing Fragmentation and Multiplicity in Dense Cores of Orion A
- 2025ApJ...990..183U (2025): Multiwavelength Dust Characterization of the HL Tau Disk and Implications for Planet Formation
- 2025ApJ...992..103Z (2025): Impact of Gravity on Changing Magnetic Field Orientations in a Sample of Massive Protostellar Clusters Observed with ALMA
- 2025NatAs...9..526O (2025): Observationally derived magnetic field strength and 3D components in the HD 142527 disk
- 2026ApJ..1001..124M (2026): Multiwavelength ALMA Imaging of HD 34282: Dust-trapping Signatures of a Vortex Candidate
- 2026ApJ..1002L..28Y (2026): A Close Quasar Pair in a Massive Galaxy Merger at z = 5.7
- 2026ApJ..1003..215F (2026): Reading between the Rings: Observed Dust Ring Properties as Probes of Planet Masses
