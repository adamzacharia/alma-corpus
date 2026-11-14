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

=== SKILL.md (free-free-synchrotron) ===
---
name: alma-free-free-synchrotron
description: "Separate thermal dust, free-free (bremsstrahlung) and synchrotron emission in ALMA continuum, and turn the separated components into physical quantities: free-free fraction, ionizing photon rate and SFR, HII region emission measure and density, electron temperature from radio recombination lines, ionized jet mass-loss rates, and synchrotron magnetic fields or spectral ages. Use when an ALMA band (often Band 3, but also Band 6/7 in HII regions and starbursts) may contain non-dust emission, when combining ALMA with VLA/ATCA cm data, when asked for a free-free or thermal fraction, an RRL-based Te, or whether a compact mm source is dust, an HII region, a jet or a synchrotron core. Built from 119 ALMA papers (2013-2026)."
---

# Separating free-free, synchrotron and dust continuum

Splits the mm/cm continuum into dust (S ∝ nu^(2+beta) when optically thin), free-free (flat, nu^-0.1, when optically
thin; rising up to nu^2 when thick) and synchrotron (falling, nu^-0.5 to nu^-0.9), then uses each piece for physics.
The two mistakes that matter most: (1) assuming all ALMA continuum is dust, when Band 3 in starbursts is 70-84%
free-free (2016MNRAS.463..252B, 2015MNRAS.450L..80B, 2017ApJ...849...90S) and even 0.88 mm in 30 Dor clumps is
50-85% free-free (2025A&A...699A.369V); and (2) quoting a component fraction as if it were measured when it is set
by a fixed spectral index you chose (2015ApJ...813..118M, 2017ApJ...849...90S says its fit "is not unique").

Counts below are from the `free-free-synchrotron` evidence pack: either its aggregates (said so) or my own count of
its per-paper lines. The pack was tagged by regex on words like "HII region" and "recombination", so roughly a dozen
of its 119 papers are off-topic for decomposition (for example HII-region metallicity gradients, 2020MNRAS.499..193K,
or molecular-ion abundances, 2019A&A...622A..26G). I ignored those when counting.

For alpha maps, the alpha-to-beta conversion and grain-growth arguments, use the `spectral-index` skill. This skill
only covers getting the non-dust part out first, and what the non-dust part tells you.

## When to use

- Band 3 (85-115 GHz) continuum of starbursts, galaxy nuclei or Galactic HII regions, where free-free can dominate
  (fractions above; the aggregates list 32 nearby_galaxies and 53 star_formation papers).
- Dust masses of cores, clumps or disks near massive stars or HII regions, where free-free must come off first
  (2024ApJ...967...15K, 2015A&A...577A..30A, 2019MNRAS.483.1624B, 2016ApJ...833L...6C).
- ALMA plus VLA/ATCA SEDs of protostars and disks, to find ionized jets or winds at 1-5 cm (2021A&A...653A.117B,
  2024A&A...684A.134R, 2017A&A...602A..19L, 2019ApJ...884...97L).
- Radio recombination lines (H29alpha to H42alpha) for Te, kinematics or ionizing photon rate
  (2016MNRAS.463..252B, 2015MNRAS.450L..80B, 2024ApJ...967...15K, 2018ApJ...864L..17G, 2014ApJ...791...95A).
- Star formation rates or Q_Lyc from mm free-free (2017ApJ...849...90S, 2018ApJ...869..126L, 2016ApJ...833L...6C).
- AGN cores, radio galaxies, SNRs and PWNe where ALMA sits on a synchrotron spectrum (2019A&A...621A..27F,
  2020A&A...634A...9M, 2020MNRAS.496.1834L, 2014ApJ...796...82Z, 2025A&A...699A..62J).
- Stellar flares and coronae (gyrosynchrotron) (2018ApJ...855L...2M, 2020ApJ...891...80M, 2019ApJ...881...33H).

## When not to use

| Situation | Use instead |
|---|---|
| You already know the emission is dust and want alpha or beta, or grain growth | `spectral-index` |
| Dust mass from a single band once free-free is removed (kappa, T, gas-to-dust) | `dust-continuum-mass` |
| Full far-IR to radio SED with T_dust, stellar mass, SFR (CIGALE, MAGPHYS, MR-MOOSE) | `sed-fitting` (radio modules are a small part of it; 2017A&A...606A..17M, 2021A&A...646A.127H) |
| GRB, TDE, FBOT or blazar afterglow synchrotron light curves | `variability-time-domain` (2018ApJ...862...94L, 2023NatAs...7...80U are in this pack but are shock modelling, not decomposition) |
| Solar chromosphere brightness temperatures (thermal free-free as an atmospheric probe) | treat as atmospheric inversion; this pack has 8 sun papers (aggregate), e.g. 2017A&A...605A..78A, 2018ApJ...863...96Y; the recipes below do not transfer |
| Continuum subtraction for line cubes | `continuum-subtraction` |
| You need the free-free model in the uv plane (sizes, offsets) | combine with `uv-plane-fitting` (2014ApJ...796...82Z subtracted templates with MIRIAD uvmodel) |

## Steps

1. **Decide which components can matter at your frequency.**
   - Goal: avoid both "all dust" and "all free-free" by default.
   - Evidence of the size of the effect: free-free is 84 ± 10% of 85.69 GHz in NGC 4945 (2016MNRAS.463..252B), 70 ± 10%
     of 99 GHz in NGC 253 (2015MNRAS.450L..80B), 0.72 of 93 GHz in NGC 1808 with synchrotron 0.22 and dust 0.06
     (2017ApJ...849...90S), 6.7 of 9.7 mJy at 870 um in II Zw 40 (2016ApJ...833L...6C, card), 47-100% at 32.9 GHz in
     5 of 16 OMC-2/3 protostars (2021A&A...653A.117B). Synchrotron and free-free were below 5% at 220 GHz in NGC 253
     (2016ApJ...821..112K).
   - In AGN-hosting radio galaxies synchrotron can reach ALMA bands; MR-MOOSE was run with synchrotron without a
     cutoff to get the maximum contribution (2019A&A...621A..27F).
   - If you have only one ALMA band and nothing at cm wavelengths, say the decomposition is assumed, not measured
     (2015ApJ...813...45L assumed 100% dust at 345 GHz and gave a factor-of-5 uncertainty).

2. **Build a matched multi-band SED.**
   - Goal: fluxes that measure the same structure in every band.
   - Method: convolve to a common beam and regrid before ratios (2015ApJ...813..118M convolved 94.5 GHz to the 33 GHz
     beam, card), or restrict to a matched uv range (2017MNRAS.467L.120M used 40-610 klambda).
   - Record per-band absolute calibration errors (3% at 33 GHz and 5% at 94.5 GHz in 2015ApJ...813..118M, card) and
     add them to the fit; 2021A&A...656A..46M notes its fit errors left the calibration term out.
   - For variable sources, use simultaneous epochs; 2019ApJ...881L...2B flagged an 868 GHz point taken four days
     away, longer than the source's variability coherence time.
   - Software: CASA (13 matched steps in the aggregates), `imfit` for compact components (2 in the aggregates;
     2024ESC.....8..665M fit two 2D Gaussians to a hot core and a UC HII region).

3. **Choose a decomposition method.** Five patterns appear in the pack (my reading of the excerpts):

   | Method | What it needs | Examples |
   |---|---|---|
   | Sum of power laws with fixed indices, free amplitudes, least squares | 3+ bands spanning cm to submm | 2017ApJ...849...90S (alpha_s = -0.9, alpha_ff = -0.1, alpha_d = 3.8); 2016MNRAS.463..252B (synchrotron index free, Te 5000 K Gaunt factor, dust index 4, Monte Carlo errors) |
   | Two-band per-pixel algebra | Band 3 + Band 6 maps, adopted beta | 2019MNRAS.483.1624B: S_B6 = S_d + S_ff and S_B3 = S_d (nu3/nu6)^(2+beta) + S_ff (nu3/nu6)^-0.1, solved per pixel with beta = 1.49 |
   | Extrapolate free-free from a cleaner tracer and subtract | a band or line where free-free dominates | 3 mm scaled to 870 um with index -0.118 (2016ApJ...833L...6C, card); Brgamma to Halpha to free-free at 338.5 GHz (2025A&A...699A.369V); H29alpha-based free-free at 256 GHz removed before dust mass (2024ApJ...967...15K) |
   | Bayesian multi-component SED (MCMC) | many bands, priors | MR-MOOSE + emcee with AGN, modified blackbody and synchrotron (2019A&A...621A..27F); emcee with dust slabs plus free-free (2019ApJ...884...97L) |
   | Template subtraction in the uv plane | a high-resolution template band | scaled 44 GHz and Band 9 models removed with MIRIAD `uvmodel`, scaling tuned on the brighter lobe to avoid over-subtraction (2014ApJ...796...82Z) |

   Recommendation: use the fixed-index power-law sum only when you vary the indices as a test (step 7); use the
   per-pixel two-band method only with an independent check against cm data, as 2019MNRAS.483.1624B did.

4. **Model the free-free component physically when it is resolved or optically thick.**
   - HII regions: fit the turnover frequency (tau = 1) and size with Te fixed at 10^4 K, then emission measure from
     tau = 1, and N_Lym from the 23 GHz flux compared with ZAMS tables (2015A&A...577A..30A). With one band and a
     line, use Mezger-Henderson relations for n_e, EM, ionized mass and Lyman photons, assuming a spherical
     homogeneous region (2024ApJ...967...15K).
   - Photoionized outflows: grid of isothermal bipolar cavity models with n ∝ r^-2, chi2 over Te (5e3-2e4 K),
     n0 (3e6-3e8 cm^-3), launch radius (30-300 au) and opening angle, fitted at 1.3 and 7 mm together
     (2019ApJ...886L...4Z; best Te about 10,000 K, model fluxes within 5%).
   - Ionized shells: spherical shell radiative transfer, Ne and R fitted for Te = 1e4 to 2e4 K and DeltaR/R from
     0.05 to 1 (2014ApJ...791...95A).
   - Ionized jets from YSOs: Reynolds (1986) jet model with T = 1e4 K, nu_m = 40 GHz, theta_min/theta_maj = 0.5,
     v_jet = 140 (M*/0.5 Msun)^0.5 km/s, jet perpendicular to the disk (2024A&A...684A.134R; median ionized to
     total mass-loss ratio 0.019).
   - Stellar winds: Te = 0.5 Teff with mean ionic mass, ionization and electron number per spectral class
     (2018A&A...617A.137F).
   - General practice (not from the pack): optically thin free-free tau_ff ≈ 3.28e-7 (Te/1e4 K)^-1.35
     (nu/GHz)^-2.1 (EM / pc cm^-6), so tau = 1 near 100 GHz needs EM of order 1e10 pc cm^-6 at 1e4 K. Check that
     your ALMA band is above the turnover before using the -0.1 index.

5. **Use recombination lines when you have them.**
   - Te from the line-to-continuum ratio with Storey and Hummer emissivities, case B and fixed n_e = 1e3 cm^-3,
     after scaling the continuum by the free-free fraction (2016MNRAS.463..252B, 84 ± 10%; 2015MNRAS.450L..80B,
     0.70 ± 0.10). Results: 5400 ± 600 K in NGC 4945 (2016MNRAS.463..252B), 8094 ± 1534 K in a HC HII region
     (2024ApJ...967...15K).
   - Non-LTE and maser effects matter for compact, dense regions: 2014ApJ...791...95A fit H and He lines in NLTE
     (poorer fit for H40alpha and H42alpha); 2019ApJ...886L...4Z left H30alpha non-LTE modelling out; RRL masers
     are variable (2020ApJ...897L..33J).
   - Kinematics: H41alpha centroids with `pyspeckit` gave HII-region velocity dispersions, checked against earlier
     VLA velocities to within 5 km/s (2018ApJ...864L..17G).
   - He+/H+ = 0.08 is the usual adopted value (4 papers, my count: 2019ApJ...871..185L, 2025A&A...694A.166C,
     2019NatAs...3..517Z, 2025A&A...699A.369V); 0.096 in 2024ApJ...967...15K.

6. **Convert free-free to ionizing photons and SFR.**
   - Assume the band is free-free dominated (or scale by the fraction) and pick Te: 5000 K at 93 GHz in NGC 1808
     (2017ApJ...849...90S), 7000 K at 36 GHz with a ZAMS population and M* = Q0/4e46 (2018ApJ...869..126L, card),
     13000 K in II Zw 40 with a 72% correction for dust absorption of UV photons (2016ApJ...833L...6C, card).
   - General practice (Murphy et al. 2011 form, not quoted in the pack): Q(H0) ≈ 6.3e25 s^-1 (Te/1e4 K)^-0.45
     (nu/GHz)^0.1 (L_nu,ff / erg s^-1 Hz^-1). The Te dependence is weak, but state the Te you used.

7. **Model synchrotron when it is the science.**
   - Minimum-energy field: classical equipartition with c12 = 3.2e6 and k = 40, on pixels with alpha < -0.3 and
     > 5 sigma in both bands, as an upper limit if all emission is synchrotron (2019ApJ...886L...4Z, 15-17 mG).
     Self-absorbed coronae: equipartition with the photon field gave B of 100-300 G and sizes of 100-200 R_g
     (2025A&A...699A..62J).
   - Spectral ageing: CI and CI_OFF models in `SYNAGE++` with Jaffe-Perola losses, B fixed (2.6 uG for lobes),
     chosen by reduced chi2 (2020A&A...634A...9M). Break frequency plus remnant age gives B (2020MNRAS.496.1834L,
     3.9e-4 G).
   - Gyrosynchrotron flares: optically thin alpha = 1.22 - 0.9 delta (2018ApJ...855L...2M, delta = 3.32 ± 0.83;
     2020ApJ...891...80M, delta = 2.80 ± 0.06).
   - Thermal synchrotron (Sgr A*): one-zone sphere with n, Te, B in emcee, log priors, Te >= Tb, refit without
     Herschel points as a check (2019ApJ...881L...2B).

8. **Hand the dust residual on.** Free-free subtracted fluxes go to `dust-continuum-mass` (2024ApJ...967...15K,
   2015A&A...577A..30A) and multi-band dust residuals to `spectral-index`.

## Parameter defaults and ranges

Counts are my count of pack lines (parameters, assumptions, excerpts), off-topic papers excluded. A longer per-paper
list is in `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Electron temperature Te (fixed) | 1e4 K | 5000-20000 K | 18 | 1e4: 2015A&A...577A..30A, 2024A&A...684A.134R, 2021A&A...656A..46M; 5000: 2016MNRAS.463..252B, 2017ApJ...849...90S; 8000: 2019ApJ...871..185L; 16000: 2017A&A...602A..19L |
| Optically thin free-free index | -0.1 | -0.118 to -0.1 | 7 | 2020A&A...640A..27V, 2019MNRAS.483.1624B, 2024A&A...687A.163B, 2025ApJ...991...53C |
| Partially thick jet or wind free-free index | 0.6 | 0.6-1 | 2 | 2017ApJ...840...32T (0.6), 2018MNRAS.478.2505I (1) |
| Synchrotron index (fixed) | -0.8 | -0.5 to -0.9 | 8 | -0.7: 2015ApJ...802...69B; -0.8: 2017A&A...606A..17M; -0.85: 2015ApJ...813..118M; -0.9: 2017ApJ...849...90S |
| Dust index in the decomposition | alpha_d 3.5-4 or beta 1.5-1.9 | alpha_d 2.3-4; beta 1-2.5 | 14 | alpha_d 4: 2016MNRAS.463..252B; 3.8: 2017ApJ...849...90S; beta 1.49: 2019MNRAS.483.1624B; beta 1.75: 2018ApJ...853..171G |
| He+/H+ | 0.08 | 0.08-0.096 | 5 | 2019NatAs...3..517Z, 2024ApJ...967...15K |
| n_e for RRL emissivities | 1e3 cm^-3, case B | n/a | 1 | 2016MNRAS.463..252B |
| Thermal fraction at 1.4 GHz (SED codes) | 0.1 | n/a | 1 | 2017A&A...606A..17M |
| Free-free fraction at Band 3 (measured) | 0.7-0.85 | 0.70-0.84 | 3 | 2016MNRAS.463..252B, 2015MNRAS.450L..80B, 2017ApJ...849...90S |
| MCMC setup | emcee, uniform or log priors | 84 walkers x 1500 steps, 500 burn-in; 128 chains | 4 (aggregate: emcee) | 2019ApJ...884...97L, 2018ApJ...862...94L |
| Flux uncertainty floor | 10% | 10-20% | 3 | 2016MNRAS.463..252B, 2018ApJ...862...94L, 2019ApJ...881L...2B (20% at 868 GHz) |

## Software

From the pack aggregates ("software named in the matched steps"); real use is higher because many cards name software
only in the reduction section.

| Software | Count | Used for |
|---|---|---|
| CASA | 13 | calibration, imaging, flux extraction |
| CASA `imfit` | 2 | Gaussian fits to compact free-free and dust sources (2024ESC.....8..665M) |
| emcee | 4 | SED and afterglow MCMC (2019ApJ...884...97L, 2019ApJ...881L...2B, 2018ApJ...862...94L) |
| CLOUDY | 2 | HII + PDR photoionization grids (2025ApJ...990...29H, with BPASS) |
| Starburst99 | 2 | ionizing photon to stellar population conversion |
| MR-MOOSE | 1 | multi-resolution AGN + dust + synchrotron SED (2019A&A...621A..27F) |
| Hyper | 1 | modified blackbody fit after free-free removal (2015A&A...577A..30A) |
| SYNAGE++ | 1 | synchrotron spectral ageing (2020A&A...634A...9M) |
| MIRIAD `uvmodel`, `uvfit` | 1 | uv-plane template subtraction (2014ApJ...796...82Z) |
| pyspeckit | 1 | RRL fitting (2018ApJ...864L..17G) |
| linmix | 1 | regression of ionized vs total mass-loss rate (2024A&A...684A.134R) |
| astropy.modelling | 1 | Gaussian clump models before free-free subtraction (2025A&A...699A.369V) |
| MAGPHYS, CIGALE | 1 each | panchromatic SEDs with a radio module (2017A&A...606A..17M, 2021A&A...646A.127H) |

## Pitfalls

- **The fixed indices set the answer.** Changing alpha_NT from -0.85 to -0.6 moved 33 GHz thermal fractions from
  85/82/70% to 80/76/62% (2015ApJ...813..118M, card). 2017ApJ...849...90S calls its three-component fit not unique;
  2017A&A...602A..19L says its SED models are degenerate. Report the fraction with the index range you tried.
- **Two bands cannot split three components.** With 36 and 350 GHz only, free-free in the submm and synchrotron at
  36 GHz are indistinguishable (2018ApJ...869..126L, card). Without an intermediate frequency, synchrotron
  steepening cannot be tested (2019A&A...621A..27F).
- **Optically thick free-free.** The turnover can lie above your data: the MM1a fit was least robust because flux
  may keep rising past 25 GHz (2015A&A...577A..30A). Hypercompact HII regions and jets do not follow -0.1.
- **The RRL Te depends on the free-free fraction.** With no correction Te rose to 5800-7100 K; with a 50% fraction it
  fell to 2500-3000 K (2015MNRAS.450L..80B).
- **Missing flux differs by band.** Extended emission resolved out at one band but not another fakes a spectral
  slope (2015ApJ...801...82H, 2018ApJ...860....9M, 2016ApJ...821..112K on different uv coverage per transition,
  2025A&A...699A.369V without Total Power).
- **Variability and non-simultaneous data.** Accretion and free-free measured at different times (2024A&A...684A.134R);
  older periastron spectra used because new low-frequency data were missing (2019PASJ...71L...3F).
- **Line contamination of the continuum.** RRLs and molecular lines inside the continuum window dominated flux
  accuracy in 2020ApJ...903...29M; STATCONT continuum was not optimal for weak lines (2021A&A...656A..46M).
- **Calibration systematics.** CASA versions before 5.0 overestimated 7m mosaic fluxes by about 8% in Band 6 and 2% in
  Band 3, uncorrected in 2019MNRAS.483.1624B; 2015MNRAS.450L..80B allows for unidentified amplitude errors;
  2015ApJ...802...69B needed a Tsys correction for Sgr A*.
- **Uniform temperatures overestimate free-free.** 2024A&A...687A.163B assumed 100 K everywhere and warns free-free
  may be overestimated.
- **Other non-dust emission at 20-40 GHz.** Spinning dust (nu_pk = 21 GHz) was needed for PDS 70 (2024ApJ...972..163L);
  2015ApJ...813..118M assumed AME negligible.
- **Thermal contamination of a synchrotron core.** The Fornax A core result holds only if thermal emission is below
  about 80% at 108 GHz (2020A&A...634A...9M).
- **Ignoring free-free in dust masses.** 2020ApJ...896...35J did not remove it at 1.2 mm; 2015ApJ...813...45L did not
  correct for synchrotron. 2020A&A...640A..27V tested it with indices 2.3 and -0.1 and found it negligible; do that test.
- **What cards say is missing.** The aggregates flag self-calibration solution intervals (at least 17 cards across
  phrasings), CASA or pipeline version (at least 13), line-free channels (at least 15) and flux scale uncertainty or
  flux calibrator (at least 7) as not stated. State all four.

## Verification checks

What the papers did:
- Vary Te (3000-10000 K) and the fixed indices and report how much the free-free fraction moves (2016MNRAS.463..252B,
  at most 10%); vary alpha_NT (2015ApJ...813..118M).
- Compare a decomposed free-free map with an independent extrapolation from cm data: 30 Dor agreed to 15%, N159E
  disagreed by about 4x (2019MNRAS.483.1624B, card).
- Test the free-free level against optical or near-IR hydrogen lines: Halpha limits (2014ApJ...796...82Z),
  Brgamma (2025A&A...699A.369V).
- Compare model images, spectral index maps, SED and profiles with the data, not only total flux
  (2019ApJ...886L...4Z, within 5%).
- Refit with an extra point or without a dataset: 43 GHz for MM1a (2015A&A...577A..30A); without Herschel
  (2019ApJ...881L...2B).
- Compare Te or kinematics with Milky Way or earlier values (2016MNRAS.463..252B, 2018ApJ...864L..17G).
- Check residuals against the noise after template subtraction (2014ApJ...796...82Z).
- Cross-check ionized mass-loss against an independent tracer ([OI] HVC in 2024A&A...684A.134R).

What a careful referee adds:
- Propagate per-band calibration errors into the fractions, not only fit errors.
- Show the uv range or beam matching used for every ratio.
- State whether each band is above the free-free turnover, and why.
- For RRL Te, give the continuum fraction, n_e and case assumed, and whether non-LTE was considered.
- Report results for at least two plausible synchrotron indices.

## Source cards

All 119 papers are listed in `references/sources.md`. The most informative for this technique:

- 2016MNRAS.463..252B: four-component SED decomposition plus H42alpha Te, with sensitivity tests
- 2015MNRAS.450L..80B: H40alpha Te and the effect of the free-free fraction on it
- 2017ApJ...849...90S: fixed-index three-component least squares; SFR from 93 GHz free-free
- 2015ApJ...813..118M: VLA 33 GHz + ALMA 94.5 GHz thermal fractions and alpha_NT test
- 2019MNRAS.483.1624B: per-pixel Band 3/Band 6 free-free removal validated with ATCA
- 2016ApJ...833L...6C: 3 mm free-free extrapolated to 870 um, dust-only map
- 2025A&A...699A.369V: Brgamma-based free-free subtraction at 0.88 mm
- 2024ApJ...967...15K: H29alpha Te, Mezger-Henderson, free-free removed before dust mass
- 2015A&A...577A..30A: turnover-frequency fit, N_Lym, then dust SED
- 2019ApJ...886L...4Z: photoionized outflow model grid and equipartition B
- 2014ApJ...791...95A: ionized shell continuum and NLTE recombination lines
- 2021A&A...653A.117B: free-free identification in protostars from 32.9 GHz
- 2024A&A...684A.134R: jet free-free and ionized mass-loss rates in transition disks
- 2019ApJ...884...97L: emcee multi-component disk plus free-free SED
- 2019A&A...621A..27F: MR-MOOSE with synchrotron for radio galaxies
- 2020A&A...634A...9M: synchrotron spectral ageing with SYNAGE++
- 2014ApJ...796...82Z: uv-plane template subtraction for SN 1987A
- 2018ApJ...855L...2M: gyrosynchrotron index to electron index
- 2018ApJ...869..126L: free-free stellar masses and the two-band limitation
- 2020A&A...640A..27V: quick free-free contamination test for disk masses

=== EVIDENCE PACK (free-free-synchrotron) ===
# Evidence pack: Separating free-free, synchrotron and dust continuum (`free-free-synchrotron`)

Scope: continuum decomposition and ionized gas diagnostics

Built from 119 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2013-2026.
Matcher (regex over analysis steps): `free[- ]free|synchrotron|thermal (?:radio|bremsstrahlung)|\bhii region|h ?ii regions|radio recombination|recombination line`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- star_formation: 53
- nearby_galaxies: 32
- milky_way_ism: 25
- agn_and_quasars: 25
- protoplanetary_disks: 16
- astrochemistry: 15
- high_z_galaxies: 11
- sun: 8
- stellar_physics: 8
- transients: 6
- evolved_stars: 3
- exoplanets: 3
- debris_disks: 2
- cosmology: 1
- other: 1

### Software named in the matched steps
- casa: 13
- emcee: 4
- cloudy: 2
- casa imfit: 2
- starburst99: 2
- mr-moose: 1
- hyper: 1
- linmix: 1
- magphys: 1
- bpass: 1
- pyspeckit: 1
- synage++: 1
- cigale: 1
- astropy.modelling: 1
- miriad uvmodel: 1
- miriad uvfit: 1
- jpl: 1
- splatalogue: 1
- cdms: 1
- stic: 1
- dmpr12 code: 1
- gildas: 1
- heisenberg: 1
- hiiphot: 1

### Fitting methods (most common phrasings)
- Monte Carlo for uncertainty; 10% errors for two datasets: 1
- Monte Carlo power-law fits, median taken as index: 1
- Grid chi2 minimization over regions with I_obs>0.1 I_center: 1
- flat priors from 0.5x to 2x initial value; likelihood set to -inf if FU Ori S 9 GHz flux exceeds 3 sigma: 1
- emcee MCMC, chi2 likelihood with upper-limit treatment of Sawicki2012, uniform priors: 1
- Gaussian fits: 1
- non-linear least squares: 1
- Least squares on logarithmic form; residual RMS ~60 K: 1
- emcee MCMC with uniform priors: 1
- Power-law fit with Poisson bin errors: 1
- linmix linear regression: 1
- Bayesian library fitting in MAGPHYS; upper limits entered as zero flux with 3 sigma error: 1
- Best model chosen where model/observed peak ratios approach unity for all lines: 1
- reduced chi-squared comparison of CI vs CI_OFF: 1
- CIGALE grid with Bayesian analysis; model comparison by BIC: 1
- Least-squares, amplitudes free: 1
- analytic inversion over temperature grid; error propagation: 1
- not a formal fit: 1
- emcee default sampler with logarithmic priors on n, Te and plasma beta: 1
- two elliptical Gaussians for B and D: 1
- Scaling tuned to minimize difference on eastern lobe without over-subtraction: 1
- Not a formal fit; parameters chosen by hand: 1
- Best model is where L_X and 1.3 mm flux contours intersect; no formal fit: 1
- Gaussian profiles: 1
- chi^2 minimisation: 1
- power-law fit to centimeter fluxes: 1
- by eye: 1
- two power laws, statistical uncertainties only; sampler/priors not stated: 1
- Chi2 comparison and F-test: 1
- chi2 grid: 1
- Product of pairwise distributions; 99.7th percentile upper limit: 1
- Gaussian and Voigt profile fits: 1
- Monte Carlo bootstrapping: 1
- linear fit to bright end; slopes consistent within errors: 1

### Validation checks used
- tests varying Te 3000-10000 K and indices; fraction varied ≤10%: 1
- compared with Milky Way Te: 1
- Compared with Williams et al. 2008 dust model: 1
- Compared with images, spectral index, SED and profiles; model fluxes within 5% of observed: 1
- Monitored likelihood contributions; model also close to unfitted Spitzer/Herschel spectra: 1
- lambda_cut calibrated on 4C 23.56; comparison with Drouart2014 luminosities: 1
- Posteriori refit of MM1a with 43 GHz point consistent: 1
- Adding a quadratic term did not change results; power series unstable; compared with Eddington-Barbier and models: 1
- Repeated with other calibrations in Appendix: 1
- Compared with 100 random shuffles of metallicities and bootstrapping over 100 realizations: 1
- Sensitivity tests with no correction (Te 5800-7100 K) and 50% (Te 2500-3000 K): 1
- Compared with Mdot_i/Mdot from [OI] HVC (Nisini 2018): 1
- chi2 below threshold ~14 for 33 bands; refits without upper limits; AGN contribution to L_IR checked with SED3FIT (mean…: 1
- Compared with local compact HII size-density relation (Kim2001): 1
- Compared with previous unresolved mm and cm spectral indices: 1
- Good fits for all Te and DeltaR/R combinations; Fig. 5 examples: 1
- Compared with LTE models and He lines; poorer fit for H40alpha and H42alpha: 1
- Compared with De Pree et al. 2011 velocities (agree within 5 km/s except F10.37): 1
- Free-free contribution estimated negligible using spectral indices 2.3 and -0.1: 1
- Model also explains X-ray and optical: 1
- chi2, reduced chi2 and BIC compared among laws; stellar-only vs IR-only fits: 1
- compared with Scoville COSMOS IR-bright median: 1
- Fit stated to be not unique: 1
- Compared ISM and molecular masses, agree within factor of few: 1
- Model SEDs overplotted on measured fluxes as self-consistency check: 1
- comparison with Robitaille/Zhang models, HOPS Orion sources, and MUSTANG Orion data: 1
- compared with Schmiedeke2016a mass estimates: 1
- Compared with fluxes and X-band limits: 1
- Repeated without Herschel data: 1
- Residuals compared with noise levels: 1
- Free-free tested against Halpha flux limits: 1
- Compared with spicule densities from IRIS spectra (Alissandrakis 2018): about an order of magnitude lower: 1
- Compared with Perez-Beaupuits 2018 cold component of 37 K and mass 1e6 Msun: 1
- Tested alpha_NT=-0.6; AGN contribution <3% estimated: 1
- Consistency with 193 A absorption and Rutten (2017) temperature range: 1
- Check against ALMA 97.5/145 GHz fluxes and spectral indices: 1
- Independent R23 optical estimate and q_IR check against AGN origin: 1
- Compared T_dust with local (U)LIRGs: 1
- Compared with Chandra temperatures, densities, UV pressure and radio upper limits: 1
- Optical depth checked against expected thick/thin flux vs L*: 1

### Key parameters and settings (bibcode: value)
- 2016MNRAS.463..252B: Te fixed 5000 K; dust index 4
- 2020MNRAS.496.1834L: 10 000 simulated data sets, 500 seeds averaged, 68% bounds
- 2020MNRAS.496.1834L: remnant age 1100 yr; D = 50 kpc; T_dust = 55 K
- 2019ApJ...886L...4Z: theta_w,sky fixed at 40 deg; PA 3 deg; Te 5e3-2e4 K; n0 3e6-3e8 cm-3; varpi0 30-300 au; theta_w 20-40 deg
- 2019ApJ...886L...4Z: c12=3.2e6, k=40
- 2019ApJ...884...97L: 84 walkers, 1500 steps, first 500 discarded
- 2019ApJ...884...97L: Herschel/SPIRE, PACS, Spitzer/IRS errors set to 1000, 10, 1 times the fluxes
- 2019A&A...621A..27F: lambda_cut=33 um fixed; T prior [20,70] K; gamma [0,6]; alpha [-4,0]
- 2015A&A...577A..30A: Omega_c fixed to radius 11.4 arcsec; priors Td 25 K, nu0 4.3 THz, beta 2.0
- 2017A&A...605A..78A: ALMA data used up to theta~70 deg
- 2018ApJ...862...94L: 128 chains, 10^4 posterior samples, 10% uncertainty floor
- 2024A&A...684A.134R: T = 1e4 K, nu_m = 40 GHz, theta_min/theta_maj = 0.5, v_jet = 140 (M*/0.5 Msun)^0.5 km/s, jet inclination = outer disk inclination
- 2017A&A...606A..17M: q_FIR centred at 2.34 with sigma 0.25; thermal fraction f_T = 0.1; synchrotron nu^-0.8
- 2025ApJ...990...29H: log n_H,c 1.0-4.0 step 0.1; log U -4.0-0.0 step 0.1; cov_PDR 0-1 step 0.01
- 2014ApJ...791...95A: Te = 1e4, 1.5e4, 2e4 K; DeltaR/R from 0.05 to 1
- 2014ApJ...791...95A: Te 1.4e4-2e4 K; DeltaR/R = 0.05, 0.1, 0.2
- 2020A&A...640A..27V: d = 414 pc, T = 20 K, kappa(1000 GHz) = 10 cm2/g, beta = 1
- 2020A&A...634A...9M: B = 2.6 uG for lobes
- 2015ApJ...813...45L: dust temperatures 30 K and 90 K
- 2019ApJ...881...33H: B = 600 G, delta = 2, d = 12.45 pc, nu = 97.5 GHz, S = 10.6 uJy
- 2021A&A...653A.117B: beta constrained to 0-2 to bound T_SED
- 2017A&A...602A..19L: β=1.75 fixed; Te=16000 K
- 2019ApJ...881L...2B: Te >= Tb, 1e-3 < beta < 1e3; 20% uncertainty on 868 GHz
- 2018ApJ...863...96Y: T = 1e4–4e5 K; Tb=135 K; L≈1.5''
- 2021A&A...656A..46M: kappa0=0.1 cm2/g at 250 GHz; T_e=1e4 K; SFR=2.5 Msun/yr
- 2024ApJ...972..163L: amax=1.5 mm; Sigma_dust=5.0 g cm^-2; Omega=2e-12 sr; q=3.5; amin=1e-4 mm
- 2024ApJ...972..163L: Spinning dust: nu_pk=21 GHz, F_sd,0=0.07 mJy
- 2013ApJ...772..149C: Grid 250 v_perp × 250 ε, 0.2–200 km/s, ε 0–2.5
- 2020ApJ...892..111F: flaring angle 0.02; R_sub=0.07 sqrt(L*) au; kappa 10 cm2/g at 1000 GHz, beta=1; assumed R_inner=5 au for unresolved
- 2016ApJ...833L...6C: Te = 13000 K; D = 10 Mpc
- 2020ApJ...898...54T: beam sizes 0.3" Core A, 0.5" others
- 2019ApJ...871..185L: N(He+)/N(H+)=0.08
- 2019A&A...628A..85V: beta=1, kappa_1000GHz=10 cm2/g, T=20 K (30 K test), d=414 pc
- 2018ApJ...869..114I: eta=0.04 fixed; free-free index 0.1, galactic synchrotron index 0.8
- 2025A&A...694A.166C: Te = 6000 K, N(He+)/N(H+) = 0.08
- 2015ApJ...801...82H: Disk 0.20x0.03 arcsec = 84 AU x 12.6 AU, edge-on, uniform density and temperature
- 2019PASJ...71L...3F: nu = 97 GHz, T = 64 days
- 2016MNRAS.459.3629I: Ne=Np=1e9 cm^-3, Te=1e4 K, L=4.5e-7 pc, f_a~0.1, r_in~0.13 pc
- 2020ApJ...890..129K: kappa_8.1 = 0.144 cm2/g
- 2018ApJ...866..141K: radius 21 au, Omega = 2.4e-12 sr, T_bg = 2.7 K
- 2019ApJ...883...71C: Ka and Q combined into 8.0 mm image; K band excluded
- 2019ApJ...883...71C: 175 uJy at 32.5 GHz, spectral index 0.7, size 22 mas
- 2017ApJ...835L..35M: four knots: N=2e-14, gamma=0.35, nu1=4e11 Hz, beta=0.25
- 2015ApJ...804...37L: Te ~ 8000 K
- 2017MNRAS.468L..87C: T_dust <= 14 K upper limit from PACS 160 um
- 2019MNRAS.483.1624B: beta=1.49, free-free index -0.1
- 2018ApJ...860...77E: free parameters: turnover wavelength, free-free and dust fluxes at ALMA wavelength
- 2017ApJ...851..126V: robust 0.5, 0.05'' pixel
- 2016ApJ...821..112K: Td 2.5-150 K; tau220 0.02-1
- 2018A&A...617A.137F: Te = 0.5 Teff; d = 5 kpc; mu=1.4,Z=1,gamma=1 for OB; mu=4.0 (WN6 or earlier), 2.0 (later WN), 4.7 (WC8/9); mu=1.6, gamma=0.8, Z=0.9 for BHGs
- 2018ApJ...860....9M: knot B: R=50 pc, B=1 mG, delta=1 (leptohadronic)
- 2017ApJ...850...54C: 5 Myr star formation timescale
- 2017MNRAS.467L.120M: matched uv range 40 to 610 k lambda
- 2019NatAs...3..517Z: Te = 8000 K, N(He+)/N(H+)=0.08


### Assumptions (bibcode: value)
- 2016MNRAS.463..252B: 84±10% of continuum is free-free
- 2020MNRAS.496.1834L: Gaussian flux uncertainties; frequencies uniform within bins
- 2020MNRAS.496.1834L: Small silicate (forsterite) grains, kappa from Mennella et al.
- 2019ApJ...886L...4Z: Each ion has single charge
- 2019ApJ...886L...4Z: All emission in these regions is synchrotron (upper limit)
- 2019ApJ...884...97L: DSHARP opacities, 170 K ice sublimation, power-law grain size q=3.5, amin=1e-4 mm, face-on slabs
- 2019A&A...621A..27F: beta=2.5, nu0=1.5 GHz; uniform priors; synchrotron without cutoff (maximum contribution)
- 2024ApJ...967...15K: Spherical homogeneous HII region, LTE, He+/H+=0.096
- 2024ApJ...967...15K: T_dust = 250 K, gas-to-dust 100, k=0.0078 cm2/g, D=2.38 kpc
- 2015A&A...577A..30A: Te fixed to 10,000 K
- 2015A&A...577A..30A: Cylindrical homogeneous HII region, D=3.25 kpc
- 2015A&A...577A..30A: kappa=0.1(lambda/0.3mm)^-beta cm2/g, dust-to-gas 0.01
- 2017A&A...605A..78A: LTE thermal free-free and H- absorption proportional to f^-2
- 2020MNRAS.499..193K: Case B, Te=10^4 K, Fitzpatrick1999 law with R_V=3.1
- 2018ApJ...862...94L: ISM environment; uniform priors, log-uniform for scale parameters
- 2015MNRAS.450L..80B: Continuum multiplied by 0.70±0.10
- 2021A&A...652A..92N: height equals horizontal size; filling factor unity
- 2024A&A...684A.134R: central emission is jet free-free emission
- 2017A&A...606A..17M: Chabrier (2003) IMF; no AGN contribution to dust heating
- 2025ApJ...990...29H: Zgas=Zstar=0.2 Zsun, solar abundances except He, MW grains, HII stop at H+/Htot=0.01, PDR stop at A_V=5
- 2017A&A...602L..10O: Tb ~ Tgas(tau=1) for slowly varying temperature; free-free H- opacity
- 2025A&A...699A..62J: outflow velocity taken as escape velocity
- 2014ApJ...791...95A: Spherical symmetry; constant density and temperature; H fully ionized, He as He+ (Ni=Ne); distance 2.3 kpc
- 2014ApJ...791...95A: Pressure broadening neglected
- 2018ApJ...864L..17G: Upper stellar mass limit of 200 Msun; each VLA source is an H II region with a star of at least 20 Msun
- 2018ApJ...864L..17G: H II regions trace stellar motions
- 2020A&A...640A..27V: Optically thin emission, no free-free contamination, 20 K midplane (40 K tested)
- 2023NatAs...7...80U: Uniform density medium, energy injection E_iso propto t^0.25
- 2020A&A...634A...9M: Jaffe & Perola isotropic electron distribution; no escape of particles (T_conf = infinity)
- 2021A&A...646A.127H: Chabrier IMF, solar-like metallicity (Z=0.02)
- 2015ApJ...813...45L: uncertainty factor of 5; synchrotron contamination not corrected
- 2019ApJ...881...33H: Electron-to-proton ratio ~10^3 as in solar flares; flux scaled by R/r^2 with pi sr
- 2026ApJ..1004..126K: dust kappa 0.37 m2/kg at 250um, beta=2, T=30 K; Galactic CO-to-H2 2e20
- 2020ApJ...891...80M: Peak frequency 50 GHz for energy contours
- 2018ApJ...855L...2M: Optically thin gyrosynchrotron emission
- 2015ApJ...802...69B: optically thin synchrotron index -0.7
- 2026ApJ..1003L..17Y: B = 44 G, sinθ = 1
- 2017ApJ...849...90S: Fixed indices alpha_s=-0.9, alpha_ff=-0.1, alpha_d=3.8
- 2017ApJ...849...90S: Td = 20 and 100 K; X_CO = 0.8e20; Te = 5000 K; d = 10.8 Mpc
- 2021A&A...653A.117B: mu=2.8, dust-to-gas R=0.01, kappa0=0.9 cm2/g at 230 GHz, d=393 pc, no free-free at 246.2/333 GHz
- 2018ApJ...853..171G: beta=1.75, kappa(3.1mm)=0.0018 cm2/g per gram gas (Ossenkopf1994a), gas-to-dust 100, d=8.4 kpc
- 2018ApJ...853..171G: age t=0.74 Myr from Kruijssen2015a
- 2017A&A...602A..19L: gas-to-dust 100, d=353 pc; parameters degenerate
- 2019ApJ...881L...2B: Relativistic effects and radiative cooling neglected; thermal electrons; constant ion temperature proportional to virial
- 2025A&A...699A.369V: Te=1e4 K, He+/H+~0.08, Halpha/Brgamma=101.78
- 2014ApJ...796...82Z: 1<=beta<=2; kappa~2.5 cm2/g for amorphous carbon; free-free with Te~1e4 K, sphere radius 0.40"
- 2018ApJ...863...96Y: 100% filling factor, small optical thickness
- 2021A&A...656A..46M: Beta=1.9 emissivity law
- 2019ApJ...878L..26L: Omega_m=0.31, Omega_Lambda=0.69, H0=68 km/s/Mpc
- 2015ApJ...813..118M: alpha_NT = -0.85; free-free optically thin; negligible AME and thermal dust
- 2020ApJ...888L..28S: negligible background, T<10,000 K, thermal LTE electron-proton free-free emission
- 2024ApJ...972..163L: Dust temperature 20 K
- 2024ApJ...972..111L: Optically thin above nu_0 = 1.5 THz; synchrotron negligible at 1 mm
- 2017ApJ...835L..13S: excess emission is thermal dust; free-free negligible
- 2025A&A...695A.233R: gamma_j=10, phi=0.01 rad, viewing angle 0.1 rad, equipartition, m=1, n=2, alpha=-0.5
- 2013ApJ...772..149C: Vertical loops, no limb effects, S_ν = π R*² I_ν / D²
- 2020ApJ...892..111F: Scattering and free-free emission ignored
- 2023Natur.623..927H: epsilon_e = epsilon_B = 1/3; peak frequency is SSA frequency
- 2016ApJ...833L...6C: Synchrotron and dust negligible at 3mm
- 2016ApJ...833L...6C: Dust contribution at 3mm negligible for beta=1.7
- 2020ApJ...898...54T: Tdust = 100 K, beta = 1.6, kappa = 0.1 (nu/THz)^beta
- 2019ApJ...871..185L: Te~8000 K
- 2019A&A...628A..85V: Optically thin dust emission
- 2018ApJ...869..114I: spherical corona
- 2025A&A...694A.166C: Free-free optically thin at 99,023 MHz
- 2015ApJ...801...82H: Dust temperature 100 K for graybody component
- 2017ApJ...841L...5S: filling factor unity
- 2020A&A...633A.127F: Synchrotron from nucleus dominates at low frequencies
- 2017ApJ...848L..21A: epsilon_e=0.1, eta_gamma=0.1
- 2020A&A...643A..41D: fully ionized hydrogen plasma
- 2019PASJ...71L...3F: Instantaneous injection of power-law electrons
- 2025ApJ...991...53C: kappa renormalization of Draine2014; synchrotron S ∝ nu^-0.8 and free-free nu^-0.1
- 2025MNRAS.540..364A: Torus blackbody T=10^3 K; BLR covering factor 0.1; IR covering 0.4-0.6
- 2016MNRAS.459.3629I: Component fractions and spectral indices as above
- 2016MNRAS.459.3629I: LTE, uniform density and temperature clouds, stimulated emission by non-thermal background neglected
- 2020ApJ...890..129K: 8 mm optically thin, negligible free-free, gas-to-dust 100:1, distance 400 pc
- 2018ApJ...866..141K: kappa = 0.1 (nu/1e12 Hz)^beta cm2/g; 7.3 mm emission is thermal dust with no free-free; D = 137 pc
- 2017ApJ...850...35L: Thermal free-free emission in LTE
- 2020ApJ...901..151S: Te=5000 K; 80% free-free
- 2013AJ....146...91I: Far-infrared luminosity entirely starburst (upper limit on free-free)
- 2020ApJ...891L...8M: Free-free hydrogen absorption main opacity source
- 2017MNRAS.468L..87C: kappa160 = 1.6 m2/kg, beta = 1.7
- 2020ApJ...895L...2N: free-free spectral index -0.1
- 2019MNRAS.483.1624B: Only dust and free-free contribute; synchrotron neglected (<=4 per cent of Band 6 oversubtracted)
- 2024A&A...687A.163B: alpha_dust = 3.5, free-free alpha = -0.1, Td 50-150 K
- 2016ApJ...821..112K: beta=1.8; free-free/synchrotron <5% at 220 GHz
- 2018A&A...617A.137F: mm flux not affected by binarity; wind emission thermal; two non-thermal sources excluded
- 2016ApJ...826...16E: dust beta=1
- 2017ApJ...850...54C: Kroupa IMF
- 2020ApJ...897L..33J: Tdust=500-1200 K, gas-to-dust ratio 100, kappa=25.8 cm2/g
- 2017MNRAS.467L.120M: Rayleigh-Jeans; free-free modelled as point sources for Main and SE
- 2017ApJ...840...32T: Free-free jet spectral index 0.6
- 2019ApJ...883L...2M: X-ray emission entirely IC/CMB; gamma_min = 10; H0=73, OmegaM=0.27, OmegaL=0.73
- 2019Natur.569..519K: Diffuse Halpha originated from HII regions
- 2018A&A...619A..40M: gamma=2.48 from alpha=-0.74; slowed (p=1/2) vs free (p=1) expansion
- 2016ApJ...822L..10I: Emission purely thermal free-free (upper limit)
- 2020ApJ...904L..24S: eta=1, Vs=3900 km/s
- 2019A&A...627L...6M: gas-to-dust 100, kappa=1.0 cm2/g at 1.3 mm, Td 50-150 K, d=2.2 kpc
- 2018PASJ...70...73H: Cardelli extinction curve, intrinsic Halpha/Pabeta=17.1, median A_Halpha=1.9 mag outside Pabeta FOV
- 2021A&A...649A.139I: Turnover frequency of 100 GHz
- 2017A&A...601L...3P: beta between 1.5 and 1.85; free-free ~7 mJy
- 2020ApJ...889..178B: Line-of-sight depth equals minor axis
- 2018MNRAS.478.2505I: Teff ~1e4 K for the bloated protostar; free-free spectral index 1
- 2018ApJ...867...48I: Synchrotron spectral index -0.7
- 2019ApJ...870...59S: ALMA/ATCA points extrapolated back assuming fireball evolution
- 2017ApJ...834....6S: Free-free emission dominates 110 GHz
- 2019ApJS..241...19I: Te = 10^4 K
- 2018ApJ...869..126L: Te = 7000 K, all 36 GHz is free-free, ZAMS population


### Limitations the authors admit
- 2016MNRAS.463..252B: Herschel photometry may include extended emission biasing SFR high; mid-IR Spitzer central pixels may be saturated
- 2020MNRAS.496.1834L: Band 6 cannot reliably trace the shell; deeper image needed
- 2019ApJ...886L...4Z: Opening angle and inclination weakly constrained by the model
- 2019ApJ...886L...4Z: Detailed non-LTE H30alpha modeling not done
- 2019ApJ...884...97L: Dust masses uncertain due to opacity; analytic heating comparison not conclusive
- 2019A&A...621A..27F: Upper limits dominate many SFRs; no intermediate-frequency data to determine synchrotron steepening
- 2024ApJ...967...15K: Errors do not include distance uncertainty or density gradients
- 2015A&A...577A..30A: MM1a free-free fit least robust as turnover may be above 25 GHz
- 2017A&A...605A..78A: 100 GHz results 30-55'' from the limb may be affected by the 60'' beam
- 2020MNRAS.499..193K: MUSE spectral resolution is larger than measured Halpha dispersions, so these are uncertain
- 2018ApJ...862...94L: nu_a not constrained, causing parameter degeneracies; epsilon_e~0.9 problematic
- 2015MNRAS.450L..80B: Unidentified systematic amplitude calibration effects could affect flux densities
- 2015MNRAS.450L..80B: Attenuation analysis uses simple sheet model
- 2021A&A...652A..92N: Observed p-mode rms is a lower limit since resolution is coarse and pixels are correlated
- 2024A&A...684A.134R: Dust masses highly uncertain; radiative transfer needed
- 2024A&A...684A.134R: Non-simultaneous accretion and free-free measurements; variability
- 2017A&A...606A..17M: Gas masses depend on uniform Galactic alpha_CO; may be overestimated by factor >~8 if alpha_CO ~0.8
- 2017A&A...606A..17M: Selection bias at z>~3 toward warmer, brighter sources
- 2025ApJ...990...29H: Only three free parameters due to few observables; single-phase ionized gas cannot reproduce [O II]
- 2017A&A...602L..10O: Limited resolution smears fine structures and reduces contrast; spectral index errors may be underestimated
- 2025A&A...699A..62J: Detailed SED modeling is needed to constrain the magnetic field
- 2014ApJ...791...95A: Departure from spherical symmetry would make the solution degenerate; finer resolution needed
- 2014ApJ...791...95A: Wind parameters during eruption cannot be strictly constrained
- 2018ApJ...864L..17G: Completeness of the core catalog is hard to evaluate and depends on the models used
- 2020A&A...640A..27V: Stellar mass differences and binarity cannot be accounted for in the comparison
- 2020A&A...640A..27V: Kaplan-Meier assumption of nondetection independence not met at low masses
- 2023NatAs...7...80U: PA difference between radio and optical only ~90% significant
- 2020A&A...634A...9M: Core result holds only if thermal contamination of 108 GHz flux is below ~80%, which is poorly constrained
- 2021A&A...646A.127H: Cannot exclude a faint diffuse larger-scale CO component given data depth
- 2015ApJ...813...45L: Dust temperature unconstrained for most sources; L_BB and SFR uncertain by orders of magnitude
- 2019ApJ...881...33H: Short observations may miss flares; emission mechanism cannot be inferred from non-detections
- 2026ApJ..1004..126K: Spectral shape uncertain with narrow frequency range and large errors
- 2015ApJ...802...69B: ALMA lacked Tsys measurements on Sgr A* itself, requiring a correction
- 2026ApJ..1003L..17Y: Fit decay timescales are approximate because of limited light-curve duration
- 2024ESC.....8..665M: Coarse resolution; morphology cannot be determined
- 2017ApJ...849...90S: X_CO analysis beyond scope; masses uncertain by factor of few
- 2021A&A...653A.117B: Low statistics and poorly constrained temperatures hamper strong conclusions
- 2018ApJ...853..171G: Catalog potentially incomplete; completeness cannot be quantified
- 2018ApJ...853..171G: Column density maps not very accurate; SFR strongly dependent on assumed timescale
- 2017A&A...602A..19L: SED models are degenerate and non-unique
- 2019ApJ...881L...2B: 868 GHz measured four days from the others, longer than variability coherence time
- 2025A&A...699A.369V: Most clumps unresolved; missing extended flux without Total Power data; non-LTE modeling out of scope
- 2014ApJ...796...82Z: Equipartition estimates may be inaccurate for flat spectra; double-subtracted images unusable due to errors
- 2018ApJ...863...96Y: Absolute brightness temperature is hard to determine; S/N poor beyond 10'' off limb; resolution comparable to blob size
- 2018ApJ...863...96Y: Could not confirm jet generation models
- 2021A&A...656A..46M: Calibration uncertainty not included in fit uncertainties; line flux scaling anomalies in some tunings
- 2021A&A...656A..46M: STATCONT continuum subtraction not optimal for lines near noise level
- 2019ApJ...878L..26L: Systematic uncertainties from RS dynamics approximations and stochastic random walk; forward-shock parameters degenerate since nu_a not located
- 2015ApJ...813..118M: Only three regions; nuclear HCN cut off by bandpass; single-component fit poor for Enuc. 2
- 2020ApJ...888L..28S: Width comparable to beam, so the actual width may be narrower
- 2020ApJ...888L..28S: Only relative brightness temperatures because single-dish data not combined
- 2024ApJ...972..163L: Q band hard to calibrate and marginal; detailed spinning-dust model beyond scope
- 2019ApJ...882....1L: Core continuum flux is a lower limit due to resolved-out extended emission
- 2024ApJ...972..111L: Only projected distances and radial velocities known; spatial offset of redshifted [C II] smaller than beam
- 2017ApJ...835L..13S: Blob ages uncertain due to assumed uniform radial velocity
- 2025A&A...695A.233R: Sparse uv-coverage causes large systematic uncertainties on core size and flux
- 2013ApJ...772..149C: Only time-steady heating modeled; no flares, nonthermal emission, or 3D geometry
- 2019A&A...622A..26G: CF+ and C3H+ lines are weak and contaminated; Galactic center abundances cannot be determined absolutely
- 2020ApJ...892..111F: Sensitivity non-uniform so occurrence is likely underestimated; sample biased toward large bright disks
- 2016ApJ...833L...6C: Large structures (>~12") undersampled in Band 7; could matter for dust
- 2016ApJ...833L...6C: Dust mass may be underestimated since warm dust dominates SED peak; LMC X_CO may overestimate gas
- 2020ApJ...898...54T: Low velocity resolution (3 km/s) hindered line identification and Gaussian fitting; CH3CN optical thickness cannot be ruled out
- 2019ApJ...871..185L: Source catalogue edits are subjective
- 2019ApJ...871..185L: Thickness H(r) cannot be measured; assumption oversimplified
- 2019A&A...628A..85V: Spitzer catalog is incomplete, so low-mass disks may be underrepresented
- 2019A&A...628A..85V: Dust masses assume optically thin emission and a fixed temperature; the D31 binary is variable
- 2018ApJ...869..114I: Eta, B and R are degenerate; eta had to be fixed
- 2025A&A...694A.166C: 3 mm data cannot resolve the emission distribution in distant sources
- 2015ApJ...801...82H: Missing flux and lack of short baselines; BN outside field of view; flux calibration unreliable for sources outside primary beam; no size correction in SED
- 2017ApJ...841L...5S: ALMA-XRT alignment uncertain by up to 5"
- 2017ApJ...841L...5S: Three-dimensional path unknown
- 2020A&A...633A.127F: Mass uncertainty dominated by assumed alpha and geometry; values are lower limits due to projection
- 2017ApJ...848L..21A: Bad weather may cause flux decorrelation at high frequency in the Sep 5 epoch
- 2015ApJ...811...39I: 150 pc resolution mixes AGN and SB contributions; CO(3-2) only partially covered
- 2020A&A...643A..41D: Simulation magnetic topology not comparable to the observed region; no IRIS data; DEM coronal estimates are lower limits
- 2025ApJ...993...90S: 12CO affected by foreground absorption; gas mass a lower limit
- 2025ApJ...993...90S: Dust mass depends heavily on opacity and temperature
- 2019PASJ...71L...3F: Low-frequency spectra for 2017 are unavailable; earlier periastron spectra used instead
- 2025ApJ...991...53C: Halo internal structure and magnification are poorly constrained; lens redshifts uncertain
- 2019MNRAS.484L..85M: Single object; possible geometric asymmetries or time dependence
- 2025MNRAS.540..364A: Sparse simultaneous multiwavelength data prevent detailed study of the double flare
- 2016MNRAS.459.3629I: LSB covers only part of the broad line, so continuum level is highly uncertain
- 2020ApJ...890..129K: Mass uncertainty from dust opacity exceeds one order of magnitude
- 2018ApJ...866..141K: Source-X has too little visibility data for size analysis; Td assumed
- 2018ApJ...866..141K: Lack of redshifted counterpart for SM1-A outflow is puzzling
- 2019ApJ...883...71C: Resolution comparable to ring separations smooths contrasts
- 2025ApJ...993..120H: Dust mass may be a lower limit if emission is optically thick
- 2025ApJ...993..120H: A closer unresolved binary cannot be ruled out
- 2015ApJ...804...37L: Kinematic analysis preliminary since arm inclinations unknown
- 2017ApJ...850...35L: Side lobes may affect 1.3 mm umbral brightness, which should be treated as an upper limit
- 2020ApJ...901..151S: Electron density of ionized gas is uncertain, and xi is difficult to estimate
- 2019ApJ...871...73H: Band 9 excess is only 2 sigma
- 2020ApJ...891L...8M: Model is 2D and may limit LOS superposition
- 2017MNRAS.468L..87C: Cold dust mass is only an estimate; alternative dust properties would change it
- 2020ApJ...895L...2N: Masses highly uncertain due to cm dust opacity
- 2019MNRAS.483.1624B: CASA <5.0 7m mosaic flux scaling issue: Band 6 overestimated ~8 per cent, Band 3 ~2 per cent, not corrected
- 2019MNRAS.483.1624B: Completeness tested only for beam-sized sources
- 2018ApJ...860...77E: Dust masses are inaccurate due to optical depth and temperature assumptions
- 2017ApJ...851..126V: Cycle 2 band 4 CO(3-2) data too noisy and unresolved, so cycle 3 data used
- 2024A&A...687A.163B: Temperature assumed uniformly (100 K), uncertain; free-free may be overestimated
- 2016ApJ...821..112K: Four lines insufficient to constrain four free parameters; two-phase model still only within 1.5-2 sigma
- 2016ApJ...821..112K: Different uv-coverages across transitions; 6-5 least well sampled
- 2020ApJ...896...35J: Free-free contribution at 1.2 mm not removed; relative astrometry insufficient
- 2018A&A...617A.137F: Heterogeneous S/N precludes flux-limited survey; non-detections bias OB sample; mm flux of extended sources partly resolved out
- 2016ApJ...826...16E: Background molecular cloud emission could hide gas from background disks
- 2016ApJ...826...16E: Cluster membership of new GeMS sources uncertain
- 2018ApJ...860....9M: Knot D lacks a Band 3 limit due to missing flux from limited largest angular scale
- 2024ApJ...962...48J: Single-temperature, single-velocity assumption and non-LTE excitation of some lines (5-4) not explored
- 2024ApJ...962...48J: Dust temperature not well known and assumed equal to Trot
- 2017ApJ...850...54C: Missing short spacings; about half of expected flux recovered
- 2020ApJ...897L..33J: Some centroid positional errors are large at high velocities; RRL masers are variable
- 2017MNRAS.467L.120M: Possible unresolved binary cannot be excluded
- 2017ApJ...840...32T: Missing flux on scales >2.1" affects spiral morphology and contrast
- 2019ApJ...883L...2M: For PKS 1510-089 the minimum may be a low state of the core matching IC/CMB by chance.
- 2019Natur.569..519K: Extinction correction might underestimate attenuation toward GMC density peaks
- 2019Natur.569..519K: eps_sf and eta_fb depend on CO-to-H2 and Halpha-to-SFR conversion factors
- 2020ApJ...903...29M: Molecular line contamination dominates flux accuracy; G328.8076 slope unreliable; ages unknown; photon escape in evolved regions
- 2018A&A...619A..40M: Only one epoch; limited frequency coverage; no nutation; simple model
- 2016ApJ...821L..16C: Mass estimates are rough; detailed radiative transfer modeling needed; free-free correction adds uncertainty at the center
- 2016ApJ...822L..10I: Only one pointing; star-forming ring at 10-15 arcsec not adequately probed

### Settings cards flag as needed but not stated
- self-calibration solution intervals and number of iterations: 6
- self-calibration solution intervals: 6
- casa version: 5
- casa version and pipeline version: 4
- flux scale uncertainty: 3
- casa version and calibration procedure: 3
- line-free channels used for continuum subtraction: 3
- line-free channels used for continuum: 3
- self-calibration solution intervals and number of rounds: 2
- flux calibrator and flux-scale uncertainty: 2
- flagging details: 2
- source coordinates: 2
- image size and cell size: 2
- self-calibration solution intervals and reference antenna: 2
- line-free channel selection for continuum: 2
- line-free channel ranges used for uvcontsub: 2
- clean threshold, masks, image size and cell size: 2
- pipeline version: 2
- flux calibrator and flux scale uncertainty: 2
- line-free channels for continuum subtraction: 2
- exact clean parameters (niter, threshold, masks): 1
- region definitions for t, n, c, s apertures (only in figure): 1
- image rms values: 1
- monte carlo and gauss-hermite fitting algorithm details: 1
- phase centre coordinates: 1
- fit algorithm and optimizer for disc model: 1
- clean threshold, niter, masks, image size and cell size for the aca tclean imaging: 1
- exact self-calibration solint sequence for band 4 intermediate rounds and reference antenna: 1
- per-pixel definition of pwn area and shell masks used in the smearing experiment: 1
- power-law fit method details (fit weights) beyond monte carlo description: 1
- pulsar coordinates and atca/aca alignment offsets: 1
- interpolated kappa and beta values for forsterite dust: 1
- whether flux in table 4 for aca is from peak times correction or integrated aperture: 1
- image sizes, cell sizes, deconvolver, masking and clean thresholds: 1
- line-free channels and continuum subtraction method: 1
- casa version and whether pipeline used: 1
- channel width for h30alpha cubes: 1
- final beams (only in figure) and rms noise: 1
- spectral window setup: 1
- vla calibration/imaging details: 1

## Paper excerpts (40 of 119, chosen for detail and spread over fields/years)

### 2016MNRAS.463..252B: Free-free and H42α emission from the dusty starburst within NGC 4945 as observed by ALMA (2016; nearby_galaxies, star_formation; observational_alma_primary)
- question: Measure free-free emission, electron temperature and star formation rate in the NGC 4945 central starburst from ALMA 85.69 GHz continuum and H42α, and compare with infrared and radio SFRs
- step 4: SED decomposition for free-free fraction
  - method: fit power laws for synchrotron (free index), free-free (Gaunt factor, Te=5000 K), dust (index 4) to 3-350 GHz data [5 SED: "We model the synchrotron, free-free, and thermal dust emission components as power laws."]
  - parameter: Te fixed 5000 K; dust index 4 [5 SED: "The spectral index of the dust emission is fixed to 4"]
  - fitting: Monte Carlo for uncertainty; 10% errors for two datasets [5 SED: "Using a Monte Carlo approach, we found that the uncertainty in the percent of total emission from free-free emission is 7%."]
  - validation: tests varying Te 3000-10000 K and indices; fraction varied ≤10% [5 SED: "we found that the percent of the flux density from free-free emission at 85.69 GHz varied by $\leq$10%."]
- step 5: Electron temperature
  - method: line-to-free-free continuum ratio with Storey & Hummer emissivities, case B, ne=1e3 cm-3 [6 Electron temperature: "we use $\epsilon_\nu$ values corresponding to case B recombination and a fixed $n_e$ value of $10^3$ cm$^{-3}$"]
  - assumption: 84±10% of continuum is free-free [6 Electron temperature: "All $T_e$ are derived assuming that 84$\pm$10% of the continuum emission originates from free-free emission."]
  - validation: compared with Milky Way Te [6 Electron temperature: "The $T_e$ measurements are broadly consistent with the low end of $T_e$ measurements within the Milky Way"]
- result: Free-free fraction at 85.69 GHz = 84 ± 10% % [abstract: "84%$\pm$10% of the 85.69 GHz continuum emission originates from free-free emission"]
- result: Electron temperature (T region) = 5400 ± 600 K [Table 2 (Te): "T | $0.31 \pm 0.04$ | $12.9 \pm 0.8$ | $42 \pm 5$ | $5400 \pm 600$"]
- limitation (authors): Herschel photometry may include extended emission biasing SFR high; mid-IR Spitzer central pixels may be saturated [7.3: "these measurements may include additional emission from circumnuclear structures that are more extended than the structures seen in the ALMA data"]
- not stated (card): Exact clean parameters (niter, threshold, masks); Region definitions for T, N, C, S apertures (only in figure); Image rms values; Monte Carlo and Gauss-Hermite fitting algorithm details; Phase centre coordinates; Fit algorithm and optimizer for disc model

### 2020MNRAS.496.1834L: Atacama Compact Array observations of the pulsar-wind nebula of SNR 0540-69.3 (2020; star_formation, milky_way_ism; observational_alma_primary)
- question: What is the synchrotron spectrum of the PWN of SNR 0540-69.3 from radio through mm to UV/IR, how does it join at higher frequencies, and is there room for dust in the PWN?
- step 3: Fit synchrotron power laws
  - method: Power-law fits to radio/mm and IR/UV flux densities, excluding line-contaminated HST filters [4 Discussion: "we have discarded HST filters which encapsulate strong nebular lines from our analysis"]
  - parameter: 10 000 simulated data sets, 500 seeds averaged, 68% bounds [4 Discussion: "We did this 500 times with different seed values for the randomizer"]
  - assumption: Gaussian flux uncertainties; frequencies uniform within bins [4 Discussion: "the flux uncertainty is assumed to have a Gaussian distribution, and the frequency distribution to be evenly distributed within the frequency bins"]
  - fitting: Monte Carlo power-law fits, median taken as index [4 Discussion: "assigned the median value to be the preferred $\alpha_{\nu,{\rm radio/mm}}$"]
- step 4: Derive break, B field and dust mass
  - method: Intersect power laws for break; equate synchrotron lifetime to age for B; optically thin forsterite dust emission model [4 Discussion: "The dust emission was calculated assuming optically thin forsterite dust."]
  - parameter: remnant age 1100 yr; D = 50 kpc; T_dust = 55 K [4 Discussion: "assumed to be 1 100 years (cite: rey85)"]
  - assumption: Small silicate (forsterite) grains, kappa from Mennella et al. [4 Discussion: "We have assumed small-sized dust particles"]
  - validation: Compared with Williams et al. 2008 dust model [4 Discussion: "Our dust mass estimate is consistent with the $\sim 3\times10^{-3} ~{\rm M}_\odot$ of silicate dust"]
- result: radio/mm spectral index 1.449-233.5 GHz = 0.17 ± 0.02 dimensionless [abstract: "the spectral index $\alpha_{\nu} = 0.17\pm{0.02}$"]
- result: UV/IR spectral index = 0.87 ± +0.08/-0.10 dimensionless [abstract: "we arrive at $\alpha_{\nu} = 0.87^{+0.08}_{-0.10}$"]
- result: SNR shell spectral index 8.6-145 GHz = 0.64 ± 0.05 dimensionless [abstract: "we derive $\alpha_{\nu} = 0.64\pm{0.05}$ for the range $8.6-145$ GHz"]
- result: magnetic field from break = 3.9e-4 ± +1.1/-0.7 e-4 G [4 Discussion: "$B = (3.9^{+1.1}_{-0.7}) \times10^{-4}$ G"]
- result: dust mass = 2.5e-3 ± not stated Msun [abstract: "There is room for $2.5\times10^{-3} ~{\rm M}_\odot$ of dust with temperature $\sim 55$ K"]
- limitation (authors): Band 6 cannot reliably trace the shell; deeper image needed [3.1 Morphology revealed by ACA and ATCA: "but a deeper image is needed to draw firm conclusions"]
- not stated (card): CLEAN threshold, niter, masks, image size and cell size for the ACA tclean imaging; Exact self-calibration solint sequence for Band 4 intermediate rounds and reference antenna; Per-pixel definition of PWN area and shell masks used in the smearing experiment; Power-law fit method details (fit weights) beyond Monte Carlo description; Pulsar coordinates and ATCA/ACA alignment offsets; Interpolated k…

### 2019ApJ...886L...4Z: Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05 (2019; star_formation; observational_alma_primary)
- question: Does the massive protostar G45 drive a photoionized (photoevaporative) bipolar outflow, and what do its properties imply for radiation feedback and ongoing accretion?
- step 4: Fit free-free model to 1.3 and 7 mm images
  - method: Grid of isothermal bipolar cavity models with density power law n~r'^-2; minimize chi2_tot over Te, n0, varpi0, theta_w [Model Fitting of 1.3 and 7 mm Free-free…: "we minimize $\chi^2_\mathrm{tot}\equiv (\chi^2_\mathrm{1.3mm}+\chi^2_\mathrm{7mm})/2$ by varying the free parameters within reasonable ranges"]
  - parameter: theta_w,sky fixed at 40 deg; PA 3 deg; Te 5e3-2e4 K; n0 3e6-3e8 cm-3; varpi0 30-300 au; theta_w 20-40 deg [Model Fitting of 1.3 and 7 mm Free-free…: "we fix $\theta_{w,\mathrm{sky}}=40^\circ$ based on the observed 1.3 mm continuum morphology"]
  - assumption: Each ion has single charge [Model Fitting of 1.3 and 7 mm Free-free…: "Here we only consider a situation that each ion has only one charge (1$e$)"]
  - fitting: Grid chi2 minimization over regions with I_obs>0.1 I_center [Model Fitting of 1.3 and 7 mm Free-free…: "Here the integration is over a region with $I_\mathrm{obs}>0.1 I_\mathrm{obs,center}$ at each wavelength."]
  - validation: Compared with images, spectral index, SED and profiles; model fluxes within 5% of observed [Model Fitting of 1.3 and 7 mm Free-free…: "The model fluxes are slightly lower (within $5\%$) than the observed values."]
- step 7: Minimum-energy magnetic field from synchrotron regions
  - method: Classical equipartition formula for regions with alpha<-0.3 and >5 sigma [Estimating the Magnetic Field Strength …: "We define the synchrotron emission region as the region with intensity spectral indices of $\alpha<-0.3$ and both 1.3 and 7 mm emissions $>5\sigma$."]
  - parameter: c12=3.2e6, k=40 [Estimating the Magnetic Field Strength …: "we obtain $c_{12}=3.2\times 10^6$ following (cite: Govoni04)"]
  - assumption: All emission in these regions is synchrotron (upper limit) [Estimating the Magnetic Field Strength …: "Assuming all the 1.3 and 7 mm emissions from these regions are due to synchrotron emission"]
- result: Best-fit electron temperature = 10,000 ± not stated K [Model Fitting of 1.3 and 7 mm Free-free…: "The best-fit model (minimum $\chi^2_\mathrm{tot}$) has $T_\mathrm{e}\approx10,000\:{\rm K}$"]
- result: Central electron density n0 = 1.5e7 ± not stated cm^-3 [Model Fitting of 1.3 and 7 mm Free-free…: "$n_0\approx1.5\times 10^7~\mathrm{cm}^{-3}$"]
- result: Launching region outer radius = 110 ± not stated au [Model Fitting of 1.3 and 7 mm Free-free…: "$\varpi_0\approx110~\mbox{au}$"]
- result: Minimum-energy B field (north, south) = 15 and 17 ± not stated mG [Estimating the Magnetic Field Strength …: "These values give $B_\mathrm{min}=15$ and 17 mG in the northern and southern regions, respectively."]
- limitation (authors): Opening angle and inclination weakly constrained by the model [Model for Free-free Emission: "The model constraints on the true outflow opening angle (which depends on the inclination) are weak."]
- limitation (authors): Detailed non-LTE H30alpha modeling not done [Model for Free-free Emission: "detailed modeling of the H30$\alpha$ emission including the maser effects is out of the scope of this paper"]
- not stated (card): Image sizes, cell sizes, deconvolver, masking and clean thresholds; Line-free channels and continuum subtraction method; Self-calibration solution intervals and number of iterations; CASA version and whether pipeline used; Channel width for H30alpha cubes; Final beams (only in figure) and rms noise; Spectral window setup; VLA calibration/imaging details; Model grid sampling steps for chi2 minimiz…

### 2019ApJ...884...97L: Diagnosing 0.1-10 au Scale Morphology of the FU Ori Disk Using ALMA and VLTI/GRAVITY (2019; protoplanetary_disks, star_formation; observational_alma_primary)
- question: What is the 0.1-10 au scale morphology and thermal structure of the FU Ori disk (and companion FU Ori S), as constrained by new ALMA Band 3/4 continuum and VLTI/GRAVITY data plus the broadband SED?
- step 4: Multi-component SED model with MCMC
  - method: Sum of dust slab and free-free components with mutual obscuration, fit to SED with MCMC [4.3 Abstracted geometric model and inte…: "After we obtained an approximate fit, we used MCMC to simultaneously optimize all free parameters"]
  - software: emcee
  - parameter: 84 walkers, 1500 steps, first 500 discarded [4.3 Abstracted geometric model and inte…: "The MCMC fittings were initialized with 84 walkers with 1500 iterative steps each; in the end, the results from the first 500 steps were discarded."]
  - parameter: Herschel/SPIRE, PACS, Spitzer/IRS errors set to 1000, 10, 1 times the fluxes [4.3 Abstracted geometric model and inte…: "artificially assigning the flux errors of the *Herschel*/SPIRE, *Herschel*/PACS, and *Spitzer*/IRS to be 1000, 10, and 1 times the detected fluxes"]
  - assumption: DSHARP opacities, 170 K ice sublimation, power-law grain size q=3.5, amin=1e-4 mm, face-on slabs [4.2 Individual emission components: "we simply assumed the typical power-law grain size distribution with a power-law index $q=$3.5, the minimum grain size $a_{\mbox{\scriptsize min}}=$10$^{-4}$ mm"]
  - fitting: flat priors from 0.5x to 2x initial value; likelihood set to -inf if FU Ori S 9 GHz flux exceeds 3 sigma [4.3 Abstracted geometric model and inte…: "We assumed flat priors, which permitted each parameter to vary from half of its initial value to two times of the initial value."]
  - validation: Monitored likelihood contributions; model also close to unfitted Spitzer/Herschel spectra [4.3 Abstracted geometric model and inte…: "We have monitored how the likelihood evolved over the MCMC iterations to make sure that the contribution of the *Herschel* and *Spitzer* data are on the same order with the rest of the data."]
- result: FUOri_dust1 temperature = 370 ± +63/-49 K [Table 4: "370$^{+63}_{-49}$ & 45$^{+10}_{-12}$"]
- result: FUOri_dust1 amax = 2.4 ± +0.40/-0.32 mm [Table 4: "2.4$^{+0.40}_{-0.32}$ & Comp. 2"]
- result: FUOri_dust2 temperature = 140 ± +20/-26 K [Table 4: "2 & 140$^{+20}_{-26}$ & 0.63$^{+0.12}_{-0.099}$"]
- result: FUOri_dust4 temperature = 690 ± +18/-12 K [Table 4: "4 & 690$^{+18}_{-12}$ & 0.0095$^{+0.0019}_{-0.0018}$"]
- result: FUOri_dust1 dust mass = 510 ± +210/-190 Earth masses [Table 4: "510$^{+210}_{-190}$"]
- limitation (authors): Dust masses uncertain due to opacity; analytic heating comparison not conclusive [4.4.1 FU Ori model: "We cannot accurately determine the dust masses of these two components due to the uncertainties of the dust mass opacities."]
- not stated (card): Line-free channel selection and masks for clean; Image size, cell size, number of clean iterations/threshold; Self-calibration solution intervals and number of rounds; Gaussian fit regions/procedure for flux extraction; Initial parameter values for MCMC and the full likelihood form; Stated GRAVITY reduction/calibration details beyond pipeline version; Pérez et al. 225 GHz fluxes and other SED dat…

### 2019A&A...621A..27F: Massive galaxies on the road to quenching: ALMA observations of powerful high redshift radio galaxies (2019; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What are the star-formation rates of powerful high-z radio galaxy hosts once synchrotron contamination and spatially resolved components are separated using ALMA data, and how do they compare with the main sequence and SMBH growth?
- step 2: Fit MIR-radio SEDs with three components
  - method: MR-MOOSE Bayesian MCMC fit of AGN power-law with cutoff, modified blackbody for SF dust, and synchrotron power law, with multi-resolution component assignment [3 MR-MOOSE: "The code fits simultaneously all pre-selected analytic models and uses Bayesian statistics to find the most likely solution given the set of observed fluxes."]
  - software: MR-MOOSE, emcee
  - parameter: lambda_cut=33 um fixed; T prior [20,70] K; gamma [0,6]; alpha [-4,0] [Table 2: "N$_\text{BB}$, T \[20,70K\]"]
  - assumption: beta=2.5, nu0=1.5 GHz; uniform priors; synchrotron without cutoff (maximum contribution) [3.1.2 Star-formation model: "A value of $\beta=2.5$ has been adopted in this paper."]
  - fitting: emcee MCMC, chi2 likelihood with upper-limit treatment of Sawicki2012, uniform priors [3.2 Fitting procedure: "it uses Bayesian parameter estimation to find posterior distributions of the free parameters which are determined based on the prior distribution (uniform) and the likelihood function."]
  - validation: lambda_cut calibrated on 4C 23.56; comparison with Drouart2014 luminosities [3.1.1 AGN model: "This value was determined by letting $\lambda_\text{cut}$ be a free parameter for one galaxy and finding the best fit value."]
- limitation (authors): Upper limits dominate many SFRs; no intermediate-frequency data to determine synchrotron steepening [MRC 1017-220: "without a data point at an intermediate frequency between the radio and ALMA data, it is not possible to make a final conclusion"]
- not stated (card): Number of walkers, steps and burn-in for emcee; Exact line-free/flagged channels per source; CASA version used for imaging; Image size and clean threshold/masks; Flux calibrator and flux-scale uncertainty; How ALMA band 3/4 photometry was extracted per source in detail (regions, apertures); Prior treatment of normalisations in MR-MOOSE

### 2024ApJ...967...15K: Infall Motions in the Hot Core Associated with the Hypercompact H II Region G345.0061+01.794 B (2024; star_formation, astrochemistry; observational_alma_primary)
- question: What are the physical and kinematical characteristics of the hot molecular core around the HC HII region G345.0061+01.794 B, and is it rotating and infalling?
- step 3: Ionized gas properties from H29alpha
  - method: Gaussian fits to H29alpha map and spectrum; T_e from line-to-continuum ratio; Mezger-Henderson equations for n_e, EM, mass, Lyman photons [3.2 Ionized gas: "Assuming that the HII region is spherical and homogeneous, using the values of the continuum flux density at 256 GHz (325$\pm$65 mJy)"]
  - assumption: Spherical homogeneous HII region, LTE, He+/H+=0.096 [3.2 Ionized gas: "Assuming that the HII region is spherical and homogeneous"]
  - fitting: Gaussian fits [3.2 Ionized gas: "A Gaussian fit to the line profile gives a linewidth of 33.7$\pm$2.3 km s$^{-1}$"]
- step 4: Dust mass
  - method: Optically thin dust mass after subtracting free-free from total continuum [3.3 Dust continuum: "We estimate the dust continuum flux of 565$\pm$112 mJy by subtracting the contribution of the free-free emission of 325$\pm$65 mJy"]
  - assumption: T_dust = 250 K, gas-to-dust 100, k=0.0078 cm2/g, D=2.38 kpc [3.3 Dust continuum: "Adopting $T_\text{dust}$ = 250 K (see Section [4.1](#sec:T_rot)), we derive a dust mass of $\sim$4 M$_{\odot}$"]
- result: Electron temperature = 8094 ± ±1534 K [3.2 Ionized gas: "we get an electron temperature $T^*_e$=8094$\pm$1534 Kelvin"]
- result: Emission measure = 4.6e8 ± ±0.9e8 pc cm^-6 [3.2 Ionized gas: "an emission measure of (4.6$\pm$0.9)$\times$10$^8$ pc cm$^{-6}$"]
- result: Ionized gas mass = 3.6e-3 ± ±0.3e-3 Msun [3.2 Ionized gas: "a mass of ionized gas (3.6$\pm$0.3)$\times$10$^{-3}$ $M_{\odot}$"]
- result: Dust mass = ~4 ± not stated Msun [3.3 Dust continuum: "we derive a dust mass of $\sim$4 M$_{\odot}$ (for a distance of 2.38 kpc)"]
- result: H29alpha linewidth = 33.7 ± ±2.3 km/s [3.2 Ionized gas: "gives a linewidth of 33.7$\pm$2.3 km s$^{-1}$"]
- limitation (authors): Errors do not include distance uncertainty or density gradients [3.2 Ionized gas: "The errors do neither include the distance uncertainty nor potentially strong density gradients"]
- not stated (card): CASA version and whether the pipeline or manual calibration was used; Line-free channels chosen for uvcontsub; Weighting/robust, cleaning threshold, masks, cell and image size; Flux scale uncertainty; Moment integration ranges and clipping for CH3CN and SO2; MADCUBA fit settings (source size, linewidth, priors); Fitting procedure and free parameters of the infall model; fit weights; How S_ff at 2…

### 2015A&A...577A..30A: Tightening the belt: Constraining the mass and evolution in SDC335 (2015; star_formation, milky_way_ism; multi_facility_alma_minor)
- question: What are the properties (ionising photon flux, spectral type, luminosity, gas mass) of the stars forming in the massive mm-cores MM1 and MM2 of SDC335, and what stellar population will form?
- step 2: Fit free-free emission
  - method: Non-linear least squares of free-free model for turnover frequency and size; EM from tau=1 [3.1.1: "implementing a non-linear least square regression algorithm. The fitted parameters are the free-free turnover frequency, $\nu_t$, (where the optical depth, $\tau=1$) and the physical diameter of the source, $l$."]
  - assumption: Te fixed to 10,000 K [3.1.1: "fixing $T_e$ to the fiducial 10,000K"]
  - fitting: non-linear least squares [3.1.1: "implementing a non-linear least square regression algorithm"]
- step 3: Derive Lyman flux and ZAMS type
  - method: N_Lym from 23 GHz flux, compared to Davies11 ZAMS values [3.1.3: "For each source we calculate $N_{Lym}$ using the 23 GHz continuum integrated flux density value."]
  - assumption: Cylindrical homogeneous HII region, D=3.25 kpc [3.1.3: "Assuming a cylindrical homogeneous HII region"]
- step 4: Fit dust SED and derive Lbol and gas mass
  - method: Modified blackbody to free-free subtracted SED; integrate 100 kHz-100 THz; mass from 3.2mm flux [3.2: "The resulting best fit parameters are then used in a direct integration of the SED between 100 kHz and 100 THz"]
  - software: Hyper
  - parameter: Omega_c fixed to radius 11.4 arcsec; priors Td 25 K, nu0 4.3 THz, beta 2.0 [3.2: "are given priors of 25.0K, 4.3 THz and 2.0 respectively"]
  - assumption: kappa=0.1(lambda/0.3mm)^-beta cm2/g, dust-to-gas 0.01 [3.2: "assuming a dust to gas ratio of 0.01"]
  - validation: Posteriori refit of MM1a with 43 GHz point consistent [3.2.2: "The new fitted properties for MM1 and MM1a are consistent with the initial fitted values for each source"]
- result: Lbol MM1 = 1.8e4 ± not stated Lsun [Table 3 (properties): "| MM1 | \- | \- | \- | \- | 1.8$\times10^{4}$ | 28.7($\pm$2.3) | 1.97($\pm$0.15) | 763($^{+165}_{-171}$) |"]
- result: Gas mass MM2 = 173 ± +65/-66 Msun [Table 3 (properties): "9.9$\times10^{3}$ | 29.6($\pm$7.2) | 2.26($\pm$0.52) | 173($^{+65}_{-66}$)"]
- limitation (authors): MM1a free-free fit least robust as turnover may be above 25 GHz [3.1.2: "The fit to MM1*a* is the least robust as the data for this source allows a rise in flux beyond 25 GHz."]
- not stated (card): ALMA project code and calibration/imaging of the Cycle 0 data; Peretto13 ALMA flux densities (16% mass correction pending); ATCA imaging weights, cell size and Gaussian-fit details; Fit uncertainties/sampler for the nonlinear least squares; 43 GHz ATCA data are unpublished

### 2017A&A...605A..78A: Center-to-limb observations of the Sun with ALMA . Implications for solar atmospheric models (2017; sun; archival_reuse)
- question: To derive information on the temperature structure of the solar chromosphere and compare it with existing models.
- step 4: Invert CLV to Te(tau)
  - method: Assumed Te = a1 + a2 ln tau; Tb(mu)=a1+a2(ln mu - gamma); least-squares fit; data reduced to common reference frequency using f^-2 absorption [Inversion of the center-to-limb curve: "The coefficients $a_1$ and $a_2$ can be determined by least square fit of the observations."]
  - parameter: ALMA data used up to theta~70 deg [Inversion of the center-to-limb curve: "we used ALMA measurements up to $\theta\simeq70$$^\circ$"]
  - assumption: LTE thermal free-free and H- absorption proportional to f^-2 [Inversion of the center-to-limb curve: "both the free-free and the H$^-$ absorption coefficients are proportional to $f^{-2}$"]
  - fitting: Least squares on logarithmic form; residual RMS ~60 K [Inversion of the center-to-limb curve: "The fit was very good, with an RMS of residuals of $\sim60$ K"]
  - validation: Adding a quadratic term did not change results; power series unstable; compared with Eddington-Barbier and models [Inversion of the center-to-limb curve: "the addition of a quadratic term in ([\[logform\]](#logform)) did not change appreciably either the data fit or the inversion results"]
- result: Global inversion slope a2 = -608 ± not stated K [Inversion of the center-to-limb curve: "The global inversion gave a slope of $a_2=-608$ K."]
- result: Slopes per band (100, 239, 343 GHz) = -608, -519, -818 ± not stated K [Inversion of the center-to-limb curve: "with slopes of $-608$, $-519$ and $-818$ K at 100, 239 and 343 GHz respectively"]
- limitation (authors): 100 GHz results 30-55'' from the limb may be affected by the 60'' beam [Summary and conclusions: "which may have been affected by the 60$''$ antenna beam"]
- not stated (card): Calibration and image reconstruction details of the Science Verification full-disk images (CASA version, procedure); Absolute flux scale/uncertainty; Pixel size and how limb irregularities and the ellipticity were corrected; Voigt fit parameters for diffuse-light correction; Exact mask thresholds; Details of the Fig 4 CLV binning and elliptical radius fitting; Handling of 230 vs 239 GHz naming an…

### 2020MNRAS.499..193K: Measuring the mixing scale of the ISM within nearby spiral galaxies (2020; nearby_galaxies, milky_way_ism; multi_facility_alma_minor)
- question: How homogeneous is the 2D gas-phase metallicity distribution (after radial gradient subtraction) in nearby spiral galaxies, and over what scale are HII region metallicities correlated (the mixing scale)?
- step 1: Compute metallicities and residuals
  - method: Pilyugin2016 S-calibration on extinction-corrected HII region lines; subtract linear radial gradient to get Delta(O/H) [2.1 HII region metallicities: "All metallicity calculations in this paper adopt the empirical (cite: Pilyugin2016) S-calibration (Scal)."]
  - assumption: Case B, Te=10^4 K, Fitzpatrick1999 law with R_V=3.1 [2.1 HII region metallicities: "assuming case B recombination and $T_{\rm e}=10^4$ K, we apply the (cite: Fitzpatrick1999) extinction law assuming a value of $R_V=3.1$"]
  - validation: Repeated with other calibrations in Appendix [2.1 HII region metallicities: "In Appendix [7](#appendix), we repeat our calculations using other common metallicity calibrations."]
- step 2: Measure scatter vs spatial scale
  - method: Standard deviation of Delta(O/H) in circular apertures of increasing diameter, min four HII regions, Cochran correction [3.2 Trends with physical scale: "we apply a correction based on Cochran’s theorem (assuming a normal distributions of values) when calculating $\sigma$(O/H)."]
  - validation: Compared with 100 random shuffles of metallicities and bootstrapping over 100 realizations [3.2 Trends with physical scale: "We repeat this shuffling procedure 100 times for each galaxy, in order to determine the confidence interval of the signal we detect"]
- result: Global scatter in Delta(O/H) = 0.03–0.05 ± not stated dex [abstract: "We observe low (0.03–0.05 dex) scatter in $\Delta$(O/H) globally in all galaxies"]
- result: Scatter on <600 pc scales = 0.02–0.03 ± not stated dex [abstract: "significantly lower (0.02–0.03 dex) scatter on small ($<$600 pc) spatial scales"]
- limitation (authors): MUSE spectral resolution is larger than measured Halpha dispersions, so these are uncertain [2.2 Ancillary data: "without an extremely careful determination of the line spread function we caution against placing high confidence in these measurements"]
- not stated (card): ALMA calibration, imaging and mask details of the PHANGS-ALMA CO maps; Exact CO maps/products used and S/N cut; Radial gradient fit parameters per galaxy (in Paper I); Binning details of correlation function; Stellar mass maps are in prep

### 2018ApJ...862...94L: First ALMA Light Curve Constrains Refreshed Reverse Shocks and Jet Magnetization in GRB 161219B (2018; transients; multi_facility_alma_minor)
- question: What do multi-wavelength (radio to X-ray) observations, including the first ALMA light curve, reveal about the forward and reverse shocks, energetics, circumburst density and jet magnetization of GRB 161219B?
- step 2: Model forward shock with SN and host in all bands
  - method: Synchrotron FS model with jet break, SN 1998bw template, SMC extinction, MCMC [4 Multi-wavelength modeling: "we carry out a Markov Chain Monte Carlo (MCMC) analysis using the Python-based code EMCEE"]
  - software: emcee
  - parameter: 128 chains, 10^4 posterior samples, 10% uncertainty floor [4 Multi-wavelength modeling: "We initialized 128 Markov chains with parameters clustered around their best fit values (with a 3% dispersion)."]
  - assumption: ISM environment; uniform priors, log-uniform for scale parameters [4 Multi-wavelength modeling: "Priors for all scale parameters ($\epsilon_{\rm e}$, $\epsilon_{\rm B}$, $n_{0}$, $E_{\rm K,iso}$, $t_{\rm jet}$, and $\Upsilon_{\rm SN}$) are uniform in logarithmic space"]
  - fitting: emcee MCMC with uniform priors [4 Multi-wavelength modeling: "We assume uninformative, uniform priors on all free parameters."]
- result: circumburst density n0 = 3.2e-4 ± +1.4/-1.2 e-4 cm^-3 [Table: "$(3.2^{+1.4}_{-1.2})\times10^{-4}$"]
- result: jet break time = 33.0 ± +1.5/-1.4 d [Table: "$33.0^{+1.5}_{-1.4}$"]
- result: jet opening angle = 13.44 ± 0.35 deg [Table: "$13.44\pm0.35$"]
- result: beaming-corrected kinetic energy = 1.27e50 ± +0.36/-0.25 e50 erg [Table: "$(1.27^{+0.36}_{-0.25})\times10^{50}$"]
- result: electron index p = 2.079 ± +0.009/-0.006 dimensionless [Table: "$2.079^{+0.009}_{-0.006}$"]
- limitation (authors): nu_a not constrained, causing parameter degeneracies; epsilon_e~0.9 problematic [4.1 Afterglow: "We note that $\ensuremath{\nu_{\rm a}}$ is not constrained by the data, resulting in some degeneracies between the physical parameters"]
- not stated (card): ALMA imaging parameters (tclean weighting, cell, masking) and how flux densities were measured; CASA version and pipeline version; ALMA flux calibrator flux scale uncertainty; Full multi-frequency data tables (only samples printed); Exact MCMC burn-in length and convergence criteria (deferred to earlier papers)

### 2015MNRAS.450L..80B: ALMA observations of 99 GHz free-free and H40α line emission from star formation in the centre of NGC 253 (2015; nearby_galaxies, star_formation; archival_reuse)
- question: Use ALMA 99 GHz free-free continuum and H40alpha emission to derive electron temperature, photoionizing photon rate, SFR and dust attenuation in the centre of NGC 253
- step 3: Determine free-free fraction
  - method: Refit SED of Rodriguez-Rico et al. allowing synchrotron slope to vary [4 Analysis: "we find that $70\pm10$% of the 99.02 GHz emission is from free-free emission"]
  - assumption: Continuum multiplied by 0.70±0.10 [Table 1: "multiplying the measured continuum by $0.70\pm0.10$"]
  - validation: Sensitivity tests with no correction (Te 5800-7100 K) and 50% (Te 2500-3000 K) [4 Analysis: "the measured $T_e$ would increase to values of 5800-7100 K"]
- limitation (authors): Unidentified systematic amplitude calibration effects could affect flux densities [2 Data: "although unidentified systematic amplitude calibration effects could affect the flux densities"]
- limitation (authors): Attenuation analysis uses simple sheet model [4 Analysis: "it is beyond the scope of this paper to explore a more complex treatment of the attenuating medium"]
- not stated (card): CLEAN threshold, iteration count and mask definitions; Line-free channels used for continuum fitting and order of baseline fit; Flagging details; Exact SED data points and fit used to derive 70% free-free fraction; Emissivity and alpha_B interpolation values; Region definitions for E, C, W; Engelbracht line fluxes used for attenuation; Source coordinates

### 2021A&A...652A..92N: ALMA observations of the variability of the quiet Sun at millimeter wavelengths (2021; sun; observational_alma_primary)
- question: Variability of the quiet solar chromosphere at 1.26 mm and 3 mm: spatially resolved p-mode oscillations and transient brightenings
- step 5: Event energies and power-law fits
  - method: Thermal free-free energy from excess Tb, FAL C electron density, and volume from area; power-law fits to frequency distributions [4.3 Energy budgets: "we assume that they emit thermal free-free radiation, the electron density and apparent volume do not change significantly in the course of the events, and that the filling factor is unity"]
  - assumption: height equals horizontal size; filling factor unity [4.3 Energy budgets: "assuming their height is equal to their horizontal size"]
  - fitting: Power-law fit with Poisson bin errors [4.2 Properties: "derived from the propagation of errors associated with the histogram bins assuming Poisson statistics"]
- result: Energy power-law index 1.26 mm / 3 mm = 1.64 / 1.73 ± 0.04 / 0.06 dimensionless [4.3 Energy budgets: "indices of $1.64 \pm 0.04$ and $1.73 \pm 0.06$ for the 1.26 mm and 3 mm events"]
- limitation (authors): Observed p-mode rms is a lower limit since resolution is coarse and pixels are correlated [5 Conclusions: "as a lower limit of the actual value"]
- not stated (card): CASA version and imaging parameters (weighting, deconvolver, self-cal solints); Exact pointing offset values from the general-relativity correction; Method to remove oscillations from light curves in detail (in Paper II); Treatment of the 2.5 sigma threshold sigma definition and network/intra-network segmentation thresholds; Energy distribution binning and fit ranges; Whether calibrated visibilit…

### 2024A&A...684A.134R: Correlation between accretion rate and free-free emission in protoplanetary disks. A multiwavelength analysis of central mm/cm emission in transition disks (2024; protoplanetary_disks; archival_reuse)
- question: What is the nature of the central mm/cm emission close to the star in transition disks (thermal dust vs free-free from a jet or wind), and does it correlate with accretion, X-ray luminosity or mass-loss properties?
- step 5: Test free-free luminosity vs L_acc and L_X
  - method: Pearson correlation between free-free luminosity (from mm flux) and accretion/X-ray luminosity [5.2 Photoevaporative wind or jet-and-MH…: "no strong correlation between the free-free luminosity, as inferred from the millimeter flux, and the accretion luminosity is found"]
- step 6: Compute ionized mass loss rate and correlate with accretion rate
  - method: Reynolds jet model equation; linmix regression of Mdot_i vs Mdot [5.3 Properties of the jet emission: "we estimated the ionized mass loss rate $\dot M_\text{i}$ following the modeling of the free-free emission from a jet by (cite: 1986Reynolds)"] [Footnote: "The liner regression was performed with `linmix`"]
  - software: linmix
  - parameter: T = 1e4 K, nu_m = 40 GHz, theta_min/theta_maj = 0.5, v_jet = 140 (M*/0.5 Msun)^0.5 km/s, jet inclination = outer disk inclination [5.3 Properties of the jet emission: "A value of $T=10^4$ K is adopted for the ionized gas"] [5.3 Properties of the jet emission: "We assumed that the jet is perpendicular to the plane of the disk"]
  - assumption: central emission is jet free-free emission [5.3 Properties of the jet emission: "Under the assumption that the central emission in those ten systems is associated with the gas from an ionized jet"]
  - fitting: linmix linear regression [Footnote: "The liner regression was performed with `linmix`"]
  - validation: Compared with Mdot_i/Mdot from [OI] HVC (Nisini 2018) [5.3 Properties of the jet emission: "These results are consistent with ionized mass ejection rates measured from HVC \[O I\]6300"]
- result: Pearson r, free-free luminosity vs L_acc = 0.49 ± 0.28 (p=0.10) dimensionless [5.2: "pearson correlation coefficient $r=0.49\pm0.28$, p-value $p=0.10$"]
- result: Pearson r, free-free luminosity vs L_X = -0.09 ± 0.37 (p=0.82) dimensionless [5.2: "pearson correlation coefficient $r=-0.09\pm0.37$, p-value $p=0.82$"]
- result: Pearson r, Mdot_i vs Mdot = 0.86 ± 0.17 (p=0.0009) dimensionless [5.3: "pearson correlation coefficient, $r =0.86 \pm 0.17$ and p-value $p=0.0009$"]
- result: Power-law slope of Mdot_i vs Mdot = 0.62 ± 0.21 dimensionless [5.3: "10^{-4.47 \pm 1.53} \left(\frac{\dot M}{\text{M}_\odot \text{yr}^{-1}} \right)^{0.62\pm 0.21}"]
- result: median Mdot_i/Mdot = 0.019 ± not stated dimensionless [5.3: "with a median ratio of 0.019"]
- limitation (authors): Dust masses highly uncertain; radiative transfer needed [5.1: "A full radiative transfer modeling approach is thus required to obtain a better estimate of the inner disk dust masses."]
- limitation (authors): Non-simultaneous accretion and free-free measurements; variability [5.3: "since a correlation is observed despite the accretion rates and the free-free emission having not been estimated at the same time"]
- not stated (card): Which ALMA execution blocks/configurations were used for each project and spectral windows used for continuum; Mask, niter, threshold and cell/image size for tclean; Aperture radius used for total flux photometry; Fit function details for imfit (initial guesses, region); Exact data used to compute the correlations (luminosity definitions for free-free luminosity and frequency); Flux values for Ta…

### 2017A&A...606A..17M: An ALMA survey of submillimetre galaxies in the COSMOS field: Physical properties derived from energy balance spectral energy distribution modelling (2017; high_z_galaxies; multi_facility_alma_minor)
- question: What are the physical properties (stellar, dust and gas masses, SFR, dust temperature, main-sequence offset) of ALMA 1.3 mm-detected, AzTEC 1.1 mm-selected SMGs in COSMOS, and what do they imply for SMG evolution?
- step 3: Fit panchromatic SEDs
  - method: MAGPHYS high-z version energy balance fits; parameters are medians of likelihood distribution with 16-84 percentile range [3.1.2: "We adopted the median of the likelihood distribution as an estimate of each `MAGPHYS`-based parameter"]
  - software: MAGPHYS
  - parameter: q_FIR centred at 2.34 with sigma 0.25; thermal fraction f_T = 0.1; synchrotron nu^-0.8 [3.1.1: "The thermal radio emission is assumed to amount to 10% ($f_{\rm T}=0.1$) of the total flux density at $\nu_{\rm rest}=1.4$ GHz."]
  - assumption: Chabrier (2003) IMF; no AGN contribution to dust heating [1: "A Chabrier (2003) Galactic-disk initial mass function (IMF) is assumed in the calculation of $M_{\star}$ and SFR."]
  - fitting: Bayesian library fitting in MAGPHYS; upper limits entered as zero flux with 3 sigma error [3.1.1: "setting the nominal value to zero, and using the upper limit value (here $3\sigma$) as the flux density error"]
  - validation: chi2 below threshold ~14 for 33 bands; refits without upper limits; AGN contribution to L_IR checked with SED3FIT (mean 1.4%); spec-z vs photo-z [3.1.2: "the mean (median) AGN contribution to $L_{\rm IR}$ was found to be only about 1.4% (0.2%)"]
- result: median stellar mass log(M*/Msun) = 11.09 ± +0.41/-0.53 dex(Msun) [Table 2: "$11.09^{+0.41}_{-0.53}$"]
- result: median T_dust = 39.7 ± +9.7/-7.4 K [abstract: "$T_{\rm dust}=39.7^{+9.7}_{-7.4}$ K"]
- result: median log M_dust = 9.01 ± +0.20/-0.31 dex(Msun) [abstract: "$\log(M_{\rm dust}/{\rm M}_{\ensuremath{\odot}})=9.01^{+0.20}_{-0.31}$"]
- limitation (authors): Gas masses depend on uniform Galactic alpha_CO; may be overestimated by factor >~8 if alpha_CO ~0.8 [3.2: "then the dust-based gas masses can be overestimated by a factor of $\gtrsim8$"]
- limitation (authors): Selection bias at z>~3 toward warmer, brighter sources [3.1.2: "our $z\gtrsim3$ SMGs are likely biased towards warmer objects than at lower redshifts"]
- not stated (card): Flux densities and rms/beam of the 1.3 mm ALMA catalogue are not described (in Aravena et al. in prep.); calibration and imaging details for 2013.1.00118.S not given; CASA version, weighting, cleaning and masking for the Band 7 continuum images of C5, C17, C42 not given; Exact MAGPHYS high-z library version/filter list and handling of redshift uncertainties; How Herschel deblending was done in de…

### 2025ApJ...990...29H: Compact Ionized Gas Region Surrounded by Porous Neutral Gas in a Dusty Lyman Break Galaxy at Redshift z = 8.312 (2025; high_z_galaxies; theory_or_simulation_compared_to_alma)
- question: What are the ionization parameter, gas density and neutral gas (PDR) covering fraction of the ISM in the z=8.312 LBG MACS0416_Y1, derived by fitting CLOUDY multi-phase photoionization models to ALMA line/continuum and HST luminosities?
- step 2: Build CLOUDY model grid
  - method: Spherical HII region + PDR models; L_out=(1-cov)L_HII + cov L_HII+PDR [3.1 Model parameters: "$L_\mathrm{out} = \left(1-cov_\mathrm{PDR}\right)L_\mathrm{\textsc{H\,ii}}+cov_\mathrm{PDR}L_\mathrm{\textsc{H\,ii}+PDR}$"]
  - software: CLOUDY, BPASS
  - parameter: log n_H,c 1.0-4.0 step 0.1; log U -4.0-0.0 step 0.1; cov_PDR 0-1 step 0.01 [Table 1: "$\log U$ | \[-4.0:0.0, 0.1 intervals\]"]
  - assumption: Zgas=Zstar=0.2 Zsun, solar abundances except He, MW grains, HII stop at H+/Htot=0.01, PDR stop at A_V=5 [Table 1: "$Z_\mathrm{gas}=0.2~\mathrm{Z_\odot}(=Z_\mathrm{star})$"]
- step 4: Derive HII region size
  - method: Stromgren radius from CLOUDY where H0/Htot=0.5, D=2 r_s [5.2: "In the CLOUDY code, $r_\mathrm{s}$ is defined as the point where the neutral hydrogen fraction reaches $\mathrm{H^0}/\mathrm{H_\mathrm{tot}}=0.5$."]
  - software: CLOUDY
  - validation: Compared with local compact HII size-density relation (Kim2001) [5.2: "follow the local size–density relation presented in (cite: Kim2001)"]
- result: HII region diameter = 0.90 ± not stated pc [5.2: "Our model estimates $r_\mathrm{s}=0.45~\mathrm{pc}$, corresponding to the H II region size of $D=0.90~\mathrm{pc}$ in diameter."]
- limitation (authors): Only three free parameters due to few observables; single-phase ionized gas cannot reproduce [O II] [4.2: "our modeling assumes a single-phase ionized gas component characterized by a single set of gas density and ionization parameter."]
- not stated (card): ALMA calibration and imaging details (all from earlier papers); Measured [O III], [C II] and continuum fluxes (only luminosities given); Exact rest frequencies and cosmology-to-luminosity conversion details; Exact CLOUDY input scripts and the way PDR-only and HII-only models are combined; Which three luminosity ratios define the chi2 (ratios with [O III]88 as denominator: [C II], UV, IR assumed);…

### 2017A&A...602L..10O: The inhomogeneous submillimeter atmosphere of Betelgeuse (2017; evolved_stars, stellar_physics; observational_alma_primary)
- question: What is the thermal structure of Betelgeuse's extended atmosphere at ~1.3 R_star, and is it spherically symmetric or does it show localized heating?
- step 3: Derive brightness temperatures and spectral index
  - method: Brightness temperature from fitted flux and size (Rayleigh-Jeans); spectral index from integrated flux in lower (331.86 GHz) and upper (344.09 GHz) band images; Eddington-Barbier Tb ~ Tgas [Results: "by separately imaging the lower (at 331.86 GHz) and upper (at 344.09 GHz) portions of the bandpass and calculating the integrated flux density in each image"]
  - software: CASA
  - assumption: Tb ~ Tgas(tau=1) for slowly varying temperature; free-free H- opacity [Discussion: "Eddington-Barbier relations show that for temperatures varying slowly with optical depth $T_\textrm{b}\simeq T_\textrm{gas}(\tau=1)$"]
  - validation: Compared with previous unresolved mm and cm spectral indices [Results: "This is slightly larger than the $\alpha = 1.57 \pm 0.05$ that can be derived from previous unresolved millimeter observations"]
- result: NE-peak total brightness temperature = 3815 ± 165 K [Results: "The total brightness temperature of the NE-peak was $3815\pm165$ K."]
- result: Global spectral index = 1.67 ± 0.09 dimensionless [Results: "We find the global spectral index to be $\alpha = 1.67\,\pm 0.09$"]
- limitation (authors): Limited resolution smears fine structures and reduces contrast; spectral index errors may be underestimated [Discussion: "our limited spatial resolution would smear out these fine structures and would reduce the contrast in the brightness temperatures"]
- not stated (card): Which spw channels were flagged as line-contaminated for the continuum; Image size and cell size; Initial uv-fit starting parameters and the fitting procedure details for UVMULTIFIT; Stellar distance and R_star value used to convert 1.3 R_star; Clean threshold and masks

### 2025A&A...699A..62J: ALMA observation of an evolving magnetized corona in the radio-quiet changing-state active galactic nucleus NGC 1566 (2025; agn_and_quasars, nearby_galaxies; archival_reuse)
- question: What is the origin of the mm continuum emission in the changing-state AGN NGC 1566, and how does it vary with X-ray flux and accretion state?
- step 5: Test origin scenarios and estimate source size and magnetic field
  - method: Order-of-magnitude estimates for SF, jet, outflow shock and self-absorbed synchrotron corona (equipartition) [3.3.4 Synchrotron emission in X-ray cor…: "considering magnetic energy density is in equipartition with the photon energy density"]
  - assumption: outflow velocity taken as escape velocity [3.3.3 Outflow driven shock: "Conservatively assuming the outflow velocity as the escape velocity"]
- result: Self-absorbed source size = 4-7e-5 pc (~100-200 Rg) ± not stated pc [3.3.4 Synchrotron emission in X-ray cor…: "$R_{\rm mm}\sim 4-7 \times 10^{-5}$ pc or $\sim 100-200$ $R_{\rm g}$"]
- result: Equipartition magnetic field = 100-300 ± not stated G [3.3.4 Synchrotron emission in X-ray cor…: "The equipartition magnetic field ($B_{\rm eq}$) is found in the range $\sim 100-300$ G"]
- limitation (authors): Detailed SED modeling is needed to constrain the magnetic field [3.3.4 Synchrotron emission in X-ray cor…: "This suggests a detailed SED modeling is required to constrain the magnetic field in NGC 1566."]
- not stated (card): Line-free/continuum channel selection per epoch; Cell size, image size, masking and cleaning threshold; Fitting method for the flux-flux relation and the intrinsic scatter; Black hole mass used for lambda_Edd and Rg; Exact BAT/XRT fluxes and time-matching to ALMA epochs; Swift/XRT fit details (the model description is inconsistent: BB vs DISKBB); How peak flux and uncertainty were measured (Gauss…

### 2014ApJ...791...95A: η Carinae Baby Homunculus Uncovered by ALMA (2014; stellar_physics, milky_way_ism; observational_alma_primary)
- question: What are the nature and physical parameters of the compact ionized region around eta Carinae, as probed by mm/submm continuum and H and He recombination lines?
- step 2: Fit continuum spectrum with shell model
  - method: Spherical shell radiative transfer with free-free emission in cells; fit Ne and R for given Te and DeltaR/R [3.1 The continuum spectrum: "determined the electron density and radius necessary to fit the observed spectrum"]
  - parameter: Te = 1e4, 1.5e4, 2e4 K; DeltaR/R from 0.05 to 1 [3.1 The continuum spectrum: "for three values of $T_e$: $10^4$, $1.5\times 10^4$ and $2\times 10^4$ K"]
  - assumption: Spherical symmetry; constant density and temperature; H fully ionized, He as He+ (Ni=Ne); distance 2.3 kpc [3.1 The continuum spectrum: "We assumed that H is completely ionized and He is in the form of He$^+$, implying that $N_i = N_e$."]
  - validation: Good fits for all Te and DeltaR/R combinations; Fig. 5 examples [3.1 The continuum spectrum: "Good fits were obtained for all combinations of electron temperature and shell width"]
- step 3: Model recombination line profiles in NLTE
  - method: Solve line+continuum transfer with expansion velocity gradient, Doppler broadening with TD=Te; compare model/observed peak flux ratios [3.2 Recombination line emission: "we assumed $T_D = T_e$ in equation (B6) and introduced an expansion velocity, with a linear gradient across the shell"]
  - parameter: Te 1.4e4-2e4 K; DeltaR/R = 0.05, 0.1, 0.2 [3.2 Recombination line emission: "for values of $T_e$ ranging from $1.4\times 10^4$ K to $2\times 10^4$ K and for three values of $\Delta R/R$: 0.05, 0.1 and 0.2"]
  - assumption: Pressure broadening neglected [Appendix B: "for that reason presure broadening was not included in the calculations"]
  - fitting: Best model chosen where model/observed peak ratios approach unity for all lines [3.2 Recombination line emission: "the ratio becomes close to unity for all lines for $T_e \sim 1.7\times 10^4$ and $\Delta R/R \sim 0.1$"]
  - validation: Compared with LTE models and He lines; poorer fit for H40alpha and H42alpha [3.2 Recombination line emission: "The fitting is not so good for the H40$\alpha$ and H42$\alpha$ lines"]
- result: Shell electron temperature = 1.68e4 ± not stated K [3.2 Recombination line emission: "$T=1.68\times 10^4$ K and a relative shell width $\Delta R/R = 0.1$"]
- result: Shell electron density = 1.25e7 ± not stated cm^-3 [3.2 Recombination line emission: "$N_e = 1.25 \times 10^7$ cm$^{-3}$ and $R= 2.2 \times 10^{-3}$ pc"]
- result: Shell radius = 2.2e-3 ± not stated pc [3.2 Recombination line emission: "$N_e = 1.25 \times 10^7$ cm$^{-3}$ and $R= 2.2 \times 10^{-3}$ pc"]
- result: Bulk velocity of shell (LSR) = -52 ± not stated km/s [3.2 Recombination line emission: "In all cases the bulk velocity of the model is $-52$ km s$^{-1}$."]
- result: Expansion velocity inner/outer shell = 60 / 20 ± not stated km/s [3.2 Recombination line emission: "expansion velocity of 60 km s$^{-1}$ in the internal part of the shell and of 20 km s$^{-1}$ in the external part"]
- limitation (authors): Departure from spherical symmetry would make the solution degenerate; finer resolution needed [3.2 Recombination line emission: "the velocity distribution necessary to fit the line profiles will depend on the density and temperature distributions and the solution will be degenerate."]
- limitation (authors): Wind parameters during eruption cannot be strictly constrained [3.4 Dynamical evolution: "we cannot strictly constrain the wind parameters during the eruption"]
- not stated (card): CASA version and calibration procedure; weighting/robust, deconvolver, masks, iterations, thresholds; line-free channel ranges; flux scale accuracy/Titan model; fitting procedure and goodness-of-fit criterion for the shell model; code for radiative transfer model; quantitative uncertainties on model parameters

### 2018ApJ...864L..17G: A High Cluster Formation Efficiency in the Sagittarius B2 Complex (2018; milky_way_ism, star_formation; archival_reuse)
- question: What fraction of stars in Sgr B2 form in bound clusters (the CFE), and is it consistent with environmentally dependent CFE models?
- step 1: Census of stellar population
  - method: Combine VLA and ALMA catalogs of H II regions and cores, extrapolate to total stellar mass with Kroupa IMF [Census of the Stellar Population: "each H II region implies the presence of a total of 326 $\mathrm{M}_{\odot}$ of stars, while each 8-20 $\mathrm{M}_{\odot}$ core represents 135 $\mathrm{M}_{\odot}$"]
  - assumption: Upper stellar mass limit of 200 Msun; each VLA source is an H II region with a star of at least 20 Msun [Census of the Stellar Population: "assuming an upper stellar mass limit of 200 $\mathrm{M}_{\odot}$"]
- step 2: Measure H II region velocities and velocity dispersion
  - method: Fit H41alpha lines, take standard deviation of V_LSR and compare with escape speed [Velocity Dispersion Measurements - boun…: "We measure the 1D velocity dispersion in Sgr B2 M by taking the standard deviation of the measured V$_{\rm LSR}$ values."]
  - software: pyspeckit
  - assumption: H II regions trace stellar motions [Velocity Dispersion Measurements - boun…: "they closely follow the motions of their stars and serve as probes of the underlying stellar kinematics."]
  - validation: Compared with De Pree et al. 2011 velocities (agree within 5 km/s except F10.37) [Velocity Dispersion Measurements - boun…: "Our measurements agree to within 5 km s$^{-1}$ with those of (cite: De-Pree2011a) for all sources we both measured except F10.37"]
- result: 1D velocity dispersion of Sgr B2 M, full data set = 12 ± not stated km/s [Velocity Dispersion Measurements - boun…: "Using the full data set, we obtain a higher $\sigma_{\rm 1D}\approx12~\textrm{km~s}\ensuremath{^{-1}}$."]
- limitation (authors): Completeness of the core catalog is hard to evaluate and depends on the models used [Effects of completeness: "For the less massive ‘cores’, the completeness is much more difficult to evaluate"]
- not stated (card): ALMA calibration and imaging details (all deferred to Ginsburg et al. 2018); H41alpha line fitting setup (line model, initial guesses, baseline handling); Distance to Sgr B2; Exact Monte Carlo setup for the model prediction

### 2020A&A...640A..27V: Protoplanetary disk masses in NGC 2024: Evidence for two populations (2020; protoplanetary_disks, star_formation; observational_alma_primary)
- question: How does external photoevaporation and environment affect the dust masses of disks across the young NGC 2024 cluster, compared with other star-forming regions?
- step 3: Convert flux to dust mass and derive mass distribution
  - method: Optically thin relation M = d^2 F/(kappa B(T)); Kaplan-Meier estimator including nondetections [3.2 Dust masses of NGC 2024 disks: "the Kaplan-Meier estimator is used to infer the disk mass distribution for the full sample, including nondetections."]
  - parameter: d = 414 pc, T = 20 K, kappa(1000 GHz) = 10 cm2/g, beta = 1 [3.2 Dust masses of NGC 2024 disks: "$\kappa_{1000\,\text{GHz}} = 10$ cm$^{2}$ g$^{-1}$ (cite: beckwith90)"]
  - assumption: Optically thin emission, no free-free contamination, 20 K midplane (40 K tested) [3.2.2 Impact of midplane temperature va…: "The size of this effect is shown in Fig. [2](#fig:mdisk_v1) for a 40 K effective midplane temperature"]
  - validation: Free-free contribution estimated negligible using spectral indices 2.3 and -0.1 [3.2.1 Impact of free-free emission: "assuming spectral indices of $2.3$ for the dust and $-0.1$ for the free-free emission"]
- limitation (authors): Stellar mass differences and binarity cannot be accounted for in the comparison [4.2 Comparison to other star-forming re…: "we cannot take into account possible differences in stellar masses, even though these may be significant"]
- limitation (authors): Kaplan-Meier assumption of nondetection independence not met at low masses [3.2 Dust masses of NGC 2024 disks: "The third requirement is not met"]
- not stated (card): tclean cell size, image size, deconvolver, threshold and masks; Line-free channels flagged; Self-calibration solution intervals and reference antenna; Details of aperture photometry (aperture size, background); Which Kaplan-Meier implementation was used; How spectral indices of IRS 2 and IRC 101 were computed; CASA calibration pipeline version and manual vs pipeline calibration

### 2023NatAs...7...80U: Simultaneous radio and optical polarimetry of GRB 191221B afterglow (2023; transients; observational_alma_primary)
- question: Is the radio (97.5 GHz) polarization of the GRB 191221B afterglow depolarized relative to the optical, and what does this say about magnetic field configuration and cool electrons / jet energy?
- step 3: Model afterglow light curves and SED
  - method: Numerical forward-shock synchrotron model with Blandford-McKee solution, equal arrival time surface, fixed theta_j; adjust parameters to fit radio-optical-X-ray data [Methods: "We performed numerical calculations of flux from the shock with a fixed $\theta_j$ which evolves as the Blandford-McKee (BM) self-similar solution"]
  - assumption: Uniform density medium, energy injection E_iso propto t^0.25 [Methods: "the ambient density is uniform and the energy continues to be injected to the shock by long activity of the central engine"]
  - validation: Model also explains X-ray and optical [Introduction: "The model also explains the X-ray and optical afterglows"]
- result: 97.5 GHz light curve break time = 3.77 ± 0.35 days [Introduction: "a break-time at $3.77\pm 0.35$ days"]
- result: Pre-break index alpha = 0.26 ± 0.02 dimensionless [Introduction: "$\alpha = 0.26\pm 0.02$ (before the break)"]
- result: Post-break index alpha = -1.62 ± 0.13 dimensionless [Introduction: "$\alpha = -1.62\pm 0.13$ (after the break)"]
- limitation (authors): PA difference between radio and optical only ~90% significant [Methods: "the PA between radio and optical is different at $\sim$90% confidence level."]
- not stated (card): tclean parameters: weighting/robust, cell size, image size, masks; Self-calibration solution intervals; Beam sizes and image rms values; Fitting method/priors for the afterglow model and light curve broken power law; Numerical afterglow polarization code is not public; ALMA configurations and on-source times; Source coordinates

### 2020A&A...634A...9M: The flickering nuclear activity of Fornax A (2020; agn_and_quasars, nearby_galaxies; multi_facility_alma_minor)
- question: What are the timescale and duty cycle of the nuclear activity of Fornax A, from the radio spectrum of its lobes, jets and core?
- step 3: Fit synchrotron spectra with CI and CI_OFF models
  - method: Fit continuous injection and injection-plus-turn-off models to lobe, core and jet spectra, choosing by reduced chi-squared [5 Spectral analysis: "To determine the best-fit models, we use the software package `SYNAGE++` (cite: murgia1999)"]
  - software: SYNAGE++
  - parameter: B = 2.6 uG for lobes [5.1 Spectral modelling of the lobes: "Assuming that the magnetic field of the lobes is $2.6\pm 0.3\mu$G (cite: isobe2006; tashiro2009)"]
  - assumption: Jaffe & Perola isotropic electron distribution; no escape of particles (T_conf = infinity) [5 Spectral analysis: "We assume that the distribution of electrons stays isotropic during its losses, which is known as the Jaffe &Perola approximation (cite: jaffe1973)."]
  - fitting: reduced chi-squared comparison of CI vs CI_OFF [5.1 Spectral modelling of the lobes: "We use the reduced-chi-squared to determine which model is best fits the spectrum."]
- result: East lobe CI_OFF injection index = 0.57 ± +0.02/-0.10 dimensionless [5.1: "the injection spectral index of the particles in the East lobe is $\alpha_{\rm inj}= 0.57^{+0.02}_{-0.10}$"]
- limitation (authors): Core result holds only if thermal contamination of 108 GHz flux is below ~80%, which is poorly constrained [5.2: "This result holds as long as the thermal contamination to the 108 GHz flux of the kpc-core, poorly constrained by currently available data, is $\lesssim 80\%$."]
- not stated (card): ALMA image size and cell size; number of clean iterations and threshold; CASA version used for tclean; how the 108 GHz continuum flux scale uncertainty was set; how the kpc-core thermal contamination at 108 GHz was handled in detail; SYNAGE++ fitting details (grid, priors, error estimation); regions used for flux extraction (coordinates); whether the fourth spectral window frequency is given (tex…

### 2021A&A...646A.127H: Multiwavelength dissection of a massive heavily dust-obscured galaxy and its blue companion at z∼2 (2021; high_z_galaxies; observational_alma_primary)
- question: Is the ultra-massive dusty galaxy Astarte quenching or has it always been on the main sequence, using SED modelling and its ALMA CO(3-2) gas mass?
- step 5: SED fitting for SFR, M*, Ldust
  - method: CIGALE with BC03, Ciesla17 SFH, Draine&Li 2014 dust, synchrotron, three attenuation laws (C00, CF00, LF17); model choice by BIC [3.2.1 The SED modeling: "We use the SED modeling code CIGALE (cite: Boquien19) to derive the physical properties of our sources."]
  - software: CIGALE
  - assumption: Chabrier IMF, solar-like metallicity (Z=0.02) [Table 3: "Metallicity"]
  - fitting: CIGALE grid with Bayesian analysis; model comparison by BIC [3.2.3 Attenuation laws: "we employ the Bayesian information criterion (BIC), defined as the $\chi^2 + k\ln{n}$"]
  - validation: chi2, reduced chi2 and BIC compared among laws; stellar-only vs IR-only fits [Table 3: "Comparison between the quality of fits of Astarte and Adonis produced with CIGALE with the three attenuation laws."]
- result: Astarte SFR = 395 ± 20 Msun/yr [Table 4: "$395\pm20$"]
- result: Astarte stellar mass = 3.74e11 ± 0.19e11 Msun [Table 4: "$(3.74\pm0.19)\times10^{11}$"]
- result: Astarte depletion time = 0.22 ± 0.07 Gyr [4 Discussion: "a rather small depletion time of $0.22\pm0.07$ Gyrs"]
- limitation (authors): Cannot exclude a faint diffuse larger-scale CO component given data depth [3.1.2 Line integrated flux and luminosi…: "we cannot formally exclude another faint and diffuse component at larger scale considering the depth of our data"]
- not stated (card): Which spectral window and channels used for the line and for the continuum map; Disk radius R used for the dynamical mass (CO size ~74 kpc seems inconsistent); CIGALE version and exact module set/priors; Channel range summed for the moment-0 map; Self-calibration and flux calibrator not stated

### 2015ApJ...813...45L: Radio Jet Feedback and Star Formation in Heavily Obscured, Hyperluminous Quasars at Redshifts ∼ 0.5-3. I. ALMA Observations (2015; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: How much cool dust emission / star formation accompanies highly obscured, radio-powerful WISE-selected quasars at z~0.5-3, as measured with ALMA 870 um snapshot photometry?
- step 2: Derive ISM masses
  - method: Scoville et al. 2014 relation scaling 870 um flux, assuming all flux is thermal dust [5.1 Interstellar Medium Mass: "We derive the ISM masses assuming that 100% of the 345 GHz flux is thermal dust emission."]
  - parameter: dust temperatures 30 K and 90 K [5.1 Interstellar Medium Mass: "We derive ISM masses (Table [5](#tbl-mass), columns 13 & 14), for dust temperatures of 30 K and 90 K"]
  - assumption: uncertainty factor of 5; synchrotron contamination not corrected [5.1 Interstellar Medium Mass: "We estimate the overall uncertainty to be a factor of 5"]
  - validation: compared with Scoville COSMOS IR-bright median [5.1 Interstellar Medium Mass: "Their “IR Bright” sample has a median ISM mass of 11.91$\pm$0.77 ${\times} 10^{10} M_{\odot}$, about twice that of our sample."]
- result: Median ISM mass (30 K) of detected sources = 5.9e10 ± factor of 5 Msun [5.1 Interstellar Medium Mass: "with a median for the 26 ALMA-detected sources of 5.9 ${\times}10^{10} M_{\odot}$"]
- limitation (authors): Dust temperature unconstrained for most sources; L_BB and SFR uncertain by orders of magnitude [5.2 Spectral Energy Distribution Fits: "is uncertain by 2-3 dex without measurements at the FIR peak of the dust SED."]
- not stated (card): CASA version and calibration/imaging procedure (pipeline vs manual, weighting, cleaning); Region used for imfit and how upper limits were set (3 sigma assumed?); Rest-frame Gamma_RJ/Gamma_0 values and temperature-scaled constant for 30 K and 90 K ISM masses; Fitting code and parameter priors for the AGN+BB+stellar fits; photometry weighting; Redshift-tied details of k-correction templates

### 2019ApJ...881...33H: Constraining the Radio Emission of TRAPPIST-1 (2019; exoplanets, stellar_physics; observational_alma_primary)
- question: Does TRAPPIST-1 emit gyrosynchrotron radio emission at 44 and 97.5 GHz, and what do upper limits imply for magnetic properties and energetic proton flux at its planets?
- step 4: Constrain emitting region size and proton flux
  - method: Gyrosynchrotron equations: region size x, electron density N, scaled to outgoing proton flux at TRAPPIST-1e [Discussion: "Following the gyrosynchrotron equations arranged by (cite: white) for an assumed electron energy index $\delta=2$, the number density of trapped electrons is given by"]
  - parameter: B = 600 G, delta = 2, d = 12.45 pc, nu = 97.5 GHz, S = 10.6 uJy [Discussion: "the $3 \sigma$ flux $S = 10.6 ~\upmu \textrm{Jy}$, size of emitting region $R = 0.02 ~R_J$, magnetic field $B=600~ G$"]
  - assumption: Electron-to-proton ratio ~10^3 as in solar flares; flux scaled by R/r^2 with pi sr [Discussion: "we scale the outgoing rate by $\frac{R}{r^2}$, where R is the size of the emitting region and r is the semi-major axis"]
- result: Emitting region size upper limit = <= 0.02 ± not stated R_J [Discussion: "the emitting region is constrained by our ALMA upper limits to $\leq 0.02~ R_J$"]
- result: Trapped electron density upper limit = <= 5e8 ± not stated cm^-3 [Discussion: "The resulting number density of electrons is $N \leq 5 \times 10^8~ cm^{-3}$."]
- result: Proton flux at TRAPPIST-1e = 1e5 ± not stated pfu [Discussion: "We find a particle flux incident on the closest habitable planet, TRAPPIST-1e (0.02 au), to be $10^5 pfu$."]
- limitation (authors): Short observations may miss flares; emission mechanism cannot be inferred from non-detections [Discussion: "While we cannot infer an emission mechanism from only non-detections"]
- not stated (card): tclean parameters (weighting, robust, cell, image size, deconvolver, threshold); How the 3-sigma limit was derived (3 x RMS at target position assumed); Whether ALMA archive/pipeline products were used as delivered; flux calibrator flux density and scale uncertainty; Exact brightness temperature calculation and electron energy distribution details for Dulk equations; Details of per-scan imaging a…

### 2026ApJ..1004..126K: An Active Galactic Nucleus in the Antennae Galaxies? (2026; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: Does the Antennae merger host an AGN, as revealed by 100 GHz time variability of compact sources S3 and S4 in NGC 4039?
- step 6: Assess emission origin
  - method: compare luminosity, brightness temperature, spectral slope with dust, free-free, SNR, microquasar, AGN mm-X-ray relation [4.2: "We finally assess whether S3 and S4 are consistent with an AGN."]
  - assumption: dust kappa 0.37 m2/kg at 250um, beta=2, T=30 K; Galactic CO-to-H2 2e20 [4.2: "dust emissivity index of 2, and a dust temperature of 30 K"]
- result: S4 100 GHz luminosity = 9.1e36 ± not stated erg/s [4.2: "$8.8\times 10^{36}\ \mathrm{erg\ s^{-1}}$ and $9.1\times 10^{36}\ \mathrm{erg\ s^{-1}}$ for S3 and S4"]
- result: S4 brightness temperature lower limit (size<0.01 pc) = 1.3e6 ± not stated K [4.2: "we obtain a lower limit for the brightness temperature of $1.3\times 10^6\ \mathrm{K}$"]
- limitation (authors): Spectral shape uncertain with narrow frequency range and large errors [Conclusion: "the large flux uncertainties do not allow for any robust conclusions regarding the SED"]
- not stated (card): Line-free channel/line mask definitions; tclean niter, image size, scales; Power-spectrum/Fourier algorithm and normalization details; Photometry code used; CO imaging parameters (Saito et al., in prep); Self-calibration not mentioned

### 2020ApJ...891...80M: Properties of M Dwarf Flares at Millimeter Wavelengths (2020; stellar_physics, star_formation; archival_reuse)
- question: What are the properties and likely emission mechanism of millimeter flares from M dwarfs (AU Mic and Proxima Cen) detected by ALMA?
- step 5: Emission mechanism constraints
  - method: Faraday rotation limits on density and B; gyrosynchrotron/synchrotron formulae of Dulk 1985 for electron index; non-thermal energy contours [4.3.1: "Using the formulae for homogeneous sources (cite: Dulk:1985), the derived particle distribution indices for these M dwarfs are consistent with a hard distribution of electrons"]
  - assumption: Peak frequency 50 GHz for energy contours [4.3.1: "The peak frequency of the emission was assumed to be 50 GHz"]
- result: Electron distribution index delta (A1, gyrosynchrotron) = 2.80 ± 0.06 dimensionless [4.3.1: "$\delta_\text{A1}=2.80\pm0.06$ and $\delta_\text{P4}=3.3\pm0.5$"]
- not stated (card): Proxima Cen project code and data reduction details; Clean parameters (image size, cell size, niter, threshold); Initial point-source parameters and fit settings for uvmodelfit; Flare-peak time definition and how Gaussian fits were done for t1/2; Flare luminosity/spectral index error propagation; Details of the non-linear least squares polarization fit; How the delta from spectral index is conver…

### 2018ApJ...855L...2M: Detection of a Millimeter Flare from Proxima Centauri (2018; stellar_physics, debris_disks, exoplanets; archival_reuse)
- question: Does the 1.3 mm emission from Proxima Cen require dust belts, or is it explained by stellar flaring and coronal emission?
- step 4: Infer electron power-law index
  - method: Optically thin gyrosynchrotron relation alpha = 1.22 - 0.9 delta [4.1 Nature of the Detected Stellar Flare: "$\alpha = 1.22 - 0.9\delta$ (cite: Dulk:1985; Osten:2016)"]
  - assumption: Optically thin gyrosynchrotron emission [4.1 Nature of the Detected Stellar Flare: "This spectral index may indicate that we are seeing the optically thin part of the gyrosynchrotron spectrum"]
- result: Electron power-law index delta = 3.32 ± 0.83 dimensionless [4.1 Nature of the Detected Stellar Flare: "we can determine $\delta=3.32\pm0.83$"]
- not stated (card): CASA version; clean cell size, image size, niter, and threshold; uvmodelfit starting parameters; how the spectral index and uncertainties were derived; how flux density in the 2 s and 5 s bins was extracted; how the number of background sources was computed from the counts

### 2015ApJ...802...69B: Radio and Millimeter Monitoring of Sgr A*: Spectrum, Variability, and Constraints on the G2 Encounter (2015; milky_way_ism, agn_and_quasars; observational_alma_primary)
- question: Did the G2 encounter change the radio-to-millimeter flux density or spectrum of Sgr A*, and what is the millimeter spectral index?
- step 3: Constrain bow shock area from 1 GHz excess
  - method: Extrapolate excess at 1.5, 3.1, 5.4 GHz to 1 GHz and compare with model predictions [4.1 Presence of a Bow Shock: "We extrapolate the flux density excess at 1.5, 3.1, and 5.4 GHz to 1 GHz, assuming a power-law spectrum with index $\alpha=-0.7$"]
  - assumption: optically thin synchrotron index -0.7 [4.1 Presence of a Bow Shock: "assuming a power-law spectrum with index $\alpha=-0.7$, appropriate for optically thin synchrotron emission."]
- result: Upper limit on G2 cross-sectional area (95%) = 2e29 ± not stated cm^2 [4.1 Presence of a Bow Shock: "we can set an upper limit to the size of G2 of $\sim 2\times 10^{29} {\rm\, cm^2}$"]
- limitation (authors): ALMA lacked Tsys measurements on Sgr A* itself, requiring a correction [2.2 ALMA Observations: "ALMA observations did not include system temperature measurements on Sgr A\* itself."]
- not stated (card): CASA version used for ALMA and VLA; ALMA flux models for Titan/Neptune and calibrator flux values adopted; Details of the fitted system-temperature opacity correction; The authors' custom code for VLA visibility subtraction and ALMA point-source fitting; Which spectral windows/channels were averaged for ALMA fluxes; Coordinates and distance of Sgr A*

### 2026ApJ..1003L..17Y: Evidence for Multiple Orbiting Hotspots in the 340 GHz Variability of Sgr A* (2026; milky_way_ism, agn_and_quasars; archival_reuse)
- question: Does the 340 GHz light curve of Sgr A* show periodic variability from orbiting hotspots, and can multiple decaying hotspots explain it?
- step 5: Estimate synchrotron cooling timescale
  - method: t_syn = 6π m_e/(σ_T B² γ) with γ from nu_syn = 337.5 GHz [Discussion: "Assuming $\nu_{\mathrm{syn}} = 337.5\,\mathrm{GHz}$ and $\sin\theta = 1$"]
  - assumption: B = 44 G, sinθ = 1 [Discussion: "adopting a magnetic field strength of $B = 44\,\mathrm{G}$"]
- result: t_syn = ~150 ± not stated min [Discussion: "we obtain a synchrotron cooling timescale of $t_{\mathrm{syn}} \sim 150\,\mathrm{min}$"]
- limitation (authors): Fit decay timescales are approximate because of limited light-curve duration [Multiple Hotspot Model: "these values should be regarded as approximate constraints"]
- not stated (card): Self-calibration solution intervals and number of iterations; Imaging parameters (weighting, cell, image size) and how the flux density is measured per time bin; Which SpWs and which of the 11 epochs belong to which project; MCMC sampler, priors and chain settings; GPR implementation and noise amplitude hyperparameters; Source of the spectral index variation (alpha decreases by ~0.4); method not …

### 2024ESC.....8..665M: Detection and Chemical Modeling of Complex Prebiotic Molecule Cyanamide in the Hot Molecular Core G31.41 + 0.31 (2024; astrochemistry, star_formation; archival_reuse)
- question: Is cyanamide (NH2CN) present in the hot molecular core G31.41+0.31, what are its column density and abundance, and how is it formed (grain-surface NH2 + CN)?
- step 2: measure continuum
  - method: Two 2D Gaussian fits with imfit to the hot core and UC HII region [3.1 Continuum emission towards the G31.…: "We fit the two individual 2D Gaussian using the CASA task `IMFIT` over the hot core and UC HII region to estimate the physical properties."]
  - software: CASA imfit
- result: Main hot core integrated continuum flux (99.9 GHz) = 249.3 ± 7.9 mJy [3.1 Continuum emission towards the G31.…: "174.4$\pm$3.6 mJy beam$^{-1}$ and 249.3$\pm$7.9 mJy with RMS of 3.36 mJy"]
- limitation (authors): Coarse resolution; morphology cannot be determined [3.3 Spatial distribution: "Therefore, understanding the morphology of NH$_{2}$CN from the spatial distribution maps towards G31.41+0.31 is not possible."]
- not stated (card): Line-free channels for continuum and uvcontsub; tclean robust, cell size, image size, masking, threshold; Self-calibration solints and number of iterations; Spectral window frequency/channel details and rest frequency for velocity; UCLCHEM version, warm-up timescale and exponent n, initial abundances, dust/grain parameters; Whether the 250±25 K or 250±35 K uncertainty is correct (text is inconsis…

### 2017ApJ...849...90S: Evolution of Molecular Clouds in the Superwind Galaxy NGC 1808 Probed by ALMA Observations (2017; nearby_galaxies; observational_alma_primary)
- question: What are the distribution, kinematics, star formation properties and evolution of molecular clouds, and the molecular outflow, in the central 1 kpc starburst of NGC 1808?
- step 2: Spectral index and SED decomposition
  - method: Least-squares fit of synchrotron + free-free + dust power laws to 21-350 GHz core flux [3.1.2 Spectral energy distribution of t…: "Also shown is a least-squares fit that includes contributions from three different types of emission: synchrotron (non-thermal), free-free, and dust (thermal)."]
  - assumption: Fixed indices alpha_s=-0.9, alpha_ff=-0.1, alpha_d=3.8 [3.1.2 Spectral energy distribution of t…: "we fixed the spectral indices as $\alpha_\mathrm{s}=-0.9$ (synchrotron)"]
  - fitting: Least-squares, amplitudes free [3.1.2 Spectral energy distribution of t…: "where $K$ is the proportionality factor to be determined"]
  - validation: Fit stated to be not unique [3.1.2 Spectral energy distribution of t…: "The fitting result is not unique"]
- step 4: Masses, SFR and SFE in regions
  - method: ISM mass from 350 GHz continuum; molecular mass from CO(1-0); SFR from 93 GHz free-free [4.2 Star formation rate and efficiency …: "The star formation rate (SFR)[^3] in the CND and regions R1-R5 can be estimated from the band 3 continuum assuming that the SED is dominated by free-free emission at 93 GHz."]
  - assumption: Td = 20 and 100 K; X_CO = 0.8e20; Te = 5000 K; d = 10.8 Mpc [4.1 ISM mass from 350 GHz dust continuum: "we calculated the ISM mass for dust temperatures of 20 and 100 K."]
  - validation: Compared ISM and molecular masses, agree within factor of few [4.1 ISM mass from 350 GHz dust continuum: "The two measurements agree within the uncertainty of $T_\mathrm{d}$ and $X_\mathrm{CO}$ (a factor of few)"]
- result: Free-free fraction at 93 GHz (S_s:S_ff:S_d) = 0.22:0.72:0.06 ± not stated dimensionless [3.1.2 Spectral energy distribution of t…: "$S_\mathrm{s}:S_\mathrm{ff}:S_\mathrm{d}=0.22:0.72:0.06$"]
- result: Q_Lyc central region = 4.4e53 ± not stated s^-1 [3.1.2 Spectral energy distribution of t…: "we find $Q_\mathrm{Lyc}=4.4\times10^{53}~\mathrm{s}^{-1}$"]
- result: Total SFR r<15'' = ~4.5 ± not stated Msun/yr [4.2 Star formation rate and efficiency …: "$\mathrm{SFR}(r<15\ensuremath{''})\sim4.5~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$"]
- result: Total molecular gas mass in central starburst = 9.7e8 ± not stated Msun [4.2 Star formation rate and efficiency …: "$M_\mathrm{mol}=9.7\times10^8~M_\ensuremath{\odot}$"]
- limitation (authors): X_CO analysis beyond scope; masses uncertain by factor of few [6.2 GMC evolution: inflow, star formati…: "the analysis of the conversion factor $X_\mathrm{CO}$ is beyond the scope of this paper"]
- not stated (card): CASA version and ALMA pipeline version for ALMA data; Line-free channels and continuum subtraction method for CO cubes; Image size, cell size, and clean thresholds/masks; feather scaling and cube channel definitions; Moment clipping thresholds other than the 5 sigma total flux; Equation (3) of Sco15 constants applied; Aperture definitions for region fluxes; CLUMPFIND contour levels and step

### 2021A&A...653A.117B: ORion Alma New GEneration Survey (ORANGES). I. Dust continuum and free-free emission of OMC-2/3 filament protostars (2021; star_formation; observational_alma_primary)
- question: Are the small-scale dust properties and evolutionary status of solar-type protostars in the OMC-2/3 filament affected by nearby HII regions and UV illumination?
- step 2: Derive beta and T_SED, tau, N_H2, mass, free-free fraction
  - method: SED method: F=B(Td)(1-exp(-tau))Omega with beta from flux ratios for Td 10-200 K; free-free identified when beta_333-246.2 exceeds beta with 32.9 GHz [6.2 Step 1: "we derived the indexes for $T_{\text{SED}}$ ranging from 10 to 200 K, with steps of 10 K between 10 and 100 K and steps of 20 K between 100 and 200 K"]
  - parameter: beta constrained to 0-2 to bound T_SED [6.3 T_SED: "we took into account that $\beta$ should range between 0 and 2"]
  - assumption: mu=2.8, dust-to-gas R=0.01, kappa0=0.9 cm2/g at 230 GHz, d=393 pc, no free-free at 246.2/333 GHz [6.2 Method: "R=0.01 is the mass dust-to-gas ratio"]
  - fitting: analytic inversion over temperature grid; error propagation [11.2 Derivation of uncertainties: "we use error propagation."]
  - validation: Model SEDs overplotted on measured fluxes as self-consistency check [6.2 Step 7: "as a self-consistency check, we added the latter on the dust SED plots."]
- result: Free-free emission sources = 5 of 16 (~31%) ± not stated sources [7.2 Free-free emission: "We clearly found evidence of free-free emission at 32.9 GHz towards 5 out of 16 sources"]
- result: Sources with beta<1 = 9/16 ± not stated sources [6.4: "The majority of the sources (9/16) have a dust emissivity spectral index $< 1$."]
- result: Free-free fraction at 32.9 GHz = 47-100% in free-free sources; <=24% otherwise ± not stated % [6.6: "the derived free-free emission ranges between 47% and 100%"]
- result: Envelope+disk mass range = 2e-4 to 0.1 ± not stated Msun [6.5: "the derived (envelope + disk) masses range between $2\times10^{-4}$ M$_\odot$ and 0.1 M$_\odot$"]
- limitation (authors): Low statistics and poorly constrained temperatures hamper strong conclusions [7.4 Environment influence: "the low statistics and relatively large errors in the parameters of the sources where the dust temperature is not well constrained hamper very strong conclusions"]
- not stated (card): Solution intervals and number of channels per source for self-calibration; Line-free channel selection for continuum; CLEAN mask, threshold, cell and image size; CASA version; Exact fit starting parameters and which sources use point vs Gaussian in uv_fit; Weighting scheme for averaging beta and N_H2 across frequencies; Arbitrary sizes chosen for FIR1a-a and CSO33-b beyond Table values

### 2018ApJ...853..171G: Distributed Star Formation throughout the Galactic Center Cloud Sgr B2 (2018; star_formation, milky_way_ism; observational_alma_primary)
- question: Is there extended, distributed star formation across the Sgr B2 cloud beyond the N, M, S protoclusters, and how do star formation thresholds and surface density relations compare with local clouds?
- step 3: Cross-match and classify sources
  - method: Positional matching within 0.5-1" to VLA HII, MMB, H2O maser, Chandra, Spitzer catalogs; test alternative nature hypotheses (prestellar cores, EGGs, HII regions, YSOs) [3.2: "We cross-matched our source catalog with catalogs of NH$_3$ sources, H II regions, X-ray sources, Spitzer sources, and methanol and water masers."]
  - assumption: beta=1.75, kappa(3.1mm)=0.0018 cm2/g per gram gas (Ossenkopf1994a), gas-to-dust 100, d=8.4 kpc [3.3.1: "assuming a dust opacity index $\beta=1.75$ (spectral index $\alpha=3.75$ if measured on the Rayleigh-Jeans tail of the spectral energy distribution)"]
  - validation: comparison with Robitaille/Zhang models, HOPS Orion sources, and MUSTANG Orion data [3.3.5: "We compare our detected sample to that of the Herschel Orion Protostar Survey (cite: Furlan2016a)"]
- step 4: Infer stellar mass and SFR
  - method: Assign 12 Msun to cores and 45 Msun to HII regions (Kroupa IMF), extrapolate with mass fractions 0.09 and 0.14, divide by age 0.74 Myr [4.1: "we assume each source not associated with an H II region contains or will form a star with mass equal to the average over the range 8-20 $M_{\odot}$ assuming a (cite: Kroupa2001a) initial mass function"]
  - assumption: age t=0.74 Myr from Kruijssen2015a [4.1: "We divide the inferred stellar mass by this age"]
  - validation: compared with Schmiedeke2016a mass estimates [4.1: "We compare our mass estimates to those of (cite: Schmiedeke2016a)"]
- result: Sources with HII region counterparts = 31 ± not stated sources [3.2 H II regions: "31 of our sources are classified as H II regions"]
- result: Total inferred stellar mass = 26000 (max 46000) ± not stated Msun [Table clustermassestimates: "| Total | 240 | 57 | 5500 | 26000 | 19000 | 33000 | 1993 | 33400 | 0.035 |"]
- result: Total SFR (max) = 0.062 ± not stated Msun/yr [4.1.1: "Our estimated total inferred SFR of the Sgr B2 cloud is 0.062$M_{\odot}$$\textrm{yr}^{-1}$"]
- limitation (authors): Catalog potentially incomplete; completeness cannot be quantified [3.1: "Our selection criteria result in a reliable but potentially incomplete catalog"]
- limitation (authors): Column density maps not very accurate; SFR strongly dependent on assumed timescale [4.1.1: "our estimate of the star formation rate remains strongly dependent on the assumed star formation timescale"]
- not stated (card): tclean image size, cell size, multiscale scales and primary-beam mask details; self-calibration solution intervals and per-iteration imaging parameters (only in script); exact by-eye source selection and per-source peak/photometry procedure; Herschel SED-fitting details (Battersby et al. in prep) and dust opacity for column density maps; uvcombine/feather weighting parameters; cluster radius defi…

### 2017A&A...602A..19L: A concordant scenario to explain FU Orionis from deep centimeter and millimeter interferometric observations (2017; protoplanetary_disks, star_formation; multi_facility_alma_minor)
- question: What are the properties (size, spectral indices, dust and gas mass) of the disks around FU Ori and FU Ori S, constrained with ~25 au resolution centimeter and millimeter observations?
- step 4: Three-component SED model (free-free + thick dust + thin dust)
  - method: Co-add free-free and two modified black body components; parameters set by hand to match fluxes and X-band limit [4.1 Fiducial SED model: "the overall fluxes for each of FU Ori and FU Ori S at all frequencies were evaluated by simply co-adding the fluxes of a free-free emission component, an optically thicker dust thermal emission component, and an optically thinner dust component."]
  - parameter: β=1.75 fixed; Te=16000 K [4.1 Fiducial SED model: "We fix the dust opacity index to $\beta$=1.75"]
  - assumption: gas-to-dust 100, d=353 pc; parameters degenerate [4.1 Fiducial SED model: "the parameters $\kappa_{\mbox{\tiny{230 GHz}}}$$\Sigma$, $T$, and $\Omega$ are degenerated."]
  - fitting: not a formal fit [4.1 Fiducial SED model: "Our present models do not uniquely explain the measured fluxes, but serve as simplified cases"]
  - validation: Compared with fluxes and X-band limits [Discussion, Fiducial SED model: "can result in $\alpha$$<$2.0 at 29-37 GHz and a rapidly dropping overall flux toward lower frequency such that it cannot be detected by sensitive JVLA X band observations at 8-10 GHz."]
- limitation (authors): SED models are degenerate and non-unique [4.1 Fiducial SED model: "Our present models do not uniquely explain the measured fluxes, but serve as simplified cases for qualitatively comprehending the observational results."]
- not stated (card): ALMA data processing and calibration used for the 346 GHz flux (taken from Hales et al. 2015); Clean threshold, masking and niter for JVLA imaging; SED model fitting procedure: how parameters of Table were chosen (apparently by hand); Uncertainties on SED model parameters; Details of the 224 GHz SMA observations (in Liu et al. 2016a)

### 2019ApJ...881L...2B: ALMA Observations of the Terahertz Spectrum of Sagittarius A* (2019; agn_and_quasars, milky_way_ism; observational_alma_primary)
- question: What is the submm/THz spectrum of Sgr A* and what do the flat spectrum and one-zone thermal synchrotron model imply for the emitting plasma and its optical depth?
- step 3: Fit one-zone thermal synchrotron model
  - method: Uniform sphere of angular diameter 40 uas with n, Te, B; fit to ALMA data plus Herschel ranges; ν_p, L_bol, n, Te, B derived [Discussion and Conclusions: "We parameterize the emission region as a sphere of constant particle density $n$, electron temperature $T_e$, and magnetic field strength $B$."]
  - software: emcee
  - parameter: Te >= Tb, 1e-3 < beta < 1e3; 20% uncertainty on 868 GHz [Discussion and Conclusions: "Parameter bounds are $T_e \ge T_b$ the brightness temperature, necessary for obtaining a one zone solution, and $10^{-3} < \beta < 10^{3}$."]
  - assumption: Relativistic effects and radiative cooling neglected; thermal electrons; constant ion temperature proportional to virial [Discussion and Conclusions: "We neglect all relativistic effects in the spatial and velocity distribution of the material and on the photon trajectories."]
  - fitting: emcee default sampler with logarithmic priors on n, Te and plasma beta [Discussion and Conclusions: "We use the default sampler with logarithmic priors $n$, $T_e$, and plasma $\beta = p_g/p_B \propto n/B^2$"]
  - validation: Repeated without Herschel data [Discussion and Conclusions: "We find similar results with somewhat larger ranges when leaving out the Herschel data"]
- result: SED peak frequency = (1-2)e12 ± 68% interval Hz [Discussion and Conclusions: "The peak of the SED in $\nu L_\nu$ is well constrained to be at $\nu_p = (1-2) \times 10^{12}$ Hz"]
- result: Bolometric luminosity of submm bump = (4-6)e35 ± not stated erg/s [Discussion and Conclusions: "The bolometric luminosity of the submm bump is found to be $L_{\rm bol} = (4-6) \times 10^{35}\,\ensuremath{{\rm erg\,s}}^{-1}$."]
- result: Electron density, temperature, field = n=2-5e6 cm^-3, Te=1-3e11 K, B=10-50 G ± not stated cm^-3, K, G [Discussion and Conclusions: "$n = 2-5 \times 10^6 \hspace{2pt} \rm cm^{-3}$, $T_e = 1-3 \times 10^{11}$ K, $B = 10-50$ G."]
- limitation (authors): 868 GHz measured four days from the others, longer than variability coherence time [Discussion and Conclusions: "the four-day separation with the 868 GHz measurements is significantly longer than the variability coherence time"]
- not stated (card): Exact CASA version and whether the pipeline or manual scripts were used; Calibrator flux model details and extrapolation spectral index for J1924-2914; Antenna flagging and spectral-window handling; emcee settings (walkers, steps, burn-in); One-zone code is from von Fellenberg and not released; Exact prior ranges for n and Te; Uv-fit procedure details

### 2025A&A...699A.369V: Dense clumps survive in the vicinity of R136 in 30 Doradus (2025; star_formation, nearby_galaxies, milky_way_ism; observational_alma_primary)
- question: Why do dense molecular clumps survive so close in projection to the massive cluster R136 in 30 Dor, and what are their physical properties?
- step 6: Continuum source photometry and free-free subtraction
  - method: 3sigma sources, 1.5sigma contour area, aperture photometry with background subtraction; Brgamma->Halpha->free-free scaled to 338.5 GHz and subtracted [4.4.1: "We determined the free-free emission towards each clump through aperture photometry."]
  - software: astropy.modelling
  - assumption: Te=1e4 K, He+/H+~0.08, Halpha/Brgamma=101.78 [4.4.1: "We used $T_e=10^4$ K and $n(He^{+})/n(H^{+})\sim0.08$"]
  - fitting: two elliptical Gaussians for B and D [Clump identification in continuum emiss…: "so to determine their area, we modeled the emission from both clumps as two elliptical Gaussians."]
- result: Continuum free-free fraction at 0.88 mm = 50-85 ± not stated percent [4.4.1: "These values represent between 50 and 85% of the total 0.88 mm flux measured in the ALMA images"]
- limitation (authors): Most clumps unresolved; missing extended flux without Total Power data; non-LTE modeling out of scope [5.4: "Total Power (TP) observations would be necessary to detect extended continuum emission."]
- not stated (card): Line-free channel ranges used for uvcontsub; Clean thresholds, iterations and mask definitions; Number of execution blocks, observing dates, integration time; Flux, bandpass and phase calibrators and flux accuracy; Free-free image (Brgamma) is private communication; Exact Gaussian-fitting starting parameters and spectral ranges; Extrapolation settings of CPROPS beyond those listed

### 2014ApJ...796...82Z: Spectral and Morphological Analysis of the Remnant of Supernova 1987A with ALMA and ATCA (2014; star_formation, astrochemistry; observational_alma_primary)
- question: What are the thermal and non-thermal components of SNR 1987A's emission from radio to FIR, how are they distributed, and is there evidence for a pulsar wind nebula?
- step 2: Subtract synchrotron and dust templates
  - method: Scaled 44 GHz and B9 models subtracted from visibilities with uvmodel [2 Observations and Analysis: "the model flux density at 44 GHz was scaled to fit the SNR emission over the ER ($I_{44}$)"]
  - software: MIRIAD uvmodel, MIRIAD uvfit
  - fitting: Scaling tuned to minimize difference on eastern lobe without over-subtraction [2 Observations and Analysis: "Scaling of the 44 GHz model was tuned by minimizing the flux density difference on the brighter eastern lobe"]
  - validation: Residuals compared with noise levels [3.1 Subtracted Images: "The residual emission at both 102 and 213 GHz is above noise levels and, thus, unlikely to be the result of image artefacts."]
- step 4: Fit SED components
  - method: Power law fit to scaled 44 GHz fluxes plus ATCA; modified Planck function for dust; free-free and second synchrotron alternatives [5.3 Dust Emission: "yields $\beta=1.23$ and dust temperature $T=22.2$ K"]
  - assumption: 1<=beta<=2; kappa~2.5 cm2/g for amorphous carbon; free-free with Te~1e4 K, sphere radius 0.40" [5.3 Dust Emission: "$k_{\nu}\sim2.5$ cm$^{2}$ g$^{-1}$ for amorphous carbon"]
  - validation: Free-free tested against Halpha flux limits [5.1 Free-Free Emission: "the estimated $S_{\rm H\alpha}$ would have to undergo $7.4$ magnitudes of extinction"]
- result: Synchrotron spectral index at day 9280 = -0.727 ± 0.020 dimensionless [5 Spectral Energy Distribution: "$\alpha_{s}=-0.727\pm0.020$"]
- result: Dust temperature = 22.2 ± not stated K [5.3 Dust Emission: "yields $\beta=1.23$ and dust temperature $T=22.2$ K"]
- result: Dust emissivity index beta = 1.23 ± not stated dimensionless [5.3 Dust Emission: "yields $\beta=1.23$"]
- result: Second synchrotron index = -0.231 ± not stated dimensionless [5.2 Flat-Spectrum Synchrotron Emission: "a synchrotron component with spectral index $\alpha_{p}=-0.231$"]
- limitation (authors): Equipartition estimates may be inaccurate for flat spectra; double-subtracted images unusable due to errors [7 PWN constraints: "these $B_{_{\rm PWN}}$ estimates might be inaccurate"]
- not stated (card): Scaling factors for 44 GHz and B9 models; Exact MEM and CLEAN parameters (iterations, masks); Polygons used for flux integration; Line-free channel selection beyond band edges; Fitting weights and procedure for SED, beta and T; Unpublished ATCA exponential scaling parameters; Distance adopted for SNR 1987A

### 2018ApJ...863...96Y: ALMA Observations of the Solar Chromosphere on the Polar Limb (2018; sun; observational_alma_primary)
- question: What dynamic structures (jets, blobs) does the solar polar-limb chromosphere show at 100 GHz in ALMA, and how do they correspond to IRIS and AIA features?
- step 3: Estimate electron density of blob
  - method: Thermal free-free optical depth with Gaunt factor, tau ≈ Tb/T, EM≈n^2 L [Discussion: "assuming a small optical thickness, 100% filling factor, and $L \approx 1.5\ensuremath{''}$ approximated with the width of the observed blob, and $\tau \approx T_b/T$"]
  - parameter: T = 1e4–4e5 K; Tb=135 K; L≈1.5'' [Discussion: "we obtain $n=(4.6-8.4) \times 10^{9}\ \mathrm{cm}^{-3}$ in the range of $T=(10^4- 4\times 10^5)\ \mathrm{K}$."]
  - assumption: 100% filling factor, small optical thickness [Discussion: "assuming a small optical thickness, 100% filling factor"]
  - validation: Compared with spicule densities from IRIS spectra (Alissandrakis 2018): about an order of magnitude lower [Discussion: "This number is a factor of one order of magnitude smaller than those for spicules obtained through the analysis of the IRIS spectrum data"]
- result: Blob electron density = (4.6-8.4)e9 ± not stated cm^-3 [Discussion: "we obtain $n=(4.6-8.4) \times 10^{9}\ \mathrm{cm}^{-3}$"]
- limitation (authors): Absolute brightness temperature is hard to determine; S/N poor beyond 10'' off limb; resolution comparable to blob size [Observations: "it is still difficult to determine the absolute brightness temperature in the ALMA data"]
- limitation (authors): Could not confirm jet generation models [Discussion: "Using the available data in the present observations, we could not confirm the proposed model."]
- not stated (card): CASA version and imaging task/parameters (weighting, cell, size, deconvolution); Self-calibration solution intervals and software; Array configuration and baselines; Number of antennas and spectral window setup; IRIS/AIA data processing and alignment with ALMA; Method for measuring jet length and blob proper motion

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

## All papers in this technique

- 2013AJ....146...91I (2013): ALMA Detection of the Vibrationally Excited HCN J = 4-3 Emission Line in the AGN-hosting Luminous Infrared Galaxy IRAS 20551-4250
- 2013ApJ...772..149C (2013): Constraining a Model of Turbulent Coronal Heating for AU Microscopii with X-Ray, Radio, and Millimeter Observations
- 2014ApJ...791...95A (2014): η Carinae Baby Homunculus Uncovered by ALMA
- 2014ApJ...796...82Z (2014): Spectral and Morphological Analysis of the Remnant of Supernova 1987A with ALMA and ATCA
- 2015A&A...577A..30A (2015): Tightening the belt: Constraining the mass and evolution in SDC335
- 2015ApJ...801...82H (2015): ALMA Imaging of Millimeter/Submillimeter Continuum Emission in Orion KL
- 2015ApJ...802...69B (2015): Radio and Millimeter Monitoring of Sgr A*: Spectrum, Variability, and Constraints on the G2 Encounter
- 2015ApJ...804...37L (2015): ALMA Resolves the Spiraling Accretion Flow in the Luminous OB Cluster-forming Region G33.92+0.11
- 2015ApJ...811...39I (2015): ALMA Observations of the Submillimeter Dense Molecular Gas Tracers in the Luminous Type-1 Active Nucleus of NGC 7469
- 2015ApJ...813...45L (2015): Radio Jet Feedback and Star Formation in Heavily Obscured, Hyperluminous Quasars at Redshifts ∼ 0.5-3. I. ALMA Observations
- 2015ApJ...813..118M (2015): Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations
- 2015MNRAS.450L..80B (2015): ALMA observations of 99 GHz free-free and H40α line emission from star formation in the centre of NGC 253
- 2016ApJ...821..112K (2016): SMA Observations of the Extended <SUP>12</SUP>CO(J = 6-5) Emission in the Starburst Galaxy NGC 253
- 2016ApJ...821L..16C (2016): The VLA View of the HL Tau Disk: Disk Mass, Grain Evolution, and Early Planet Formation
- 2016ApJ...822L..10I (2016): ALMA 0.1-0.2 arcsec Resolution Imaging of the NGC 1068 Nucleus: Compact Dense Molecular Gas Emission at the Putative AGN Location
- 2016ApJ...826...16E (2016): Protoplanetary Disks in the Orion OMC1 Region Imaged with ALMA
- 2016ApJ...833L...6C (2016): ALMA Reveals Potential Localized Dust Enrichment from Massive Star Clusters in II Zw 40
- 2016MNRAS.459.3629I (2016): ALMA observations of the submillimetre hydrogen recombination line from the type 2 active nucleus of NGC 1068
- 2016MNRAS.463..252B (2016): Free-free and H42α emission from the dusty starburst within NGC 4945 as observed by ALMA
- 2017A&A...601L...3P (2017): First detection of the 448 GHz H<SUB>2</SUB>O transition in space
- 2017A&A...602A..19L (2017): A concordant scenario to explain FU Orionis from deep centimeter and millimeter interferometric observations
- 2017A&A...602L..10O (2017): The inhomogeneous submillimeter atmosphere of Betelgeuse
- 2017A&A...605A..78A (2017): Center-to-limb observations of the Sun with ALMA . Implications for solar atmospheric models
- 2017A&A...606A..17M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: Physical properties derived from energy balance spectral energy distribution …
- 2017ApJ...834....6S (2017): Merger-induced Shocks in the Nearby LIRG VV 114 through Methanol Observations with ALMA
- 2017ApJ...835L..13S (2017): ALMA Observations of the Water Fountain Pre-planetary Nebula IRAS 16342-3814: High-velocity Bipolar Jets and an Expanding Torus
- 2017ApJ...835L..35M (2017): New ALMA and Fermi/LAT Observations of the Large-scale Jet of PKS 0637-752 Strengthen the Case Against the IC/CMB Model
- 2017ApJ...840...32T (2017): Planet Formation in AB Aurigae: Imaging of the Inner Gaseous Spirals Observed inside the Dust Cavity
- 2017ApJ...841L...5S (2017): The First ALMA Observation of a Solar Plasmoid Ejection from an X-Ray Bright Point
- 2017ApJ...848L..21A (2017): The Electromagnetic Counterpart of the Binary Neutron Star Merger LIGO/Virgo GW170817. VI. Radio Constraints on a Relativistic Jet and Pred…
- 2017ApJ...849...90S (2017): Evolution of Molecular Clouds in the Superwind Galaxy NGC 1808 Probed by ALMA Observations
- 2017ApJ...850...35L (2017): Solar ALMA Observations: Constraining the Chromosphere above Sunspots
- 2017ApJ...850...54C (2017): ALMA CO(3-2) Observations of Star-forming Filaments in a Gas-poor Dwarf Spheroidal Galaxy
- 2017ApJ...851..126V (2017): Galactic-scale Feedback Observed in the 3C 298 Quasar Host Galaxy
- 2017MNRAS.467L.120M (2017): The ALMA view of W33A: a spiral filament feeding the candidate disc in MM1-Main
- 2017MNRAS.468L..87C (2017): New ALMA constraints on the star-forming interstellar medium at low metallicity: a 50 pc view of the blue compact dwarf galaxy SBS 0335-052
- 2018A&A...617A.137F (2018): An ALMA 3 mm continuum census of Westerlund 1
- 2018A&A...619A..40M (2018): The radio jets of SS 433 at millimetre wavelengths
- 2018ApJ...853..171G (2018): Distributed Star Formation throughout the Galactic Center Cloud Sgr B2
- 2018ApJ...854...90E (2018): Molecular Gas Properties in M83 from CO PDFs
- 2018ApJ...855L...2M (2018): Detection of a Millimeter Flare from Proxima Centauri
- 2018ApJ...860....9M (2018): Detection of an Optical/UV Jet/Counterjet and Multiple Spectral Components in M84
- 2018ApJ...860...77E (2018): Protoplanetary Disk Properties in the Orion Nebula Cluster: Initial Results from Deep, High-resolution ALMA Observations
- 2018ApJ...862...94L (2018): First ALMA Light Curve Constrains Refreshed Reverse Shocks and Jet Magnetization in GRB 161219B
- 2018ApJ...863...96Y (2018): ALMA Observations of the Solar Chromosphere on the Polar Limb
- 2018ApJ...864L..17G (2018): A High Cluster Formation Efficiency in the Sagittarius B2 Complex
- 2018ApJ...866..141K (2018): Extremely Dense Cores Associated with Chandra Sources in Ophiuchus A: Forming Brown Dwarfs Unveiled?
- 2018ApJ...867...48I (2018): Circumnuclear Multiphase Gas in the Circinus Galaxy. II. The Molecular and Atomic Obscuring Structures Revealed with ALMA
- 2018ApJ...869..114I (2018): Detection of Coronal Magnetic Activity in nearby Active Supermassive Black Holes
- 2018ApJ...869..126L (2018): Forming Super Star Clusters in the Central Starburst of NGC 253
- 2018MNRAS.478.2505I (2018): Radiative transfer modelling of W33A MM1: 3D structure and dynamics of a complex massive star-forming region
- 2018PASJ...70...73H (2018): ALMA <SUP>12</SUP>CO (J = 1-0) imaging of the nearby galaxy M 83: Variations in the efficiency of star formation in giant molecular clouds
- 2019A&A...621A..27F (2019): Massive galaxies on the road to quenching: ALMA observations of powerful high redshift radio galaxies
- 2019A&A...622A..26G (2019): Molecular ion abundances in the diffuse ISM: CF<SUP>+</SUP>, HCO<SUP>+</SUP>, HOC<SUP>+</SUP>, and C<SUB>3</SUB>H<SUP>+</SUP>
- 2019A&A...627L...6M (2019): Substructures in the Keplerian disc around the O-type (proto-)star G17.64+0.16
- 2019A&A...628A..85V (2019): Disk masses in the Orion Molecular Cloud-2: distinguishing time and environment
- 2019ApJ...870...59S (2019): ALMA, ATCA, and Spitzer Observations of the Luminous Extragalactic Supernova SN 1978K
- 2019ApJ...871...73H (2019): AT2018cow: A Luminous Millimeter Transient
- 2019ApJ...871..185L (2019): Investigating Fragmentation of Gas Structures in OB Cluster-forming Molecular Clump G33.92+0.11 with 1000 au Resolution Observations of ALMA
- 2019ApJ...878L..26L (2019): ALMA Detection of a Linearly Polarized Reverse Shock in GRB 190114C
- 2019ApJ...881...33H (2019): Constraining the Radio Emission of TRAPPIST-1
- 2019ApJ...881L...2B (2019): ALMA Observations of the Terahertz Spectrum of Sagittarius A*
- 2019ApJ...882....1L (2019): CO and Fine-structure Lines Reveal Low Metallicity in a Stellar-mass-rich Galaxy at z ∼ 1?
- 2019ApJ...883...71C (2019): The Radial Distribution of Dust Particles in the HL Tau Disk from ALMA and VLA Observations
- 2019ApJ...883L...2M (2019): The Origin of the X-Ray Emission in Two Well-aligned Extragalactic Jets: The Case for IC/CMB
- 2019ApJ...884...97L (2019): Diagnosing 0.1-10 au Scale Morphology of the FU Ori Disk Using ALMA and VLTI/GRAVITY
- 2019ApJ...885L..21M (2019): How to Fuel an AGN: Mapping Circumnuclear Gas in NGC 6240 with ALMA
- 2019ApJ...886L...4Z (2019): Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05
- 2019ApJS..241...19I (2019): ALMA Spatially Resolved Dense Molecular Gas Survey of Nearby Ultraluminous Infrared Galaxies
- 2019MNRAS.483.1624B (2019): An ALMA archival study of the clump mass function in the Large Magellanic Cloud
- 2019MNRAS.484L..85M (2019): Circumstellar CO in metal-poor stellar winds: the highly irradiated globular cluster star 47 Tucanae V3
- 2019NatAs...3..517Z (2019): Dynamics of a massive binary at birth
- 2019Natur.569..519K (2019): Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback
- 2019PASJ...71L...3F (2019): First detection of PSR B1259-63/LS 2883 in the millimeter and submillimeter wavelengths with ALMA
- 2020A&A...633A.127F (2020): A CO molecular gas wind 340 pc away from the Seyfert 2 nucleus in ESO 420-G13 probes an elusive radio jet
- 2020A&A...634A...9M (2020): The flickering nuclear activity of Fornax A
- 2020A&A...640A..27V (2020): Protoplanetary disk masses in NGC 2024: Evidence for two populations
- 2020A&A...643A..41D (2020): ALMA observations of transient heating in a solar active region
- 2020ApJ...888L..28S (2020): Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA
- 2020ApJ...889..178B (2020): The Orion Protostellar Explosion and Runaway Stars Revisited: Stellar Masses, Disk Retention, and an Outflow from the Becklin-Neugebauer Ob…
- 2020ApJ...890..129K (2020): Detection of Irregular, Submillimeter Opaque Structures in the Orion Molecular Clouds: Protostars within 10,000 yr of Formation?
- 2020ApJ...891...80M (2020): Properties of M Dwarf Flares at Millimeter Wavelengths
- 2020ApJ...891L...8M (2020): The Formation Height of Millimeter-wavelength Emission in the Solar Chromosphere
- 2020ApJ...892..111F (2020): Dust-depleted Inner Disks in a Large Sample of Transition Disks through Long-baseline ALMA Observations
- 2020ApJ...895L...2N (2020): Substructure Formation in a Protostellar Disk of L1527 IRS
- 2020ApJ...896...35J (2020): A Detailed View of the Circumstellar Environment and Disk of the Forming O-star AFGL 4176
- 2020ApJ...897L..33J (2020): The Ionized Warped Disk and Disk Wind of the Massive Protostar Monoceros R2-IRS2 Seen with ALMA
- 2020ApJ...898...54T (2020): Chemical Composition in the IRAS 16562-3959 High-mass Star-forming Region
- 2020ApJ...901..151S (2020): Molecular Gas Outflow in the Starburst Galaxy NGC 1482
- 2020ApJ...903...29M (2020): Reconstructing the EUV Spectrum of Star-forming Regions from Millimeter Recombination Lines of H I, He I, and He II
- 2020ApJ...904L..24S (2020): ALMA CO Observations of the Gamma-Ray Supernova Remnant RX J1713.7-3946: Discovery of Shocked Molecular Cloudlets and Filaments at 0.01 pc …
- 2020MNRAS.496.1834L (2020): Atacama Compact Array observations of the pulsar-wind nebula of SNR 0540-69.3
- 2020MNRAS.499..193K (2020): Measuring the mixing scale of the ISM within nearby spiral galaxies
- 2021A&A...646A.127H (2021): Multiwavelength dissection of a massive heavily dust-obscured galaxy and its blue companion at z∼2
- 2021A&A...649A.139I (2021): Multiple molecular outflows and fragmentation in the IRDC core G34.43+00.24 MM1
- 2021A&A...652A..92N (2021): ALMA observations of the variability of the quiet Sun at millimeter wavelengths
- 2021A&A...653A.117B (2021): ORion Alma New GEneration Survey (ORANGES). I. Dust continuum and free-free emission of OMC-2/3 filament protostars
- 2021A&A...656A..46M (2021): ALCHEMI, an ALMA Comprehensive High-resolution Extragalactic Molecular Inventory. Survey presentation and first results from the ACA array
- 2023MNRAS.524.1625D (2023): The evolution of the internal structure of massive star-forming regions in the Milky Way as revealed by ALMA
- 2023NatAs...7...80U (2023): Simultaneous radio and optical polarimetry of GRB 191221B afterglow
- 2023Natur.623..927H (2023): Minutes-duration optical flares with supernova luminosities
- 2024A&A...684A.134R (2024): Correlation between accretion rate and free-free emission in protoplanetary disks. A multiwavelength analysis of central mm/cm emission in …
- 2024A&A...687A.163B (2024): ALMA-IMF. XI. The sample of hot core candidates: A rich population of young high-mass protostars unveiled by the emission of methyl formate
- 2024ApJ...962...48J (2024): Thermal Properties of the Hot Core Population in Sagittarius B2 Deep South.
- 2024ApJ...967...15K (2024): Infall Motions in the Hot Core Associated with the Hypercompact H II Region G345.0061+01.794 B
- 2024ApJ...972..111L (2024): Ongoing and Fossil Large-scale Outflows Detected in a High-redshift Radio Galaxy: [C II] Observations of TN J0924-2201 at z = 5.174
- 2024ApJ...972..163L (2024): First JVLA Radio Observation on PDS 70
- 2024ESC.....8..665M (2024): Detection and Chemical Modeling of Complex Prebiotic Molecule Cyanamide in the Hot Molecular Core G31.41 + 0.31
- 2025A&A...694A.166C (2025): The ALMA-ATOMS survey: Vibrationally excited HC<SUB>3</SUB>N lines in hot cores
- 2025A&A...695A.233R (2025): A multifrequency study of sub-parsec jets with the Event Horizon Telescope
- 2025A&A...699A..62J (2025): ALMA observation of an evolving magnetized corona in the radio-quiet changing-state active galactic nucleus NGC 1566
- 2025A&A...699A.369V (2025): Dense clumps survive in the vicinity of R136 in 30 Doradus
- 2025ApJ...990...29H (2025): Compact Ionized Gas Region Surrounded by Porous Neutral Gas in a Dusty Lyman Break Galaxy at Redshift z = 8.312
- 2025ApJ...991...53C (2025): HerS-3: An Exceptional Einstein Cross Reveals a Massive Dark Matter Halo
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025ApJ...993..120H (2025): Early Planet Formation in Embedded Disks (eDisk). XVII. A Compact but Structured Keplerian Disk and Large-scale Streamers Revealed in the C…
- 2025MNRAS.540..364A (2025): Multiwavelength study of OT 081: broadband modelling of a transitional blazar
- 2026ApJ..1003L..17Y (2026): Evidence for Multiple Orbiting Hotspots in the 340 GHz Variability of Sgr A*
- 2026ApJ..1004..126K (2026): An Active Galactic Nucleus in the Antennae Galaxies?
