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

=== SKILL.md (spectral-index) ===
---
name: alma-spectral-index
description: "Measure millimetre/submillimetre spectral indices (alpha) between or within ALMA bands, convert them to a dust opacity (emissivity) index beta, and judge grain-growth claims against optical depth, scattering, free-free and calibration systematics. Use when asked for an alpha map, radial alpha profile, disk-integrated or source-integrated alpha, beta of disks, envelopes, cores or debris rings, or whether low alpha means mm-sized grains. Built from 233 ALMA papers (2012-2026)."
---

# Spectral index and dust emissivity index (alpha, beta)

Measures how flux scales with frequency, S_nu ∝ nu^alpha, between two or more ALMA (and often VLA) bands, and
turns alpha into the dust opacity index beta (kappa ∝ nu^beta) to argue about grain growth. The two mistakes that
matter most: (1) treating low alpha as grain growth when the emission is optically thick or scattering-dominated
(2018A&A...619A.161C, 2019ApJ...883...71C), and (2) quoting only the statistical error when the per-band
flux-calibration error dominates (about 0.4 on alpha for 10% per band at B6/B7; 2018A&A...616A..88V,
2018ApJ...852..122H).

Counts below are from the `spectral-index` evidence pack: either its aggregates (said so) or my own count of its
per-paper lines, with clearly off-topic papers removed. The pack was tagged by regex, so many of its 233 papers use
"alpha" or "beta" for something else (Fermi photon index, disk viscosity, Nuker profile, `frank` hyperparameter,
disk flaring index). Ignore those.

## When to use

- Two or more continuum bands of the same source, and the question is alpha, beta, a_max or "grain growth".
- Radial alpha profiles of protoplanetary disks (rings vs gaps) (2018A&A...616A..88V, 2020ApJ...891...48H,
  2020ApJ...898...36L) or alpha maps of azimuthal features (2026ApJ..1001..124M).
- Envelope beta in Class 0/I protostars, separated from the compact disk (2025A&A...700A.188C).
- Debris-disk mm index and grain size-distribution slope q (2015ApJ...798..124R, 2017MNRAS.466.4201W,
  2019AJ....158..162F).
- Classifying compact sources as thermal dust (alpha > 2) vs free-free or synchrotron (alpha ≤ 2) in clusters,
  galaxy nuclei and stellar sources (2018ApJ...853..171G, 2021A&A...652A..98G, 2017ApJ...841..130A).
- Deciding which beta to adopt when only one band exists (see the adopted-beta counts in
  `references/parameters.md`).

## When not to use

| Situation | Use instead |
|---|---|
| Single band, you only need a dust mass | `dust-continuum-mass` skill (it covers kappa, T, gas-to-dust) |
| Many bands from far-IR to mm with T_dust free (galaxies, high z) | `sed-fitting` skill |
| You need to split dust from free-free/synchrotron at cm wavelengths | `free-free-synchrotron` skill first, then come back |
| You want ring/gap positions and widths, not alpha | `disk-substructure-profiles` or `uv-plane-fitting` |
| Full 2D/3D modelling of T, tau, scattering | `radiative-transfer-modelling` |
| Bands observed months apart on a variable source (stars, AGN, outbursts) | treat as `variability-time-domain` first; alpha is not defined across epochs if the source changed (2017ApJ...837L..29H, 2016A&A...586A..70L) |

## Steps

1. **Pick the bands for lever arm, not convenience.**
   - Goal: keep the calibration term small. The error on alpha scales as 1/ln(nu1/nu2) (general practice).
   - Papers: adjacent B6 and B7 were called "not optimal" (2020MNRAS.496..394R). Wider pairs used: 95 and 233 GHz
     (2025A&A...700A.188C), 1.1 and 2.1 mm (2020ApJ...891...48H), 1.3 and 2.9 mm (2020ApJ...898...36L), B3 to B7
     plus VLA 8 mm (2019ApJ...883...71C), 0.9 to 3.1 mm in four bands (2026ApJ..1001..124M).
   - In-band alpha (single band, two sidebands or `nterms=2`) is possible but has a short lever arm
     (2016Natur.535..258C at 218.0/232.6 GHz; 2015A&A...577L...4V within Band 3).

2. **Calibrate, self-calibrate and build the continuum.**
   - Record the flux calibrator and adopted per-band uncertainty. The pack aggregates flag "flux calibrator and flux
     scale uncertainty" or "flux scale uncertainty" as not stated in at least 10 cards, and CASA version in 18.
   - Line-free channels only; continuum is assumed flat within a spw (spectral index 2 gives <1% change;
     2024A&A...689A.317G).
   - Self-cal both bands, then align them: 2026ApJ..1001..124M aligned execution blocks in the uv plane before
     combining (peak S/N gains 42-168% after self-cal).

3. **Image both bands on a matched footing.**
   - Same uv range: 40-610 klambda (2017MNRAS.467L.120M), 17-1260 klambda (2018A&A...616A..88V), 20-360 klambda
     (2019A&A...626A..36D), 6-150 klambda (2025A&A...700A.188C).
   - Same beam: CASA `imsmooth` to the coarser beam (2020ApJ...891...48H); common 0.25" (2018A&A...616A..88V),
     1"x1" (2025A&A...700A.188C), 50 mas (2019ApJ...883...71C), 0.13-0.16" (2021A&A...652A..98G).
   - Same pixel grid: convolve and regrid before dividing (2015ApJ...813..118M).
   - CASA `tclean` with `deconvolver='mtmfs'`, `nterms=2` gives an in-band alpha image and a better continuum model
     (2018ApJ...852..122H, 2020ApJ...898...36L, 2018ApJ...853..171G, 2026ApJ..1001..124M).
   - Primary-beam correct before measuring fluxes (2025A&A...700A.188C).

4. **Measure alpha in the form the question needs.**
   - Integrated: curve-of-growth aperture (2018A&A...616A..88V), `imfit` Gaussian (2024Ap&SS.369...18M), or
     `uvmodelfit` (2020ApJ...894...76W). Then alpha = ln(S1/S2)/ln(nu1/nu2).
   - Pixel map: divide matched images where both bands pass an S/N cut (see table); 2017ApJ...841..130A also built
     the error map pixel by pixel.
   - Radial profile: deproject with fixed i and PA, average in annuli (1 au bins in 2020ApJ...891...48H, 10 mas in
     2019ApJ...883...71C), then take alpha of the two intensity profiles. Errors per annulus
     dI = rms/(Omega_ring/Omega_beam)^0.5 (2019ApJ...883...71C).
   - uv plane: alpha in azimuthally averaged baseline bins common to both bands, after subtracting a fitted compact
     component to isolate the envelope (2025A&A...700A.188C). Joint visibility fit with alpha as a free parameter,
     uniform prior 0-4 (2018ApJ...859..103W, MCMC).
   - Many bands: weighted power-law fit (2017ApJ...841..130A, 2020MNRAS.496..394R); MCMC with flat prior
     (2017MNRAS.466.4201W).

5. **Put the systematic error in.**
   - Propagate per-band flux-calibration error in quadrature (general practice). Adopted values: 10% per band
     (2020ApJ...891...48H, 2018ApJ...869..158F, 2018A&A...616A..88V), 2.5% B3 and 5% B6 giving 0.1 on alpha
     (2025A&A...700A.188C), 15% (2020MNRAS.496..394R).
   - Report statistical and absolute errors separately, e.g. alpha 2.09 ± 0.03 (stat) with 0.42 absolute
     (2018A&A...616A..88V). Monte Carlo the calibration: 1000 rescaled fits, 16th-84th percentiles
     (2019ApJ...883...71C).
   - Keep a source only if |alpha| > 5 sigma(alpha) or sigma(alpha) < 0.1 (2018ApJ...853..171G).

6. **Remove non-dust emission.**
   - Model the free-free jet from VLA data and subtract it in the uv plane before dust analysis
     (2019ApJ...883...71C: 175 uJy at 32.5 GHz, alpha about 0.7). Drop the band most affected (they dropped K band).
   - Extrapolate cm free-free into the ALMA band and subtract (2016ApJ...833L...6C used index -0.118).
   - Fixed component indices seen: free-free -0.1 (2019MNRAS.483.1624B, 2017ApJ...849...90S, 2020ApJ...895L...2N),
     synchrotron -0.7 to -0.9 (2018ApJ...867...48I, 2017ApJ...849...90S, 2015ApJ...813..118M), dust 3.8
     (2017ApJ...849...90S). Test the non-thermal index (2015ApJ...813..118M tried -0.6 as well as -0.85).

7. **Convert alpha to beta, with the assumptions stated.**
   - Optically thin and Rayleigh-Jeans: beta = alpha - 2 (2025A&A...700A.188C, 2015ApJ...798..124R).
   - Outside RJ: beta = (alpha + Delta alpha) - 2. General practice: Delta alpha = x e^x/(e^x - 1) - 1 with
     x = h nu / k T. 2019A&A...626A..36D got Delta alpha = 0.06 at 100 K and 0.20 at 35 K.
   - Temperature models used: T(R) = 38 (L/Lsun)^0.2 (R/100 au)^-0.4 K for envelopes (2025A&A...700A.188C);
     midplane 30 K and 18 K at two rings (2020ApJ...891...48H); 45 ± 5 K for a debris ring (2017MNRAS.466.4201W).
   - Optical depth: tau = -ln(1 - I/B_nu(T)); beta from the tau ratio only where tau is small (2020ApJ...891...48H;
     2026ApJ..1001..124M).
   - Include scattering when tau is not small: absorption plus scattering slab, fit T, tau_0 and beta per radius,
     iterate a_max to <5% change (2019ApJ...883...71C); DSHARP opacities via `dsharp_opac` (2020ApJ...891...48H).

8. **Interpret.**
   - ISM-like beta is about 1.5-1.7: Planck value 1.51 ± 0.13 quoted by 2025A&A...700A.188C; ISM beta upper limit
     1.7 assumed by 2018ApJ...852..122H. As general practice, beta below about 1 is read as grains of mm size or larger;
     2025A&A...700A.188C read ISM-like envelope beta as maximum grain sizes below about 100 um.
   - Debris disks: q = (alpha_mm - alpha_pl)/beta_s + 3 with beta_s = 1.8 ± 0.2 (2017MNRAS.466.4201W,
     2019AJ....158..162F); q from the Draine (2006) relation (2015ApJ...798..124R).
   - alpha near 2 in a disk centre usually means optically thick, not grain growth: 2.09 in the V1094 Sco inner disk
     with a brightness temperature of only 12.9 K (2018A&A...616A..88V); ALMA bands optically thick, tau 1-10, at
     all radii of HL Tau (2019ApJ...883...71C).

## Parameter defaults and ranges

| parameter | common choice | range seen | papers (count) | examples |
|---|---|---|---|---|
| Band pair | B3 or B4 with B6 | adjacent B6/B7 to B3 + VLA | my count: at least 6 wide-pair papers | 2025A&A...700A.188C, 2020ApJ...891...48H, 2019ApJ...883...71C |
| Flux-cal error per band | 10% | 2.5% (B3) to 15% | 10%: 4; others 1 each | 2018A&A...616A..88V, 2024A&A...689A.104D, 2025A&A...700A.188C, 2020MNRAS.496..394R |
| Resulting absolute error on alpha | 0.4 (B6/B7, 10%) | 0.1-0.42 | 3 | 2018A&A...616A..88V, 2018ApJ...852..122H, 2025A&A...700A.188C |
| Matched uv range | shortest common to longest common baseline | 6-1260 klambda | 4 | 2017MNRAS.467L.120M, 2019A&A...626A..36D |
| Common beam | coarser of the two | 50 mas to 1" | 5 | 2020ApJ...891...48H, 2018A&A...616A..88V |
| Pixel S/N cut for alpha maps | 3 sigma in both bands | 2.5 to 20 | 5 | 2018A&A...616A..88V (2.5), 2017ApJ...841..130A (3), 2026ApJ..1001..124M (15), 2018A&A...619A.161C (20) |
| In-band alpha imaging | `mtmfs`, `nterms=2` | - | 4 | 2018ApJ...852..122H, 2020ApJ...898...36L |
| Briggs robust for alpha images | 0 to 0.5 | -0.5 to 1 | 4 | 2018ApJ...852..122H (0), 2026ApJ..1001..124M (0.5), 2025A&A...700A.188C (1) |
| T for RJ correction | measured or L-scaled profile | 15-100 K | 4 | 2019A&A...626A..36D, 2025A&A...700A.188C |
| Size distribution slope p | 3.5 | 1.5-3.5 | 2 | 2019ApJ...883...71C, 2020ApJ...891...48H |
| Minimum grain size | 0.1 um | 0.05-0.1 um | 2 | 2020ApJ...891...48H, 2019ApJ...883...71C |
| beta_s (debris) | 1.8 ± 0.2 | - | 2 | 2017MNRAS.466.4201W, 2019AJ....158..162F |
| Adopted beta if not measured | 1.0 (disks, cores); 1.8-2.0 (galaxies, clumps) | 0.4-2.0 | my count: 83 papers, see references | 2016ApJ...828...46A, 2020ApJ...892...66M, 2020A&A...635A...2S |
| Free-free index | -0.1 | -0.118 to -0.1 | 4 | 2019MNRAS.483.1624B, 2016ApJ...833L...6C |
| Synchrotron index | -0.8 (4 papers) | -0.7 to -0.9 | 7 | 2020A&A...642A.155Z, 2024ApJ...961..120C, 2015ApJ...813..118M, 2018ApJ...867...48I |

Per-paper beta adoption, measured alpha values and the full list of thresholds are in `references/parameters.md`.

## Software

Counts are pack aggregates over matched steps (mentions, not unique papers), with name variants merged. Tools that
appear only in off-topic papers (Fermi `make3FGLxml`, XCLASS/MAGIX line fitting, Tiny Tim, MGE, FARGO/FARGO-3D/
LA-COMPASS hydro runs, BLOBCAT) are left out.

| Tool | Pack count | Used for |
|---|---|---|
| CASA (incl. imfit 2, uvmodelfit 1, clean 1, simobserve 1) | 38 | `tclean` mtmfs nterms=2, `imsmooth` beam matching (2020ApJ...891...48H), `imfit` fluxes (2024Ap&SS.369...18M), `uvmodelfit` (2020ApJ...894...76W) |
| emcee | 9 | joint visibility fits with alpha free, ring/disk models (2015ApJ...798..124R, 2020ApJ...898...36L) |
| GILDAS | 4 | imaging and continuum handling in IRAM-style reductions (2024A&A...689A.317G) |
| MIRIAD, AIPS (incl. IMAGR) | 3, 2 | cm data and in-band indices (2020PASJ...72...62A) |
| RADMC-3D, mcfost, DALI, DIAD | 3, 1, 1, 2 | forward models of T and tau; DALI used to test a cold optically thick inner disk (2018A&A...616A..88V) |
| galario, dynesty, Frankenstein (`frank`) | 2 each | visibility modelling (2025A&A...700A.188C, 2026ApJ..1001..124M) |
| SciPy (incl. curve_fit), lmfit | 2, 1 | least-squares SED and power-law fits (2019ApJ...883...71C, 2019ApJ...875...55W) |
| dsharp_opac | 1 | DSHARP opacities for a_max from beta (2020ApJ...891...48H) |
| STATCONT | 1 | continuum level from line-rich spectra (2020A&A...644A..84M) |
| lifelines, ASURV | 2, 1 | survival statistics with censored fluxes or indices |
| CIGALE, MAGPHYS, EAZY | 3, 2, 2 | galaxy SED fits; see `sed-fitting` |

## Pitfalls

- **Calibration, not noise, sets the error.** Absolute alpha uncertain by about 0.4 (2018ApJ...852..122H,
  2018A&A...616A..88V); absolute flux scale uncertain, affecting the spectral index (2015ApJ...812..126C).
  Several papers leave calibration out of the fit uncertainty (2021A&A...656A..46M, 2020ApJ...892...99C). Relative
  alpha changes across one disk are more robust than the absolute level, since the calibration offset is common
  (general practice).
- **Short lever arm.** Adjacent B6/B7 gave alpha 2.2 ± 0.5 (2020MNRAS.496..394R); 231/266 GHz gave
  1.18 ± 0.65 (2017NatAs...1..709O).
- **Optical depth mimics grain growth.** A spectral-index decrease may be optical thickness rather than grain growth
  (2018A&A...619A.161C); optical depth affects the grain-size estimate (2018A&A...616A..56A). Optically thick
  young disks have alpha about 2 (2.2 ± 0.2 compact component in 2025A&A...700A.188C).
- **Scattering lowers alpha further** at high optical depth; fit with scattering included (2019ApJ...883...71C,
  2020ApJ...891...48H).
- **Temperature and tau are degenerate.** tau at 680 GHz cannot be measured independently of temperature
  (2015ApJ...810L...7V); ±5 K changes tau by 25-30% (2026ApJ..1001..124M); assumed beta and T disagreed with
  Herschel FTS values (2016ApJ...826...26T).
- **Different spatial filtering per band.** Interferometers resolve out emission above about 5", biasing faint-source
  indices (2017A&A...604A...6S); ALMA-only recovered about 18% of the flux (2014ApJ...795L..25R); ALMA flux was low
  without ACA data (2024RMxAA..60..355R). Match uv ranges or combine with total power.
- **Free-free at disk centres and in protostars.** Index about 1 at the HL Tau centre from 6.7/7.3 mm sub-bands
  (2016ApJ...821L..16C); 7 mm may include free-free so no 7 mm masses (2018ApJ...855...24P).
- **Non-simultaneous bands on variable sources.** Brightening may have evolved between epochs
  (2017ApJ...837L..29H); short mm flares cannot be excluded (2019ApJ...875...55W).
- **Limits.** 53% of indices were lower limits in one radio sample (2017A&A...602A..54M); two of the brown-dwarf disk
  indices were lower limits (2017ApJ...846...70P). Use survival statistics, not detections only.
- **Map artefacts.** Edge gradients appear in spectral index maps (2017MNRAS.469L.123O); 17 GHz left out of index
  maps for artefacts (2017ApJ...841..130A); image-plane alpha maps are limited by disk-envelope contamination
  (2025A&A...700A.188C). Spectral index errors may be underestimated at limited resolution (2017A&A...602L..10O).
- **Settings the cards rarely state** (pack aggregates): CASA version (18), self-cal solution intervals (13 plus
  9 with iterations), image and cell size (10), line-free channels (dozens across phrasings), flux calibrator and
  uncertainty (at least 10). State all of these in your own write-up.

## Verification checks

What papers did:
- Compare uv-plane and image-plane alpha (2025A&A...700A.188C), model-based and image-based profiles
  (2020ApJ...898...36L), or alpha from best-fit model images (2026ApJ..1001..124M).
- Compare a disk-averaged index with the literature (2020ApJ...891...48H: 2.7 ± 0.2 vs 2.94 ± 0.44) or with
  earlier unresolved mm and cm indices (2017A&A...602L..10O).
- Check that ALMA-only indices agree with those including VLA and SMA (2017A&A...604A...6S); run a
  matched-resolution check (mean ratio 1.03 on 38 sources, 2017A&A...602A..54M).
- Split a band into sub-bands and compare (2016ApJ...821L..16C).
- Predict an independent band from the fitted model (3.0 mm image in 2019ApJ...883...71C; 43 GHz refit in
  2015A&A...577A..30A).
- Vary T by 10 K or the T-profile index within -0.3 to -0.6; beta stayed within 10% (2025A&A...700A.188C).
- Change priors (Jeffreys vs uniform, negligible change; 2018ApJ...859..103W) and compare regression methods
  (2014ApJ...796...82Z).
- Compare peak brightness temperature with a physical temperature to test optical thickness (2018A&A...616A..88V).

What a careful referee adds:
- Absolute and relative alpha errors given separately, and the per-band flux-cal values named.
- Bands at matched uv range, beam, pixel grid and astrometric registration; epochs close enough for the source.
- Free-free estimated or bounded from cm data before calling alpha "dust".
- Any beta < 1 claim shown to survive tau and scattering corrections, with the T assumption stated.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2025A&A...700A.188C: envelope beta from uv-plane alpha, B3/B6, compact-component removal, T(R) profile
- 2020ApJ...891...48H: B4/B6 radial alpha, tau from Planck, beta from tau ratio, DSHARP opacities
- 2019ApJ...883...71C: HL Tau multi-band radial SED with scattering, free-free subtraction, Monte Carlo calibration
- 2018A&A...616A..88V: matched uv and beam alpha profile, S/N mask, 0.42 absolute error, cold thick inner disk
- 2020ApJ...898...36L: B3/B6 rings, alpha minima at ring peaks, tau 0.1-0.4
- 2026ApJ..1001..124M: four-band arc, alpha map at S/N > 15, alpha 2.48 arc vs 3.11 ring
- 2018ApJ...852..122H: TW Hya alpha with mtmfs nterms=2, ±0.4 absolute
- 2018A&A...619A.161C: S/N > 20 both bands; optical depth vs grain growth caveat
- 2019A&A...626A..36D: matched uv range, RJ correction Delta alpha
- 2017MNRAS.466.4201W: debris alpha_mm and q with beta_s
- 2015ApJ...798..124R: debris alpha, beta = alpha - 2, q via Draine 2006
- 2018ApJ...859..103W: joint MCMC visibility fit with alpha free per component
- 2018ApJ...853..171G: mtmfs alpha for 62 compact sources, 5 sigma selection
- 2016ApJ...821L..16C: free-free at disk centre from sub-band index
- 2017MNRAS.467L.120M: matched uv range, free-free point sources
- 2015ApJ...813..118M: convolve and regrid, thermal fraction with fixed non-thermal index
- 2017A&A...604A...6S: spatial filtering bias on indices; ALMA vs ALMA+VLA+SMA check
- 2020MNRAS.496..394R: adjacent bands give poor alpha
- 2021A&A...652A..98G: alpha maps of AGN tori at a common resolution

=== references/parameters.md ===
# Spectral index: longer parameter tables

All entries come from the `spectral-index` evidence pack (aggregate lines "Key parameters", "Assumptions" and the
paper excerpts). Counts are my own count of those pack lines, one paper counted once per value. Papers whose "beta"
is a disk flaring index (2019A&A...622A..75L, 2019A&A...624A...7V, 2024ApJ...966...59S, 2021AJ....161..238W), a
Nuker shape parameter, or a Fermi photon index are excluded.

## 1. Adopted (fixed) dust beta when it is not measured

83 papers state a fixed beta. The split follows the science field more than any measurement.

| beta | papers | typical context | bibcodes |
|---|---|---|---|
| 0.4-0.5 | 5 | disks, with kappa about 2.3 cm2/g at 230 GHz | 2014ApJ...787...42C, 2015ApJ...798..124R, 2014ApJ...796....1T, 2019ApJ...878L...8T, 2019ApJ...878...16P |
| 1.0 | 22 | protoplanetary disks and protostars; kappa = 10 cm2/g at 1000 GHz type laws | 2014Sci...345.1584B, 2016ApJ...826...16E, 2016ApJ...828...46A, 2017ApJ...850L...2A, 2018A&A...619A.161C, 2018ApJ...861...91H, 2018ApJ...863...19A, 2018MNRAS.473..879P, 2018MNRAS.475.5322S, 2019A&A...623A.150V, 2019A&A...623L...8B, 2019A&A...628A..85V, 2019ApJ...872..112V, 2019ApJ...877L..25M, 2019ApJ...886....6T, 2019MNRAS.482..698C, 2019MNRAS.486.4114R, 2019NatAs...3..314L, 2020ApJ...898...10T, 2020MNRAS.496..394R, 2024ApJ...973...42B, 2025ApJ...993..120H |
| 1.2 | 2 | scaled single-dish data; pillars | 2014ApJ...795L..25R, 2020AJ....159...62C |
| 1.46-1.5 | 16 | high-z and nearby galaxies, some cores and disks | 2015ApJ...812...27A, 2019MNRAS.483.1624B, 2012ApJ...752L..30W, 2014ApJ...792...34O, 2015ApJ...810...91H, 2016ApJ...819...82S, 2016PASJ...68...43K, 2017ApJ...835...98U, 2017ApJ...836L...2B, 2018AJ....156..239Z, 2018ApJ...856L..12N, 2018PASJ...70...65U, 2019ApJ...871..170M, 2020ApJ...896..110L, 2024BSRSL..93..601H, 2025ApJ...992..103Z |
| 1.6 | 6 | z > 6 quasar hosts, always with T_dust = 47 K | 2013ApJ...770...13W, 2016ApJ...816...37V, 2017Natur.545..457D, 2018ApJ...854...97D, 2019ApJ...876...99S, 2024ApJ...968....9W |
| 1.7-1.75 | 5 | dense cores, low-metallicity galaxies | 2016ApJ...833L...6C, 2017MNRAS.468L..87C, 2019ApJ...881L..39B, 2024A&A...691A.180F, 2018ApJ...853..171G |
| 1.8-1.85 | 12 | galaxies (SMGs, z~1-3, clusters), some cores | 2014ApJ...785..111W, 2015ApJ...811L...3T, 2017ApJ...837..174O, 2017ApJ...840..101C, 2018Sci...362.1034D, 2019ApJ...880...15K, 2019MNRAS.482.3135B, 2020ApJ...892...66M, 2024ApJ...963....1O, 2024ApJ...966...51G, 2025A&A...698A.204H, 2020ApJ...896..127K |
| 1.9 | 2 | dense core, starburst nucleus | 2016ApJ...826...26T, 2021A&A...656A..46M |
| 2.0 | 13 | lensed high-z DSFGs; massive star-forming clumps and hot cores | 2013ApJ...767...88W, 2014ApJ...787..112C, 2015A&A...577A..30A, 2016ApJ...822...80S, 2016ApJ...826..112S, 2017ApJ...844..123F, 2018A&A...616L..10F, 2020A&A...635A...2S, 2020A&A...644A..84M, 2020ApJ...902...78R, 2025A&A...699A.369V, 2025ApJ...994..225N, 2026A&A...705A.100E |

Ranges explored instead of a single value: 1.0-2.0 tested when scaling Herschel to 3 mm (2014ApJ...795L..25R);
1.2-2.0 (2017Sci...355.1285N); 1-1.8 (2020ApJ...890..129K); bounded 0-2 to constrain T_SED (2021A&A...653A.117B);
MCMC over 1.3-2.5 (2024A&A...684A..56K); 1.5-2.0 varied for dust-mass systematics (2020ApJ...892...66M);
beta 1.0 vs 2.0 changes dust mass by a factor 2 and T 25 vs 35 K by 1.2 (2016ApJ...819...82S).

Recommendation (from the evidence): if beta is not measured, adopt the value used by the closest analogue above,
state it, and propagate at least the 1.5-2.0 (galaxies, clumps) or 1.0-1.7 (disks, envelopes) spread.

## 2. Measured alpha and beta values reported in the pack

| object type | value | bands | bibcode |
|---|---|---|---|
| T Tauri disk (GM Aur), disk-averaged | alpha 2.7 ± 0.2 | 1.1 / 2.1 mm | 2020ApJ...891...48H |
| T Tauri disks (DS Tau, GO Tau, DL Tau), integrated | alpha 2.66, 2.58, 2.40 | 1.3 / 2.9 mm | 2020ApJ...898...36L |
| Giant disk V1094 Sco | alpha 2.09 ± 0.03 inner, 3.0 ± 0.2 gap, 2.3 ± 0.3 ring | B6 / B7 | 2018A&A...616A..88V |
| Disk arc vs ring (HD 34282) | alpha 2.48 ± 0.18 vs 3.11 ± 0.25 | B3 / B4 | 2026ApJ..1001..124M |
| Inner vs outer disk (HD 141569) | alpha 1.81 ± 0.15 vs 2.28 (+0.43/-0.29) | three data sets, joint MCMC | 2018ApJ...859..103W |
| Class 0/I envelopes, FAUST mean | beta 1.42 ± 0.06 (CALYPSO 0.78 ± 0.09) | 95 / 233 GHz | 2025A&A...700A.188C |
| Compact (disk) component of a Class 0 | alpha 2.2 ± 0.2 | 95 / 233 GHz | 2025A&A...700A.188C |
| Debris disk HD 107146 | alpha 2.42 ± 0.16, q 3.25 ± 0.09 | mm SED | 2015ApJ...798..124R |
| Debris ring Fomalhaut | alpha_mm -2.73 ± 0.13 (wavelength convention), q 3.50 ± 0.14 | 350-6600 um | 2017MNRAS.466.4201W |
| Debris disk HD 32297 | alpha 2.4 | sub-mm | 2020ApJ...892...99C |
| Protostar in a globule (HH 900) | alpha 2.2 ± 0.5 | four bands, adjacent B6/B7 | 2020MNRAS.496..394R |
| Massive protostellar outburst (NGC6334I) | mean alpha MM1 2.9, MM2 3.2, MM4 2.4 | ALMA bands | 2017ApJ...837L..29H |
| Sgr B2 compact sources | 62 with significant alpha, 33 with alpha > 2 | 3 mm in-band | 2018ApJ...853..171G |
| Background galaxy | alpha about 2.5, beta about 0.5 | B6 / B7 | 2020ApJ...894...76W |
| IMBH candidate | alpha 1.18 ± 0.65 | 231 / 266 GHz | 2017NatAs...1..709O |
| Symbiotic star R Aqr centre | alpha 1.88 | 1.3 / 0.45 mm | 2024A&A...689A.317G |
| Mira A | 1.71 ± 0.05 in Band 3, 1.54 ± 0.04 B3-B6 | B3, B6 | 2015A&A...577L...4V |
| LBV central object (ionized wind) | alpha 0.78 ± 0.05 | 9-349.5 GHz | 2017ApJ...841..130A |
| Galaxy nuclear regions | alpha -0.10 to -0.27 | 33 / 94.5 GHz | 2015ApJ...813..118M |
| Black hole X-ray binary | alpha 0.28 ± 0.02 | ALMA bands | 2024Ap&SS.369...18M |

Reading guide: alpha about 2 or below in dust means optically thick, scattering, or non-dust emission
(2018A&A...616A..88V, 2019ApJ...883...71C); alpha 3-4 is optically thin dust with ISM-like beta; negative or
below about 1 is free-free or synchrotron. Sign convention matters: 2017MNRAS.466.4201W quote a negative alpha_mm,
so check whether a paper uses S ∝ nu^alpha or S ∝ lambda^alpha (S ∝ nu^-alpha in 2017MNRAS.469L.123O).

## 3. Thresholds and settings

| setting | value | bibcode |
|---|---|---|
| Pixel mask | S/N < 2.5 in either band masked | 2018A&A...616A..88V |
| Pixel mask | > 3 sigma in both maps | 2017ApJ...841..130A, 2015ApJ...813..118M |
| Pixel mask | S/N > 15 in both bands | 2026ApJ..1001..124M |
| Pixel mask | S/N > 20 in both bands | 2018A&A...619A.161C |
| Source selection | abs(alpha) > 5 sigma(alpha) or sigma(alpha) < 0.1 | 2018ApJ...853..171G |
| uv range | 40-610 klambda | 2017MNRAS.467L.120M |
| uv range | 17-1260 klambda, 0.25" beam | 2018A&A...616A..88V |
| uv range | 20-360 klambda | 2019A&A...626A..36D |
| uv range | 6-150 klambda, 1"x1" beam, robust 1 | 2025A&A...700A.188C |
| Common beam | 50 mas circular | 2019ApJ...883...71C |
| Common beam | 0.13-0.16" | 2021A&A...652A..98G |
| Radial bins | 1 au annuli, i = 53.21 deg, PA = 57.17 deg | 2020ApJ...891...48H |
| Radial bins | 10 mas elliptical rings, dI = rms/(Omega_ring/Omega_beam)^0.5 | 2019ApJ...883...71C |
| Flux-cal error | 10% per band | 2020ApJ...891...48H, 2018ApJ...869..158F, 2018A&A...616A..88V, 2024A&A...689A.104D |
| Flux-cal error | 2.5% B3, 5% B6, 0.1 on alpha | 2025A&A...700A.188C |
| Flux-cal error | 15% | 2020MNRAS.496..394R |
| RJ correction | Delta alpha 0.06 (100 K), 0.20 (35 K) | 2019A&A...626A..36D |
| Envelope T(R) | 38 (L/Lsun)^0.2 (R/100 au)^-0.4 K; ±10 K keeps beta within 10% | 2025A&A...700A.188C |
| Debris planet-law index | alpha_pl = 1.84 ± 0.02 for 45 ± 5 K; beta_s = 1.8 ± 0.2 | 2017MNRAS.466.4201W, 2019AJ....158..162F |
| Grain size distribution | p = 3.5 (also 2.5, 1.5 tested), a_min 0.1 um | 2020ApJ...891...48H |
| Grain size distribution | p = 3.5, a_min 0.05 um, a_max iterated to < 5% change | 2019ApJ...883...71C |
| Visibility fit prior on alpha | uniform 0-4 | 2018ApJ...859..103W |
| Free-free jet model | 175 uJy at 32.5 GHz, alpha about 0.7, subtracted in uv | 2019ApJ...883...71C |
| Free-free index | -0.1 | 2019MNRAS.483.1624B, 2017ApJ...849...90S, 2020ApJ...895L...2N |
| Free-free index | -0.118 (extrapolated 3 mm to 870 um) | 2016ApJ...833L...6C |
| Non-thermal index | -0.85, tested -0.6 | 2015ApJ...813..118M |
| Thermal dust index | 3.8 fixed | 2017ApJ...849...90S |
| Thermal dust index | 3.75 (beta 1.75 on the RJ tail) | 2018ApJ...853..171G |

=== EVIDENCE PACK (spectral-index) ===
# Evidence pack: Spectral index and dust emissivity index maps (`spectral-index`)

Scope: spectral index between bands, dust emissivity beta, grain growth inferences

Built from 233 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `spectral index|\bbeta\b.*(?:dust|emissivity)|emissivity index|\balpha\b.*(?:mm|spectral)|grain growth`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- star_formation: 94
- protoplanetary_disks: 76
- high_z_galaxies: 46
- agn_and_quasars: 37
- milky_way_ism: 31
- astrochemistry: 25
- nearby_galaxies: 24
- stellar_physics: 15
- evolved_stars: 11
- debris_disks: 9
- galaxy_clusters_and_sz: 9
- exoplanets: 6
- transients: 3
- other: 3
- sun: 1

### Software named in the matched steps
- casa: 33
- emcee: 9
- gildas: 4
- radmc-3d: 3
- cigale: 3
- miriad: 3
- frankenstein: 3
- galario: 2
- magphys: 2
- eazy: 2
- dynesty: 2
- casa imfit: 2
- mcfost: 2
- diad: 2
- fargo: 2
- lifelines: 2
- make3fglxml: 1
- xclass: 1
- magix: 1
- cmcirsed: 1
- dsharp_opac: 1
- scipy curve_fit: 1
- casa uvmodelfit: 1
- dust_emissivity: 1
- statcont: 1
- uvplot: 1
- uvmem: 1
- fsps: 1
- prospector: 1
- parrot: 1
- tiny tim: 1
- mcfost-python: 1
- mcmc (unnamed): 1
- mge: 1
- hyper: 1
- scipy: 1
- protomidpy: 1
- moreli: 1
- la-compass: 1
- planetalp: 1

### Fitting methods (most common phrasings)
- Metropolis-Hastings MCMC; chi2 averaged with equal weight over the three frequencies: 1
- Same MCMC; most probable values and 95% credible regions: 1
- Modified blackbody fit; Monte Carlo simulations of synthetic photometry for statistical error: 1
- chi-square minimisation, 1 sigma errors following Lampton et al.: 1
- Same MCMC procedure as step 2: 1
- Grid comparison by eye/best-fit; no formal statistic stated: 1
- Greybody fit with dust luminosity and T_dust free: 1
- weighted power-law fit: 1
- maximum likelihood: 1
- Mostly by-eye, MAGIX Levenberg-Marquardt for some: 1
- M* = C L^alpha power law per redshift bin: 1
- chi2 best fit; parameters are likelihood-weighted means and standard deviations: 1
- curve_fit least squares: 1
- least-squares Planck fit: 1
- Dynamic nested sampling with dynesty; posterior medians and 16/84 percentiles: 1
- MCMC, flat prior: 1
- MCMC; sampler not stated: 1
- emcee affine-invariant MCMC, several hundred walkers and iterations; best values are the mode of marginalized posterior…: 1
- Power law F_nu ∝ nu^alpha; fitting method not stated: 1
- MCMC with emcee; posterior medians and 16/84 percentiles: 1
- analytic inversion over temperature grid; error propagation: 1
- Chi2 comparison and F-test: 1
- MCMC (Foreman-Mackey 2013), uniform priors: 1
- MCMC with emcee: 1
- Prospector-beta with nested sampling dynesty; Chabrier IMF, 7-bin SFH, two-component dust: 1
- Uniform priors except uniform in cos i and log-uniform for dust mass and alpha; ranges in Table 2: 1
- MCMC; priors not stated: 1
- chi2 MAP power-law then emcee sampling of index; 68% binomial intervals: 1
- MCMC; log-likelihood of unresolved photometry plus resolved 870 um flux: 1
- logNormal with alpha=1.3, wsmooth=1e-4 preferred: 1
- chi2 minimisation: 1
- Minimize squared residuals per pixel: 1
- emcee MCMC linear fit; priors not stated: 1
- Manual iterative adjustment, no sampler: 1
- emcee MCMC; upper-limit likelihood following Shangguan 2018: 1
- Hyperparameter and geometry priors (Table 2) sampled in 5000 fits; 16-84th percentile as 1 sigma: 1
- Grid search, not MCMC or Levenberg-Marquardt, due to computational cost: 1
- Least squares; no priors: 1
- Least-squares, amplitudes free: 1
- MCMC over 6 parameters (center, cos i, PA, alpha, gamma): 1

### Validation checks used
- Jeffreys priors gave negligible differences; uniform-disk fit consistent with uvmodelfit: 1
- Compared reduced chi2 of the models: 1
- high/low-confidence classes; completeness not quantified: 1
- comparison with Robitaille/Zhang models, HOPS Orion sources, and MUSTANG Orion data: 1
- Compared with optically thin models and Arp 220 SED; L_IR differs by ~0.1 dex: 1
- ALMA flux recovery compared with APEX (~70%); fluxes treated as lower bounds: 1
- Dust flux agrees with Kepley et al. 2016: 1
- Compared with GTD predicted from metallicity (~400-600): 1
- BIC preference keeps the Gaussian profile for smooth disks: 1
- Cavity size degenerate with other parameters, differs by a few au: 1
- Alternative beta from 3mm/2mm fluxes gives N(H2) factor ~3 lower: 1
- Confirmation with APEX [CII], ATCA, SMA, Z-Spec, VLT for five sources: 1
- large frequency coverage deemed robust against systematics: 1
- 17 GHz excluded from index maps due to artifacts: 1
- free spectral index check gave no significant change: 1
- good fit to broadband SED except mid/far-IR: 1
- Reduced chi-square over HIFI band: 1
- Stellar mass functions agree with Mortlock+15 and Davidzon+17 above limits: 1
- Varied T (15-35 K) and beta (1.5-2.0) to assess systematics: 1
- Compared with Kneissl+19 SFRs and CIGALE with cmcirsed dust model: 1
- Compared with Pinilla et al. 2014 disk-averaged index: 1
- Alternative formulae from Birnstiel 2018 and Zhu 2019 give similar results; McClure temperature structure tested: 1
- Applied to Fomalhaut, predictions consistent with ALMA fluxes: 1
- Compared with Perez-Beaupuits 2018 cold component of 37 K and mass 1e6 Msun: 1
- Chance probability of a background submillimetre galaxy ~0.1%: 1
- Prior-only run; robustness tests varying gNFW slopes and centroid; residual dirty images: 1
- Compared Td from Gordon 2014 and Utomo 2019 models; nearly linear: 1
- compared with Ricci et al. q and collisional cascade q=3.51: 1
- Removal of zero-spacing imaging artefacts justifies beta ~1.2: 1
- Compared expected high-z galaxy counts (~0.5 in field): 1
- Different walker starting positions tested; residual maps and visibility profiles inspected: 1
- Scale-height test for PZ Tel changes flux by <~10%; comparison with Ricci2017b limits: 1
- Consistent within a factor ~4 with Rivilla et al. 2017: 1
- Checked line-free channels for residuals and no overcleaning: 1
- Tested alpha_NT=-0.6; AGN contribution <3% estimated: 1
- Compared alpha values with expectations for dust vs free-free/synchrotron: 1
- Compared with 190 GHz spectral index of Tsukagoshi et al.: 1
- Compact emission consistent with 45 GHz continuum: 1
- beta=2 alternative tested: 1
- Checked optically thin or free beta give similar L_IR: 1

### Key parameters and settings (bibcode: value)
- 2018ApJ...859..103W: Free: 345 GHz flux, spectral index, disk center, width; uniform priors flux 0.01-50 mJy, disk 0.1-300 au, index 0-4
- 2018ApJ...853..171G: alpha kept if |alpha|>5 sigma(alpha) or sigma(alpha)<0.1
- 2017ApJ...844..123F: Redshift fixed (QSO z for composites, 2.5 otherwise)
- 2020MNRAS.496..394R: nu0=230.61 GHz, kappa0=0.8 cm2/g, beta=1.0, gas-to-dust 100, r0=690 AU, 15% flux uncertainty
- 2016ApJ...833L...6C: kappa_870=0.9 cm2/g, beta=1.7; Tdust 33 K (Clouds C, W), 20 K (Cloud E)
- 2024ApJ...966...59S: Nuker priors: log10 alpha U(0,2), beta U(0,10), gamma approx uniform (-3,2); point flux U(0,1) mJy
- 2024ApJ...966...59S: beta in [1.0,1.2], H100 in [5,15], Rin between sublimation radius and mm cavity; grains 0.01-1000 um
- 2024A&A...691A.180F: beta=1.7, kappa=0.899 at 230 GHz, mu=2.8, gamma~3000
- 2013ApJ...767...88W: Retain dust temperatures with probability >10%
- 2017ApJ...835L..35M: 13 new sources added to the 3FGL model
- 2013Sci...341..630Q: Mdot 2e-9 Msun/yr, alpha0 0.0007, Rc 60 AU, Md 0.04 Msun
- 2014ApJ...787..112C: Source sizes 10'' hot core/compact ridge, 30'' plateau, 180'' extended ridge
- 2020ApJ...892...66M: Stellar masses from MAGPHYS using 0.37-8.0 um photometry plus 1.2 mm flux
- 2020ApJ...892...66M: beta=1.8; kappa=0.0431 m^2/kg at 352.6 GHz
- 2025A&A...698A.204H: beta = 1.8, dust temperature free
- 2020ApJ...891...48H: P.A. = 57.17 deg, i = 53.21 deg, 1 au bins
- 2020ApJ...891...48H: p = 3.5, 2.5, 1.5; a_min = 0.1 um; Td = 30 K (B40), 18 K (B84)
- 2021A&A...656A..46M: kappa0=0.1 cm2/g at 250 GHz; T_e=1e4 K; SFR=2.5 Msun/yr
- 2019A&A...628A.100D: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05)
- 2024ApJ...966...51G: u_nu = 8.65e-13 (Td/18 K)^(4+beta) erg cm^-3, beta=1.8
- 2014ApJ...795L..25R: beta = 1.2 ± 0.1 chosen
- 2015ApJ...798..124R: a_min ≈ 1.7 μm (blow-out), a_max = 2 cm
- 2015ApJ...798..124R: model image 2048x2048 pixels of 0.015''; flux scaled as nu^(2+beta), beta=0.4
- 2019MNRAS.488.1005P: slope -1; r_c = 0.4 or 0.04 R_Hill; minimum radius r_c/10; aspect ratio 0.1; 2 deg inclination to planet orbit
- 2019MNRAS.488.1005P: dust size 1 um to 1 cm, exponent -3.5; opacity 2.3 cm2/g at 1.3 mm
- 2020A&A...644A..84M: flux 0.1 Jy at 99.0 GHz
- 2024ApJ...963....1O: beta = 1.8, kappa_500um = 0.051 m^2/kg
- 2018ApJ...852..122H: nterms=2, robust=0, i=5 deg, PA=152 deg
- 2018ApJ...852..122H: kappa=3.3 cm2/g at 290 GHz; gas-to-dust 100; T=15 K for Q
- 2019ApJ...877L..25M: T80au = 360 K
- 2019MNRAS.482.3135B: 100 walkers, 500 steps, 100-step burn-in
- 2021A&A...653A.117B: beta constrained to 0-2 to bound T_SED
- 2017MNRAS.468L..87C: T_dust <= 14 K upper limit from PACS 160 um
- 2024ApJ...974..102S: alpha = 1.05, w_smooth = 1e-4
- 2024ApJ...974..102S: zeta = 0.02, L* = 0.25 Lsun, T_d=[zeta L/(4 pi sigma r^2)]^(1/4)
- 2025ApJ...993..120H: kappa = (nu/100 GHz)^beta, beta=1 giving 2.25 cm2/g
- 2014ApJ...785..111W: Td=35 K, beta=1.8
- 2017ApJ...841..110S: Deconvolved half-power size ~2.3" at 3.3 mm (radius ~2.6e16 cm)
- 2018Sci...362.1034D: Tdust 50–100 K for W2246, 25–50 K for companions/extended
- 2014ApJ...796....1T: Td = 10-42 K, beta=0.5, kappa0.9mm=0.053 cm2/g, d=140 pc
- 2020ApJ...902...78R: beta = 2; mask lambda_rest < 50 um
- 2021AJ....161..238W: parallel-tempered, 2 temperatures, 50 walkers; 2000 iterations (F814W), 1000 (ALMA); burn-in 100
- 2021AJ....161..238W: Free: i, H0, dust mass, gamma, beta, p, alpha, Rc; fixed distance 147 pc, Rin 1 au, Rout 191 au
- 2020ApJ...895..135K: alpha = (Gamma+2/3)/(8/3) ≈ 0.87 for Gamma=1.65
- 2019AJ....158..162F: beta_s=1.8±0.2, alpha_Pl=1.84±0.02
- 2018A&A...619A.161C: d = 136 pc, T_dust = 15 K, kappa = 10 cm2/g at 1000 GHz, beta = 1
- 2018A&A...619A.161C: S/N>20 in both bands
- 2016ApJ...826..112S: beta = 2
- 2020ApJ...898...10T: T_d = 30-100 K; S_0.9mm = 1.40 Jy
- 2019PASJ...71...68K: L(1-100 keV)=1.3e43 erg/s, Gamma 2.31, alpha ≈1.1
- 2024A&A...689A.104D: alpha={1.05,1.2,1.3}, wsmooth={1e-1,1e-4}, Rmax=5.0", p0=1e-35, 300 radial points
- 2024A&A...689A.104D: 10% flux calibration uncertainty
- 2014ApJ...787...42C: kappa=2.3 cm2/g at 230 GHz, beta=0.4, d=145 pc
- 2014ApJ...796...82Z: 0.8" circular beam
- 2020A&A...642A.155Z: radio spectral index alpha = -0.8
- 2020ApJ...898...36L: flaring angle 0.02, Td ~15 K at 50 au
- 2019A&A...624A...7V: Free parameters per region: Rin, Rout, dust mass, H100au; beta fixed to 1.1; p = -1
- 2019A&A...624A...7V: Small grains 0.01-0.5 um, large grains 10-1000 um
- 2019ApJ...886....6T: T_dust = 43 K (L/Lsun)^0.25; L=1 Lsun if unmeasured
- 2019ApJ...876...99S: beta fixed at 1.6
- 2020A&A...635A...2S: Td = 20 K (no counterpart), 50 K (IR or radio counterpart), 100 K (hot core)
- 2019ApJ...871..170M: Rgd=150, beta=1.5, Td=35 K, D=3.5 Mpc
- 2024ApJ...971..129C: Rmax=2.1", N=300, p0=1e-15 Jy^2, alpha=1.3, wsmooth=0.1
- 2013ApJ...770...13W: Td=47 K, beta=1.6
- 2016A&A...586A..70L: 1 arcsec circular aperture for A and B
- 2015A&A...577A..30A: Omega_c fixed to radius 11.4 arcsec; priors Td 25 K, nu0 4.3 THz, beta 2.0
- 2024ApJ...968....9W: T_dust=47 K, beta=1.6; T_ex=100 K for C+
- 2020ApJ...895L..46L: h/r = 0.07, alpha = 1e-3 and 1e-4
- 2018ApJ...865...37M: Mdot fixed at 7.8e-9 Msun/yr; alpha varied 0.0001-0.01; Rwall 25-40 au; mid amax 1 mm-2.5 cm; eps_atm 0.001-0.8; Rdisk 150-300 au
- 2016A&A...596A..75S: kappa at 240um 5.17 cm2/g; 100um band excluded from MBB fit
- 2020ApJ...890...76N: Apertures of 27" (prestellar) and 20" (protostellar) radius
- 2025ApJ...993...90S: 1000 iterations, 32 walkers, init from SpM cos i and PA
- 2015ApJ...801...82H: Tdust fixed to 100 K or 20 K
- 2019ApJ...882..160Q: epsilon tested at 1.0, 0.5, 0.1, 0.01, 0.001; alpha 0.00001–0.02
- 2018ApJ...866..141K: radius 21 au, Omega = 2.4e-12 sr, T_bg = 2.7 K
- 2018ApJ...867L...6B: mass-loss 5e-5 Msun/yr, Te 6000 K, expansion velocity 30 km/s
- 2025ApJ...993...85Y: PA sampling 10 deg; 3 sigma threshold
- 2025A&A...700A.188C: nu1 = 95 GHz, nu2 = 233 GHz; 0.1 systematic error from flux calibration
- 2015ApJ...811L...3T: kappa_ISM,850um = 4.84e-3 g^-1 cm^2, beta = 1.8
- 2015ApJ...809...93D: 1 mm particles; initial dust-to-gas 0.9%; T = 221 (r/AU)^-1/2 K; 1 Msun star
- 2019A&A...622A..75L: Initial H100=10 au, beta=1.1, Mdust=2e-3 Msun, Lambda=0.2, fLGP=0.85, i=36 deg; R_out,LGP=200 au
- 2019MNRAS.483.1624B: beta=1.49, free-free index -0.1
- 2016ApJ...816...37V: L_FIR 42.5–122.5 um; L_TIR 8–1000 um rest-frame
- 2020ApJ...896...35J: alpha_d upper limit 3.6, alpha_ff upper limit 2
- 2025ApJ...989....6K: Mpebble = mass in grains 0.1 mm-10 cm; R90 = radius containing 90% of flux; alpha_mm from B6 and B7 fluxes
- 2024ApJ...973...42B: kappa_1.9mm = 0.6 cm2/g scaled from 0.9 at 1.3 mm with beta=1
- 2017ApJ...837..174O: kappa = 0.008 cm2/g at 1.2 mm, beta = 1.8; mean particle mass 3.83e-24 g
- 2018ApJ...854...97D: T_dust=47 K, beta=1.6, kappa=0.77 (nu/352 GHz)^beta cm^2/g
- 2020ApJ...896..110L: kappa_98.5GHz = 0.235 cm2/g, beta = 1.5
- 2024BSRSL..93..601H: Tdust = 21 K, beta = 1.5 and 2.0
- 2018ApJ...857...87L: Grid 1024x768, disk 10-500 au, dust grain size 0.15 mm, h=0.05(r/r0)^0.25
- 2017MNRAS.467L.120M: matched uv range 40 to 610 k lambda
- 2025ApJ...984L..57O: Rc=120 au, gamma=0.8, Mdisk=0.1 Msun, alpha=1e-3, dust-to-gas 0.02, Mstar=0.8 Msun
- 2025ApJ...990...59Y: M=20 Msun, L=1.4e4 Lsun, alpha_floor=0.01, f_dg=0.01
- 2018MNRAS.473..879P: beta=1, kappa=0.023 cm2/g, T=20 K, d=414 pc
- 2016Natur.535..258C: alpha = ln(F232.6/F218.0)/ln(218.0/232.6)
- 2018MNRAS.475.5322S: disk radius 90 AU, H~40 AU
- 2025ApJ...984L..19Y: a_rep = 0.6 mm from a_max = 1.4 mm; X_CO = 7e-4; alpha = 1e-3, 2e-4, 4e-5
- 2016ApJ...828...46A: T_dust = 20 K; kappa = 10 cm^2/g at 1000 GHz; beta = 1
- 2016ApJ...826...26T: T_d = 10 K; beta = 1.9; kappa(0.87mm)=2.1e-2 cm2/g; d = 140 pc
- 2019A&A...628A..85V: beta=1, kappa_1000GHz=10 cm2/g, T=20 K (30 K test), d=414 pc
- 2019A&A...623L...8B: kappa = 2.63 at 263 GHz, beta = 1, Td = 20 K for most sources
- 2017ApJ...837L..29H: spectral index averages MM1=2.9, MM2=3.2, MM4=2.4
- 2016ApJ...822...80S: beta=2, optically thin/thick transition at 100 um, CMB included, ignore data shortward of rest-frame 50 um; free: Tdust and dust mass
- 2016ApJ...819..134B: alpha = 1e-4; (H/R)_p = 0.1; Sigma ∝ R^-1; dust-to-gas 1%
- 2017Sci...355.1285N: alpha 1.5-2.5, beta 1.2-2.0, dust T 25-45 K
- 2016PASJ...68...43K: tau_unp = 9.5 (R/1AU)^-0.4
- 2018AJ....156..239Z: kappa = 0.015 cm2/g, beta = 1.5, Td = 25 K
- 2019NatAs...3..314L: Tmid(r>0.1")=100 K x sqrt(0.1"/r); gamma=1.5; H/r=0.1; kappa 2.2 cm2/g at 1.3 mm
- 2019MNRAS.482..698C: kappa_1.3mm = 0.023 cm2/g (beta=1), d = 140 pc, T_dust = 20 K
- 2017ApJ...840..101C: beta=1.8; alpha=2.5 if <4 far-IR points; T_dust=35 K if <2 far-IR points
- 2018ApJ...860...77E: free parameters: turnover wavelength, free-free and dust fluxes at ALMA wavelength
- 2019A&A...626A..36D: Td 100 K (hot cores), 35 K (starless): Delta alpha 0.06 and 0.20
- 2018A&A...616A..88V: pixels with S/N < 2.5 masked
- 2019A&A...623A.150V: Mdisk = 100 F d^2/(kappa B(Tdust)), kappa=10 cm2/g at 1000 GHz, beta=1, Tdust=20 K
- 2019MNRAS.482L..29D: Briggs robust 0.5
- 2018A&A...610A..24F: T=190(R/100au)^-0.55, Sigma_gas=7.5(R/100au)^-1, grain size 1 mm, alpha 0 or 1e-4
- 2019ApJ...883...71C: 175 uJy at 32.5 GHz, spectral index 0.7, size 22 mas


### Assumptions (bibcode: value)
- 2018ApJ...859..103W: Flux follows a single power law in frequency
- 2018ApJ...853..171G: beta=1.75, kappa(3.1mm)=0.0018 cm2/g per gram gas (Ossenkopf1994a), gas-to-dust 100, d=8.4 kpc
- 2017ApJ...844..123F: Constant dust temperature, local thermal equilibrium
- 2020MNRAS.496..394R: 15 K for compact core; 45 K for extended emission
- 2016ApJ...833L...6C: Dust contribution at 3mm negligible for beta=1.7
- 2016ApJ...833L...6C: LMC X_CO = 4.7e20 cm-2 (K km/s)-1; R31=7.4
- 2024ApJ...966...59S: Dust model of Birnstiel et al. 2018; well-mixed gas and dust
- 2024A&A...691A.180F: Td = CH3OH Tex (gas-dust coupling)
- 2013ApJ...767...88W: Greybody beta=2, T_dust distribution of known-z sample (mean 37.2+-8.2 K) as prior
- 2017ApJ...835L..35M: fixed spectral index 2.7
- 2013Sci...341..630Q: amax small 0.25 um, big 1 mm
- 2014ApJ...787..112C: kappa_1.3mm=0.42 cm2/g, beta=2, dust-to-gas 0.01, NH2=2.5e24 cm-2 for dust opacity
- 2020ApJ...892...66M: T_dust = 25 K mass-weighted
- 2020ApJ...892...66M: GDR = 100 at solar metallicity, 12+log(O/H)=8.67; metallicity from mass-metallicity relation
- 2025A&A...698A.204H: Chabrier IMF; SFR_IR = 1.40e-10 L_IR
- 2020ApJ...891...48H: Distance 159 pc; ~10% flux calibration uncertainty per band
- 2020ApJ...891...48H: Midplane temperature from Macías et al. 2018; DSHARP opacities; gas-to-dust ratio 100 for Toomre Q
- 2019ApJ...875...55W: Rayleigh-Jeans limit, T_obs substituted for T_B
- 2021A&A...656A..46M: Beta=1.9 emissivity law
- 2017NatAs...1..709O: Distance 8.3 kpc
- 2019A&A...628A.100D: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected
- 2017MNRAS.466.4201W: alpha_pl=1.84±0.02 (dust 45±5 K), beta_s=1.8±0.2
- 2014ApJ...795L..25R: T_dust = 20 ± 1 K
- 2015A&A...577L...4V: Distance 92 pc
- 2015A&A...577L...4V: Ionized cavity gas temperature T=10^4 K
- 2020ApJ...894...76W: Rayleigh-Jeans regime, S_nu ∝ nu^(2+beta)
- 2017Natur.541...58C: sub-mm spectral index of 4
- 2015ApJ...798..124R: optically thin, Rayleigh-Jeans emission; rho = 1.2 g/cm3
- 2015ApJ...798..124R: axisymmetric, geometrically and optically thin disk; constant dust opacity across disk
- 2019MNRAS.488.1005P: Disc inclination 30 deg from face on (beta Pic b 85 deg)
- 2019MNRAS.488.1005P: Star and planet luminosities heat dust; anisotropic scattering included
- 2020A&A...644A..84M: Td = 150 K, beta = 2.0, k0 = 0.8 cm2/g at 220 GHz, mu = 2.33, gas-to-dust 100
- 2024A&A...689A.317G: Continuum constant within each spectral window (spectral index 2, <1% variation)
- 2024ApJ...963....1O: dust temperature 25 K
- 2015ApJ...813..118M: alpha_NT = -0.85; free-free optically thin; negligible AME and thermal dust
- 2014Sci...345.1584B: kappa=0.01 cm2/g at 230 GHz, beta=1.0, mu=2.8 per H2, T=150 K, all continuum from dust, distance 8.34 kpc
- 2018ApJ...852..122H: M* = 0.88 Msun, distance 59.5 pc
- 2018ApJ...852..122H: Vertically isothermal mm dust; ISM beta upper limit 1.7
- 2019ApJ...877L..25M: beta=1, kappa150=0.59 cm2/g, gas-to-dust 100, Tdust ∝ r^-0.4
- 2019MNRAS.482.3135B: beta=1.8; kappa_850=0.077 m^2/kg
- 2021A&A...653A.117B: mu=2.8, dust-to-gas R=0.01, kappa0=0.9 cm2/g at 230 GHz, d=393 pc, no free-free at 246.2/333 GHz
- 2017MNRAS.468L..87C: kappa160 = 1.6 m2/kg, beta = 1.7
- 2024ApJ...974..102S: Same geometry assumed for whole disk, azimuthal symmetry
- 2024ApJ...974..102S: optically thin emission; p = 2.5 or 3.5
- 2025ApJ...993..120H: gas-to-dust ratio 100; d=156 pc; optically thin
- 2014ApJ...785..111W: dust-to-gas ratio 0.0052 (Draine 2007); H2/HI ~2
- 2017ApJ...841..110S: Optically thin dust; 10% of stellar flux reddened to 900 K for disk case
- 2018Sci...362.1034D: beta=1.8, kappa(850µm)=0.0484 m2/kg, gas-to-dust 100, alpha_CO,MW=4.6 and ULIRG=0.8
- 2015ApJ...812..126C: Flux scale C13scale: 3.5 Jy at 345 GHz band 7, SPIRE for band 9
- 2014ApJ...796....1T: Gas-to-dust mass ratio of 100, dust opacity from Hildebrand 1983 with beta=0.5
- 2020ApJ...902...78R: kappa = 0.015 (nu/250 GHz)^beta m^2/kg, beta=2; gas-to-dust ratio 100; Kroupa IMF; flat LCDM H0=68.1
- 2025ApJS..278...45F: AID20 assumed z=2.0; AID60 assumed z=9.0
- 2021AJ....161..238W: Single species amorphous olivine, non-porous grains, a = 0.03-1000 micron, 70 log bins
- 2019MNRAS.488..191G: Distance 1.06 kpc; E(B-V)=0.30
- 2020ApJ...895..135K: Uniform gas density distribution
- 2018MNRAS.475..448T: kappa=0.1 cm2/g (nu/THz)^beta, includes gas-to-dust 100
- 2018ApJ...853..195W: radio spectral index alpha = 0.8
- 2026ApJ..1004..126K: spectral index does not change with time
- 2020ApJ...891...80M: Stokes U unconstrained so |Q/I| is a lower limit
- 2018A&A...619A.161C: Optically thin emission; T_dust = 15 K; kappa with beta=1
- 2018ApJ...863...19A: Optically thin, Tdust=20 K, kappa(850um)=0.035, beta=1, gas-to-dust 100 (mass)
- 2018ApJ...863...19A: LTE, gas T = dust T = 20 K, kappa(850um)=0.035, beta=1, gas-to-dust 100, mean molecular weight 2.37
- 2016ApJ...826..112S: Uniform source emission with single Tdust and lambda0
- 2020ApJ...898...10T: gas-to-dust 100; kappa_250um=0.1 cm2/g, beta=1.0 giving kappa_0.9mm=0.028; d=140 pc
- 2019PASJ...71...68K: Nucleus distance R > 60 pc; gas-phase C and O abundances 3e-4 and 5e-4
- 2024A&A...689A.104D: azimuthally symmetric, geometrically thin, optically thick disk
- 2025ApJ...994..225N: Td = 20 K, kappa230GHz = 0.00529 cm2/g (beta=2), gas-to-dust 100, D = 138 pc, tau<1
- 2012ApJ...752L..30W: beta = 1.5; dust T = 35 K (SMG), 60 K (quasar); cosmology (0.73, 0.27, 0.71)
- 2017A&A...602L..10O: Tb ~ Tgas(tau=1) for slowly varying temperature; free-free H- opacity
- 2019PASJ...71..109H: Optically thin single-temperature dust; Kroupa IMF 0.1-100 Msun; dust emission star-formation powered (upper limit on SFR)
- 2014ApJ...787...42C: dust-to-gas ratio 0.01
- 2024ApJ...961..120C: S_nu ∝ nu^alpha; alpha=-0.8 for GOODS-N and for single-frequency lensed SMGs; H0=70, OmegaL=0.7, Om=0.3
- 2020ApJ...898...36L: Td equals midplane irradiated temperature; absorption-dominated opacity
- 2020ApJ...898...75I: H2 dominates gas mass in CND; hydrogen nuclei fraction 71%; no dark matter
- 2019A&A...624A...7V: Gas-to-dust ratio 100; astronomical silicates; dn(a) ∝ a^-3.5 da
- 2019ApJ...886....6T: D=400 pc; kappa0.87mm=1.84 cm2/g; beta=1 extrapolation to 9 mm; dust-to-gas 1:100
- 2019ApJ...876...99S: kappa_125um = 18.75 cm2/g; Salpeter IMF with Kennicutt 1998 SFR
- 2020A&A...635A...2S: kappa = 0.131 cm2/g at 87.6 GHz (Ossenkopf & Henning, beta = 2), gas-to-dust 100, D = 1.3 kpc, mu = 2.3
- 2019ApJ...871..170M: Thermal dust, optically thin; hydrogen dominated by H2
- 2024ApJ...971..129C: Axisymmetric emission; i=29 deg, PA=45.7 deg
- 2025A&A...699A.369V: Td=40 K, kappa(880um)=1.23 cm2/g, beta=2, dust-to-gas 3.5e-3
- 2017ApJ...835L..13S: excess emission is thermal dust; free-free negligible
- 2015A&A...577A..30A: kappa=0.1(lambda/0.3mm)^-beta cm2/g, dust-to-gas 0.01
- 2024ApJ...968....9W: dust-to-gas ratio 100, molecular fraction 0.75
- 2020ApJ...895L..46L: gas-to-dust ratio 100; gamma = 0.1; max particle size 0.1 mm
- 2018ApJ...865...37M: Dust-to-gas ratio 0.01; distance 160 pc; inclination and PA fixed from step 3
- 2016A&A...596A..75S: T~40K for ALMA-only dust mass
- 2020ApJ...890...76N: Gas-to-dust ratio 100; kappa 1.85 cm2/g
- 2017ApJ...849...90S: Fixed indices alpha_s=-0.9, alpha_ff=-0.1, alpha_d=3.8
- 2025ApJ...992..103Z: beta=1.5; dust opacity 1 cm2/g at 230 GHz; dust temperature = gas temperature (~100 K)
- 2015Natur.522..455C: Meurer relation typical of z<3; SMC-like dust model
- 2017MNRAS.469L.123O: S_nu ∝ nu^-alpha
- 2015ApJ...810L...7V: T_dust 60 K uniform; 200 K and 24 K tested
- 2015ApJ...801...82H: kappa=0.1 cm2/g at 250 um, gas-to-dust 100, D=420 pc
- 2026ApJ..1001..131C: Photon index 1.4 for X-ray; radio spectral index -0.8
- 2019ApJ...882..160Q: Draine astronomical silicates and graphite, dust-to-gas 0.0065, n(a) ∝ a^-3.5 from 0.005 μm, large grains 1 mm within 0.1H
- 2018ApJ...866..141K: kappa = 0.1 (nu/1e12 Hz)^beta cm2/g; 7.3 mm emission is thermal dust with no free-free; D = 137 pc
- 2017ApJ...835...98U: Literature counts scaled to 1.1 mm with modified blackbody beta=1.5, T=35 K, z=2.5
- 2020AJ....159...62C: kappa=0.015 cm2/g, beta=1.2, Td=50 K (30 K for source B), dust-to-gas 100, D=2.3 kpc
- 2018ApJ...867L...6B: Isothermal ionized wind with Ne ∝ r^-b_d; Te up to 12000 K considered
- 2025ApJ...993...85Y: arc coplanar with outer ring (same inclination and PA)
- 2015ApJ...811L...3T: Dust temperature from Genzel+15 scaling relation
- 2019MNRAS.490.5300D: Gamma=20, theta_max=9 deg, alpha=1.7 in R band
- 2015ApJ...809...93D: Schmidt number Sc=1; Epstein drag; no dust feedback
- 2015ApJ...812...27A: dust kappa(1 THz)=10 cm2/g, beta=1.46, Tc=28 K, gas/dust=100, d=140 pc
- 2019A&A...622A..75L: 75% silicate + 25% carbon, Mie opacities, a^-3.5 size distribution, amin 0.01 um, amax 3 mm (LGP), 2 um (SGP); gas-to-dust 100 initially
- 2019MNRAS.483.1624B: Only dust and free-free contribute; synchrotron neglected (<=4 per cent of Band 6 oversubtracted)
- 2016ApJ...816...37V: Td=47 K, beta=1.6, tau<<1 at lambda>40 um; Kroupa IMF; emission powered by star formation
- 2019A&A...632A..61G: Dust spectral index alpha ~3-4 in dust-dominated CND regions to estimate dust fraction at S1
- 2025ApJ...989....6K: Optically thin emission, T=20 K for observed dust masses
- 2024ApJ...973...42B: T_dust = 30 K, optically thin, d = 125 pc
- 2014ApJ...792...34O: Dwarf-galaxy T_dust=27.6 K, beta=1.5; Salpeter IMF; cosmology (0.3,0.7,0.7)
- 2017ApJ...839...99P: d = 137 pc, kappa(1.3 mm) ~3 cm2/g, T = 20 K
- 2017ApJ...839...99P: Mid-plane temperature from van der Marel et al. 2015 models
- 2017ApJ...837..174O: Dust temperature 100 K (70-130 K), gas temp equals dust temp
- 2018ApJ...854...97D: Single modified blackbody, T_dust=47 K, beta=1.6; Planck15 cosmology
- 2020ApJ...896..110L: Gas-to-dust ratio 100
- 2019MNRAS.484.4239R: S proportional to nu^alpha
- 2025NatAs...9..526O: M*=2.4 Msun, T=30 K, Sigma_g=0.2 g cm-2, zeta_CR=1e-17 s-1, HCO+ dominant ion, H_dust~H_gas, r~200 au, H~20 au
- 2024BSRSL..93..601H: gas-to-dust ratio 100; kappa = 10 (nu/1.2 THz)^beta; distance 3.26 kpc
- 2015ApJ...810...91H: kappa_d(125 um)=2.64±0.29 m^2/kg, beta=1.5, T_dust=30-40 K
- 2018ApJ...857...87L: Isothermal T(r)=24.1(r/r0)^-0.5; viscosity nu=alpha c_s h
- 2017MNRAS.467L.120M: Rayleigh-Jeans; free-free modelled as point sources for Main and SE
- 2019ApJ...880...15K: T_dust = 25 K mass-weighted
- 2019ApJ...880...15K: beta = 1.8, constant gas-to-dust ratio
- 2025ApJ...984L..57O: Dust-to-gas ratio of 0.02 chosen to match the 1.3 mm flux of Elias 2-24
- 2025ApJ...990...59Y: a_max=0.1 um at the disk outer edge
- 2018ApJ...859...21A: Md = 100 Mdust, Td = 20 K (following Rafikov 2017)
- 2018MNRAS.473..879P: gas to dust mass ratio of 100
- 2018PASJ...70...65U: Fluxes scaled to 1.1 mm with modified blackbody, beta=1.5, T=35 K, z=2.5
- 2020ApJ...895L...2N: free-free spectral index -0.1
- 2018ApJ...867...48I: Synchrotron spectral index -0.7
- 2026A&A...705A.100E: Clump kappa300=10 cm2/g, beta=2, gas-to-dust 100; non-deconvolved sizes for surface density
- 2018MNRAS.475.5322S: beta=1, kappa0=0.035 g cm-2 at 850 um, Tdust=90 K
- 2020A&A...640A..19T: Optically thin: Delta = 0
- 2016ApJ...828...46A: T_dust=20 K, median for Taurus disks; not scaled with L*
- 2016ApJ...826...26T: Optically thin, uniform dust temperature
- 2016ApJ...819...82S: kappa_d(125 um)=1.875 m2/kg, beta=1.5, T_dust=30 K
- 2020ApJ...890..129K: Rayleigh-Jeans limit, constant dust temperature, beta 1-1.8
- 2019A&A...628A..85V: Optically thin dust emission
- 2019A&A...623L...8B: Gas-to-dust ratio 100
- 2017ApJ...836L...2B: beta = 1.5, T_dust = 45 K
- 2020ApJ...896..127K: Tdust = 150 K (75-300 K); D = 5.0 kpc; kappa=0.1(250um/lambda)^beta cm2/g, beta=1.85; gas-to-dust 100; starless cores at 15 K
- 2017ApJ...846...70P: inclination 20 deg; distance 140 pc
- 2016ApJ...822...80S: calibration uncertainty added: 7% PACS, 10% others
- 2021A&A...649A.139I: Turnover frequency of 100 GHz
- 2016ApJ...819..134B: Dust size distribution dn ∝ a^-3.5 da between 0.1 um and 5.3 mm; grain density 3 g cm^-3
- 2018A&A...616A..56A: optically thin, Rayleigh-Jeans
- 2016PASJ...68...43K: alpha=1e-3, beta=1.5, M*=1 Msun; constant opacity; gas and dust gap widths similar (weak dust filtration)
- 2018AJ....156..239Z: Distance 200 pc, dust-to-gas 100, optically thin emission (so masses are lower limits)
- 2018ApJ...856L..12N: alpha=1.5, beta=1.5, T_dust=35 K
- 2018ApJ...859..111H: Deprojected disk is circular
- 2019MNRAS.486.4114R: kappa = 0.1 (nu/1e12)^beta cm2/g, beta = 1, Tdust = 10 K, gas-to-dust 100, d = 410 pc
- 2017Natur.545..457D: Tdust=47 K, beta=1.6, CMB-corrected, gas-to-dust ~100, LCDM H0=70, Om=0.3
- 2019NatAs...3..314L: gas-to-dust ratio 100; Tatm/Tmid = 2; beta = 1; gas and dust temperatures equal
- 2018MNRAS.478.2505I: Teff ~1e4 K for the bloated protostar; free-free spectral index 1
- 2017ApJ...850..178A: Unreddened Lyα/Hα = 8.7:1; radio spectral index alpha = -0.8; templates Arp 220, M82, ALESS composite, SMM J2135-0201
- 2019MNRAS.482..698C: Optically thin emission, T=20 K, beta=1, Beckwith opacity, 140 pc
- 2018A&A...616L..10F: gas-to-dust ratio 100; kappa_300um=10 cm2/g with beta=2; T_dust = host core temperature; D=1.3 kpc
- 2017ApJ...840..101C: Chabrier IMF; H0=71, Om=0.27
- 2019ApJ...878...16P: kappa=2.3 cm2/g (nu/230GHz)^0.4, T=20 K
- 2018ApJ...869..158F: 10% calibration error at both frequencies
- 2016ApJ...833...68A: single-component modified blackbody, optically thin, Rayleigh-Jeans
- 2018A&A...616A..88V: 10% flux calibration error in both bands gives 0.42 error on alpha
- 2018ApJ...855...24P: spectral index 2 to map 7 mm limit to 18 mJy/beam at 1.3 mm
- 2016ApJ...828...56W: Metallicity of M*~10^11.2 galaxy from Erb et al. 2006
- 2019A&A...623A.150V: gas-to-dust ratio 100, optically thin dust
- 2019ApJ...879..101L: Rayleigh-Jeans limit
- 2017ApJ...840...32T: Free-free jet spectral index 0.6
- 2016ApJ...823..160D: same dust temperatures in Chamaeleon I as in Perseus; emission compact/unresolved
- 2019ApJ...878L...8T: kappa = 2.3 cm2/g at 233 GHz (beta ~0.5), T_dust = 18 K, d = 59.5 pc, uniform background
- 2018ApJ...861...91H: kappa = 10 (nu/1 THz)^beta cm2/g, beta=1, gas-to-dust 100, Td = 30 K, central mass 0.15 Msun
- 2019ApJ...881L..39B: beta=1.7, dust-to-gas 100, distance 6.75 kpc
- 2019ApJ...886L...4Z: kappa_1.3mm=0.899 cm2/g, gas-to-dust 141, T=30 or 60 K
- 2016ApJ...826...16E: d=400 pc, kappa0=2 cm2/g at 1.3 mm, beta=1, T=20 K, gas-to-dust 100
- 2017ApJ...850L...2A: Tdust 20-50 K, kappa850=0.035, beta=1, gas-to-dust 100
- 2016ApJ...823L..27H: 1.3 mm emission all dust; dust spectral index fixed at 3.2
- 2019ApJ...871...72M: Distance 389 pc; stellar radius 2.5 Rsun for upper Tb limit
- 2019ApJ...872..112V: T=20 K, kappa=10 cm2/g at 1000 GHz, beta=1, gas-to-dust 100


### Limitations the authors admit
- 2018ApJ...859..103W: Equal weighting of frequencies may not reflect each data set's beam and sensitivity; image plane detection not convincing
- 2018ApJ...853..171G: Catalog potentially incomplete; completeness cannot be quantified
- 2018ApJ...853..171G: Column density maps not very accurate; SFR strongly dependent on assumed timescale
- 2017ApJ...844..123F: Redshifts of non-QSO SMGs unknown (assumed 2.5), making their results less reliable
- 2017ApJ...844..123F: Size measurements at SNR<10 are biased high
- 2017ApJ...844..123F: Duty cycle is an upper limit since no BH accretion assumed in SMGs without QSOs
- 2020MNRAS.496..394R: Single excitation temperature is a large source of uncertainty.
- 2020MNRAS.496..394R: Spectral index poorly constrained because bands 6 and 7 are adjacent; fluxes and globule mass are lower bounds.
- 2016ApJ...833L...6C: Large structures (>~12") undersampled in Band 7; could matter for dust
- 2016ApJ...833L...6C: Dust mass may be underestimated since warm dust dominates SED peak; LMC X_CO may overestimate gas
- 2024ApJ...966...59S: Short snapshot observations, lack of short spacings, gas radii as lower limits
- 2024ApJ...966...59S: Dust masses are lower limits if optically thick
- 2024A&A...691A.180F: Tex fixed to CH3OH value for all species; N_tot uncertain up to factor 2
- 2024A&A...691A.180F: Static models cannot reproduce all ratios; dynamical models needed
- 2013ApJ...767...88W: Eight ambiguous redshifts hamper determination of the distribution shape; small sample
- 2013ApJ...767...88W: Dust temperatures not physical; lensing size-evolution bias cannot be excluded
- 2017ApJ...841..130A: Planned ALMA sensitivity not reached, so nebula undetected
- 2017ApJ...841..130A: Central-object size is an upper limit; flux systematics from differing beams and nebular contamination
- 2013Sci...341..630Q: Vertical disk structure is uncertain; vertical N2H+ boundaries fixed
- 2014ApJ...787..112C: LTE, no radiative pumping, constant source size assumed; some species optically thick
- 2020ApJ...892...66M: Pencil-beam survey affected by cosmic variance (~42-58%)
- 2020ApJ...892...66M: Dust-based gas may be biased against atomic phase; low-metallicity GDR relation uncertain
- 2025A&A...698A.204H: Gas mass has large systematic uncertainties from alpha_CO, which are ignored; CI excitation not constrained
- 2025A&A...698A.204H: Simulation comparison is only qualitative
- 2020ApJ...891...48H: Temperature, flux calibration and degeneracies prevent precise grain size measurements
- 2019ApJ...875...55W: Cannot exclude short-lived mm flares; Sirius A not necessarily a template for rapid rotators like Altair
- 2021A&A...656A..46M: Calibration uncertainty not included in fit uncertainties; line flux scaling anomalies in some tunings
- 2021A&A...656A..46M: STATCONT continuum subtraction not optimal for lines near noise level
- 2019A&A...628A.100D: Systematics from cluster geometry and complex post-shock gas distribution; model does not capture X-ray morphology
- 2024ApJ...966...51G: LTE assumptions, possibly optically thin 12CO; sensitivity limited to several Msun/pc^2
- 2024ApJ...966...51G: 8um may trace gas column rather than star formation at these scales
- 2017MNRAS.466.4201W: Ring ansae near primary beam edge, so N/S asymmetries and vertical structure unreliable
- 2014ApJ...795L..25R: Core unresolved so density is a lower limit; deviation may be from temperature
- 2015A&A...577L...4V: Band 3 resolution too poor to confirm the hotspot there; 25 Oct Band 3 epoch affected by resolved calibrator
- 2020ApJ...894...76W: gamma Vir models lack constraints at other wavelengths; temperature minimum cannot be analyzed
- 2020ApJ...894...76W: Variability at longer timescales cannot be ruled out for gamma Lep
- 2024A&A...684A..56K: Data not standardized, resolution limited, CO SLED turnover unconstrained
- 2015ApJ...798..124R: Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density
- 2019MNRAS.488.1005P: System ages uncertain by ~50%
- 2019MNRAS.488.1005P: Gas (CO) not analysed
- 2020A&A...644A..84M: Tex-Ntot degeneracy for AA gives a factor ~2 uncertainty on Ntot
- 2020A&A...644A..84M: Some MF transitions under-reproduced; unidentified blends possible
- 2024A&A...689A.317G: In-falling component size is not conclusive
- 2024ApJ...963....1O: X_CO uncertainty may overestimate molecular mass by a factor of a few
- 2024ApJ...963....1O: Chandra data too shallow to resolve cavity
- 2015ApJ...813..118M: Only three regions; nuclear HCN cut off by bandpass; single-component fit poor for Enuc. 2
- 2021A&A...652A..98G: Common T_dust adopted for all sources; mass estimates depend on assumed conversion factors
- 2021A&A...652A..98G: Spectral index maps only possible for 3 sources
- 2021A&A...652A..98G: Small-number statistics for orientation and correlations
- 2014Sci...345.1584B: Preliminary LTE model not fully optimized for ALMA; abundance uncertainties exclude free-free contamination and dust property uncertainties
- 2024Ap&SS.369...18M: Cannot draw conclusions on continuum morphology
- 2020ApJ...892...99C: Temperature poorly constrained by the data
- 2020ApJ...892...99C: Calibration uncertainty not included in MCMC fit
- 2024RMxAA..60..355R: ALMA flux lower than Faramaz et al. because ACA data were not included
- 2015A&A...573L...4L: Sparse spectral sampling prevents a conclusive statement on changing opacities
- 2024NatAs...8..774B: The afterglow/SN decomposition is uncertain and affects the Ni mass
- 2018ApJ...852..122H: Models are not optimal; dust modeling and multi-line fitting deferred; perturbed temperature model not physically self-consistent
- 2018ApJ...852..122H: Absolute alpha uncertain by ~0.4 from flux calibration
- 2019ApJ...877L..25M: Beta uncertainty dominates Q; kinematic model not finely fitted; larger-scale envelope resolved out
- 2019MNRAS.482.3135B: Small sample and ambiguous total fluxes of IDs 1 and 2; modest dynamic range
- 2021A&A...653A.117B: Low statistics and poorly constrained temperatures hamper strong conclusions
- 2017MNRAS.468L..87C: Cold dust mass is only an estimate; alternative dust properties would change it
- 2024ApJ...974..102S: Compact source gap rms is enhanced, low effective SNR
- 2024ApJ...974..102S: Kink structure only marginally resolved; error bars large
- 2025ApJ...993..120H: Dust mass may be a lower limit if emission is optically thick
- 2025ApJ...993..120H: A closer unresolved binary cannot be ruled out
- 2014ApJ...785..111W: Single-component SFH cannot model multiple bursts; ages and masses uncertain
- 2017ApJ...841..110S: Envelope size only a lower limit because CO is in absorption
- 2018Sci...362.1034D: U1 may be at a different redshift; stellar mass and SFR uncertain by factor of 2
- 2015ApJ...812..126C: Absolute flux scale uncertain, affecting spectral index and optical depths
- 2014ApJ...796....1T: Missing flux and outflow complicate other lines near systemic velocity; temperatures in hydrodynamics (isothermal 13.5 K) and radiative transfer (power law) are inconsistent.
- 2020ApJ...902...78R: Lens models exist for only 39 sources; median magnification adopted for rest, so intrinsic properties are estimates
- 2025ApJS..278...45F: 1-2 sources may be spurious; no completeness correction for IRLF; z>9 detections marginal
- 2021AJ....161..238W: Midplane thermal emission not vertically resolved; smooth tapered density model too simple
- 2019MNRAS.488..191G: Observations not simultaneous across radio, mm and IR; no firm conclusions
- 2020ApJ...895..135K: Anti-correlation is tentative; H2 dissociation conflicts with Spitzer-based H2 surface density of Rosario+19; follow-up observations needed
- 2018MNRAS.475..448T: Distance mismatch between GRS 1915+105 and IRAS source; jet power assumes constant power and density
- 2018MNRAS.475..448T: ALMA continuum lacks single-dish data so flux is underestimated
- 2018ApJ...853..195W: Optical selection of members may bias the star-forming census; small samples of CO detections.
- 2026ApJ..1004..126K: Spectral shape uncertain with narrow frequency range and large errors
- 2019AJ....158..162F: Apocenter-glow detection remains qualitative; lacks sensitivity
- 2019AJ....158..162F: Perturber constraints are degenerate without extra constraint; S1 comoving unknown
- 2015ApJ...802...69B: ALMA lacked Tsys measurements on Sgr A* itself, requiring a correction
- 2015A&A...573L...1O: Dust mass of C is a lower limit as it may not be optically thin; much flux is resolved out
- 2025A&A...699A..62J: Detailed SED modeling is needed to constrain the magnetic field
- 2019ApJ...876L..10E: ALMA 100 GHz limit is too shallow to constrain a star formation origin
- 2018A&A...619A.161C: Emission only marginally optically thin so masses are lower limits; large uncertainties in opacity and gas surface density
- 2018A&A...619A.161C: Spectral index decrease may be due to optical thickness rather than grain growth
- 2018ApJ...863...19A: Uncertain orientation and inclination prevent measuring rotation and infall; abundance not derivable for SMM4A
- 2016ApJ...826..112S: Lens model uncertainties on source properties are dominated by systematics from source parameterization
- 2020ApJ...898...10T: Model CBD larger than observed; magnetic field not included; high-velocity blueshifted components near Source N not reproduced; infall not identified observationally
- 2019PASJ...71...68K: Nucleus distance is hard to determine due to line of sight
- 2019PASJ...71...68K: CO(3-2) shows negative signals from sparse uv coverage
- 2024A&A...689A.104D: Band 8 resolution insufficient to resolve the substructure; large location uncertainties
- 2025ApJ...994..225N: Missing flux from interferometric filtering hinders prestellar core detection
- 2025ApJ...994..225N: Ejected cores may not survive; CO structures affected by missing flux
- 2012ApJ...752L..30W: Lack of Tsys and WVR in the data adds 15% flux uncertainty; SW redshift unknown; outflow needs higher resolution
- 2017A&A...602L..10O: Limited resolution smears fine structures and reduces contrast; spectral index errors may be underestimated
- 2019PASJ...71..109H: SFR_IR and Td uncertain due to possible AGN heating; local SFR relation may not apply to quasars
- 2019PASJ...71..109H: J2310+1855 SPW1 data lost to atmospheric absorption
- 2014ApJ...787...42C: Dust mass errors exclude opacity uncertainty; upper limits treated inconsistently between samples; multiplicity unknown for most stars
- 2014ApJ...796...82Z: Equipartition estimates may be inaccurate for flat spectra; double-subtracted images unusable due to errors
- 2020A&A...642A.155Z: Single lines cannot give definitive redshifts
- 2024ApJ...961..120C: Radio resolution cannot identify which of B, C, G hosts the AGN; spectral index from only two points plus limits
- 2024ApJ...961..120C: 5 arcsec ATCA-ASKAP offset unexplained
- 2020ApJ...898...36L: Uncertainties of GO Tau and DL Tau ring properties likely underestimated; function choice affects results; resolution washes out alpha variations
- 2017MNRAS.464L..75F: Bipolar outflow versus rotating disc origin of H41alpha cannot be distinguished; filaments need more sensitive follow-up
- 2020ApJ...898...75I: Dominance of H2 in the CND is assumed; HI/HII may contribute
- 2020ApJ...898...75I: RADEX assumes single homogeneous medium though real structure is complex; single transition limits Tex
- 2017ApJ...837...93Y: Orbit not determined a priori; line-of-sight velocity and position unknown
- 2019A&A...624A...7V: Model is a compromise and working model, not best fit; J1852 modeling degenerate
- 2019ApJ...886....6T: Only ~2% of single-dish flux recovered; masses likely lower limits because emission partly optically thick
- 2019ApJ...886....6T: CO non-detections of outflows inconclusive owing to spatial filtering
- 2019ApJ...876...99S: Lack of NIR/MIR data prevents distinguishing dust models
- 2020A&A...635A...2S: Temperatures assumed rather than measured; unresolved multiplicity biases CMF
- 2020A&A...635A...2S: Low number statistics limit Q-parameter conclusions
- 2019ApJ...871..170M: Rgd for diffuse Milky Way gas may not apply to the dense CMZ
- 2019ApJ...871..170M: H3O+/SO ratio affected by optical depth and calibration; factor of two differences possible
- 2019ApJ...871..170M: Total Power data unusable so no zero-spacing beyond ACA
- 2024ApJ...971..129C: Only two bands constrain four parameters; priors needed; porosity unconstrained

### Settings cards flag as needed but not stated
- casa version: 18
- self-calibration solution intervals: 13
- image size and cell size: 10
- self-calibration solution intervals and number of iterations: 9
- casa version and pipeline version: 6
- line-free channels and continuum subtraction method: 6
- casa/pipeline version: 5
- line-free channels used for continuum subtraction: 4
- line-free channels for continuum subtraction: 4
- line-free channel selection: 4
- flux scale uncertainty: 4
- flux calibrator and flux scale uncertainty: 4
- line-free channels used for continuum: 4
- uvmodelfit starting parameters: 3
- line-free channel selection for continuum: 3
- line-free channel ranges for uvcontsub: 3
- primary-beam correction details: 3
- line-free channel ranges for continuum: 3
- whether pipeline or manual calibration and casa version: 2
- cell and image sizes: 2
- clean threshold, mask, niter, cell and image size: 2
- line-free channels for uvcontsub: 2
- line-free channel ranges for continuum and uvcontsub: 2
- clean mask, threshold, cell and image size: 2
- self-calibration use: 2
- primary beam correction treatment: 2
- casa version and whether pipeline or manual calibration was used: 2
- flux calibrator and flux-scale uncertainty: 2
- spectral setup and continuum bandwidth: 2
- self-calibration solution intervals and iterations: 2
- rest frequencies of lines: 2
- self-calibration solution intervals, number of rounds and reference: 2
- clean threshold, masks, cell and image size: 2
- self-calibration solution intervals and reference models: 2
- line-free channel ranges: 2
- moment-map clipping thresholds: 2
- continuum channel selection / line-free channels: 2
- line-free channels used for uvcontsub: 2
- primary beam correction details: 2
- clean threshold, masks, image size and cell size: 2

## Paper excerpts (40 of 233, chosen for detail and spread over fields/years)

### 2018ApJ...859..103W: Extended Millimeter Emission in the HD 141569 Circumstellar Disk Detected with ALMA (2018; protoplanetary_disks, debris_disks; archival_reuse)
- question: Is there extended millimeter emission exterior to the inner disk of HD 141569, and how do the grain size distributions of the inner and outer disks compare?
- step 2: Fit single-component disk model
  - method: MCMC fit of a surface brightness ∝ r^-1 disk with inner and outer edges to all three data sets at once [Single-Component Model: "The single-component model used here adopts a surface brightness profile $\propto r^{-1}$ and assumes the disk has an inner and outer edge."]
  - parameter: Free: 345 GHz flux, spectral index, disk center, width; uniform priors flux 0.01-50 mJy, disk 0.1-300 au, index 0-4 [Single-Component Model: "A uniform prior distribution is chosen for the flux to range from .01 to 50 mJy, the disk from 0.1 to 300 au, and the spectral index from 0 to 4."]
  - assumption: Flux follows a single power law in frequency [Single-Component Model: "(and assuming the flux is well defined by a single power law in frequency)"]
  - fitting: Metropolis-Hastings MCMC; chi2 averaged with equal weight over the three frequencies [Visibility Fitting: "The three are averaged together with equal weighting to get a representative $\chi^{2}$."]
  - validation: Jeffreys priors gave negligible differences; uniform-disk fit consistent with uvmodelfit [Single-Component Model: "we ran MCMC modeling for the single component using Jeffreys priors, which resulted in negligible differences."]
- step 3: Fit two-component disk model
  - method: MCMC fit of inner and outer disks, each with own center, width and spectral index; non-overlapping [Two-Component Model: "The inner disk prior range is from 0.1 to 100 and the outer disk prior range is from 50 to 500 au, and models are not accepted if the two disks overlap."]
  - fitting: Same MCMC; most probable values and 95% credible regions [Two-Component Model: "A summary of the most probable model parameters, 95% Credible Region, and reduced $\chi^{2}$ at each frequency are given in Table [\[obs\]](#obs)."]
  - validation: Compared reduced chi2 of the models [Discussion: "the two-component model is preferred (1.74 versus 1.08 averaged reduced $\chi^{2}$)"]
- result: Inner disk extent (two-component) = 16 to 45 au ± not stated au [abstract: "The inner disk ranges from approximately 16 to 45 au"]
- result: Outer disk extent = 95 to 300 au ± not stated au [abstract: "the outer disk ranges from 95 to 300 au"]
- result: Inner disk spectral index = 1.81 ± ±0.15 dimensionless [Discussion: "The best fit spectral indicies of $1.81\pm0.15$ and $2.28^{+0.43}_{-0.29}$"]
- result: Outer disk spectral index = 2.28 ± +0.43/-0.29 dimensionless [Discussion: "The best fit spectral indicies of $1.81\pm0.15$ and $2.28^{+0.43}_{-0.29}$"]
- result: Average reduced chi2 single vs two-component = 1.72 vs 1.08 ± not stated dimensionless [Table 1: "Average $\chi^{2}_{red}$ | 1.72 | 1.08"]
- result: Outer disk 345 GHz flux (two-component) = 11 ± 95% range 8.4-13 mJy [Two-Component Model: "For the outer disk, the best fit 345 GHz flux is 11 mJy"]
- limitation (authors): Equal weighting of frequencies may not reflect each data set's beam and sensitivity; image plane detection not convincing [Visibility Fitting: "an equal weighting of each frequency may not directly reflect the contribution from each set of visibilities."]
- not stated (card): Disk inclination and position angle values used for the models and the radial profiles; Phase center and stellar position; Imaging parameters for the continuum images (weighting, cell, size); Details of the 345 and 100 GHz calibration; MCMC settings (chain length, walkers, burn-in, step size); Dust temperature used for alpha_pl; Which channels or SPWs were used as continuum; Visibility weighting …

### 2018ApJ...853..171G: Distributed Star Formation throughout the Galactic Center Cloud Sgr B2 (2018; star_formation, milky_way_ism; observational_alma_primary)
- question: Is there extended, distributed star formation across the Sgr B2 cloud beyond the N, M, S protoclusters, and how do star formation thresholds and surface density relations compare with local clouds?
- step 2: Identify compact continuum sources and measure photometry/spectral index
  - method: By-eye selection of peaks >5x lowest RMS across images, excluding r>1" sources; local noise via MAD in 0.5-1.5" annulus; alpha from mtmfs maps [3.1: "Outside of the dense clusters, every peak that is higher than five times the lowest measured RMS noise value was visually inspected."]
  - software: CASA
  - parameter: alpha kept if |alpha|>5 sigma(alpha) or sigma(alpha)<0.1 [3.1: "We include in the analysis only those sources with $|\alpha| > 5 \sigma(\alpha)$ or $\sigma(\alpha) < 0.1$"]
  - validation: high/low-confidence classes; completeness not quantified [3.1: "we cannot readily quantify our completeness"]
- step 3: Cross-match and classify sources
  - method: Positional matching within 0.5-1" to VLA HII, MMB, H2O maser, Chandra, Spitzer catalogs; test alternative nature hypotheses (prestellar cores, EGGs, HII regions, YSOs) [3.2: "We cross-matched our source catalog with catalogs of NH$_3$ sources, H II regions, X-ray sources, Spitzer sources, and methanol and water masers."]
  - assumption: beta=1.75, kappa(3.1mm)=0.0018 cm2/g per gram gas (Ossenkopf1994a), gas-to-dust 100, d=8.4 kpc [3.3.1: "assuming a dust opacity index $\beta=1.75$ (spectral index $\alpha=3.75$ if measured on the Rayleigh-Jeans tail of the spectral energy distribution)"]
  - validation: comparison with Robitaille/Zhang models, HOPS Orion sources, and MUSTANG Orion data [3.3.5: "We compare our detected sample to that of the Herschel Orion Protostar Survey (cite: Furlan2016a)"]
- result: Number of compact 3 mm sources = 271 ± not stated sources [3.1: "We detected 271 compact continuum sources"]
- result: Sources with HII region counterparts = 31 ± not stated sources [3.2 H II regions: "31 of our sources are classified as H II regions"]
- result: Sources with significant spectral index = 62 (33 with alpha>2) ± not stated sources [3.3.2: "We measured spectral indices for 62 sources, of which 33 have $\alpha>2$."]
- limitation (authors): Catalog potentially incomplete; completeness cannot be quantified [3.1: "Our selection criteria result in a reliable but potentially incomplete catalog"]
- limitation (authors): Column density maps not very accurate; SFR strongly dependent on assumed timescale [4.1.1: "our estimate of the star formation rate remains strongly dependent on the assumed star formation timescale"]
- not stated (card): tclean image size, cell size, multiscale scales and primary-beam mask details; self-calibration solution intervals and per-iteration imaging parameters (only in script); exact by-eye source selection and per-source peak/photometry procedure; Herschel SED-fitting details (Battersby et al. in prep) and dust opacity for column density maps; uvcombine/feather weighting parameters; cluster radius defi…

### 2017ApJ...844..123F: The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters below 100 kpc (2017; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: Are Herschel-selected SMGs near QSOs (5-30 arcsec) true projected SMG-QSO pairs, or are the QSOs hosted by SMGs, and what are the properties of the composites?
- step 7: Fit IR luminosity and SFR
  - method: Fit modified blackbody (optically thick, lambda0 = 150 um, beta = 2) to SPIRE+ALMA photometry; integrate 8-1000 um; SFR = L_IR/1e10 (Kennicutt98, Chabrier IMF) [4.1.3 IR Luminosity and SFR Surface Den…: "We fixed $\lambda_0$ at 150 $\mu$m for a typical power-law slope of $\beta = 2$"]
  - parameter: Redshift fixed (QSO z for composites, 2.5 otherwise) [4.1 Properties of the QSO Host Galaxies: "assume a redshift of 2.5 for the remaining ALMA sources"]
  - assumption: Constant dust temperature, local thermal equilibrium [4.1.3 IR Luminosity and SFR Surface Den…: "assuming local thermal equilibrium at a constant temperature $T$"]
  - fitting: Modified blackbody fit; Monte Carlo simulations of synthetic photometry for statistical error [4.1.3 IR Luminosity and SFR Surface Den…: "through Monte Carlo simulations of synthetic *Herschel* and ALMA photometry"]
  - validation: Compared with optically thin models and Arp 220 SED; L_IR differs by ~0.1 dex [4.1.3 IR Luminosity and SFR Surface Den…: "The resulting $L_{\rm IR}$ can be higher than the blackbody fits by $\sim$0.1 dex"]
- result: Mean SFR surface density of SMG-QSO composites = ~260 ± not stated Msun/yr/kpc^2 [4.1.3 IR Luminosity and SFR Surface Den…: "The mean SFR surface density of the SMG-QSO composites is $\sim$260 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$."]
- limitation (authors): Redshifts of non-QSO SMGs unknown (assumed 2.5), making their results less reliable [4.1.3 IR Luminosity and SFR Surface Den…: "The results for the rest of the sample are less reliable because of their unknown redshifts"]
- limitation (authors): Size measurements at SNR<10 are biased high [4.1.2 Mass and Surface Density of the I…: "Note that the size estimates are biased high at ${\rm SNR} < 10$"]
- limitation (authors): Duty cycle is an upper limit since no BH accretion assumed in SMGs without QSOs [4.3 Star-Formation-AGN Co-evolution at …: "This estimate of the QSO duty cycle should be considered as an upper limit"]
- not stated (card): Number of clean iterations / niter and the exact mask definition procedure; Whether continuum was formed from all four spws without line flagging; Details of the SED fitting code, fitting method and priors (modified blackbody fit procedure); QSO template fit procedure to SDSS/WISE photometry; Stacking procedure details for undetected QSOs; Bootstrapping details for mean size; CASA version used fo…

### 2020MNRAS.496..394R: Illuminating a tadpole's metamorphosis II: observing the ongoing transformation with ALMA (2020; star_formation, milky_way_ism; observational_alma_primary)
- question: What are the structure, kinematics, outflow, embedded protostar and mass (hence survival time) of the tadpole globule hosting the HH 900 jet+outflow, as seen by ALMA?
- step 5: Continuum flux, spectral index and dust masses
  - method: Flux within 0.3" radius at four continuum bands; weighted least-squares power-law fit; spherical dusty core model rho~r^-2 with T(r)=T0 (r/r0)^-0.4; whole-globule mass from Band 6 continuum at 45 K [3.6 Dust continuum emission: "We obtain the best-fit model by minimizing the squared differences between the model and the fluxes, weighted by the inverse of their squared uncertainties."]
  - parameter: nu0=230.61 GHz, kappa0=0.8 cm2/g, beta=1.0, gas-to-dust 100, r0=690 AU, 15% flux uncertainty [3.6 Dust continuum emission: "a $\beta=1.0$, and a gas-to-dust mass ratio of 100."]
  - assumption: 15 K for compact core; 45 K for extended emission [3.6 Dust continuum emission: "We adopt a higher temperature for the extended emission around the compact source (45 K, see Section [3.4](#s:tadpole_temp)) to compute a mass of $1.9~M_{\ensuremath{\odot}}$"]
  - fitting: chi-square minimisation, 1 sigma errors following Lampton et al. [3.6 Dust continuum emission: "we derive 1$\sigma$ error bars in the spectral index of $\pm0.5$ (cite: lampton1976)"]
  - validation: ALMA flux recovery compared with APEX (~70%); fluxes treated as lower bounds [Appendix: Maximum recoverable scale: "our ALMA observations recover approximately a 70% from the tadpole emission."]
- result: Spectral index of HH 900 YSO = 2.2 ± ±0.5 dimensionless [Table 3: "| HH 900 YSO$^a$ | 10:45:19.296 | $-$59:44:22.55 | 4.70 | 5.86 | 12.54 | 13.48 | $2.2\pm0.5$ |"]
- result: Globule dust mass (45 K) = 1.9 ± not stated Msun [3.6 Dust continuum emission: "to compute a mass of $1.9~M_{\ensuremath{\odot}}$ for the entire tadpole"]
- result: Compact HH 900 YSO core mass (15 K) = 1.0 ± not stated Msun [3.6 Dust continuum emission: "we obtain $1.0~M_{\ensuremath{\odot}}$ for the compact HH 900 YSO core"]
- result: Fraction of tadpole emission recovered by ALMA = ~70 ± not stated percent [Appendix: Maximum recoverable scale: "our ALMA observations recover approximately a 70% from the tadpole emission."]
- limitation (authors): Single excitation temperature is a large source of uncertainty. [3.2 Molecular column density: "Assuming a single excitation temperature is a large source of uncertainty as this is often a poor assumption"]
- limitation (authors): Spectral index poorly constrained because bands 6 and 7 are adjacent; fluxes and globule mass are lower bounds. [3.6 Dust continuum emission: "with adjacent bands (6 and 7) not being optimal to estimate accurate spectral indices."]
- not stated (card): tclean parameters: robust/weighting, cell size, image size, deconvolver, masks, niter and threshold; Self-calibration solution intervals, reference antenna and which datasets/bands were self-calibrated; Line-free channels and method for continuum subtraction and continuum aggregation; How the Band 7 and Band 6 images were primary-beam corrected and the final per-line cube properties; Details of o…

### 2016ApJ...833L...6C: ALMA Reveals Potential Localized Dust Enrichment from Massive Star Clusters in II Zw 40 (2016; nearby_galaxies, star_formation, milky_way_ism; observational_alma_primary)
- question: How well do gas, dust and free-free emission correlate on cluster/cloud scales in II Zw 40, and is the gas-to-dust ratio low and variable because of local dust enrichment by massive clusters?
- step 3: Separate dust from free-free at 870um
  - method: Extrapolate 3mm free-free to 870um with spectral index -0.118 and subtract to get dust-only map [4.1: "we extrapolate the 3mm free-free emission to 870$\mu$m using the spectral index -0.118"] [4.1: "Subtracting the scaled 3mm free-free continuum from the 870$\mu$m gives a map of the dust emission alone"]
  - assumption: Dust contribution at 3mm negligible for beta=1.7 [4.1: "for dust emissivity $\beta = 1.7$, is $S_{3mm}^{dust}<0.1$ mJy"]
  - validation: Dust flux agrees with Kepley et al. 2016 [4.1: "This value agrees with that of (cite: 2016arXiv160701779K)."]
- step 4: Derive dust masses, gas masses and GTD for clouds
  - method: Dust mass from 870um dust flux with kappa and temperature; gas mass from CO(1-0) with X_CO (and CO(3-2) via R31=7.4); GTD = gas/dust in three 0.6" regions and central 5" [4.3 Gas-to-Dust: "We calculate GTD by determining dust and gas masses separately."]
  - parameter: kappa_870=0.9 cm2/g, beta=1.7; Tdust 33 K (Clouds C, W), 20 K (Cloud E) [4.3 Gas-to-Dust: "For Clouds C and W, we use the 33K IRAS 60/100 color temperature (cite: 2008ApJ...678..804E) and for the isolated Cloud E, we use T$_{Dust}$=20K."]
  - assumption: LMC X_CO = 4.7e20 cm-2 (K km/s)-1; R31=7.4 [4.3 Gas-to-Dust: "using $R_{31}$=7.4 to obtain the equivalent CO(1-0) flux"]
  - validation: Compared with GTD predicted from metallicity (~400-600) [4.3 Gas-to-Dust: "so the predicted GTD is $\sim$400-600."]
- result: 870um total flux (inner 6") = 9.7 ± 0.5 mJy [4.1: "total flux for the inner 6$''$ is $S_{870\mu m}= 9.7\pm0.5$ mJy"]
- result: 870um dust flux density = 3.0 ± 0.5 mJy [4.1: "we obtain $S_{870\mu m}^{dust}= 3.0\pm0.5$ mJy"]
- result: Dust mass, central 5" (T=33 K) = 17000 ± 5000 Msun [4.3 Gas-to-Dust: "We obtain a total dust mass for the central 5$''$ of 17000$\pm$5000 M$_\odot$(for T=33K)."]
- result: Gas mass from CO(1-0) = 1.1e6 ± not stated Msun [4.3 Gas-to-Dust: "The overall gas mass based on CO(1-0) is $M_{gas}=1.1\times10^6$ M$_\odot$, including helium."]
- result: Gas-to-dust ratio, Cloud W (CO1-0) = 69 ± not stated dimensionless [Table 1: "| Cloud W$^d$ | 42.609, 32.03 | 0.06 | 0.71 | 12 | 13 | 21 | 0.34 | 1940 | 69, 110 |"]
- result: Gas-to-dust ratio, Cloud E (CO1-0) = >270 ± not stated dimensionless [Table 1: "$<$450 | $>$270, $>$350"]
- result: S_CO32/S_870dust range = 1400 to 13000 ± not stated km/s [4.3 Gas-to-Dust: "varies from $S_{CO32}/S_{870}^{dust}\sim 1400$ km s$^{-1}$ to $S_{CO32}/S_{870}^{dust}\sim 13000$ km s$^{-1}$"]
- limitation (authors): Large structures (>~12") undersampled in Band 7; could matter for dust [2 Observations: "However, it could be an issue for dust, which traces both atomic and molecular gas."]
- limitation (authors): Dust mass may be underestimated since warm dust dominates SED peak; LMC X_CO may overestimate gas [4.3 Gas-to-Dust: "This may underestimate the true dust mass, since the SED peak is dominated by the warmest dust, which will not dominate the mass."]
- not stated (card): Number of ALMA execution blocks, array configurations and antenna numbers; CASA version and pipeline version; Imaging parameters (weighting, robust, cell, image size, deconvolver, masking); Line-free channels used for continuum subtraction; Velocity ranges for integrated intensity maps; Primary-beam correction and flux-scale uncertainty; Exact regions/apertures for flux measurements; Procedure to…

### 2024ApJ...966...59S: Small and Large Dust Cavities in Disks around Mid-M Stars in Taurus (2024; protoplanetary_disks; observational_alma_primary)
- question: Do disks around mid-M stars in Taurus show dust substructures (rings and cavities) at ~50 mas resolution, and what could cause them?
- step 3: Test for hidden small cavities (Nuker) and central emission
  - method: Fit Nuker profile to 2M0450 and CIDA 12; compare via BIC; add central point source to 2M0436 ring model [3.2.2 Potential cavities: "However, the Nuker profile has more parameters than the Gaussian profile, which results in a larger Bayesian Information Criterion"]
  - software: galario, emcee
  - parameter: Nuker priors: log10 alpha U(0,2), beta U(0,10), gamma approx uniform (-3,2); point flux U(0,1) mJy [9 Nuker fitting results: "$p(\log_{10}\alpha)=\mathcal{U}(0,2),\ p(\beta)=\mathcal{U}(0,10)$"]
  - fitting: Same MCMC procedure as step 2 [9 Nuker fitting results: "The modeling procedure follows Section [3.1](#subsec:result_uvfit)"]
  - validation: BIC preference keeps the Gaussian profile for smooth disks [3.2.2 Potential cavities: "Hence, we still treat 2M0450 and CIDA 12 as non-structured disks in this work."]
- step 6: SED radiative transfer for micron-grain cavity sizes
  - method: RADMC-3D flared disk with BT-Settl star; grid over Rin, beta, H100; p=-1, Rout=R90 mm [10 SED Fitting: "We fix $p$ to -1 and $R_{\rm out}$ to the $R_{90\%}$ in millimeter images"]
  - software: RADMC-3D
  - parameter: beta in [1.0,1.2], H100 in [5,15], Rin between sublimation radius and mm cavity; grains 0.01-1000 um [10 SED Fitting: "$\beta$ in \[1.0, 1.2\] and $H_{100}$ in \[5,15\]"]
  - assumption: Dust model of Birnstiel et al. 2018; well-mixed gas and dust [10 SED Fitting: "we adopt the model in (cite: birnstiel2018) with grain sizes ranging from 0.01 $\mu \rm m$ to 1000 $\mu \rm m$"]
  - fitting: Grid comparison by eye/best-fit; no formal statistic stated [SED Fitting: "We test each combination of the other three parameters with $R_{\rm in}$ between dust sublimation radius and mm cavity size, $\beta$ in \[1.0, 1.2\] and $H_{100}$ in \[5,15\]."]
  - validation: Cavity size degenerate with other parameters, differs by a few au [4.2 Substructures in disks around mid-t…: "the constrained cavity sizes of small dust grains can differ by a few au under different combinations of other parameters"]
- result: Nuker emission peak 2M0450 / CIDA 12 = 1.7 / 5.7 ± not stated au [3.2.2: "emission peak at $\sim$ 1.7 au for 2M0450 and 5.7 au for CIDA 12"]
- result: 2M0436 central point flux = 0.04 ± +0.03/-0.03 mJy [8 Central emission: "the point flux being $0.04^{+0.03}_{-0.03}$ mJy"]
- result: Micron-dust cavity radius 2M0412 / 2M0434 / 2M0508 / CIDA 12 = 0.9 / 4 / 4 / 0.3 ± not stated au [Table 5: "| $R_{\rm in}$ | 0.90 | 4 | 0.03 | 0.02 | 0.3 | 4 | au |"]
- limitation (authors): Short snapshot observations, lack of short spacings, gas radii as lower limits [3.5 CO emission: "the gas emission at large radii is likely resolved out"]
- limitation (authors): Dust masses are lower limits if optically thick [3.4: "We note that these dust masses serve as lower limits, since part of the disk could be optically thick in reality"]
- not stated (card): uv-taper values for continuum images; Multiscale scales, cell size, image size, masks and clean thresholds; Self-calibration solution intervals; Per-source MCMC priors bounds for ring models; Flux/continuum visibility weighting treatment and reference for ALMA pipeline versions; Exact CO velocity/channel settings for moment maps and extraction radii; SED fit: dust opacity composition details, inc…

### 2024A&A...691A.180F: CHEMOUT: CHEMical complexity in star-forming regions of the OUTer Galaxy: IV. ALMA observations of organic species at a galactocentric radius of 23 kpc (2024; star_formation, astrochemistry, milky_way_ism; observational_alma_primary)
- question: What are the spatially resolved molecular emission and abundances of organics in the outer-Galaxy star-forming region WB670 at R_GC 23.4 kpc, and do chemical models reproduce them?
- step 4: H2 column density and abundances
  - method: N(H2) from continuum flux with Battersby equation; abundances = N_tot/N(H2) [4.2 Fractional abundances in the contin…: "We show the molecular fractional abundances derived from the $N_{\rm tot}$-to-$N({\rm H_2})$ ratio in Table [4](#tab:lines-cont)."]
  - parameter: beta=1.7, kappa=0.899 at 230 GHz, mu=2.8, gamma~3000 [4.2 Fractional abundances in the contin…: "We also assume dust opacity index $\beta =1.7$, a typical value used for ice-coated dust grains in dense cores"]
  - assumption: Td = CH3OH Tex (gas-dust coupling) [4.2 Fractional abundances in the contin…: "We adopt for $T_{\rm d}$ the excitation temperature derived from CH$_3$OH (Table [4](#tab:lines-cont)) for each core, assuming coupling between gas and dust."]
  - validation: Alternative beta from 3mm/2mm fluxes gives N(H2) factor ~3 lower [4.2 Fractional abundances in the contin…: "i.e. a factor $\sim 3$ smaller than those given in Table"]
- result: N(H2) core N = 5.7e21 ± 1.2e21 cm^-2 [Table: "| N | 05:37:41.55 | 36:07:31.9 | $3.0\times 10^{-4}$ | $8.3 \times 10^{-4}$ | 2.4 | 0.18 | 5.7(1.2) | 2.9(1.5) | 1.1 | 0.34 |"]
- result: Dust mass core N = 2.9 ± 1.5 Msun [Table: "| N | 05:37:41.55 | 36:07:31.9 | $3.0\times 10^{-4}$ | $8.3 \times 10^{-4}$ | 2.4 | 0.18 | 5.7(1.2) | 2.9(1.5) | 1.1 | 0.34 |"]
- result: CH3OH abundance cores N and S = 0.4e-9 and 11e-9 ± not stated relative to H2 [5.3 Comparison with sub-Solar metallici…: "while in N and S is $0.4\times 10^{-9}$ and $11\times 10^{-9}$, respectively."]
- result: Gas-to-dust ratio at 23.4 kpc = 3000 ± +700/-2200 dimensionless [4.2 Fractional abundances in the contin…: "$\gamma$ is $3000^{+700}_{-2200}$"]
- limitation (authors): Tex fixed to CH3OH value for all species; N_tot uncertain up to factor 2 [4.2: "$N_{\rm tot}$ can vary up to a factor 2 depending on the species."]
- limitation (authors): Static models cannot reproduce all ratios; dynamical models needed [5.4 Chemical modelling: "Overall, it is very unlikely to find a model that fits all ratios well."]
- not stated (card): Clean parameters in GILDAS (iterations, threshold, masks, pixel size, image size); Continuum-free channels and continuum subtraction method; Spectral line extraction regions definition (regions 1-7 are drawn roughly by eye); Exact beam sizes per band; Which spws used for continuum and total bandwidth; UCLCHEM version, network and initial conditions beyond the table; Details of MSE ratio computati…

### 2013ApJ...767...88W: ALMA Redshifts of Millimeter-selected Galaxies from the SPT Survey: The Redshift Distribution of Dusty Star-forming Galaxies (2013; high_z_galaxies; observational_alma_primary)
- question: What is the redshift distribution of strongly lensed, mm-selected SPT dusty star-forming galaxies, measured through a blind ALMA 3 mm CO line survey, and how does lensing and selection bias affect it?
- step 2: Derive redshifts from line identification
  - method: Unique solution from multiple lines; for single lines use additional spectroscopy or SED dust temperature priors [3 Results: "In this case, a unique redshift solution can be derived from the ALMA 3 mm spectral scans alone."]
  - parameter: Retain dust temperatures with probability >10% [3.2 Ambiguous cases: "We retain only dust temperatures with probabilities $>$10%"]
  - assumption: Greybody beta=2, T_dust distribution of known-z sample (mean 37.2+-8.2 K) as prior [3.2 Ambiguous cases: "For these sources we find a mean of T$_{\rm dust}$=37.2$\pm$8.2 K and no apparent trend with redshift"]
  - fitting: Greybody fit with dust luminosity and T_dust free [3.2 Ambiguous cases: "where the only free parameters are the dust luminosity and the dust temperature, T$_{\rm dust}$"]
  - validation: Confirmation with APEX [CII], ATCA, SMA, Z-Spec, VLT for five sources [Supplementary redshift information: "The identification of the 98 GHz line as CO(3–2) is confirmed with a CO(1–0) detection using the Australia Telescope Compact Array"]
- result: Mean dust temperature of known-z sample = 37.2 ± 8.2 K [3.2 Ambiguous cases: "For these sources we find a mean of T$_{\rm dust}$=37.2$\pm$8.2 K"]
- limitation (authors): Eight ambiguous redshifts hamper determination of the distribution shape; small sample [4.3 The redshift distribution: "The determination of the shape of our redshift distribution is currently hampered by the eight ambiguous redshifts."]
- limitation (authors): Dust temperatures not physical; lensing size-evolution bias cannot be excluded [3.2 Ambiguous cases: "the “temperatures” should not be interpreted as physical temperatures"]
- not stated (card): CASA version and calibration/imaging task parameters (weighting, cleaning, masks); Line-free channels and continuum subtraction method; Line detection/integration procedure and SNR>5 criteria details; Gaussian line-fit procedure for redshift uncertainties; Calibrator names per session; Exact probability calculation for dust temperature/redshift options; Intrinsic dn/dz and size-evolution lensing …

### 2017ApJ...841..130A: The Luminous Blue Variable RMC 127 as Seen with ALMA and ATCA (2017; evolved_stars, stellar_physics; observational_alma_primary)
- question: What is the nature of the radio/sub-mm emission from the LBV RMC 127's central object and outer nebula, and what does it imply for wind geometry, mass-loss rate and nebular shaping?
- step 3: fit radio-sub-mm spectral index
  - method: weighted power-law fit S~nu^alpha, 9 to 349.5 GHz [3.2 Spectral index of the central object: "We derive a weighted fit of the power-law ($S_{\nu}\sim \nu^{\alpha}$) between the centimeter and sub-millimeter flux densities of the central object"]
  - fitting: weighted power-law fit [3.2 Spectral index of the central object: "We derive a weighted fit of the power-law ($S_{\nu}\sim \nu^{\alpha}$) between the centimeter and sub-millimeter flux densities of the central object"]
  - validation: large frequency coverage deemed robust against systematics [3.2 Spectral index of the central object: "given the large frequency coverage (9 to 349.5 GHz) we are confident of the derived spectral index."]
- step 4: nebula spectral index and index map
  - method: integrated flux densities at 5.5, 9, 17 GHz; spectral index map from 5.5 and 9 GHz maps regridded, pixels >3 sigma [3.3 Spectral index of the outer nebula: "we computed the spectral index map and its associated error map (left and right panels of Fig. [4](#fig:spix_lbv), respectively) in each common pixel $>3 \sigma$."]
  - validation: 17 GHz excluded from index maps due to artifacts [3.3 Spectral index of the outer nebula: "We prefer not to use the map at 17 GHz to derive spectral index maps"]
- result: central object spectral index = 0.78 ± 0.05 dimensionless [3.2 Spectral index of the central object: "This gives us a spectral index $\alpha$ of $0.78\pm0.05$"]
- result: outer nebula spectral index = -0.03 ± 0.08 dimensionless [3.3 Spectral index of the outer nebula: "the average spectral index is $-0.03\pm0.08$"]
- limitation (authors): Planned ALMA sensitivity not reached, so nebula undetected [2.1 ALMA observation and data reduction: "The proposed sensitivity of $40\,\mu{\rm Jy}\,{\rm beam^{-1}}$ could not be achieved"]
- limitation (authors): Central-object size is an upper limit; flux systematics from differing beams and nebular contamination [3.1 The ATCA and ALMA maps: "Hence, the size provided above must be considered an upper limit."]
- not stated (card): tclean/clean parameters (cell, image size, niter, threshold, masks); how peak/central flux densities were extracted (position, box); spectral-window flagging that yields 7.5 GHz usable bandwidth; weighted fit method for the power law and the grey-body fitting procedure and priors; SED photometry values used; ATCA calibration details and robust-free parameters for 17/23 GHz; the offline WVR contin…

### 2017ApJ...835L..35M: New ALMA and Fermi/LAT Observations of the Large-scale Jet of PKS 0637-752 Strengthen the Case Against the IC/CMB Model (2017; agn_and_quasars; multi_facility_alma_minor)
- question: Do new ALMA constraints on the synchrotron SED and deeper Fermi/LAT limits rule out the IC/CMB model for the X-ray emission of the PKS 0637-752 large-scale jet?
- step 3: Fermi progressive-binning upper limits
  - method: 155 light-curve bins ordered by TS and progressively combined; power law index 2.7 fixed; 95% limits in five energy bands [2.2 Fermi: "We ordered the 155 light curve bins according to TS and then progressively combined them in our analysis"]
  - software: make3FGLxml
  - parameter: 13 new sources added to the 3FGL model [2.2 Fermi: "We added 13 new sources to the base model populated with 3FGL catalog sources"]
  - assumption: fixed spectral index 2.7 [2.2 Fermi: "using a power-law model with a fixed spectral index of 2.7"]
  - fitting: maximum likelihood [2.2 Fermi: "using a maximum-likelihood approach as described in M15"]
  - validation: free spectral index check gave no significant change [2.2 Fermi: "Results are not significantly altered by using a free spectral index"]
- not stated (card): Which ALMA execution blocks and projects went into each band's combined image; Contour regions used for knot flux measurement; Exact Fermi analysis tool and version, IRFs, zenith and energy cuts; Cell and image size, masking of imaging; Pipeline and CASA versions; Details of the empirical SED fit beyond by eye

### 2013Sci...341..630Q: Imaging of the CO Snow Line in a Solar Nebula Analog (2013; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Where is the CO snow line in the TW Hya disk, as traced by the inner edge of N2H+ J=4-3 emission?
- step 2: Build disk physical model
  - method: Steady viscous accretion disk, irradiated, alpha prescription, two dust populations, z_big varied 2H to 3.5H, fitted to SED [Physical model: "We vary $z_{\rm big}$ between 2$H$ and 3.5$H$"]
  - parameter: Mdot 2e-9 Msun/yr, alpha0 0.0007, Rc 60 AU, Md 0.04 Msun [Table S1: "Viscosity coefficient: $\alpha_0$ | 0.0007"]
  - assumption: amax small 0.25 um, big 1 mm [Physical model: "$a_{max}^{small}=0.25 \mu$m (as in the interstellar medium) and $a_{max}^{big}=1$ mm"]
  - validation: good fit to broadband SED except mid/far-IR [Physical model: "this physical model provides a good fit to the broadband spectral energy distribution (SED) of the disk of TW Hya"]
- limitation (authors): Vertical disk structure is uncertain; vertical N2H+ boundaries fixed [Physical model: "The details of the vertical structure in the TW Hya disk are therefore uncertain"]
- not stated (card): Imaging parameters (weighting, robust, cell, image size, masking, deconvolver); Line-free channel selection and self-cal solution intervals; Grid ranges and step sizes for Rin, Rout, p, N100; Full disk model density/temperature structure files; Flux scale uncertainty for the ALMA data

### 2014ApJ...787..112C: Herschel Observations of Extraordinary Sources: Analysis of the HIFI 1.2 THz Wide Spectral Survey toward Orion KL. I. Methods (2014; star_formation, astrochemistry, milky_way_ism; multi_facility_alma_minor)
- question: What are the molecular column densities, abundances and rotation temperatures toward the Orion KL components, derived from LTE/non-LTE modeling of the full HIFI 480-1907 GHz survey combined with IRAM 30 m data?
- step 1: Fit LTE models per molecule
  - method: XCLASS models fit by hand, with MAGIX Levenberg-Marquardt in some cases, to HIFI+IRAM spectra by component [3.3 XCLASS modeling: "The emission was then fit by varying the free parameters (i.e. $T_{\rm rot}$, $N_{\rm tot}$, v$_{\rm lsr}$, and $\Delta$v) by hand until good agreement, as assessed by eye"]
  - software: XCLASS, MAGIX
  - parameter: Source sizes 10'' hot core/compact ridge, 30'' plateau, 180'' extended ridge [Table 2: "| Hot Core | 10 | 3.1 $\times$ 10$^{23}$ |"]
  - assumption: kappa_1.3mm=0.42 cm2/g, beta=2, dust-to-gas 0.01, NH2=2.5e24 cm-2 for dust opacity [3.3 XCLASS modeling: "We also set $\beta$ = 2 and $\chi_{\rm dust}$ = 0.01."]
  - fitting: Mostly by-eye, MAGIX Levenberg-Marquardt for some [3.3 XCLASS modeling: "we derived most models by hand"]
  - validation: Reduced chi-square over HIFI band [3.3 XCLASS modeling: "we computed a reduced $\chi^{2}$ metric (described in the Appendix) for each model across the entire HIFI band"]
- result: Molecules detected = 39 molecules (79 isotopologues) ± not stated count [4.1 The Full Band Model and Line Statis…: "In total, we detect 79 isotopologues of 39 molecules."]
- result: Identified lines in HIFI survey = ~13,000 ± not stated count [4.1 The Full Band Model and Line Statis…: "we obtain a total of $\sim$ 13,000 identified lines in the Orion KL HIFI survey at or above 3 $\sigma$"]
- result: Unidentified line fraction = ~12% ± not stated percent [4.4 Unidentified Lines: "leading to a U line fraction of $\sim$ 12%"]
- result: Tvib HCN nu2=1/nu=0 hot core = 270 ± 20 K [Table 9: "| HCN | $\nu_{2}$=1 / $\nu$=0 | 270 $\pm$ 20 | ... |"]
- result: CH3CN Trot hot core = 260 ± 10% K [5.1 CH3CN: "We derive $T_{\rm rot}$ = 260, 230, and 120 K for the hot core, compact ridge, and plateau, respectively."]
- limitation (authors): LTE, no radiative pumping, constant source size assumed; some species optically thick [4.1 The Full Band Model and Line Statis…: "both XCLASS and MADEX do not include radiative excitation effects which are likely important for some species"]
- not stated (card): CASA version, clean parameters, weighting and beam for ALMA maps; Line-free channels and integration ranges for ALMA moment maps; ALMA map noise and beam sizes; Exact XCLASS/MADEX model input files (provided only online)

### 2020ApJ...892...66M: The ALMA Spectroscopic Survey in the HUDF: The Cosmic Dust and Gas Mass Densities in Galaxies up to z ∼ 3 (2020; high_z_galaxies; large_program_or_survey)
- question: How do the cosmic dust and gas (H2+HI) mass densities in galaxies, above given stellar masses, evolve with redshift up to z~3, from stacking the ASPECS 1.2 mm map at positions of H-band selected galaxies?
- step 1: Select H-band sample and stellar-mass completeness
  - method: Select H<=27 galaxies from master catalogue (555 galaxies); completeness limit from fitting L_H–M* power law plus 1 sigma scatter [3 Sample: "we kept only the 555 galaxies with an observed total[^3] $H$-band magnitude brighter than 27, of which 281 had a spectroscopic redshift."]
  - software: MAGPHYS, EAZY
  - parameter: Stellar masses from MAGPHYS using 0.37-8.0 um photometry plus 1.2 mm flux [3 Sample: "We used the galaxy’s photometry between 0.37$\,\mu$m and 8.0$\,\mu$m, as well as their 1.2 mm flux density (or upper limit)."]
  - fitting: M* = C L^alpha power law per redshift bin [3 Sample: "we fitted the correlation between the observed-frame $H$–band (1.6 $\mu$m) luminosities of galaxies and their stellar masses (derived as described above) with a simple power law"]
  - validation: Stellar mass functions agree with Mortlock+15 and Davidzon+17 above limits [3 Sample: "Down to our stellar mass–completeness limits, these stellar mass functions agree, within the uncertainties, with the fits inferred by (cite: mortlock_2015) and (cite: davidzon_2017)"]
- step 2: Convert 1.2 mm flux to dust and gas mass
  - method: Optically thin dust mass equation (Kovacs 2010) with CMB correction; gas mass from metallicity-dependent gas-to-dust ratio [4.1: "In the optically thin approximation, which is almost always valid at the long wavelengths probed by our observations, the dust mass ($M_{\rm dust}$ in $M_{\odot}$) of a galaxy can be inferred"]
  - parameter: beta=1.8; kappa=0.0431 m^2/kg at 352.6 GHz [4.1: "we adopted $\kappa_{\nu_0} = 0.0431\,$m$^2\,$kg$^{-1}$ with $\nu_{0}=352.6\,$GHz (cite: li_2001)"]
  - assumption: T_dust = 25 K mass-weighted [4.1: "we used a mass-weighted mean dust temperature of $\langle T\rangle_{\rm M}=T=25\,$K"]
  - assumption: GDR = 100 at solar metallicity, 12+log(O/H)=8.67; metallicity from mass-metallicity relation [4.1: "is equal to 100 at solar metallicity, $[12+{\rm log(O/H)}]_\odot=8.67$"]
  - validation: Varied T (15-35 K) and beta (1.5-2.0) to assess systematics [4.1: "a dust temperature range of $T\sim15-35\,$K implies a systematic uncertainty for our dust masses of 25%–50%."]
- limitation (authors): Pencil-beam survey affected by cosmic variance (~42-58%) [5.3: "our estimates of $\rho_{\rm dust}$ are affected by cosmic variance, which is only partly included in the Poissonian uncertainties."]
- limitation (authors): Dust-based gas may be biased against atomic phase; low-metallicity GDR relation uncertain [6.1: "This implies that dust-based gas mass estimates might be biased against the dust in the atomic phase."]
- not stated (card): Exact astrometric-offset-corrected catalogue and MAGPHYS stellar masses/metallicities are not tabulated; MAGPHYS configuration and priors; Stack pixel scale and stamp handling of primary-beam correction; Fitting method (algorithm, priors) for f_dust power-law and joint fits; Method for combined uncertainty on extrapolated M>1e8 densities; Cosmic comoving volume per bin calculation details beyond …

### 2025A&A...698A.204H: An ALMA spectroscopic survey of the Planck high-redshift object PLCK G073.4−57.5 confirms two protoclusters (2025; high_z_galaxies, star_formation; observational_alma_primary)
- question: What is the redshift distribution of the galaxies in the Planck-selected field G073, are the two suspected structures (z~1.5 and z~2) real protoclusters, and what are their gas and star-formation properties?
- step 5: Derive stellar mass and SFR
  - method: CIGALE SED fitting (delayed SFH with burst, BC03, Draine14 dust, Calzetti attenuation, solar metallicity); SFR_IR from cmcirsed modified blackbody with Kennicutt&Evans relation [4.1 Stellar masses and star-formation r…: "we assumed a delayed star-formation history with an optional burst, a (cite: chabrier03) IMF, the stellar population models of (cite: bruzual03), the dust models from (cite: draine14), the (cite: calzetti00) attenuation law, and solar metallicity"]
  - software: CIGALE, cmcirsed
  - parameter: beta = 1.8, dust temperature free [4.1 Stellar masses and star-formation r…: "assuming the CO-derived redshift and a dust emissivity-index $\beta$ equal to 1.8 (cite: cortese14; pokhrel16), leaving the dust temperatures as free parameters."]
  - assumption: Chabrier IMF; SFR_IR = 1.40e-10 L_IR [4.1 Stellar masses and star-formation r…: "${\rm SFR_{\rm IR}}\,=\,1.40\times 10^{-10}\times L_{\rm IR}$"]
  - fitting: chi2 best fit; parameters are likelihood-weighted means and standard deviations [4.1 Stellar masses and star-formation r…: "The best-fit is assessed through $\chi^2$, and the best-fit parameters and associated uncertainties are estimated as the likelihood-weighted means and standard deviations."]
  - validation: Compared with Kneissl+19 SFRs and CIGALE with cmcirsed dust model [4.1 Stellar masses and star-formation r…: "However, the differences were within the uncertainties."]
- result: Average dust temperature = 27 ± ±3 K [4.1 Stellar masses and star-formation r…: "The resulting average dust temperature of the sample was found to be (27$\pm$3) K."]
- limitation (authors): Gas mass has large systematic uncertainties from alpha_CO, which are ignored; CI excitation not constrained [4.2 Molecular gas masses: "there are large systematic uncertainties involved in estimating the gas mass, which we ignore here for simplicity."]
- limitation (authors): Simulation comparison is only qualitative [6.1 The large-scale structure probed by…: "this comparison only qualitatively illustrates broad agreement."]
- not stated (card): Exact CASA version and pipeline version; Line-free channel ranges used for continuum subtraction per source; LineSeeker S/N threshold settings beyond the negative-peak cutoff and kernel details; Whether Cycle 2 Band 6 data were reprocessed or Kneissl+19 products used; CIGALE module parameter grids and cmcirsed fit details; Exact selection of the comparison literature sample and the corrections ap…

### 2020ApJ...891...48H: A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk (2020; protoplanetary_disks; observational_alma_primary)
- question: What are the dust substructures, spectral index variations, optical depths and gas cavity of the GM Aur disk at high resolution in Bands 4 and 6?
- step 2: Radial profiles and spectral index
  - method: Deproject images, azimuthally average, smooth 1.1 mm to 2.1 mm resolution, compute alpha = log(I1/I0)/log(nu1/nu0) [3.2. Continuum spectral index: "the CASA imsmooth task is used to smooth the 1.1 mm continuum image to the same resolution as the 2.1 mm image"]
  - software: CASA
  - parameter: P.A. = 57.17 deg, i = 53.21 deg, 1 au bins [3.1. Continuum substructures: "deprojecting the continuum images using P. A. = 57 ◦ . 17 and i = 53 ◦ . 21, then averaging the pixel intensities within annular bins one au wide."]
  - assumption: Distance 159 pc; ~10% flux calibration uncertainty per band [3.2. Continuum spectral index: "Accounting for the ∼ 10% systematic flux calibration uncertainty in each band and assuming that the probability distribution is Gaussian"]
  - validation: Compared with Pinilla et al. 2014 disk-averaged index [3.2. Continuum spectral index: "This is similar to the disk-averaged spectral index (2 . 94 ± 0 . 44) that Pinilla et al. (2014) measured"]
- step 4: Optical depth and grain size constraints
  - method: tau_nominal = -ln(1 - I/B(T)); beta from tau ratio; emergent intensity with scattering via analytic slab approximation [4.2.2. Constraints on dust grain sizes: "we can use the τ nominal values measured from the 1.1 and 2.1 mm surface brightness models to estimate β in optically thin parts of the disk."]
  - software: dsharp_opac
  - parameter: p = 3.5, 2.5, 1.5; a_min = 0.1 um; Td = 30 K (B40), 18 K (B84) [4.2.2. Constraints on dust grain sizes: "fix the minimum grain size at 0.1 µ m"]
  - assumption: Midplane temperature from Macías et al. 2018; DSHARP opacities; gas-to-dust ratio 100 for Toomre Q [4.2.2. Constraints on dust grain sizes: "assuming the standard gas-to-dust ratio of 100 and a stellar mass of 1.32 M ⊙"]
  - validation: Alternative formulae from Birnstiel 2018 and Zhu 2019 give similar results; McClure temperature structure tested [4.2.2. Constraints on dust grain sizes: "Similar results are obtained using formulae based on the Eddington-Barbier approximation from Birnstiel et al. (2018) and Zhu et al. (2019)."]
- result: Disk-averaged spectral index 1.1-2.1 mm = 2.7 ± ±0.2 dimensionless [3.2. Continuum spectral index: "the disk-averaged spectral index between 1.1 and 2.1 mm is α = 2 . 7 ± 0 . 2"]
- result: Peak nominal optical depth B40 and B84 at 1.1 mm = 0.94 and 0.70 ± not stated dimensionless [4.2.1. Constraints on optical depths: "( τ nominal = 0 . 94 and 0 . 70, respectively)"]
- result: Central unresolved flux within 100 mas = 0.28 (1.1 mm), 0.09 (2.1 mm) ± ±0.02 each mJy [6.2. Origin of the central compact emis…: "0 . 28 ± 0 . 02 mJy at 1.1 mm and 0 . 09 ± 0 . 02 mJy at 2.1 mm"]
- limitation (authors): Temperature, flux calibration and degeneracies prevent precise grain size measurements [4.2.2. Constraints on dust grain sizes: "the aim of this section is to comment on which regions of parameter space are consistent with the observations rather than to provide precise measurements."]
- not stated (card): Line-free channels flagged for Band 6 continuum; Self-calibration solution intervals and number of iterations; Gaussian taper parameters for the HCO+ cube; CLEAN thresholds and image size/cell size; Exact visibility binning and weight handling code for the MCMC fits; Which data reduction scripts were used (not released)

### 2019ApJ...875...55W: The MESAS Project: Long-wavelength Follow-up Observations of Sirius A (2019; stellar_physics, debris_disks; observational_alma_primary)
- question: What is the long-wavelength (1.4-9 mm) emission of Sirius A, and is it consistent with PHOENIX stellar atmosphere models and stable over time?
- step 3: Fit power-law brightness temperature template
  - method: Non-linear least squares fit of T_obs = C0 T_phot (lambda/0.45mm)^alpha over 0.45-9.0 mm [Discussion: "Using a non-linear least squares model fitting procedure with the Python SciPy function *curve_fit*, we find best fit values of C$_{0} = 0.67\pm 0.03$ and $\alpha = 0.05\pm 0.02$."]
  - software: SciPy curve_fit
  - assumption: Rayleigh-Jeans limit, T_obs substituted for T_B [Discussion: "by assuming the stellar emission is in the Rayleigh-Jeans limit and substituting $T_{obs}$ for T$_{B}$"]
  - fitting: curve_fit least squares [Discussion: "Using a non-linear least squares model fitting procedure with the Python SciPy function *curve_fit*, we find best fit values of C$_{0} = 0.67\pm 0.03$ and $\alpha = 0.05\pm 0.02$."]
  - validation: Applied to Fomalhaut, predictions consistent with ALMA fluxes [Discussion: "yields a predicted flux of 1.88 mJy and 0.84 mJy for the 2 ALMA wavelengths, respectively."]
- result: C0 = 0.67 ± 0.03 dimensionless [Discussion: "C$_{0} = 0.67\pm 0.03$ and $\alpha = 0.05\pm 0.02$"]
- result: alpha (temperature spectral index) = 0.05 ± 0.02 dimensionless [Discussion: "C$_{0} = 0.67\pm 0.03$ and $\alpha = 0.05\pm 0.02$"]
- result: Predicted Fomalhaut flux at 0.87 and 1.3 mm = 1.88 and 0.84 ± not stated mJy [Discussion: "yields a predicted flux of 1.88 mJy and 0.84 mJy for the 2 ALMA wavelengths, respectively."]
- limitation (authors): Cannot exclude short-lived mm flares; Sirius A not necessarily a template for rapid rotators like Altair [Discussion: "Indeed, we can not exclude the possibility of short-lived mm flares"]
- not stated (card): uvmodelfit starting parameters and fit options; Which ALMA channels/SPWs were averaged and any flagging; ALMA imaging details (weighting, cell size, deconvolver, masks); MUSTANG2 data pipeline details; Data points and weights used in the power-law fit; Fitting range handling for Sirius B

### 2021A&A...656A..46M: ALCHEMI, an ALMA Comprehensive High-resolution Extragalactic Molecular Inventory. Survey presentation and first results from the ACA array (2021; nearby_galaxies, astrochemistry; large_program_or_survey)
- question: What is the molecular richness of the central molecular zone of NGC 253, probed by an unbiased ALMA spectral scan, and what do ACA 15'' spectra reveal about its chemistry, vibrational emission, organics and isotopic ratios?
- step 3: Fit continuum SED
  - method: Grey-body dust plus free-free and synchrotron fitted to STATCONT continuum at the analysis pixel, with Herschel at high frequencies [4.1 Continuum emission: "fits well to a grey-body with dust temperature $T_d=42\pm1$ K, mass $M_d=8.0\pm0.2\times10^5$ M$_\odot$, emissivity $\beta=1.9$"]
  - parameter: kappa0=0.1 cm2/g at 250 GHz; T_e=1e4 K; SFR=2.5 Msun/yr [4.1 Continuum emission: "plus a free-free component to account for the lower frequency emission with SFR=2.5 M$_\odot$ yr$^{-1}$ and $T_e=10^4$ K (cite: DeZotti2019)."]
  - assumption: Beta=1.9 emissivity law [4.1 Continuum emission: "emissivity $\beta=1.9$ (i.e., $S\propto\nu^{3.9}$)"]
  - validation: Compared with Perez-Beaupuits 2018 cold component of 37 K and mass 1e6 Msun [4.1 Continuum emission: "finding good agreement with the cold component fit of 37 K by (cite: Perez-Beaupuits2018)."]
- result: Dust temperature = 42 ± 1 K [4.1 Continuum emission: "dust temperature $T_d=42\pm1$ K, mass $M_d=8.0\pm0.2\times10^5$ M$_\odot$"]
- result: Dust mass = 8.0e5 ± 0.2e5 Msun [4.1 Continuum emission: "mass $M_d=8.0\pm0.2\times10^5$ M$_\odot$"]
- limitation (authors): Calibration uncertainty not included in fit uncertainties; line flux scaling anomalies in some tunings [3.1 Flux calibration accuracy: "only the statistical uncertainty in the fits due the noise in the spectra are considered and not the absolute flux calibration uncertainty mentioned above"]
- limitation (authors): STATCONT continuum subtraction not optimal for lines near noise level [3.3 Continuum subtraction: "continuum subtraction is seen not to be optimal for spectral lines close to the noise level."]
- not stated (card): Explicit line-free channels or STATCONT settings per spectral window; Exact MADCUBA fit settings (algorithm options, mask choices per molecule); CASA version used for processing; tclean threshold values per spectral window; Distance to NGC 253 adopted; Observing dates and per-execution details; Pixel/spectral window data selection for line subsets used in each species fit

### 2017NatAs...1..709O: Millimetre-wave emission from an intermediate-mass black hole candidate in the Milky Way (2017; milky_way_ism, agn_and_quasars; observational_alma_primary)
- question: Is there a compact object (IMBH candidate) at the centre of the broad-velocity-width cloud CO–0.40–0.22, as suggested by the gravitational kick model?
- step 2: Characterise continuum source spectrum and luminosity
  - method: Flux densities at 231 and 266 GHz, spectral index, Planck-function least-squares fit, luminosity at 8.3 kpc, comparison to Sgr A* and X-ray limit [main text: "A least-squares fit to the 231 and 266 GHz fluxes by the Planck function gives $T\simeq\! 9$ K."]
  - assumption: Distance 8.3 kpc [main text: "at a distance of 8.3 kpc(cite: Gillessen09)"]
  - fitting: least-squares Planck fit [main text: "A least-squares fit to the 231 and 266 GHz fluxes by the Planck function gives $T\simeq\! 9$ K."]
  - validation: Chance probability of a background submillimetre galaxy ~0.1% [main text: "the chance probability of a submillimetre galaxy with a flux greater than 10 mJy within a $10\hbox{$^{\prime\prime}$}$ diameter circle is estimated to be only $\sim 0.1\,\%$"]
- result: Continuum flux density at 231 GHz = 8.38 ± 0.34 mJy [main text: "flux densities of $8.38\!\pm\!0.34$ and $9.91\!\pm\!0.74$ mJy, respectively"]
- result: Continuum flux density at 266 GHz = 9.91 ± 0.74 mJy [main text: "flux densities of $8.38\!\pm\!0.34$ and $9.91\!\pm\!0.74$ mJy, respectively"]
- result: Spectral index 231/266 GHz = 1.18 ± 0.65 dimensionless [main text: "The spectral index at 231/266 GHz is $\alpha\!=\!1.18\!\pm\!0.65$"]
- result: Planck-fit temperature = 9 ± not stated K [main text: "gives $T\simeq\! 9$ K"]
- result: Millimetre-wave luminosity nuL_nu = 10^32.3 ± not stated erg/s [main text: "$\nu L_{\nu}\!\sim\! 10^{32.3}$ erg s$^{-1}$"]
- result: X-ray 1–7 keV flux upper limit = 1.4e-14 ± not stated erg cm^-2 s^-1 [main text: "$1.4\!\times\!10^{-14}$ erg cm$^{-2}$ s$^{-1}$ ($\sim\!1$ nJy)"]
- not stated (card): Briggs robust value for continuum imaging; Line-free channels used for uvcontsub and fit order; Which calibrators were used in which epoch; Clean threshold, masks and iterations; Method for measuring continuum flux densities and their errors; Excitation model details for HCN clump mass (60 K, 10^6.5 cm^-3); Method for XMM-Newton upper limit; Mapping of simulation to observed PV diagram, how the s…

### 2019A&A...628A.100D: An ALMA+ACA measurement of the shock in the Bullet Cluster (2019; galaxy_clusters_and_sz; observational_alma_primary)
- question: What are the Mach number and electron-ion equilibration behaviour of the western shock in the Bullet Cluster, measured from the thermal SZ pressure jump with ALMA+ACA plus X-ray priors?
- step 3: Forward-model SZ signal and fit visibilities
  - method: Integrate 3D pressure model (power-law downstream, gNFW upstream) along LoS, apply SZ spectrum with relativistic correction, FFT and sample at uv points, fit jointly ALMA+ACA [2.1 ALMA/ACA observations: "The SZ model image is then Fourier transformed and sampled to the position of the sparse interferometric data."]
  - software: galario, dynesty
  - parameter: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05) [Table 1: "$\mathcal{M}$ | uniform | $\mathrm{min}=1$, $\mathrm{max}=10$"]
  - assumption: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected [2.2.2 Bulk pressure distribution: "we then decide to not include the kinetic SZ effect in our model"]
  - fitting: Dynamic nested sampling with dynesty; posterior medians and 16/84 percentiles [2.3 Implementation details: "we improved the posterior sampling algorithm by adopting the dynamic nested sampling by (cite: Higson2017)."]
  - validation: Prior-only run; robustness tests varying gNFW slopes and centroid; residual dirty images [2.2 Sunyaev-Zeldovich model: "We test for biases in the parameter reconstruction arising from our specific choice for the distribution of priors by performing a *prior-only* run"]
- result: Delta log evidence (instantaneous vs adiabatic) = 1.30 ± +0.71/-1.48 dimensionless [3.2 Collisional equilibration: "$\Delta\log{\mathcal{Z}}=1.30\substack{+0.71\\-1.48}$"]
- limitation (authors): Systematics from cluster geometry and complex post-shock gas distribution; model does not capture X-ray morphology [abstract: "Our analysis is however limited by systematics related to the overall cluster geometry and the complexity of the post-shock gas distribution."]
- not stated (card): Exact binning parameters for visibilities; dynesty settings (live points, stopping criterion); Likelihood form and noise treatment details; Hyperbola shock-geometry best-fit values and X-ray image/region selection; Which ALMA/ACA execution blocks, calibrators and flagging were used; Gridding pixel scale and galario settings; Chandra X-ray values for prior derivation (Markevitch in prep. unpublish…

### 2024ApJ...966...51G: The Size─Linewidth Relation and Signatures of Feedback from Quiescent to Active Star Forming Regions in the LMC (2024; nearby_galaxies, star_formation, milky_way_ism; archival_reuse)
- question: How does stellar feedback affect the size-linewidth relation and virial state of CO clumps in nine LMC GMCs, compared with gravity-driven explanations?
- step 4: Measure clump-averaged star-formation tracers
  - method: Project dendrogram masks to sky and average 8um, Halpha, and u_nu (from Td) maps; noise-addition uncertainties [2.4 Star-Formation Tracer-Based Clump P…: "we project the maximum extent of the dendrogram structure boundaries at any velocity channel onto the sky, and then calculate the average of each star-formation tracer map in this mask."]
  - parameter: u_nu = 8.65e-13 (Td/18 K)^(4+beta) erg cm^-3, beta=1.8 [2.3 IR and Optical Star Formation Indic…: "is $$\begin{equation} \label{eq:u_nu} u_{\nu} = 8.65\times 10^{-13} \left(\frac{T_d}{18\text{K}}\right)^{4+\beta} \text{ erg cm}^{-3} \end{equation}$$"]
  - validation: Compared Td from Gordon 2014 and Utomo 2019 models; nearly linear [2.3 IR and Optical Star Formation Indic…: "We find a nearly linear relationship between $T_d$ from the two models in our sample"]
- limitation (authors): LTE assumptions, possibly optically thin 12CO; sensitivity limited to several Msun/pc^2 [4.3 Caveats and future directions: "the effects of optically thin $^{12}$CO on our mass estimates remains uncertain."]
- limitation (authors): 8um may trace gas column rather than star formation at these scales [2.3 IR and Optical Star Formation Indic…: "These results indicate that $8\ensuremath{\mu}m$ could be preferentially tracing molecular gas column densities over star formation"]
- not stated (card): Exact native data products and which project code maps to which cloud; How the original cubes were calibrated/imaged (taken from earlier papers); SCIMES parameters other than save_isol_leaves (e.g. criterion, similarity kernel); Exact LTE equations, excitation temperature handling and opacity solution; Fiducial relation citation (reference elided in text); ODR weighting details and the confidence…

### 2017MNRAS.466.4201W: 1.3-mm ALMA observations of the Fomalhaut debris system (2017; debris_disks, stellar_physics; observational_alma_primary)
- question: What is the 1.3 mm morphology of Fomalhaut's debris ring, its mm spectral index and grain size slope, and is there central emission in excess of the stellar photosphere indicating an inner debris component?
- step 5: Spectral index and grain size slope
  - method: Bayesian MCMC fit of F_nu ∝ nu^alpha to ring fluxes; q=(alpha_mm-alpha_pl)/beta_s+3 [4 SED Modelling: "The posterior distribution for the spectral index is determined by performing a Bayesian parameter estimation for $F_\nu$."]
  - assumption: alpha_pl=1.84±0.02 (dust 45±5 K), beta_s=1.8±0.2 [4 SED Modelling: "Assuming a dust temperature of $45\pm5$ K yields $\alpha_{pl} = 1.84 \pm 0.02$"]
  - fitting: MCMC, flat prior [4 SED Modelling: "We use an MCMC approach similar to that used for the disc model fitting, incorporating the listed flux uncertainties, and assume a flat prior distribution."]
  - validation: compared with Ricci et al. q and collisional cascade q=3.51 [4 SED Modelling: "Both of these results are also consistent with the predicted $q=3.51$"]
- result: Spectral index 350-6600 um = -2.73 ± 0.13 dimensionless [4 SED Modelling: "$\alpha_{mm} = -2.73 \pm 0.13$"]
- result: Grain size slope q (350-6600 um) = 3.50 ± 0.14 dimensionless [4 SED Modelling: "$q = 3.50\pm 0.14$"]
- limitation (authors): Ring ansae near primary beam edge, so N/S asymmetries and vertical structure unreliable [3.4: "As noted above, the ring ansae are close to the edges of the primary beam. As such, any potential North/South asymmetries are not reliable."]
- not stated (card): Image size and cell size for CLEAN; Whether pipeline or manual calibration and CASA version; Flux scale uncertainty treatment (calibration uncertainty inflating 0.12 vs 0.15 mJy); MCMC proposal widths and initial parameter values, prior ranges; Mapping of image-plane sigma and treatment of primary beam in the fits; Code for the ring model is not provided

### 2014ApJ...795L..25R: Turbulence Sets the Initial Conditions for Star Formation in High-pressure Environments (2014; milky_way_ism, star_formation; observational_alma_primary)
- question: Do theoretical predictions of supersonically turbulent, isothermal cloud structure and star formation thresholds, validated in solar neighbourhood clouds, hold in a high-pressure CMZ cloud?
- step 1: Combine ALMA with scaled Herschel 500 um
  - method: Scale Herschel 500 um to 3 mm assuming greybody nu^(2+beta); combine with ALMA in CASA via CLEAN; test beta values 1.0-2.0 [Deriving the column density: "we performed the image scaling using a range of values for $\beta$ (1.0, 1.2, 1.5, 1.75, 1.9, 2.0)."]
  - software: CASA
  - parameter: beta = 1.2 ± 0.1 chosen [Deriving the column density: "Thus, we assume $\beta$ of 1.2 $\pm$ 0.1."]
  - assumption: T_dust = 20 ± 1 K [Deriving the column density: "thus, we assume T$_{dust}$ is 20 $\pm$ 1 K ."]
  - validation: Removal of zero-spacing imaging artefacts justifies beta ~1.2 [Deriving the column density: "The removal of the image artefacts justifies the value for $\beta$ $\sim$1.2"]
- result: Flux fraction recovered by ALMA-only = ~18 ± not stated % [The column density PDF: "Since the ALMA-only image recovers a small fraction of the total flux ($\sim$ 18%)"]
- limitation (authors): Core unresolved so density is a lower limit; deviation may be from temperature [The column density PDF: "the density is a lower limit since this core is unresolved"]
- not stated (card): Imaging weighting/robust, deconvolver, masks, and CLEAN parameters; Details of the SD+interferometer combination (feathering vs CLEAN model, scaling); N-PDF binning, fitting method, and range used for log-normal fits; Calibrator names and flux scale; Source coordinates and distance adopted; How the 72 Msun core was defined (aperture) and the velocity dispersion source line; CASA/Miriad versions

### 2015A&A...577L...4V: Resolving the stellar activity of the Mira AB binary with ALMA (2015; evolved_stars, stellar_physics; observational_alma_primary)
- question: What are the size, shape, flux densities and spectral indices of Mira A and Mira B at mm wavelengths, and what do they imply about the extended atmosphere, stellar activity and the wind around Mira B?
- step 3: Derive spectral indices and brightness temperatures
  - method: Spectral index within Band 3 from MFS/uv-fits and between bands from flux densities; Tb for uniform disc [Discussion: "For a uniform disc we find $T_b\sim5300$ K at Band 3 ($\sim1.3$ R$_*$) and $T_b\sim2500$ K at Band 6"]
  - assumption: Distance 92 pc [Relative astrometry: "corresponds to $43.4$ AU at a distance of $92$ pc."]
- step 4: Compare with radio photosphere and wind models
  - method: Compare SED/spectral index and Tb with Reid & Menten model and expected Mira B wind emission [Discussion: "Both spectral indexes are not quite in agreement with the model prediction by (cite: reidment97)"]
  - assumption: Ionized cavity gas temperature T=10^4 K [Discussion: "assuming a gas temperatures of $T=10^4\,$K"]
- result: Mira A spectral index within Band 3 = 1.71 ± 0.05 dimensionless [abstract: "from 1.71$\pm$0.05 within Band 3 to $1.54\pm0.04$ between Band 3 and 6"]
- result: Mira A spectral index Band 3 to 6 = 1.54 ± 0.04 dimensionless [abstract: "from 1.71$\pm$0.05 within Band 3 to $1.54\pm0.04$ between Band 3 and 6"]
- result: Mira B spectral index in Band 3 = 1.3 ± 0.2 dimensionless [abstract: "The spectral index of Mira B is 1.3$\pm$0.2 in Band 3"]
- result: Mira B spectral index Band 3 to 6 = 1.72 ± 0.11 dimensionless [abstract: "it rises to $1.72\pm0.11$ between the bands"]
- result: Mira A Band 3 brightness temperature = ~5300 ± not stated K [abstract: "(with brightness temperature $T_b\sim5300$ K)"]
- result: Mira A Band 6 brightness temperature = ~2500 ± not stated K [abstract: "$\sim4.0\times3.6$ AU in Band 6 ($T_b\sim2500$ K)"]
- result: Mira A hotspot brightness temperature = ~10000 ± not stated K [Discussion: "With a size of $\sim4.7$ mas, we find $T_b\sim10000$ K"]
- limitation (authors): Band 3 resolution too poor to confirm the hotspot there; 25 Oct Band 3 epoch affected by resolved calibrator [Discussion: "the worse angular resolution did not allow us to confidently distinguish between a fit of a stellar disc plus compact component or a stellar disc alone."]
- not stated (card): CASA version; Image size and cell size; Initial models/starting parameters for UVMULTIFIT fits and fit-selection criteria; Details of self-calibration (solints, reference antennas, number of iterations); How brightness temperatures were computed (uniform disc assumptions, exact formula); How spectral indices and uncertainties were derived in uv-fits; Baseline range / configuration details

### 2020ApJ...894...76W: The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B (2020; stellar_physics, debris_disks; observational_alma_primary)
- question: What are the submm/mm fluxes and chromospheric structure of debris-poor F-type stars, and is there short-term variability or bias for debris disk studies?
- step 3: Characterize background source near gamma Vir
  - method: Point and Gaussian uvmodelfit; Gaussian preferred; spectral index and beta from two bands [3.2 Additional source: "we fit both a point source and Gaussian model to the object with *uvmodelfit* and find it to be more consistent with a Gaussian."]
  - software: CASA uvmodelfit
  - assumption: Rayleigh-Jeans regime, S_nu ∝ nu^(2+beta) [3.2 Additional source: "assuming the object is in the Rayleigh-Jeans regime with $S_\nu \propto \nu^{2+\beta}$"]
  - validation: Compared expected high-z galaxy counts (~0.5 in field) [3.2 Additional source: "meaning the expected number of objects within our ALMA Band 6 field-of-view is about 0.5"]
- result: Background source Band 7 flux = 430 ± 25 uJy [3.2 Additional source: "The Band 7 total flux is $430\pm25~\mu \rm Jy$ and the Band 6 total flux is $160\pm16~\mu \rm Jy$."]
- result: Background source Band 6 flux = 160 ± 16 uJy [3.2 Additional source: "The Band 7 total flux is $430\pm25~\mu \rm Jy$ and the Band 6 total flux is $160\pm16~\mu \rm Jy$."]
- result: Background source spectral index = ≈2.5 ± not stated dimensionless [3.2 Additional source: "This corresponds to a spectral index $\alpha\approx 2.5$ and a dust emissivity $\beta\approx 0.5$"]
- limitation (authors): gamma Vir models lack constraints at other wavelengths; temperature minimum cannot be analyzed [4.1 Semi-empirical chromospheric model: "Therefore, it is not possible to perform an analysis of the temperature minimum in these two stars."]
- limitation (authors): Variability at longer timescales cannot be ruled out for gamma Lep [4.2 Potential millimeter wavelength var…: "we cannot rule out the possibility of variability at time periods longer than the length of the EBs."]
- not stated (card): CLEAN mask, niter, cell and image size; Whether pipeline products were used or manually re-imaged; spectral line flagging; uvmodelfit starting parameters; KINICH-PAKAL settings, convergence criteria and weighting of data points; Source of stellar parameters (footnotes a-e); How per-scan time series were binned and uncertainties assigned; Gamma Vir EB combination procedure

### 2024A&A...684A..56K: Probing the interstellar medium of the quasar BRI 0952‒0115. An analysis of [C II], [C II], CO, OH, and H<SUB>2</SUB>O (2024; agn_and_quasars, high_z_galaxies, milky_way_ism; archival_reuse)
- question: What are the ISM properties and heating mechanisms (PDR vs XDR) of the lensed quasar BRI 0952-0115 at z=4.432, and what is its evolutionary stage?
- step 6: dust temperature from modified blackbody
  - method: MCMC fit, T 14.742-120 K, beta 1.3-2.5 [5.1: "We explored the parameter space of both of these values using a Markov chain Monte Carlo (MCMC) approach"]
  - software: dust_emissivity
  - fitting: MCMC; sampler not stated [5.1 The -IR luminosity relation: "We explored the parameter space of both of these values using a Markov chain Monte Carlo (MCMC) approach in which the dust temperature was allowed to vary between 14.742 K and 120 K"]
- result: Dust temperature = ~45 K, beta ~2.0 ± large K [5.1: "The best-fit parameters returned from this method were $T_{\rm dust} \sim 45$ K and $\beta \sim 2.0$"]
- limitation (authors): Data not standardized, resolution limited, CO SLED turnover unconstrained [5.3: "these observations are not standardized and suffer from angular resolution limitations"]
- not stated (card): Line-free channel ranges per band; Velocity ranges for moment maps and spectral extraction; Extraction ellipse coordinates; Taper size for band 3; Visilens parameter ranges and priors; Gaussian fit procedure details; Band 7 reduction details (in Kade23); Band 3 and 4 CASA versions inconsistent; Starburst99 assumptions; SFR and LIR values used for depletion time

### 2017Natur.541...58C: A direct localization of a fast radio burst and its host (2017; transients, other; multi_facility_alma_minor)
- question: Where does the repeating FRB 121102 originate, and what are its host and persistent counterpart? ALMA was used to constrain 230 GHz emission and hence host star formation.
- step 2: Convert flux limit to host star formation rate
  - method: Carilli & Yun relation applied to the 3 sigma limit across z = 0.01 to 0.32 [main text: "For our ALMA 3$\sigma$ upper limit of 51 $\mu$Jy and a sub-mm spectral index of 4, we estimate the star formation rate(cite: cy99)"]
  - assumption: sub-mm spectral index of 4 [main text: "a sub-mm spectral index of 4"]
- result: Host SFR upper limit = 0.06 to 19 (z = 0.01 to 0.32) ± not stated Msun/yr [main text: "less than 0.06 to 19 M$_\odot$ yr$^{-1}$ for redshifts $z$ ranging from 0.01 to 0.32"]
- not stated (card): ALMA flux and bandpass calibrators; CASA/pipeline version; Weighting/robust, cell size, image size, continuum channel selection; Exact ALMA position used for the upper limit; Conversion from the 51 uJy limit to the SFR (luminosity scaling details)

### 2015ApJ...798..124R: ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146 (2015; debris_disks; observational_alma_primary)
- question: What is the radial distribution of mm-sized dust in the HD 107146 debris disk, and is there a gap or dip in the dust surface density?
- step 3: derive grain size slope q from mm spectral index
  - method: Fit mm SED alpha, beta = alpha - 2, then Draine (2006) relation for q [4.1 Debris Disk Model: "We then obtained $q = 3.25 \pm 0.09$ from the (cite: Draine:2006) relation."]
  - parameter: a_min ≈ 1.7 μm (blow-out), a_max = 2 cm [4.1 Debris Disk Model: "For this reason we adopted $a_{\rm{max}} = 2$ cm."]
  - assumption: optically thin, Rayleigh-Jeans emission; rho = 1.2 g/cm3 [4.1 Debris Disk Model: "the dust emission at these wavelengths is optically thin and in the Rayleigh-Jeans regime"]
- step 4: fit disk models to visibilities
  - method: Model image multiplied by Gaussian primary beam (24.3''), Fourier transformed and sampled at observed uv points; chi2 minimised for single power-law, power-law with gap, double power-law [4.2 Models - data comparison: "The model visibilities were obtained through a Fourier transform of the image and sampling the model using the same $(u,v)$ data points in the ALMA observations."]
  - software: emcee
  - parameter: model image 2048x2048 pixels of 0.015''; flux scaled as nu^(2+beta), beta=0.4 [4.2 Models - data comparison: "The model image has a size of 2048x2048 pixel with 0.015$''$ pixels."]
  - assumption: axisymmetric, geometrically and optically thin disk; constant dust opacity across disk [4.1 Debris Disk Model: "Our models consider a debris disk as an axisymmetric, geometrically thin and optically thin layer of solids."]
  - fitting: emcee affine-invariant MCMC, several hundred walkers and iterations; best values are the mode of marginalized posteriors with 68.3% intervals [4.2 Models - data comparison: "For each surface density parameterization, `emcee` was run with several hundreds walkers (see (cite: Foreman:2013)) for several hundreds iterations."]
  - validation: Different walker starting positions tested; residual maps and visibility profiles inspected [4.2 Models - data comparison: "We also ran several trials by either varying or not varying the starting positions of the walkers"]
- result: Millimeter spectral index alpha = 2.42 ± 0.16 dimensionless [4.1 Debris Disk Model: "we measured a millimeter spectral index $\alpha = 2.42 \pm 0.16$"]
- result: Grain size distribution slope q = 3.25 ± 0.09 dimensionless [4.1 Debris Disk Model: "We then obtained $q = 3.25 \pm 0.09$"]
- result: Gap radius (single power-law with gap) = 80.9 ± +1.8/-2.6 AU [Table 2: "$R_{\rm{gap}}$ \[AU\] | ... | $80.9^{+1.8}_{-2.6}$"]
- result: Gap width = 9.0 ± +1.0/-1.5 AU [5.2 Single power-law with gap: "radial width $\Delta R_{\rm{gap}} = 9.0^{+1.0}_{-1.5}$ AU"]
- result: Single power-law slope p = 0.74 ± +0.06/-0.05 dimensionless [5.1 Single power-law models: "The $p$ value of $0.74^{+0.06}_{-0.05}$ indicates a surface density which is increasing with radius"]
- result: Double power-law R_break = 68.5 ± +6.2/-2.6 AU [5.3 Double power-law: "$R_{\rm{break}} = 68.5^{+6.2}_{-2.6}$ AU"]
- result: Inclination (single power-law) = 20.6 ± 1.9 deg [Table 2: "$i$ \[deg\] | $20.6 \pm 1.9$"]
- result: Dust mass of best-fit models = ≈0.2 ± not stated Earth masses [7 The non-detection of CO: "have a dust mass of $\approx 0.2~M_{\oplus}$"]
- limitation (authors): Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density [5.3 Double power-law: "The ALMA data presented in this paper do not allow us to distinguish between these possible different functional forms"]
- not stated (card): Number of emcee walkers and iterations (only 'several hundreds') and burn-in; Priors and bounds on model parameters; Clean threshold, mask, cell and image size of the CLEAN images; Whether CASA clean or other tools were used for the visibility extraction and weight rescaling in detail; Which spectral windows/channels were used for continuum (line-free channels excluded CO); Exact dust opacity tab…

### 2019MNRAS.488.1005P: Upper limits on protolunar disc masses using ALMA observations of directly imaged exoplanets (2019; exoplanets, protoplanetary_disks; observational_alma_primary)
- question: How much circumplanetary (protolunar) dust surrounds young directly-imaged exoplanets, and is it enough to form regular satellite systems (~1e-4 Mp)?
- step 2: Radiative transfer disc models to convert flux limit to dust mass limit
  - method: Viscous self-similar surface density disc, vary disc mass until model 1.3 mm flux equals 3 sigma limit, with radmc3d [3 CPD models: "we varied the disc mass until the 3$\sigma$ flux upper limit is matched for each disc"]
  - software: RADMC-3D
  - parameter: slope -1; r_c = 0.4 or 0.04 R_Hill; minimum radius r_c/10; aspect ratio 0.1; 2 deg inclination to planet orbit [3 CPD models: "A constant disc vertical aspect ratio of 0.1 is assumed."]
  - parameter: dust size 1 um to 1 cm, exponent -3.5; opacity 2.3 cm2/g at 1.3 mm [3 CPD models: "This yields an absorption opacity of 2.3 cm$^2$ g$^{-1}$ at 1.3 mm."]
  - assumption: Disc inclination 30 deg from face on (beta Pic b 85 deg) [3 CPD models: "we assumed disc inclinations of $30\deg$ from face on for all systems"]
  - assumption: Star and planet luminosities heat dust; anisotropic scattering included [3 CPD models: "The star and planet luminosities are included as energy sources that set the dust temperature."]
  - validation: Scale-height test for PZ Tel changes flux by <~10%; comparison with Ricci2017b limits [footnote 5: "found that a more realistic scale-height only affects the emitted fluxes by $\ensuremath{\lesssim}$10%"]
- result: Mmax/Mp PZ Tel b (0.4 / 0.04 R_Hill) = 2.5e-7 / 2.0e-7 ± not stated dimensionless [Table 1: "2.5$\times$10$^{-7}$ | 2.0$\times$10$^{-7}$"]
- result: Mmax/Mp 51 Eri b (0.4 R_Hill) = 2.2e-6 ± not stated dimensionless [Table 1: "2.2$\times$10$^{-6}$"]
- result: Mmax/Mp AB Pic b (0.4 / 0.04 R_Hill) = 5.0e-6 / 2.4e-6 ± not stated dimensionless [Table 1: "5.0$\times$10$^{-6}$ | 2.4$\times$10$^{-6}$"]
- result: Mmax/Mp kappa And b (0.4 / 0.04 R_Hill) = 9.0e-7 / 1.4e-6 ± not stated dimensionless [Table 1: "9.0$\times$10$^{-7}$ | 1.4$\times$10$^{-6}$"]
- result: Dust opacity at 1.3 mm = 2.3 ± not stated cm2 g-1 [3 CPD models: "This yields an absorption opacity of 2.3 cm$^2$ g$^{-1}$ at 1.3 mm."]
- limitation (authors): System ages uncertain by ~50% [4.1 Viscous evolution: "the age of these systems is uncertain and could vary by $\sim$50%"]
- limitation (authors): Gas (CO) not analysed [2 Data description: "Searching for low-level gas in these systems is beyond the scope of this paper"]
- not stated (card): Which observing blocks and how many per target; target phase centres; Measured RMS values per target in uJy (only 3-sigma limits in table); Dust composition fractions and optical constants for astrosilicate, amorphous carbon, water ice; Dust grain internal density and scattering treatment details for radmc3d; Stellar and planetary luminosity inputs and grid resolution for RT; Number of photons an…

### 2020A&A...644A..84M: The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. I. Isomers of C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> (2020; astrochemistry, star_formation; observational_alma_primary)
- question: Which C2H4O2 isomers (methyl formate, glycolaldehyde, acetic acid) are detected in the hot core G31.41+0.31, with what abundances and emission sizes, and what do they imply for formation pathways?
- step 1: Create continuum map and N(H2)
  - method: STATCONT continuum from spec5 BB1; 2D Gaussian fit with imfit; N(H2) from flux in the extraction area [3.1 Continuum: "We have fitted a 2D gaussian to the continuum emission of the main core using the task *imfit* of CASA"]
  - software: CASA, STATCONT
  - parameter: flux 0.1 Jy at 99.0 GHz [3.1 Continuum: "The flux of the continuum inside the area from which we extracted the spectrum is of 0.1 Jy at the mean frequency of 99.0 GHz"]
  - assumption: Td = 150 K, beta = 2.0, k0 = 0.8 cm2/g at 220 GHz, mu = 2.33, gas-to-dust 100 [3.1 Continuum: "Assuming a dust temperature of $150\,\mathrm{K}$, $\beta = 2.0$, a dust opacity coefficient $k_0 = 0.8\,\mathrm{cm^2/g}$ at 220 GHz"]
  - validation: Consistent within a factor ~4 with Rivilla et al. 2017 [3.1 Continuum: "This value is consistent within a factor $\sim4$ with the previous estimate by (cite: rivilla2017a)."]
- result: N(H2) in 1.2'' beam = 1.0e25 ± ±0.2e25 cm-2 [Table 3: "$N_{\rm{H_2}}=(1.0\pm0.2)\mathrm{\times10^{25}\,cm^{-2}}$"]
- result: Continuum deconvolved size of HMC = 1.41'' x 1.22'' ± not stated arcsec [3.1 Continuum: "the deconvolved size of the continuum being $1.41\ensuremath{''}\times1.22\ensuremath{''}$"]
- limitation (authors): Tex-Ntot degeneracy for AA gives a factor ~2 uncertainty on Ntot [4.2 Acetic Acid: "with an uncertainty on $N_{\rm{tot}}$ of a factor $\sim2$"]
- limitation (authors): Some MF transitions under-reproduced; unidentified blends possible [4.1 Methyl Formate: "we cannot exclude that some of these transitions may also be blended with still unidentified molecular species"]
- not stated (card): Whether the archive pipeline or manual calibration and CASA version were used; Exact tclean parameters (deconvolver, niter, threshold, masks, image size); How the beam was matched to 1.2'' (imsmooth/restoringbeam details); STATCONT parameters; XCLASS optimizer algorithm, start values, iterations and the preliminary-fit FWHM/vLSR procedure; Exact fit frequency ranges and line lists (only in append…

### 2024A&A...689A.317G: Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii (2024; evolved_stars, astrochemistry, stellar_physics; observational_alma_primary)
- question: What do ALMA continuum, H30alpha and molecular line maps reveal about the inner regions of the symbiotic system R Aqr, and how are weak molecules distributed there?
- step 2: Subtract continuum and clean maps
  - method: uv-plane continuum subtraction then Hogbom CLEAN with two-pass stopping criteria [2 Observations: "We completed a first cleaning using a maximum number of clean components of $\sim$4000."]
  - software: GILDAS
  - assumption: Continuum constant within each spectral window (spectral index 2, <1% variation) [2 Observations: "assuming a spectral index of two, differences in the intensity of the continuum emission smaller than 1 % are expected"]
  - validation: Checked line-free channels for residuals and no overcleaning [2 Observations: "We checked that the final clean maps do not show overcleaned regions."]
- step 3: Measure continuum fluxes and spectral index
  - method: Compare central compact component intensities at 1.3 and 0.45 mm [4.1 Continuum maps: "By comparing the intensities measured for the compact central component of the high-resolution continuum maps at 1.3 and 0.45 mm, we estimated a spectral index of 1.88."]
- result: Continuum spectral index of central component (1.3-0.45 mm) = 1.88 ± not stated dimensionless [4.1 Continuum maps: "we estimated a spectral index of 1.88"]
- result: Central compact continuum flux at 1.3 and 0.45 mm = 30 and 220 ± not stated mJy [4.1 Continuum maps: "The flux of this central component is 30 and 220 mJy at 1.3 and 0.45 mm, respectively."]
- limitation (authors): In-falling component size is not conclusive [5 Modeling: "Therefore, the obtained result concerning the size of the in-falling component is not conclusive."]
- not stated (card): Robust parameter values; Line-free channel ranges per spectral window; Self-calibration solution intervals and reference components; Cell and image sizes; CASA and GILDAS versions; Model code and fitting figure of merit; dust Gaussian parameters; Band 7 flux date inconsistency (November 2018 vs 2017)

### 2024ApJ...963....1O: "Beads-on-a-string" Star Formation Tied to One of the Most Powerful Active Galactic Nucleus Outbursts Observed in a Cool-core Galaxy Cluster (2024; galaxy_clusters_and_sz, star_formation, agn_and_quasars; multi_facility_alma_minor)
- question: How do the cooling ICM, an AGN outburst, the warm ionized gas, cold molecular gas and the 'beads on a string' star formation relate in the merging cool-core cluster SDSS 1531?
- step 4: Constrain continuum and dust mass
  - method: 2-sigma continuum upper limit converted to dust mass via modified blackbody [3.4.4 Undetected Continuum: "we modeled the emission $S_\nu$ as a modified blackbody using the following equation"]
  - parameter: beta = 1.8, kappa_500um = 0.051 m^2/kg [3.4.4 Undetected Continuum: "$\kappa_{500 \mu\mathrm{m}} = 0.051$ m$^2$ kg$^{−1}$, and $\beta = 1.8$"]
  - assumption: dust temperature 25 K [3.4.4 Undetected Continuum: "Assuming a dust temperature of 25 K (cite: davis_wisdom_2017)"]
- result: Dust mass upper limit = 3.7e8 ± not stated Msun [3.4.4 Undetected Continuum: "we obtain a maximum dust mass of $3.7 \times 10^8$ M$_\odot$"]
- result: Continuum 2-sigma upper limit = 4.87e-4 ± not stated mJy/beam [3.4.4 Undetected Continuum: "we place $2\sigma$ upper limits of $4.87 \times10^{-4}$ mJy beam$^{-1}$ on the continuum"]
- limitation (authors): X_CO uncertainty may overestimate molecular mass by a factor of a few [3.4.3 Mass Distribution: "we may overestimate the total molecular mass by a factor of a few"]
- limitation (authors): Chandra data too shallow to resolve cavity [3.1.1: "the current X-ray data is too shallow to resolve"]
- not stated (card): Briggs robust value tested; Line-free channels and order used for continuum subtraction; clean threshold, mask, niter, cell and image size; Which of the Compact/Extended execution blocks were combined in the final cube; Aperture definition and four-Gaussian fit initial guesses for spectrum; Rest frequency/velocity frame used for channel binning; Whether archive pipeline products were used or the …

### 2015ApJ...813..118M: Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations (2015; nearby_galaxies, star_formation; observational_alma_primary)
- question: How do free-free continuum (33 and 94.5 GHz) and dense gas tracers (HCN, HCO+ J=1-0) compare on ~90 pc scales in three regions of NGC 3627, and how do dense gas fraction and star formation efficiency relate?
- step 3: Spectral index map and thermal fraction
  - method: Convolve 94.5 GHz to 33 GHz beam, regrid, compute alpha for >3 sigma pixels; thermal fraction with fixed non-thermal index [3.1 Spectral Indices: "after convolving the slightly higher resolution 94.5 GHz data to match the beam of the 33 GHz data and putting the data on the same grid"]
  - software: CASA
  - assumption: alpha_NT = -0.85; free-free optically thin; negligible AME and thermal dust [3.1 Spectral Indices: "We took the non-thermal spectral index to be $\alpha^{\rm NT} = -0.85$"]
  - validation: Tested alpha_NT=-0.6; AGN contribution <3% estimated [3.1 Spectral Indices: "by instead assuming $\alpha^{\rm NT} = -0.6$, the mean 33 GHz thermal fractions over the nucleus, Enuc. 1, and 2 are 80, 76, and 62%, respectively"]
- result: mean 33-94.5 GHz spectral index (nucleus, Enuc.1, Enuc.2) = -0.10, -0.15, -0.27 ± std 0.20, 0.18, 0.15 dimensionless [3.1 Spectral Indices: "we measured mean spectral indices of $\alpha_{\rm 33\,GHz}^{\rm 94.5\,GHz} = -0.10, -0.15,$ and $-0.27$"]
- result: mean 33 GHz thermal fraction (nucleus, Enuc.1, Enuc.2) = 85, 82, 70 ± std 19, 19, 20 % [3.1 Spectral Indices: "we measure corresponding mean 33 GHz thermal fractions over the nucleus, Enuc. 1 and 2 of 85, 82 and 70%, respectively"]
- limitation (authors): Only three regions; nuclear HCN cut off by bandpass; single-component fit poor for Enuc. 2 [2.5 Line Imaging and Photometry: "the detection of HCN towards the nucleus is cut off by the bandpass at a radial velocity of $v_\mathrm{LSRK} \approx 800\mathrm{\,km\,s^{-1}}$"]
- not stated (card): Line-free channels for uvcontsub; ALMA array configuration, baselines, and time on source; CASA version; Image size and cell size; Clean masks and thresholds; Velocity ranges for moment 0 integration; SFR calibration formula and how L33 converts to SFR; Monte Carlo details for velocity dispersion errors; Unit conversion from Jy/beam to K km/s for HCO+, HCN, CO

### 2021A&A...652A..98G: The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies (2021; agn_and_quasars, nearby_galaxies; large_program_or_survey)
- question: What are the sizes, orientations, masses and gas properties of dusty molecular tori in nearby Seyferts, and does AGN feedback leave an imprint on the radial distribution of molecular gas?
- step 3: Spectral index maps
  - method: Combine 230 GHz and 351 GHz images convolved to common resolution 0.13-0.16"; alpha maps before and after point-source subtraction [4.3: "We convolved all the images employed in this analysis to obtain a common range of spatial resolutions $0.13\ensuremath{''}$–$0.16\ensuremath{''}$ (11-18 pc)."]
  - validation: Compared alpha values with expectations for dust vs free-free/synchrotron [4.3 Spectral index maps: "The value derived for $\alpha$ throughout the starburst ring, $\geq2-3$, can be accounted for by dust thermal emission."]
- limitation (authors): Common T_dust adopted for all sources; mass estimates depend on assumed conversion factors [4.4: "In the absence of estimates for each galaxy, we were constrained to adopt a common $T_{\rm dust}$ for all sources"]
- limitation (authors): Spectral index maps only possible for 3 sources [4.3: "meaningful spectral index maps cannot be obtained for the rest of the GATOS galaxies"]
- limitation (authors): Small-number statistics for orientation and correlations [4.5: "Within the limits imposed by the sparse statistics"]
- not stated (card): Exact line-free channels / velocity masks per target; CASA version and pipeline details, calibrators; Cell size, image size, deconvolution and cleaning thresholds in GILDAS; How CO/dust masses were integrated (apertures, noise masks); Details of the 1D-Gaussian strip fits (initial guesses); Subtraction of point source in spectral index maps and beam matching details; XSPEC fit priors/start values…

### 2014Sci...345.1584B: Detection of a branched alkyl molecule in the interstellar medium: iso-propyl cyanide (2014; astrochemistry, star_formation; observational_alma_primary)
- question: Can a branched alkyl molecule (iso-propyl cyanide) be detected in the ISM, and how does its abundance compare with its straight-chain isomer and with chemical model predictions?
- step 6: Derive H2 column density from continuum
  - method: Thermal dust emission at 98.8 GHz with opacity, beta, T assumed; extrapolated to 1'' with r^-1.5 density profile [Continuum emission: "We extrapolate these results for the more compact region where the PrCN emission comes from (FWHM $\sim 1.0''$) by assuming spherical symmetry and a density profile proportional to $r^{-1.5}$(cite: Osorio99)."]
  - assumption: kappa=0.01 cm2/g at 230 GHz, beta=1.0, mu=2.8 per H2, T=150 K, all continuum from dust, distance 8.34 kpc [Continuum emission: "a dust emissivity index $\beta = 1.0$, a mean molecular weight per H$_2$ molecule of 2.8, a temperature of 150 K, and that all the continuum flux is due to thermal dust emission"]
- result: i-PrCN abundance relative to H2 = 1.3e-8 ± 0.2e-8 dimensionless [main text: "we deduce average abundances relative to H$_2$ of $1.3 \pm 0.2 \times 10^{-8}$ for *i*-PrCN and $3.2 \pm 0.5 \times 10^{-8}$ (SEM) for *n*-PrCN"]
- result: n-PrCN abundance relative to H2 = 3.2e-8 ± 0.5e-8 dimensionless [main text: "we deduce average abundances relative to H$_2$ of $1.3 \pm 0.2 \times 10^{-8}$ for *i*-PrCN and $3.2 \pm 0.5 \times 10^{-8}$ (SEM) for *n*-PrCN"]
- result: Peak continuum flux density at 98.8 GHz, northern hot core = 0.24 ± not stated Jy/1.8''x1.3'' beam [Continuum emission: "The peak flux density measured toward the northern hot core at 98.8 GHz is 0.24 Jy/1.8$''$$\times$1.3$''$-beam."]
- result: Average N_H2(1'') = 5.6e24 ± 0.4e24 (rms) cm^-2 [Continuum emission: "$N_{{\rm H}_2}(1'') = 5.6 \pm 0.4 \times 10^{24}$ cm$^{-2}$, $M(1'') = 232 \pm 17$ $M_\odot$"]
- limitation (authors): Preliminary LTE model not fully optimized for ALMA; abundance uncertainties exclude free-free contamination and dust property uncertainties [Line identification and spectral modeli…: "This model has not been fully optimized for ALMA yet but it is already sufficiently reliable to allow for detecting new molecules in the ALMA spectra."]
- not stated (card): Exact line-free channel ranges used for continuum subtraction; CLEAN parameters (weighting/robust, cell size, image size, masks, threshold); Which spectral line and reference antenna/solint used for self-calibration; Full list and frequencies of i-PrCN and n-PrCN transitions used in population diagrams; Weeds LTE parameters for all other molecules in the preliminary model; Details of free-free co…

### 2024Ap&SS.369...18M: Multi-wavelength observation of MAXI J1348─630 during the outburst in 2019 (2024; stellar_physics; observational_alma_primary)
- question: What are the broadband spectral properties of MAXI J1348–630 and its radio/X-ray luminosity correlation during the decay phase of the January 2019 outburst?
- step 2: Measure flux densities and spectral index
  - method: 2D Gaussian fit with imfit in each band, then power-law fit to the continuum spectrum [3.1 Continuum image of MAXI J1348–630 u…: "we fitted the 2D Gaussian over the black hole candidate MAXI J1348–630 using the `CASA` task `IMFIT`."]
  - software: CASA imfit
  - fitting: Power law F_nu ∝ nu^alpha; fitting method not stated [3.1 Continuum image of MAXI J1348–630 u…: "The continuum radio spectrum is fitted using power law ($F_{\nu}\propto \nu ^{\alpha}$) with a spectral index of $\alpha = 0.28\pm 0.02$."]
- result: Millimeter flux density range = 12.18–18.47 ± not stated mJy [3.1 Continuum image of MAXI J1348–630 u…: "The measured flux densities at different frequencies vary between $\sim$12.18 mJy and $\sim$18.47 mJy."]
- result: Millimeter spectral index alpha = 0.28 ± 0.02 dimensionless [3.1 Continuum image of MAXI J1348–630 u…: "spectral index of $\alpha = 0.28\pm 0.02$"]
- limitation (authors): Cannot draw conclusions on continuum morphology [3.1 Continuum image of MAXI J1348–630 u…: "So, we cannot draw any conclusions about the continuum morphology of MAXI J1348–630."]
- not stated (card): Image size, cell size, number of clean iterations, threshold and masking; Self-calibration solution intervals, number of rounds, and solution type; Spectral windows used for each band's continuum and line-free channels; Method for the molecular line search and column density upper limits (software, excitation temperature, line width); Band 6 frequency range is misprinted in Table 1; Whether the p…

### 2020PASJ...72...62A: Discovery of radio jets in the Phoenix galaxy cluster center (2020; galaxy_clusters_and_sz, agn_and_quasars; multi_facility_alma_minor)
- question: Are there spatially resolved radio jets/lobes (AGN feedback) in the Phoenix cluster BCG, and what is the origin of the radio emission near the center?
- step 1: ATCA flux measurement and spectral index
  - method: Point-source fits with IMFIT; error-weighted least-squares power-law fit of four in-band images [4.1 Synthesized Images: "We evaluated flux densities of Sources C1 and W using the MIRIAD task IMFIT with the option OBJECT=POINT."]
  - software: MIRIAD
- step 2: Combine ATCA 18 GHz with ALMA 92 GHz for spectra and astrometric cross-match
  - method: Spectral index from ATCA 18 GHz and ALMA 92 GHz; positions cross-matched [4.2 Frequency Spectra: "The results of the spectral index measurement using ATCA 18 GHz and ALMA 92 GHz data are shown in figure [2](#f02)."]
- result: Source C1 flux density at 18 GHz = 3.395 ± 0.132 mJy [4.1 Synthesized Images: "We obtained the flux densities of 3.395 $\pm$ 0.132 mJy for Source C1"]
- result: Source C1 spectral index ATCA+ALMA = -0.37 ± not stated dimensionless [4.2 Frequency Spectra: "We obtain a flatter ($\alpha=-0.37$) spectrum for Source C1 compared to the in-band spectrum"]
- result: Source C1 in-band spectral index = -0.50 ± not stated dimensionless [4.2 Frequency Spectra: "We obtained the in-band spectral index of $\alpha=-0.50$ for the brightest Source C1."]
- result: Source W spectral index = -0.58 (with 19.5 GHz), -0.62 (without) ± not stated dimensionless [4.2 Frequency Spectra: "for Source W, $\alpha= -0.58$ and $-0.62$ with and without the data at 19.5 GHz in the fit"]
- not stated (card): ALMA project code, calibration, imaging parameters for Band 3 data; ALMA Band 3 flux density of Sources C1-C4 and W; ALMA Band 6 upper limits values

### 2020ApJ...892...99C: The Surprisingly Low Carbon Mass in the Debris Disk around HD 32297 (2020; debris_disks; observational_alma_primary)
- question: What are the spatial distribution and mass of neutral carbon in the HD 32297 debris disk, and can a secondary gas production model explain the C0 and CO observations?
- step 2: Measure total CI and continuum fluxes and spectral index
  - method: Integrate emission above 3 sigma; error from flux samples in empty regions plus 10% calibration in quadrature [3.1 Total C I and continuum emission: "by integrating all emission above 3$\sigma$"]
- result: Total CI 492 GHz flux = 4.0e-20 ± 0.4e-20 W m-2 [3.1 Total C I and continuum emission: "We find a total 492 GHz C I flux of $(4.0\pm0.4)\times10^{-20}$ W m$^{-2}$"]
- result: Total 487 GHz continuum flux = 22.0 ± 2 mJy [3.1 Total C I and continuum emission: "($22.0\pm2$ mJy)"]
- result: Sub-millimeter spectral index = 2.4 ± not stated dimensionless [3.1 Total C I and continuum emission: "we derive a sub-millimeter spectral index of 2.4"]
- limitation (authors): Temperature poorly constrained by the data [3.3 Modeling of the C I emission: "We note that the temperature is not well constrained by our data."]
- limitation (authors): Calibration uncertainty not included in MCMC fit [3.3 Modeling of the C I emission: "We note that the calibration uncertainty, not included in the MCMC fit, might introduce some additional uncertainty in the fitted parameters."]
- not stated (card): Line-free channels and continuum fit order for uvcontsub; Clean threshold, niter, mask, cell and image size, channel width of the cube; Exact model grid size/resolution and the likelihood form; Initial walker positions and convergence checks for emcee; Photodissociation cross-section files (private communication); ISRF scaling used (Draine 1978 normalisation); Whether the line cube was Hanning-sm…

### 2024RMxAA..60..355R: The Radio Continuum Source Projected Near HR 8799 (2024; debris_disks, exoplanets; archival_reuse)
- question: Is the radio continuum source seen near HR 8799 (VLA 3 GHz and ALMA 340 GHz) physically associated with the star/exoplanets, or is it a background galaxy?
- step 3: Spectral index and variability
  - method: Split the 2-4 GHz band into two 1 GHz halves; compare positions and fluxes in VLA and ALMA and per-epoch [3.1 VLA data: "Dividing the data in two windows of 1 GHz wide each centered at 2.5 and 3.5 GHz, we obtain flux densities of 16.5$\pm$4.1 and 25.3$\pm$2.9 $\mu$Jy"]
- result: VLA in-band spectral index = 1.3 ± 0.9 dimensionless [3.1 VLA data: "spectral index of $\alpha$ = 1.3$\pm$0.9"]
- result: Spectral index 3 to 340 GHz = 0.69 ± 0.03 dimensionless [3.3 Comparison between the VLA and the …: "The spectral index between the 3.0 and 340.0 GHz flux densities is 0.69$\pm$0.03."]
- limitation (authors): ALMA flux lower than Faramaz et al. because ACA data were not included [2.2 ALMA: "This difference is probably due to the fact that Faramaz et al. (2021) included in their analysis data from the Atacama Compact Array, recovering more extended flux."]
- not stated (card): ALMA calibration procedure (pipeline vs manual) and flux scale; cell size, image size, masks, clean threshold and iterations; Spectral window/channel selection details for the CO exclusion; VLA image rms, cell and size, and clean parameters; How the 0.49 mJy at 338 GHz flux was derived; Method for per-epoch flux measurement

### 2015A&A...573L...4L: ALMA observations of α Centauri. First detection of main-sequence stars at 3 mm wavelength (2015; stellar_physics, sun; observational_alma_primary)
- question: Can ALMA resolve the alpha Cen A and B components at mm/submm wavelengths, give their flux ratios, and extend the SED to 3 mm to probe the chromospheric temperature minimum and free-free emission?
- step 2: measure flux densities, ratios and spectral indices
  - method: Fluxes of A and B in each band; B/A ratios; spectral index alpha between bands [Results: "The measured flux densities are reported in Table [\[data\]](#data) and also displayed graphically in Fig. [2](#freq)."]
- result: alpha Cen A flux density Band 3 (3075 um) = 3.373 ± 0.011 mJy [Table 1: "$3.373\pm 0.011$ \[307\]"]
- result: alpha Cen B flux density Band 3 = 1.585 ± 0.016 mJy [Table 1: "$1.585\pm 0.016$ \[99\]"]
- result: alpha Cen A flux density Band 7 = 26.06 ± 0.19 mJy [Table 1: "$26.06\pm 0.19$ \[137\]"]
- result: alpha Cen B flux density Band 7 = 12.04 ± 0.23 mJy [Table 1: "$12.04\pm 0.23$ \[52\]"]
- result: alpha Cen A flux density Band 9 = 107.2 ± 1.5 mJy [Table 1: "$107.2\pm 1.5$ \[71\]"]
- result: alpha Cen B flux density Band 9 = 57.6 ± 4.5 mJy [Table 1: "$57.6\pm 4.5$ \[13\]"]
- result: flux ratio B/A at 3.1 mm = 0.47 ± 0.006 dimensionless [Results: "$=0.47\pm0.006$ at 3.1 mm"]
- result: flux ratio B/A at 870 um = 0.46 ± 0.01 dimensionless [Results: "$=0.46\pm0.01$ at 870 $\mu$m"]
- result: flux ratio B/A at 440 um = 0.54 ± 0.04 dimensionless [Results: "$S_{\!\nu}^{\rm B}/S_{\!\nu}^{\rm A}=0.54\pm0.04$ at 440 $\mu$m"]
- result: spectral index alpha(7,3) A / B = 1.62 / 1.61 ± not stated dimensionless [Table 1: "| 2.08 | 1.62 |"]
- limitation (authors): Sparse spectral sampling prevents a conclusive statement on changing opacities [Discussion: "a more conclusive statement would require a tighter spectral sampling, including the intermediate ALMA bands."]
- not stated (card): CASA version; Briggs robust value; Method of flux extraction (aperture vs Gaussian fit) and uncertainties; Phase/pointing offsets and details of self-cal solint; Distance to alpha Cen used

### 2024NatAs...8..774B: JWST detection of a supernova associated with GRB 221009A without an r-process signature (2024; transients, star_formation; multi_facility_alma_minor)
- question: Is there a supernova associated with GRB 221009A, does it show r-process enrichment, and what is the host galaxy environment (JWST NIRSpec/NIRCam; ALMA used to constrain the afterglow)?
- step 2: Extrapolate mm flux to NIRSpec epoch and build ALMA-XRT power law
  - method: Fit decline rate using the previous ALMA point, extrapolate to 194 d, and compute spectral index to the XRT flux [5.4 ALMA Observations: "implying an extrapolated mm-band flux density of $(99\pm23)\,\mu$Jy at the time of the NIRSPEC observations (194 days, observer frame)"]
- result: mm-band temporal decline index = -1.54 ± 0.08 dimensionless [5.4 ALMA Observations: "$\alpha_{\rm mm}=-1.54\pm0.08$"]
- result: ALMA-XRT spectral index = 0.63 ± 0.03 dimensionless [5.5 Swift/XRT Observations: "$\beta_{\rm ALMA-XRT}=0.63\pm0.03$"]
- limitation (authors): The afterglow/SN decomposition is uncertain and affects the Ni mass [2.2: "Of course, assuming a different afterglow contribution in our spectrum will affect the estimated mass."]
- not stated (card): ALMA CASA version and pipeline version; ALMA flux calibrator and imaging parameters (weighting, cell, size); imfit region and fitting details; ALMA array configuration, integration time, and beam

## All papers in this technique

- 2012ApJ...752L..30W (2012): [C II] Line Emission in Massive Star-forming Galaxies at z = 4.7
- 2013ApJ...767...88W (2013): ALMA Redshifts of Millimeter-selected Galaxies from the SPT Survey: The Redshift Distribution of Dusty Star-forming Galaxies
- 2013ApJ...770...13W (2013): Redshift 6.4 Host Galaxies of 10<SUP>8</SUP> Solar Mass Black Holes: Low Star Formation Rate and Dynamical Mass
- 2013Sci...341..630Q (2013): Imaging of the CO Snow Line in a Solar Nebula Analog
- 2014ApJ...784...62A (2014): Circumstellar Disks around Binary Stars in Taurus
- 2014ApJ...785..111W (2014): Properties of Submillimeter Galaxies in the CANDELS GOODS-South Field
- 2014ApJ...787...42C (2014): An ALMA Continuum Survey of Circumstellar Disks in the Upper Scorpius OB Association
- 2014ApJ...787..112C (2014): Herschel Observations of Extraordinary Sources: Analysis of the HIFI 1.2 THz Wide Spectral Survey toward Orion KL. I. Methods
- 2014ApJ...791...20R (2014): Brown Dwarf Disks with ALMA
- 2014ApJ...792...34O (2014): ALMA Observation of 158 μm [C II] Line and Dust Continuum of a z = 7 Normally Star-forming Galaxy in the Epoch of Reionization
- 2014ApJ...795L..25R (2014): Turbulence Sets the Initial Conditions for Star Formation in High-pressure Environments
- 2014ApJ...796....1T (2014): Angular Momentum Exchange by Gravitational Torques and Infall in the Circumbinary Disk of the Protostellar System L1551 NE
- 2014ApJ...796...82Z (2014): Spectral and Morphological Analysis of the Remnant of Supernova 1987A with ALMA and ATCA
- 2014Sci...345.1584B (2014): Detection of a branched alkyl molecule in the interstellar medium: iso-propyl cyanide
- 2015A&A...573L...1O (2015): ALMA observations of anisotropic dust mass loss in the inner circumstellar environment of the red supergiant VY Canis Majoris
- 2015A&A...573L...4L (2015): ALMA observations of α Centauri. First detection of main-sequence stars at 3 mm wavelength
- 2015A&A...577A..30A (2015): Tightening the belt: Constraining the mass and evolution in SDC335
- 2015A&A...577L...4V (2015): Resolving the stellar activity of the Mira AB binary with ALMA
- 2015A&A...584A..32M (2015): (Sub)millimetre interferometric imaging of a sample of COSMOS/AzTEC submillimetre galaxies. II. The spatial extent of the radio-emitting re…
- 2015ApJ...798..124R (2015): ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146
- 2015ApJ...801...82H (2015): ALMA Imaging of Millimeter/Submillimeter Continuum Emission in Orion KL
- 2015ApJ...802...69B (2015): Radio and Millimeter Monitoring of Sgr A*: Spectrum, Variability, and Constraints on the G2 Encounter
- 2015ApJ...809...93D (2015): Observational Signatures of Planets in Protoplanetary Disks I. Gaps Opened by Single and Multiple Young Planets in Disks
- 2015ApJ...810...91H (2015): Optical-Infrared Properties of Faint 1.3 mm Sources Detected with ALMA
- 2015ApJ...810L...7V (2015): A Concentration of Centimeter-sized Grains in the Ophiuchus IRS 48 Dust Trap
- 2015ApJ...811L...3T (2015): SXDF-ALMA 1.5 arcmin<SUP>2</SUP> Deep Survey: A Compact Dusty Star-forming Galaxy at z = 2.5
- 2015ApJ...812...27A (2015): ALMA Observations of the Transition from Infall Motion to Keplerian Rotation around the Late-phase Protostar TMC-1A
- 2015ApJ...812..126C (2015): A Compact Concentration of Large Grains in the HD 142527 Protoplanetary Dust Trap
- 2015ApJ...813..118M (2015): Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations
- 2015Natur.522..455C (2015): Galaxies at redshifts 5 to 6 with systematically low dust content and high [C II] emission
- 2015PASJ...67...72T (2015): High-resolution ALMA observations of SDP.81. I. The innermost mass profile of the lensing elliptical galaxy probed by 30 milli-arcsecond im…
- 2016A&A...586A..70L (2016): Anatomy of a blazar in the (sub-)millimeter: ALMA observations of PKS 0521-365
- 2016A&A...596A..75S (2016): Characterizing elusive, faint dusty star-forming galaxies: a lensed, optically undetected ALMA galaxy at z 3.3
- 2016ApJ...816...37V (2016): Bright [C II] and Dust Emission in Three z &gt; 6.6 Quasar Host Galaxies Observed by ALMA
- 2016ApJ...819...82S (2016): Properties of the Interstellar Medium in Star-Forming Galaxies at z ~ 1.4 Revealed with ALMA
- 2016ApJ...819..134B (2016): Planetary Signatures in the SAO 206462 (HD 135344B) Disk: A Spiral Arm Passing through Vortex?
- 2016ApJ...821...82O (2016): Sintering-induced Dust Ring Formation in Protoplanetary Disks: Application to the HL Tau Disk
- 2016ApJ...821L..16C (2016): The VLA View of the HL Tau Disk: Disk Mass, Grain Evolution, and Early Planet Formation
- 2016ApJ...822...80S (2016): The Redshift Distribution of Dusty Star-forming Galaxies from the SPT Survey
- 2016ApJ...823...68S (2016): Gas Dynamics and Outflow in the Barred Starburst Galaxy NGC 1808 Revealed with ALMA
- 2016ApJ...823..160D (2016): An ALMA Search for Substructure, Fragmentation, and Hidden Protostars in Starless Cores in Chamaeleon I
- 2016ApJ...823L..27H (2016): An Extremely High Velocity Molecular Jet Surrounded by an Ionized Cavity in the Protostellar Source Serpens SMM1
- 2016ApJ...826...16E (2016): Protoplanetary Disks in the Orion OMC1 Region Imaged with ALMA
- 2016ApJ...826...26T (2016): Revealing a Detailed Mass Distribution of a High-density Core MC27/L1521F in Taurus with ALMA
- 2016ApJ...826..112S (2016): ALMA Imaging and Gravitational Lens Models of South Pole Telescope—Selected Dusty, Star-Forming Galaxies at High Redshifts
- 2016ApJ...828...46A (2016): ALMA Survey of Lupus Protoplanetary Disks. I. Dust and Gas Masses
- 2016ApJ...828...56W (2016): Discovery of a Galaxy Cluster with a Violently Starbursting Core at z = 2.506
- 2016ApJ...833...68A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Proper…
- 2016ApJ...833L...6C (2016): ALMA Reveals Potential Localized Dust Enrichment from Massive Star Clusters in II Zw 40
- 2016MNRAS.461.4276D (2016): Space reconstruction of the morphology and kinematics of axisymmetric radio sources
- 2016Natur.535..258C (2016): Imaging the water snow-line during a protostellar outburst
- 2016PASJ...68...43K (2016): Mass constraint for a planet in a protoplanetary disk from the gap width
- 2017A&A...597A..32V (2017): Cavity and other radial substructures in the disk around HD 97048
- 2017A&A...602A..54M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: The extent of the radio-emitting region revealed by 3 GHz imaging with the Ve…
- 2017A&A...602L..10O (2017): The inhomogeneous submillimeter atmosphere of Betelgeuse
- 2017A&A...604A...6S (2017): The physical and chemical structure of Sagittarius B2. II. Continuum millimeter emission of Sgr B2(M) and Sgr B2(N) with ALMA
- 2017ApJ...835...98U (2017): ALMA Deep Field in SSA22: Source Catalog and Number Counts
- 2017ApJ...835L..13S (2017): ALMA Observations of the Water Fountain Pre-planetary Nebula IRAS 16342-3814: High-velocity Bipolar Jets and an Expanding Torus
- 2017ApJ...835L..35M (2017): New ALMA and Fermi/LAT Observations of the Large-scale Jet of PKS 0637-752 Strengthen the Case Against the IC/CMB Model
- 2017ApJ...836L...2B (2017): ALMA [C II] 158 μm Detection of a Redshift 7 Lensed Galaxy behind RXJ1347.1-1145
- 2017ApJ...837...93Y (2017): Tidal Distortion of the Envelope of an AGB Star IRS 3 near Sgr A*
- 2017ApJ...837..174O (2017): L483: Warm Carbon-chain Chemistry Source Harboring Hot Corino Activity
- 2017ApJ...837L..29H (2017): An Extraordinary Outburst in the Massive Protostellar System NGC6334I-MM1: Quadrupling of the Millimeter Continuum
- 2017ApJ...838..146L (2017): ALMA Observations of the Interaction of a Radio Jet with Molecular Gas in Minkowski's Object
- 2017ApJ...839...99P (2017): A Multi-wavelength Analysis of Dust and Gas in the SR 24S Transition Disk
- 2017ApJ...840...32T (2017): Planet Formation in AB Aurigae: Imaging of the Inner Gaseous Spirals Observed inside the Dust Cavity
- 2017ApJ...840..101C (2017): Near-infrared MOSFIRE Spectra of Dusty Star-forming Galaxies at 0.2 &lt; z &lt; 4
- 2017ApJ...841..110S (2017): The Coldest Place in the Universe: Probing the Ultra-cold Outflow and Dusty Disk in the Boomerang Nebula
- 2017ApJ...841..130A (2017): The Luminous Blue Variable RMC 127 as Seen with ALMA and ATCA
- 2017ApJ...844..123F (2017): The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters …
- 2017ApJ...846...70P (2017): Millimeter Spectral Indices and Dust Trapping By Planets in Brown Dwarf Disks
- 2017ApJ...849...90S (2017): Evolution of Molecular Clouds in the Superwind Galaxy NGC 1808 Probed by ALMA Observations
- 2017ApJ...850..178A (2017): Deep Submillimeter and Radio Observations in the SSA22 Field. I. Powering Sources and the Lyα Escape Fraction of Lyα Blobs
- 2017ApJ...850L...2A (2017): ALMA Observations of SMM11 Reveal an Extremely Young Protostar in Serpens Main Cluster
- 2017ApJ...851...83C (2017): Protoplanetary Disks in ρ Ophiuchus as Seen from ALMA
- 2017MNRAS.464L..75F (2017): ALMA observations of the supergiant B[e] star Wd1-9
- 2017MNRAS.466.4201W (2017): 1.3-mm ALMA observations of the Fomalhaut debris system
- 2017MNRAS.467L.120M (2017): The ALMA view of W33A: a spiral filament feeding the candidate disc in MM1-Main
- 2017MNRAS.468L..87C (2017): New ALMA constraints on the star-forming interstellar medium at low metallicity: a 50 pc view of the blue compact dwarf galaxy SBS 0335-052
- 2017MNRAS.469L.123O (2017): ALMA polarization observations of the particle accelerators in the hotspot of the radio galaxy 3C 445
- 2017NatAs...1..709O (2017): Millimetre-wave emission from an intermediate-mass black hole candidate in the Milky Way
- 2017Natur.541...58C (2017): A direct localization of a fast radio burst and its host
- 2017Natur.545..457D (2017): Rapidly star-forming galaxies adjacent to quasars at redshifts exceeding 6
- 2017Sci...355.1285N (2017): [C II] 158-μm emission from the host galaxies of damped Lyman-alpha systems
- 2018A&A...610A..24F (2018): ALMA continuum observations of the protoplanetary disk AS 209. Evidence of multiple gaps opened by a single planet
- 2018A&A...612A.103C (2018): Radio outburst from a massive (proto)star. When accretion turns into ejection
- 2018A&A...616A..56A (2018): Magnetic field in a young circumbinary disk
- 2018A&A...616A..88V (2018): V1094 Scorpii: A rare giant multi-ringed disk around a T Tauri star
- 2018A&A...616L...3B (2018): High-resolution observations of the symbiotic system R Aqr. Direct imaging of the gravitational effects of the secondary on the stellar wind
- 2018A&A...616L..10F (2018): ALMA observations of RCW 120 Fragmentation at 0.01 pc scale&amp;star
- 2018A&A...619A..40M (2018): The radio jets of SS 433 at millimetre wavelengths
- 2018A&A...619A.161C (2018): Evidence for a massive dust-trapping vortex connected to spirals. Multi-wavelength analysis of the HD 135344B protoplanetary disk
- 2018AJ....156..239Z (2018): ALMA Reveals a Collision between Protostellar Outflows in BHR 71
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...853..171G (2018): Distributed Star Formation throughout the Galactic Center Cloud Sgr B2
- 2018ApJ...853..195W (2018): Herschel and ALMA Observations of Massive SZE-selected Clusters
- 2018ApJ...854...97D (2018): An ALMA [C II] Survey of 27 Quasars at z &gt; 5.94
- 2018ApJ...855...24P (2018): Thermal Jeans Fragmentation within ∼1000 au in OMC-1S
- 2018ApJ...855L...2M (2018): Detection of a Millimeter Flare from Proxima Centauri
- 2018ApJ...856L..12N (2018): Molecular Emission from a Galaxy Associated with a z ∼ 2.2 Damped Lyα Absorber
- 2018ApJ...857...87L (2018): New Constraints on Turbulence and Embedded Planet Mass in the HD 163296 Disk from Planet-Disk Hydrodynamic Simulations
- 2018ApJ...859...21A (2018): ALMA Survey of Lupus Protoplanetary Disks. II. Gas Disk Radii
- 2018ApJ...859..103W (2018): Extended Millimeter Emission in the HD 141569 Circumstellar Disk Detected with ALMA
- 2018ApJ...859..111H (2018): The Circumstellar Disk and Asymmetric Outflow of the EX Lup Outburst System
- 2018ApJ...859..165S (2018): Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. I. VLA 1623
- 2018ApJ...860...77E (2018): Protoplanetary Disk Properties in the Orion Nebula Cluster: Initial Results from Deep, High-resolution ALMA Observations
- 2018ApJ...861...91H (2018): ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527
- 2018ApJ...863...19A (2018): The Distinct Evolutionary Nature of Two Class 0 Protostars in Serpens Main SMM4
- 2018ApJ...865...37M (2018): Multiple Rings in the Transitional Disk of GM Aurigae Revealed by VLA and ALMA
- 2018ApJ...866..141K (2018): Extremely Dense Cores Associated with Chandra Sources in Ophiuchus A: Forming Brown Dwarfs Unveiled?
- 2018ApJ...867...48I (2018): Circumnuclear Multiphase Gas in the Circinus Galaxy. II. The Molecular and Atomic Obscuring Structures Revealed with ALMA
- 2018ApJ...867L...6B (2018): Evidence for the First Extragalactic Hydrogen Recombination Line Maser in NGC 253
- 2018ApJ...869..158F (2018): ALMA Detections of the Youngest Protostars in Ophiuchus
- 2018MNRAS.473..879P (2018): The ALMA early science view of FUor/EXor objects - IV. Misaligned outflows in the complex star-forming environment of V1647 Ori and McNeil'…
- 2018MNRAS.475..448T (2018): Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study
- 2018MNRAS.475.5322S (2018): Deuterated formaldehyde in the low-mass protostar HH212
- 2018MNRAS.478.2505I (2018): Radiative transfer modelling of W33A MM1: 3D structure and dynamics of a complex massive star-forming region
- 2018PASJ...70...65U (2018): ALMA deep field in SSA22: Survey design and source catalog of a 20 arcmin<SUP>2</SUP> survey at 1.1 mm
- 2018Sci...362.1034D (2018): The multiple merger assembly of a hyperluminous obscured quasar at redshift 4.6
- 2019A&A...622A..75L (2019): Ring structure in the MWC 480 disk revealed by ALMA
- 2019A&A...623A.150V (2019): The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN
- 2019A&A...623L...8B (2019): Unveiling a cluster of protostellar disks around the massive protostar GGD 27 MM1
- 2019A&A...624A...7V (2019): Spatial segregation of dust grains in transition disks. SPHERE observations of 2MASS J16083070-3828268 and RXJ1852.3-3700
- 2019A&A...626A..36D (2019): ALMA reveals the magnetic field evolution in the high-mass star forming complex G9.62+0.19
- 2019A&A...627A.114K (2019): Massive dust clumps in the envelope of the red supergiant VY Canis Majoris
- 2019A&A...628A..65A (2019): Nuclear molecular outflow in the Seyfert galaxy NGC 3227
- 2019A&A...628A..85V (2019): Disk masses in the Orion Molecular Cloud-2: distinguishing time and environment
- 2019A&A...628A.100D (2019): An ALMA+ACA measurement of the shock in the Bullet Cluster
- 2019A&A...632A..61G (2019): ALMA images the many faces of the <ASTROBJ>NGC 1068</ASTROBJ> torus and its surroundings
- 2019AJ....158..162F (2019): From Scattered-light to Millimeter Emission: A Comprehensive View of the Gigayear-old System of HD 202628 and its Eccentric Debris Ring
- 2019ApJ...870...39V (2019): ALMA Observations of the Molecular Gas in the Elliptical Galaxy NGC 3557
- 2019ApJ...871...72M (2019): The JCMT Transient Survey: An Extraordinary Submillimeter Flare in the T Tauri Binary System JW 566
- 2019ApJ...871..170M (2019): Fire in the Heart: A Characterization of the High Kinetic Temperatures and Heating Sources in the Nucleus of NGC 253
- 2019ApJ...872..112V (2019): Protoplanetary Disk Rings and Gaps across Ages and Luminosities
- 2019ApJ...875...55W (2019): The MESAS Project: Long-wavelength Follow-up Observations of Sirius A
- 2019ApJ...875...96N (2019): Dust Continuum Emission and the Upper Limit Fluxes of Submillimeter Water Lines of the Protoplanetary Disk around HD 163296 Observed by ALMA
- 2019ApJ...876...99S (2019): Star Formation and ISM Properties in the Host Galaxies of Three Far-infrared Luminous Quasars at z ∼ 6
- 2019ApJ...876..130H (2019): ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies
- 2019ApJ...876L..10E (2019): A Radio Source Coincident with the Superluminous Supernova PTF10hgi: Evidence for a Central Engine and an Analog of the Repeating FRB 12110…
- 2019ApJ...877L..25M (2019): The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation
- 2019ApJ...878...16P (2019): An Inner Disk in the Large Gap of the Transition Disk SR 24S
- 2019ApJ...878L...8T (2019): Discovery of An au-scale Excess in Millimeter Emission from the Protoplanetary Disk around TW Hya
- 2019ApJ...879..101L (2019): A Pseudodisk Threaded with a Toroidal and Pinched Poloidal Magnetic Field Morphology in the HH 211 Protostellar System
- 2019ApJ...880...15K (2019): The Molecular Gas Reservoirs of z ∼ 2 Galaxies: A Comparison of CO(1-0) and Dust-based Molecular Gas Masses
- 2019ApJ...881L...2B (2019): ALMA Observations of the Terahertz Spectrum of Sagittarius A*
- 2019ApJ...881L..39B (2019): Sub-arcsecond (Sub)millimeter Imaging of the Massive Protocluster G358.93-0.03: Discovery of 14 New Methanol Maser Lines Associated with a …
- 2019ApJ...882..160Q (2019): Probing CO and N<SUB>2</SUB> Snow Surfaces in Protoplanetary Disks with N<SUB>2</SUB>H<SUP>+</SUP> Emission
- 2019ApJ...883...71C (2019): The Radial Distribution of Dust Particles in the HL Tau Disk from ALMA and VLA Observations
- 2019ApJ...885L..21M (2019): How to Fuel an AGN: Mapping Circumnuclear Gas in NGC 6240 with ALMA
- 2019ApJ...886....6T (2019): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. I. Identifying and Characterizing the Protostellar Content …
- 2019ApJ...886L...4Z (2019): Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05
- 2019MNRAS.482..698C (2019): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - I: project description and continuum images at 28 au resolution
- 2019MNRAS.482.3135B (2019): The relationship between dust and [C I] at z = 1 and beyond
- 2019MNRAS.482L..29D (2019): Submillimetre dust polarization and opacity in the HD163296 protoplanetary ring system
- 2019MNRAS.483.1624B (2019): An ALMA archival study of the clump mass function in the Large Magellanic Cloud
- 2019MNRAS.484.4239R (2019): The AGN fuelling/feedback cycle in nearby radio galaxies I. ALMA observations and early results
- 2019MNRAS.486.4114R (2019): ALMA reveals a pseudo-disc in a proto-brown dwarf
- 2019MNRAS.488..191G (2019): ALMA observations of A0620-00: fresh clues on the nature of quiescent black hole X-ray binary jets
- 2019MNRAS.488.1005P (2019): Upper limits on protolunar disc masses using ALMA observations of directly imaged exoplanets
- 2019MNRAS.490.5300D (2019): Investigating the multiwavelength behaviour of the flat spectrum radio quasar CTA 102 during 2013-2017
- 2019NatAs...3..314L (2019): The ice composition in the disk around V883 Ori revealed by its stellar outburst
- 2019PASJ...71...68K (2019): A Chandra and ALMA study of X-ray-irradiated gas in the central ∼100 pc of the Circinus galaxy
- 2019PASJ...71..109H (2019): Detections of [O III] 88 μm in two quasars in the reionization epoch
- 2020A&A...635A...2S (2020): Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA
- 2020A&A...640A..13S (2020): Bipolar molecular outflow of the very low-mass star Par-Lup3-4. Evidence for scaled-down low-mass star formation
- 2020A&A...640A..19T (2020): Dust masses of young disks: constraining the initial solid reservoir for planet formation
- 2020A&A...641A.155V (2020): CO emission in distant galaxies on and above the main sequence
- 2020A&A...642A.155Z (2020): GOODS-ALMA: Optically dark ALMA galaxies shed light on a cluster in formation at z = 3.5
- 2020A&A...644A..84M (2020): The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. I. Isomers of C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB>
- 2020AJ....159...62C (2020): ALMA Observations of the Extraordinary Carina Pillars: HH 901/902
- 2020ApJ...889..155W (2020): Observations of the Orion Source I Disk and Outflow Interface
- 2020ApJ...890...76N (2020): ALMA Observations of Two Massive and Dense MALT90 Clumps
- 2020ApJ...890..129K (2020): Detection of Irregular, Submillimeter Opaque Structures in the Orion Molecular Clouds: Protostars within 10,000 yr of Formation?
- 2020ApJ...891...48H (2020): A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk
- 2020ApJ...891...80M (2020): Properties of M Dwarf Flares at Millimeter Wavelengths
- 2020ApJ...892...66M (2020): The ALMA Spectroscopic Survey in the HUDF: The Cosmic Dust and Gas Mass Densities in Galaxies up to z ∼ 3
- 2020ApJ...892...99C (2020): The Surprisingly Low Carbon Mass in the Debris Disk around HD 32297
- 2020ApJ...894...76W (2020): The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B
- 2020ApJ...895..135K (2020): AGN X-Ray Irradiation of CO Gas in NGC 2110 Revealed by Chandra and ALMA
- 2020ApJ...895L...2N (2020): Substructure Formation in a Protostellar Disk of L1527 IRS
- 2020ApJ...895L..46L (2020): Hints of a Population of Solar System Analog Planets from ALMA
- 2020ApJ...896...35J (2020): A Detailed View of the Circumstellar Environment and Disk of the Forming O-star AFGL 4176
- 2020ApJ...896..110L (2020): ALMA Observations of NGC 6334S. I. Forming Massive Stars and Clusters in Subsonic and Transonic Filamentary Clouds
- 2020ApJ...896..127K (2020): Multiple Outflows in the High-mass Cluster-forming Region G25.82-0.17
- 2020ApJ...898...10T (2020): Circumbinary Disks of the Protostellar Binary Systems in the L1551 Region
- 2020ApJ...898...36L (2020): Dual-wavelength ALMA Observations of Dust Rings in Protoplanetary Disks
- 2020ApJ...898...75I (2020): ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act
- 2020ApJ...902...78R (2020): The Complete Redshift Distribution of Dusty Star-forming Galaxies from the SPT-SZ Survey
- 2020MNRAS.496..394R (2020): Illuminating a tadpole's metamorphosis II: observing the ongoing transformation with ALMA
- 2020PASJ...72...62A (2020): Discovery of radio jets in the Phoenix galaxy cluster center
- 2021A&A...649A.139I (2021): Multiple molecular outflows and fragmentation in the IRDC core G34.43+00.24 MM1
- 2021A&A...652A..98G (2021): The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies
- 2021A&A...653A.117B (2021): ORion Alma New GEneration Survey (ORANGES). I. Dust continuum and free-free emission of OMC-2/3 filament protostars
- 2021A&A...654A.165V (2021): The effect of active galactic nuclei on the cold interstellar medium in distant star-forming galaxies
- 2021A&A...656A..46M (2021): ALCHEMI, an ALMA Comprehensive High-resolution Extragalactic Molecular Inventory. Survey presentation and first results from the ACA array
- 2021AJ....161..238W (2021): The Anatomy of an Unusual Edge-on Protoplanetary Disk. I. Dust Settling in a Cold Disk
- 2024A&A...682A..56Z (2024): Exploring the dust grain size and polarization mechanism in the hot and massive Class 0 disk IRAS 16293-2422 B
- 2024A&A...684A..56K (2024): Probing the interstellar medium of the quasar BRI 0952‒0115. An analysis of [C II], [C II], CO, OH, and H<SUB>2</SUB>O
- 2024A&A...689A.104D (2024): From traffic jams to roadblocks: The outer regions of TW Hya with ALMA Band 8
- 2024A&A...689A.317G (2024): Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii
- 2024A&A...691A.180F (2024): CHEMOUT: CHEMical complexity in star-forming regions of the OUTer Galaxy: IV. ALMA observations of organic species at a galactocentric radi…
- 2024Ap&SS.369...18M (2024): Multi-wavelength observation of MAXI J1348─630 during the outburst in 2019
- 2024ApJ...961..120C (2024): Brightest Cluster Galaxy Formation in the z = 4.3 Protocluster SPT 2349-56: Discovery of a Radio-loud Active Galactic Nucleus
- 2024ApJ...963....1O (2024): "Beads-on-a-string" Star Formation Tied to One of the Most Powerful Active Galactic Nucleus Outbursts Observed in a Cool-core Galaxy Cluster
- 2024ApJ...966...51G (2024): The Size─Linewidth Relation and Signatures of Feedback from Quiescent to Active Star Forming Regions in the LMC
- 2024ApJ...966...59S (2024): Small and Large Dust Cavities in Disks around Mid-M Stars in Taurus
- 2024ApJ...968....9W (2024): A Spatially Resolved [C II] Survey of 31 z ∼ 7 Massive Galaxies Hosting Luminous Quasars
- 2024ApJ...971..129C (2024): A Dust-trapping Ring in the Planet-hosting Disk of Elias 2-24
- 2024ApJ...973...42B (2024): Resolving Twin Jets and Twin Disks with JWST and ALMA: The Young WL 20 Multiple System
- 2024ApJ...974..102S (2024): Hints of Planet Formation Signatures in a Large-cavity Disk Studied in the AGE-PRO ALMA Large Program
- 2024BSRSL..93..601H (2024): Influence of Mid-infrared Galactic Bubble on Surroundings: A Case Study on IRAS 16489-4431
- 2024NatAs...8..774B (2024): JWST detection of a supernova associated with GRB 221009A without an r-process signature
- 2024RMxAA..60..355R (2024): The Radio Continuum Source Projected Near HR 8799
- 2025A&A...698A.204H (2025): An ALMA spectroscopic survey of the Planck high-redshift object PLCK G073.4−57.5 confirms two protoclusters
- 2025A&A...699A..62J (2025): ALMA observation of an evolving magnetized corona in the radio-quiet changing-state active galactic nucleus NGC 1566
- 2025A&A...699A.369V (2025): Dense clumps survive in the vicinity of R136 in 30 Doradus
- 2025A&A...700A.188C (2025): FAUST: XXVI. The dust opacity spectral indices of protostellar envelopes bridge the gap between interstellar medium and disks
- 2025ApJ...984L..19Y (2025): exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings
- 2025ApJ...984L..57O (2025): The Ophiuchus DIsk Survey Employing ALMA (ODISEA): A Unified Evolutionary Sequence of Planet-driven Substructures Explaining the Diversity …
- 2025ApJ...989....1Z (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). I. Program Overview and Summary of First Results
- 2025ApJ...989....6K (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). VI. Comparison of Dust Evolution Models to AGE-PRO Observations
- 2025ApJ...990...59Y (2025): The Impact of Silicate Grain Coagulation on Millimeter Emission from Massive Protostellar Disks
- 2025ApJ...992..103Z (2025): Impact of Gravity on Changing Magnetic Field Orientations in a Sample of Massive Protostellar Clusters Observed with ALMA
- 2025ApJ...993...85Y (2025): Peculiar Disk Substructures Associated with the Young Eruptive Star EX Lupi
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025ApJ...993..120H (2025): Early Planet Formation in Embedded Disks (eDisk). XVII. A Compact but Structured Keplerian Disk and Large-scale Streamers Revealed in the C…
- 2025ApJ...994..225N (2025): Unveiling Stellar Feedback and Cloud Structure in the ρ Ophiuchi-A Region Using ALMA and JWST: Discovery of Substellar Cores, C<SUP>18</SUP…
- 2025ApJS..278...45F (2025): DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey
- 2025NatAs...9..526O (2025): Observationally derived magnetic field strength and 3D components in the HD 142527 disk
- 2026A&A...705A.100E (2026): ALMAGAL: V. Relations between the core populations and the parent clump physical properties
- 2026ApJ..1001..124M (2026): Multiwavelength ALMA Imaging of HD 34282: Dust-trapping Signatures of a Vortex Candidate
- 2026ApJ..1001..131C (2026): MAGAZ3NE: Far-IR and Radio Insights into the Nature and Properties of Ultramassive Galaxies at z ≳ 3
- 2026ApJ..1004..126K (2026): An Active Galactic Nucleus in the Antennae Galaxies?
