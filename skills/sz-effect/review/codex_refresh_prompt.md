# Review task: a REFRESHED ALMA agent skill against its rebuilt evidence pack

The skill below was first written from a ~1,600-paper corpus, reviewed, and fixed (the fix record is the
RECONCILIATION section). The corpus then grew to ~3,500 papers, the evidence pack was rebuilt, and a writer began
updating the skill to the new pack. The writer may have been cut off before finishing, so expect a mix: some
counts and ranges updated to the new pack, others still at the old values, and possibly a half-edited section.

Apply every check from the standard review (attribution, unsupported practice, scientific correctness, omissions,
usability: see below), and also these refresh checks:

A. **Stale or mixed numbers.** Paper counts, "used in N papers", common choices and ranges that do not match the
   NEW pack aggregates (the old corpus was about half the size, so old counts are usually roughly half). The
   description line's "Built from N ALMA papers" must match the pack.
B. **Lost fixes.** Any item the RECONCILIATION marks FIXED that the current skill has undone or reintroduced.
C. **Broken edits.** Duplicated sections, contradictory statements left from an unfinished rewrite, tables whose
   rows disagree with the text, dangling references.
D. **Length.** Over ~300 lines is a low-severity usability finding; say what could move to references/parameters.md.

Standard checks, in this order:
1. Attribution: every number, range, default, software attribution and "papers do X" claim that cites bibcodes is
   supported by the pack for those bibcodes; counts match the pack aggregates.
2. Unsupported practice presented as literature practice.
3. Scientific correctness: formulas, units, CASA task/parameter names and semantics, unsafe advice.
4. Omissions: important pitfalls, assumptions or validation checks clearly present in the pack but missing.
5. Usability: anything an agent would misread or could not act on.

You have no file access: everything you need is in this message.

Output format (Markdown, nothing else):

```
# Codex refresh review: <slug>
VERDICT: CLEAN | FIX
REFRESH: COMPLETE | PARTIAL   (PARTIAL if any section still carries old-pack numbers or an unfinished edit)
## Findings
- RR-01 | high|medium|low | <stale|lost-fix|broken-edit|length|attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- RR-02 | ...
## Notes
<at most 5 lines>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (sz-effect) ===
---
name: alma-sz-effect
description: "Measure the thermal (and, where possible, kinetic) Sunyaev-Zeldovich decrement with ALMA and the ACA: subtract compact sources, forward-model a gNFW or shock pressure model at the measured uv points, report detection significance, Compton y, pressure profiles, M500, Mach numbers and SZ-plus-X-ray temperatures. Use when detecting or confirming galaxy clusters and protoclusters in Band 3/4, reconstructing ICM pressure or merger shocks, combining ALMA/ACA with ACT, SPT, Bolocam, Planck or MUSTANG-2 SZ data, searching for SZ halos around quasars, or checking someone else's SZ mass or significance. Built from 14 on-topic ALMA papers (2016-2024) out of 21 tagged."
---

# Sunyaev-Zeldovich effect measurements with ALMA/ACA

The SZ effect is a small negative signal in Band 3/4 (tens to hundreds of microJy) set by the line-of-sight
integral of electron pressure. ALMA and the ACA sample it only on scales below their largest recoverable scale,
so almost every paper fits a pressure model directly to the visibilities instead of reading numbers off an
image. The mistakes that matter most: (1) treating the filtered interferometric signal as the full SZ signal,
which biases amplitudes, masses and integrated Y low and makes pressure-model slopes degenerate
(2016ApJ...829L..23B, 2024A&A...689A..41V, 2024A&A...682A.186L, 2021A&A...650A.153D); and (2) leaving compact
radio or dusty sources in the data, which fill in or mimic the decrement (2020A&A...638A..70D,
2019A&A...629A.104G, 2019MNRAS.490.5134B).

> Always report: which arrays and bands entered the fit, how compact sources were modelled (spectral form, uv
> cuts), the pressure model and which of its parameters were fixed, priors and sampler, relativistic and kSZ
> treatment, cosmology, how significance was computed, and at least one external check (X-ray, another SZ
> instrument, or mock observations).

## When to use

- Confirming cluster candidates with short ACA Band 3 integrations and getting rough M500
  (2020A&A...638A..70D: SZ detected in 7 of 10 MaDCoWS clusters).
- Resolved ICM pressure and morphology in high-z clusters and protoclusters, z of about 1 to 2.2
  (2024A&A...689A..41V at z = 1.98, 2019A&A...629A.104G at z = 1.99, 2021A&A...650A.153D at z of about 1.13,
  2024A&A...682A.186L for the Spiderweb at z = 2.16).
- Merger shocks: pressure jump across a shock front gives a Mach number (2016ApJ...829L..23B El Gordo,
  2019A&A...628A.100D Bullet Cluster).
- Cool cores and inner pressure profiles at arcsec resolution (2020PASJ...72...33K Phoenix).
- Joint fits with lower-resolution SZ data that see the large scales ALMA misses: ACT (2024A&A...689A..41V,
  2021A&A...650A.153D compares with AdvACT), Bolocam plus Planck (2019MNRAS.487.4037D), MUSTANG-2 at 90 GHz
  (2020ApJ...891...90R, a multi-facility paper where ALMA is minor).
- Thermodynamics without X-ray spectroscopy: SZ pressure divided by X-ray density gives temperature
  (2024A&A...682A.186L, 2020PASJ...72...33K, proposed in 2020EPJWC.22800009E).
- Searching for hot circumgalactic gas around AGN and quasars (2019MNRAS.490.5134B single field,
  2024ApJ...969...56M stack of ten fields). Expect low significance.

## When not to use

- "Sz 65", "Sz 71", "Sz 98" are Lupus star names, and "Shakura-Sunyaev" is a disk model; papers on those are
  tagged by the regex but have nothing to do with SZ. For disks use the disk-substructure or uv-plane-fitting
  skills.
- Total cluster Y or masses out to r500 and beyond from ALMA alone: the arrays cannot constrain these scales
  (2020EPJWC.22800009E notes missing SZ data at 30 to 100 arcsec; 2020PASJ...72...33K cannot constrain
  temperature beyond 250 kpc). Add ACT, SPT, Planck, Bolocam or MUSTANG-2 data, or quote a model-dependent
  extrapolation clearly.
- Separating thermal from kinetic SZ with a single band: not possible without more frequencies
  (2024ApJ...969...56M, 2021A&A...650A.153D). Use a prior on the integrated flux at best.
- Pure dust or synchrotron continuum work on cluster members: use the continuum, spectral-index or
  source-extraction skills; here those sources are contaminants to remove.

## Steps

1. **Pick data and check uv coverage.** Goal: enough short spacings to see the decrement.
   - Papers use Band 3 (about 92 GHz) and add Band 4 to separate SZ from compact sources
     (2024A&A...689A..41V, 2021A&A...650A.153D). Band 3 near 92 GHz was chosen as a compromise between
     integration time and dust contamination, in a compact configuration (2019A&A...629A.104G, methods card).
   - ACA plus ALMA 12-m together is the norm (2019A&A...628A.100D, 2024A&A...689A..41V, 2020PASJ...72...33K);
     ACA alone suffices for detection but limits mass inference (2020A&A...638A..70D).
   - For weak signals check that the shortest-baseline bin is populated by many independent uv tracks and
     antenna pairs, not one (2019MNRAS.490.5134B checked more than 50 uv tracks and 20 antenna pairs).
2. **Model and remove compact sources.** Goal: a source-free uv dataset or a joint source model.
   - Point (Dirac delta) models fitted in the uv plane. Spectral forms seen: power law
     (2021A&A...650A.153D), modified power law with curvature for a central radio source (2021A&A...650A.153D),
     first-order polynomial (2024A&A...689A..41V), flat spectrum (2020A&A...638A..70D).
   - Isolate compact emission with uv cuts: lower uv cut of 11 klambda when fitting sources
     (2024A&A...689A..41V); CASA `uvmodelfit` on 12-m baselines longer than 30 klambda, then subtraction in the
     uv plane (2020PASJ...72...33K, methods card); subtraction of nine known sources in groups, brightest
     first (2019A&A...629A.104G, methods card).
   - For an extended radio galaxy, an upper uv threshold of 65 klambda made it unresolved across the jet so a
     point-component set could describe it (2024A&A...682A.186L).
   - Preferred practice in the newer papers: fit sources jointly with the SZ model and marginalize, rather
     than subtract and forget (2021A&A...650A.153D, 2020A&A...638A..70D, 2024A&A...682A.186L).
3. **Build the pressure model.** Goal: a model sky in SZ brightness for each band.
   - Spherical gNFW pressure (Nagai2007 form) integrated along the line of sight to Compton y, converted to
     brightness per band, multiplied by the primary beam, Fourier transformed and sampled at the data uv
     points (2021A&A...650A.153D, 2024A&A...689A..41V, 2019A&A...628A.100D).
   - Shape choices: universal profile of Arnaud2010 with free centroid, mass and inner slope
     (2021A&A...650A.153D); fixed shape with free M500 and z (2020A&A...638A..70D); eight literature templates
     (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT) each with only M500 free (2024A&A...682A.186L); LeB15,
     A10, S16, McD14 templates with free mass (2019A&A...629A.104G).
   - Shocks: gNFW upstream plus a pressure boost at the shock radius from Rankine-Hugoniot,
     p_down/p_up = (5M^2 - 1)/4 (2016ApJ...829L..23B); power-law downstream with gNFW upstream and
     gamma = 5/3 (2019A&A...628A.100D).
   - Multiple subclusters: one gNFW component each, with an ordering condition on declination so the modes
     stay identifiable (2021A&A...650A.153D).
4. **Fit in the uv plane.** Goal: posteriors and a model evidence.
   - Nested sampling with `dynesty` is the most common sampler among on-topic papers (static:
     2024A&A...689A..41V; dynamic: 2019A&A...628A.100D; 2024A&A...682A.186L). Gaussian likelihood on unbinned
     visibilities (2024A&A...689A..41V). MCMC inside CASA was used in 2016ApJ...829L..23B; `emcee` with a
     full-covariance likelihood for MUSTANG-2 profiles (2020ApJ...891...90R).
   - Fast forward modelling: `galario` for the FFT and uv sampling (2019A&A...628A.100D). An FFT approximation
     agreed with CASA `simalma` to within about 4% (2019A&A...629A.104G).
   - Marginalize flux-calibration and redshift uncertainty with Gaussian priors (2024A&A...689A..41V;
     2019A&A...628A.100D used a normal(1, 0.05) scaling).
5. **Compute significance.** Goal: a detection claim that survives a referee.
   - Bayes factor between models with and without SZ, converted with sigma_eff = sqrt(2 Delta log Z);
     sigma_eff of about 3 or more is called robust (2020A&A...638A..70D). Delta log Z = 120.72 was quoted as
     15.6 sigma (2021A&A...650A.153D). That conversion assumes a Gaussian posterior and ignores prior volume
     changes (2021A&A...650A.153D).
   - Image-plane or uv-profile alternatives: total signal and S/N after source subtraction
     (2019A&A...629A.104G reports -190 +/- 36 microJy, 5.3 sigma, methods card); dirty-image significance as a
     cross-check (2020A&A...638A..70D).
6. **Derive physical quantities.**
   - M500 from the Arnaud2010 parametrization, which assumes self-similarity and hydrostatic equilibrium
     (2021A&A...650A.153D); Y500 to M500 with Arnaud2010 local scaling relations (2024A&A...689A..41V).
   - Average across pressure models: evidence-weighted mean (2024A&A...689A..41V) or Bayesian model averaging
     with model variance propagated (2024A&A...682A.186L).
   - Integrated SZ flux in a cylinder matched to an external catalog's r500, here 1.69 arcmin to compare with
     AdvACT (2021A&A...650A.153D).
   - Temperature: kT_e = P_e / n_e per X-ray annulus, assuming the ideal gas law (2024A&A...682A.186L); or a
     pseudo-temperature map from SZ divided by the square root of X-ray surface brightness, assuming constant
     temperature along the line of sight (2024A&A...689A..41V).
   - Mach number from the pressure jump, optionally with an X-ray prior on upstream pressure
     (2016ApJ...829L..23B, 2019A&A...628A.100D).
   - Image route, if needed: CASA `tclean` multi-scale joint 12-m plus 7-m mosaic with natural weighting,
     noise from half-split difference maps, image divided by a missing-flux factor of 0.94 calibrated on
     `simobserve` mocks, mean signal at 42 arcsec subtracted (2020PASJ...72...33K, partly from the methods card).
7. **Optional kinetic SZ.** Add a kSZ term per component and break the thermal/kinetic degeneracy with a prior
   on integrated SZ flux from a survey (2021A&A...650A.153D). Expect velocity errors of thousands of km/s.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Band | Band 3 near 92 GHz | Band 3 alone to Band 3 + 4 | 6 (my count) | 2019A&A...629A.104G, 2024A&A...689A..41V |
| Pressure model | gNFW, Arnaud2010 shape | 1 template to 8 templates; free inner slope | 8 (my count) | 2021A&A...650A.153D, 2024A&A...682A.186L, 2019A&A...629A.104G |
| Free SZ parameters | M500 (+ centroid) | M500 only (centroid fixed to X-ray) to M500, centroid, inner slope, z | 4 (my count) | 2024A&A...682A.186L, 2020A&A...638A..70D |
| Centroid prior | uniform over ACA field | normal with sigma 14.3 to 15 arcsec; fixed to X-ray | 3 | 2021A&A...650A.153D, 2020A&A...638A..70D |
| Redshift | split-normal or Gaussian, marginalized | fixed | 2 | 2020A&A...638A..70D, 2024A&A...689A..41V |
| Flux-scale nuisance | normal(1, 0.05) | Gaussian priors | 2 | 2019A&A...628A.100D, 2024A&A...689A..41V |
| Point-source spectrum | varies | power law; flat; first-order polynomial; modified power law | 3 | 2020A&A...638A..70D, 2024A&A...689A..41V |
| uv cut for sources | lower cut 11 to 30 klambda | upper cut 65 klambda for extended radio galaxy | 3 | 2024A&A...689A..41V, 2024A&A...682A.186L |
| Relativistic correction | none (small at low T) | Itoh2004 / Nozawa2006; kT_e = 7 keV; X-ray projected T | 6 (my count) | 2020A&A...638A..70D, 2021A&A...650A.153D, 2020ApJ...891...90R |
| kSZ | neglected | fitted with integrated-flux prior | 4 | 2019A&A...628A.100D, 2024ApJ...969...56M |
| Cosmology | flat LCDM, Om 0.30, H0 70 | Planck H0 67.7, Om 0.307 | 4 | 2021A&A...650A.153D, 2024A&A...689A..41V |
| Mach prior (shock) | uniform 1 to 10 | free | 2 | 2019A&A...628A.100D, 2016ApJ...829L..23B |
| Detection threshold | sigma_eff of 3 or more | Bayes factor vs null | 2 | 2020A&A...638A..70D, 2024A&A...689A..41V |
| dynesty stop | Delta ln B = 0.01 | not stated elsewhere | 1 | 2024A&A...689A..41V |
| Line-of-sight integration | +/- 5 R500 | not stated in ALMA papers | 1 | 2020ApJ...891...90R |
| Compton-y background | 1.6e-6 | rarely stated | 1 | 2019A&A...629A.104G |

Counts marked "my count" are from reading the pack excerpts; the others count the bibcodes listed. Per-paper
setups are in `references/parameters.md`.

## Software

Pack aggregates count software over all 21 tagged papers (casa 6, dynesty 4, emcee 3, galario 1, simobserve 1,
casa simalma 1, tclean 1, colossus 1, ciao 1), but several casa and emcee hits come from off-topic disk
papers. Among the 14 on-topic papers (my count):

| Tool | Used for | Papers |
|---|---|---|
| CASA (`tclean`, `uvmodelfit`, `simobserve`, `simalma`) | imaging, compact-source fits, mock observations to calibrate filtering, MCMC in CASA | 2016ApJ...829L..23B, 2019MNRAS.490.5134B, 2019A&A...629A.104G, 2020PASJ...72...33K |
| dynesty | nested sampling of SZ + source models, Bayesian evidence | 2024A&A...689A..41V, 2019A&A...628A.100D, 2024A&A...682A.186L |
| galario | fast FFT and uv sampling of model images | 2019A&A...628A.100D (also GALARIO fits in 2019MNRAS.490.5134B) |
| emcee | MCMC pressure-profile fit with full covariance | 2020ApJ...891...90R |
| colossus | mass conversions for dynamical M500 | 2024A&A...689A..41V |
| CIAO | Chandra pressure profile for comparison | 2019MNRAS.487.4037D |

Several papers use an in-house uv forward-modelling code not named or versioned in the card
(2019MNRAS.487.4037D; the sampler in 2020A&A...638A..70D is not named).

## Pitfalls

- **Filtering bias.** Missing short spacings make the pressure normalization degenerate with shape and Mach
  number (2016ApJ...829L..23B, 2024A&A...689A..41V), push fits toward compact low-mass models
  (2021A&A...650A.153D), and can underestimate the SZ normalization (2024A&A...682A.186L). ALMA+ACA integrated
  SZ flux came out at 2.17e-4 arcmin^2 against 4.7e-4 from AdvACT (2021A&A...650A.153D). The outermost pressure
  bin can be biased low (2020ApJ...891...90R). A simulation-based correction factor of 2.5 was needed in one
  quasar field (2019MNRAS.490.5134B).
- **Template dependence of mass.** Eight pressure templates gave M500 from 2.01e13 to 6.54e13 Msun for one
  object (2024A&A...682A.186L). Free versus fixed slopes changed component masses from 2.60e14 and 1.34e14 to
  3.10e14 and 3.26e14 Msun (2021A&A...650A.153D). Report the model spread, not one template.
- **Hydrostatic and self-similar assumptions.** M500 inherits them; mergers and non-hydrostatic gas bias masses
  (2021A&A...650A.153D).
- **SZ temperatures can disagree with X-ray.** In the Spiderweb the SZ-based temperature was about 3 times
  lower than the X-ray spectral value, possibly from filtering, metallicity or non-thermal contamination
  (2024A&A...682A.186L).
- **tSZ/kSZ degeneracy** with one band (2024ApJ...969...56M, 2021A&A...650A.153D); stacks are blind to
  non-spherical kSZ (2024ApJ...969...56M).
- **Too few degrees of freedom.** A 17-parameter positive-source model left dof = 1 on short baselines
  (2019MNRAS.490.5134B). A best-fit model with chi-square similar to zero signal is not a detection
  (2024ApJ...969...56M).
- **Comparing non-nested models.** Statistical comparison between models with different components can mislead
  and overfitting can hide an overpressure (2019MNRAS.487.4037D).
- **Geometry.** Shock and post-shock geometry dominate systematics (2019A&A...628A.100D).
- **Undetected sources** leave positive residuals, so significance is conservative (2019A&A...629A.104G); radio
  flux boosting can be up to about 40% for faint sources (2021MNRAS.503.1174K).
- **Settings cards flag as not stated** (pack aggregates): CASA version (2 cards), dynesty live points and
  stopping, exact likelihood and visibility weights, uv selection and binning, map grid and line-of-sight
  limits, primary-beam model, numerical gNFW parameters and the Y-to-M500 implementation. State all of these.

## Verification checks

What papers did:
- Prior-only or data-free runs to show priors do not drive the result (2019A&A...628A.100D,
  2020A&A...638A..70D).
- Re-fit with alternate gNFW and source priors and with observation subsets (2021A&A...650A.153D); vary gNFW
  slopes and centroid (2019A&A...628A.100D).
- Residual maps: subtract the model in the visibility plane and image the residuals (2024A&A...689A..41V,
  2019MNRAS.490.5134B, 2019A&A...628A.100D). Images are for display; fit in the uv plane
  (2021A&A...650A.153D).
- Mock observations with known input: shocks with M = 1, 2, 4 (2016ApJ...829L..23B); FABLE simulation through
  `simobserve` (2019MNRAS.490.5134B); Monte Carlo test of SZ-X-ray peak offsets (2019A&A...629A.104G).
- External agreement: X-ray pressure profiles (2019MNRAS.487.4037D, 2020ApJ...891...90R), X-ray luminosity
  predicted from SZ mass (2021A&A...650A.153D), survey integrated SZ flux (2021A&A...650A.153D), masses from
  X-ray, CARMA and ACT (2024A&A...689A..41V), y-map morphology against X-ray (2020PASJ...72...33K).

What a careful referee adds:
- Inject a model decrement into the real visibilities (or noise realizations from the weights) and recover it
  with the full pipeline, including source fitting.
- Show the azimuthally averaged or binned real visibility amplitude versus uv distance with the model curve.
- Quote masses for every reasonable pressure template plus the averaged value, and state the uv range that
  actually constrains the fit.
- Confirm sources were modelled with a spectral form allowing both signs of spectral index across bands.

## Source cards

Full list with titles: `references/sources.md`. Most informative for this technique:

- 2021A&A...650A.153D (two-component gNFW, evidence, kSZ attempt, AdvACT comparison)
- 2024A&A...689A..41V (dynesty uv forward model, ALMA+ACA+ACT joint, template averaging)
- 2020A&A...638A..70D (ACA cluster confirmation, priors, sigma_eff)
- 2019A&A...628A.100D (Bullet shock, galario + dynamic nested sampling, prior table)
- 2016ApJ...829L..23B (El Gordo shock, Rankine-Hugoniot model, mock tests)
- 2024A&A...682A.186L (eight templates, BMA, SZ + X-ray temperature)
- 2019A&A...629A.104G (uv-profile, simalma, source subtraction)
- 2020PASJ...72...33K (image route, missing-flux factor, y map)
- 2019MNRAS.487.4037D (ALMA + Bolocam + Planck)
- 2020ApJ...891...90R (MUSTANG-2 pressure bins, full covariance)
- 2019MNRAS.490.5134B (quasar halo, residual visibilities, simulation correction)
- 2024ApJ...969...56M (stacked quasar fields, Compton y limit)
- 2020EPJWC.22800009E (SZ + X-ray + lensing shapes; preliminary ALMA data)
- 2021MNRAS.503.1174K (radio jets against an SZ residual map)

Tagged but off-topic (ignore): 2024A&A...682A..55M, 2019A&A...623A.150V, 2025A&A...694A.147G,
2018ApJ...865..157A, 2025ApJ...989....7T, 2019Natur.570...83M, 2021MNRAS.503.1459B.

=== references/parameters.md ===
# Per-paper SZ model setups (on-topic papers only)

Taken from the `sz-effect` evidence pack; "card" marks details read from that paper's methods card. "n.s." means
the card flags it as not stated.

| Paper | Data | Pressure model | Free parameters | Priors | Sampler / fit | Relativistic / kSZ | Compact sources |
|---|---|---|---|---|---|---|---|
| 2021A&A...650A.153D | ALMA+ACA Band 3/4 | gNFW, Arnaud2010 universal shape; 1 then 2 components; also all slopes fixed | centroid, mass, inner slope per component | uniform centroid over ACA field; wide uninformative mass and slope; split-normal T from X-ray | Bayesian evidence (nested), declination ordering of modes | Itoh2004 (tSZ), Nozawa2006 (kSZ run); isothermal; primary CMB neglected; kSZ fitted with AdvACT integrated-flux prior | point models, power-law spectra; central source modified power law; extended radio source not modelled, checked with alpha = -1 extrapolation |
| 2024A&A...689A..41V | ALMA+ACA Band 3 + 4, plus ACT | gNFW (theoretical) and A10/M14 templates (empirical) | M500 and shape terms; calibration, z marginalized | mostly flat; Gaussian on calibration and z | dynesty static nested sampling, Delta ln B = 0.01; Gaussian likelihood on unbinned visibilities | non-relativistic; constant T along line of sight for pseudo-T | Dirac delta, first-order polynomial spectrum, lower uv cut 11 klambda; bright source subtracted |
| 2020A&A...638A..70D | ACA Band 3 | gNFW, fixed shape | M500, z, centroid, source positions and fluxes, flux normalization | normal centroid (sigma 14.3, 15 arcsec); split-normal z; normal flux scale; wide on source flux | Bayesian forward model; sampler n.s.; sigma_eff = sqrt(2 Delta log Z) | non-relativistic; kSZ neglected | Dirac delta, flat spectrum |
| 2019A&A...628A.100D | ALMA+ACA | power-law downstream, gNFW upstream, shock surface | Mach, alpha, shock nose and angle, upstream P and T | split-normal X-ray priors on P_e,us, T_e,us, shock nose and angle; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1, 0.05) | galario + dynesty dynamic nested sampling; medians and 16/84 percentiles | relativistic SZ spectrum applied; kSZ neglected; gamma = 5/3 | n.s. in pack |
| 2016ApJ...829L..23B | ALMA Band 3 (El Gordo relic) | gNFW plus Rankine-Hugoniot pressure boost | pressure amplitude, shock radius, Mach; outer slope marginalized within 30% | X-ray pressure prior for joint fit; others n.s. | MCMC within CASA | n.s. | n.s. |
| 2024A&A...682A.186L | ALMA+ACA (Spiderweb) | 8 gNFW templates: A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT | M500 only; centroid fixed to X-ray | n.s. | dynesty; Bayesian model averaging | relativistic correction negligible (about 1.5% or less) | ordered set of point components for radio galaxy, upper uv cut 65 klambda |
| 2019A&A...629A.104G | ALMA+ACA Band 3, 92 GHz | GNFW templates LeB15, A10, S16, McD14 | mass only | n.s. | uv amplitude profile vs simalma-simulated models, chi2 ranking | n.s.; Compton-y background 1.6e-6 | nine sources subtracted in uv (card: groups, brightest first) |
| 2020PASJ...72...33K | ALMA 12-m + 7-m Band 3 mosaic | image-based; compared with gNFW sample profiles | n.a. (deprojection with X-ray density) | n.a. | tclean multi-scale, natural weighting (card); missing-flux factor 0.94 from simobserve mocks; radial bins inner 0-4 arcsec growing by 1.1 | temperature-dependent correction with projected X-ray T | uvmodelfit on 12-m baselines above 30 klambda (card) |
| 2019MNRAS.487.4037D | ALMA/ACA + Bolocam + Planck | joint forward model (details n.s.) | n.s. | Planck Y_cyl prior (n.s. details) | MCMC (walkers and steps n.s.) | n.s. | n.s. |
| 2020ApJ...891...90R | MUSTANG-2 90 GHz (ALMA minor) | 12 non-parametric bins 5 arcsec to 5 arcmin; A10 gNFW | bin pressures; gNFW parameters | n.s. | emcee with full covariance | kT_e = 7 keV; line of sight to +/- 5 R500 | fitted jointly (details n.s.) |
| 2019MNRAS.490.5134B | ALMA (quasar HE0515-4414) | residual visibilities after positive-source model | 17-parameter positive model | n.s. | GALARIO fits; residuals in 1 klambda bins; tclean residual images | n.s. | modelled then subtracted |
| 2024ApJ...969...56M | ALMA continuum, 10 quasar fields, stacked | stacked decrement converted to y (Sazonov and Sunyaev formulation) | n.a. | n.a. | image stack | pure tSZ; kSZ neglected | masked per field |

=== EVIDENCE PACK (sz-effect, rebuilt) ===
# Evidence pack: Sunyaev-Zeldovich effect measurements (`sz-effect`)

Scope: SZ decrements with ALMA/ACA, pressure profiles, filtering

Built from 21 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2016-2025.
Matcher (regex over analysis steps): `sunyaev|zel'?dovich|\bsz\b|compton[- ]?y|thermal pressure of the (?:icm|intracluster)`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- galaxy_clusters_and_sz: 13
- agn_and_quasars: 6
- protoplanetary_disks: 5
- high_z_galaxies: 3
- astrochemistry: 2
- milky_way_ism: 1
- nearby_galaxies: 1
- cosmology: 1

### Software named in the matched steps
- casa: 6
- dynesty: 4
- emcee: 3
- dali: 2
- astropy: 1
- eddy: 1
- bettermoments: 1
- colossus: 1
- pymc: 1
- radmc-3d: 1
- mathematica: 1
- tclean: 1
- simobserve: 1
- galario: 1
- ciao: 1
- frankenstein: 1
- casa simalma: 1

### Fitting methods (most common phrasings)
- Bayesian; uniform centroid prior across ACA field; wide uninformative mass/slope and point-source priors; split-normal …: 1
- Bayesian model evidence; same SZ priors as the free run, with declination ordering: 1
- Marginalized posterior for M500 and βz; integrated-flux prior reduces spectral degeneracy: 1
- MCMC: 1
- Gaussian fit to continuum emission in the image plane: 1
- MCMC fitting in eddy: 1
- Monte Carlo sampling: 1
- Static nested sampling with dynesty; significance from Bayes factor against null model: 1
- MCMC with PyMC; priors and likelihood not stated: 1
- Normal priors on centroid (sigma 14.3, 15 arcsec); split-normal priors on z; normal prior on flux scaling; wide uninfor…: 1
- Dynamic nested sampling with dynesty; posterior medians and 16/84 percentiles: 1
- Nested sampling with dynesty; priors and likelihood details not stated: 1
- Affine-invariant ensemble MCMC (emcee) with Tripathi et al. priors; special-case modified priors for 10 faint targets, …: 1
- Bayesian inference for mass, concentration, intrinsic shape and equilibrium status: 1
- Multi-probes three-dimensional Bayesian analysis: 1
- emcee MCMC; medians with 16th and 84th percentile uncertainties; priors and likelihood not stated: 1
- emcee MCMC with full covariance likelihood: 1

### Validation checks used
- Test alternate gNFW/point-source priors and observation subsets; both SZ components remain identified.: 1
- Compare Bayesian evidence and inspect raw, model, and residual ACA images; images are display-only.: 1
- Inspect velocity posterior tails and uncertainties; compare masses with the thermal-only fixed-slope estimates.: 1
- Compare predicted and observed core-excised X-ray luminosity and compare ALMA+ACA integrated SZ flux with AdvACT.: 1
- Mock ALMA observations with M=1, 2, 4 shocks: 1
- Compared derived inclination, PA, R90, and dust masses with literature values from Ansdell et al. (2016, 2018), Andrews…: 1
- Subtracted rotation models from peak velocity maps to inspect velocity residuals; ran a grid of models varying PA and i…: 1
- Tested sensitivity to eccentricity prior by comparing e_max = 0.7 and e_max = 0.9: 1
- Residual maps in uv plane; Bayes factor comparisons: 1
- Compared with X-ray, CARMA, ACT catalog masses: 1
- BIC comparison of Model 1 and 2: 1
- Compare model and observed radial profiles and integrated fluxes: 1
- Ionization equilibrium check against Sgr A* plus Wolf-Rayet star ionizing flux: 1
- Compared derived cloud temperatures and hot-region morphology with VLTI/MIDI mid-infrared observations of NGC 1068.: 1
- Assessed flux boosting upper limit (~40% assuming 1.5\sigma noise contribution per source) and tested single central je…: 1
- Checked >50 uv tracks and >20 antenna pairs in shortest bin: 1
- data-free runs show no prior-induced biases: 1
- Compared with dirty-image significance for most significant cluster: 1
- Prior-only run; robustness tests varying gNFW slopes and centroid; residual dirty images: 1
- Model parameters statistically consistent with Di Mascolo et al. 2023; BMA profile used as reference with model varianc…: 1
- Compared with the X-ray spectral kT=2.0 keV of Tozzi et al. 2022b; SZ-derived value lower by a factor of ~3, discussed …: 1
- Observed visibility profiles compared with synthetic data from posterior draws: 1
- Proposed comparison with ΛCDM predictions after correcting geometrical biases: 1
- Good overall agreement within uncertainties: 1
- Order-of-magnitude only: 1
- Convolving the visibility-fit profile with a beam-like Gaussian reproduces the image-plane profile: 1
- Agreement with XMM pressure profile: 1
- FFT approximation vs simalma differs at most ~4%: 1
- y map morphology consistent with X-rays; inner profile agrees with local cool core expectation: 1

### Key parameters and settings (bibcode: value)
- 2021A&A...650A.153D: Free SZ centroid, mass parameter, and inner slope
- 2021A&A...650A.153D: Unresolved sources: point models with power-law spectra
- 2021A&A...650A.153D: Declination ordering for separate modes
- 2021A&A...650A.153D: Also fit a model with all gNFW slopes fixed to the universal pressure profile
- 2021A&A...650A.153D: Fixed universal gNFW slopes; AdvACT cylindrically integrated SZ flux within r500
- 2021A&A...650A.153D: Cylindrical SZ integration aperture: 1.69′, equivalent to AdvACT r500
- 2016ApJ...829L..23B: Free: pressure amplitude, shock radius, Mach number; slopes consistent with X-ray; outer slope marginalized within 30%
- 2016ApJ...829L..23B: Post-shock T_X from 1' region = 16.8 keV
- 2024A&A...682A..55M: 3σ contour threshold for integrated continuum flux and moment map creation
- 2024A&A...682A..55M: robust = 0.0 cube, 1.0 km/s spectral resolution, 3σ threshold; for Sz 65 final fit: fixed inclination = 63.76◦, M_* = 0.76 M_sun, d = 153.1 pc; for Sz 66 fit: …
- 2024A&A...682A..55M: 10^6 Monte Carlo realizations per case; uniform eccentricity priors [0.0, 0.7] and [0.0, 0.9]; mass ratio q = M_Sz65 / M_Sz66 (and inverted for Sz 66)
- 2024A&A...682A..55M: Gap minimum at r = 20 au, ring peak at 24 au, gap width ∆ = 4 au, scaling constant k = 4.5 - 8, stellar mass M_* = 0.76 M_sun
- 2024A&A...689A..41V: Mostly flat priors; Gaussian priors on calibration and redshift
- 2024A&A...689A..41V: Evidence convergence threshold Δln B = 0.01
- 2024A&A...689A..41V: A = 1177.0 km/s, alpha = 0.364
- 2019A&A...623A.150V: baselines up to 800 klambda (Sz 71) and 500 klambda (Sz 98)
- 2019A&A...623A.150V: gamma=1, Rout ~200 AU, f in [0.85,0.99], chi in [0.2,1.0]
- 2019A&A...623A.150V: Sz 71: logL(912-1100A)=-5.2 (M1), -4.1 (M2); Sz 98: -3.4
- 2019Natur.570...83M: T=1e4 K, emissivity 1.25e-31 erg/s cm^3, D=8 kpc, Rmax=0.23 arcsec, Rmin=0.07 arcsec
- 2021MNRAS.503.1459B: Accretion rate M_dot = 0.2 M_sun/year (from L_bol = 5.65 x 10^44 erg/s); image grid = 100 x 100 cells; epsilon_cl = 0.01 and 0.025; theta = 45 deg
- 2020A&A...638A..70D: free: M500, z, centroid, point source positions and fluxes, flux normalization
- 2020A&A...638A..70D: sigma_eff >~ 3 indicates robust detection
- 2019A&A...628A.100D: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05)
- 2025ApJ...989....7T: 4 parameters per disk (M0, R0, generalized alpha, wind mass-loss parameter); MHD model adds omega
- 2025ApJ...989....7T: Inner disk radius 0.1 au
- 2025ApJ...989....7T: Disk dispersed when stellar accretion rate falls below 1e-12 Msun/yr
- 2025ApJ...989....7T: Total photoevaporative mass-loss rate is a free parameter scaling the Picogna et al. 2021 profile
- 2025ApJ...989....7T: MHD analytical solution with alpha_SS = 0, constant lambda and constant alpha_DW across the disk
- 2024A&A...682A.186L: uv upper threshold 65 klambda
- 2024A&A...682A.186L: SZ centroid fixed to X-ray centroid so that only the mass term (M500) is free per pressure model
- 2018ApJ...865..157A: x = 0.68 encircled luminosity fraction
- 2018ApJ...865..157A: L_mm = F_nu (d/140)^2 s
- 2025A&A...694A.147G: uv range limits: 2000 klambda (BP Tau, DL Tau, DR Tau, Sz 98, V1094 Sco), 3000 klambda (CI Tau, GW Lup), 1500 klambda (IQ Tau)
- 2025A&A...694A.147G: Binned visibility widths of 10-20 klambda
- 2025A&A...694A.147G: Only continuum spectral windows for DR Tau, GW Lup, Sz 98 (lower uncertainties) and DL Tau; all spectral windows (lines masked) for the others
- 2025A&A...694A.147G: Minimum number of additional Gaussians giving a good fit to visible features
- 2025A&A...694A.147G: MCMC iterations: 2500 (round 1), 10,000 (round 2), final 5000 used for posterior medians
- 2020ApJ...891...90R: relativistic correction with kT_e = 7 keV; line of sight integration to ±5 R500
- 2019A&A...629A.104G: Compton-y background 1.6e-6
- 2020PASJ...72...33K: Geometrically spaced bins, innermost 0-4 arcsec, size increasing by a factor 1.1


### Assumptions (bibcode: value)
- 2021A&A...650A.153D: Isothermal ICM; thermal SZ relativistic correction from Itoh2004
- 2021A&A...650A.153D: Flat Λ Cold Dark Matter: ΩM=0.30, ΩΛ=0.70, H0=70.0 km s−1 Mpc−1
- 2021A&A...650A.153D: Do not model the extended radio source; extrapolate it with α=−1 to check contamination
- 2021A&A...650A.153D: M500 parametrization assumes a self-similar pressure profile under hydrostatic equilibrium
- 2021A&A...650A.153D: Evidence-to-significance conversion assumes a Gaussian posterior and neglects changes in prior volume
- 2021A&A...650A.153D: Isothermal ICM; Nozawa2006 relativistic corrections; neglect primary CMB anisotropies
- 2021A&A...650A.153D: Use universal-profile masses for the predicted X-ray luminosity
- 2016ApJ...829L..23B: p_down/p_up = (5M^2-1)/4
- 2016ApJ...829L..23B: Upstream X-ray density and temperature measurements independent
- 2024A&A...682A..55M: Optically thin thermal dust emission, distance d = 153 pc (Sz 65) and 154.4 pc (Sz 66), midplane temperature T = 20 K, dust opacity κ_ν = 0.1 (ν/10^12 Hz)^β cm…
- 2024A&A...682A..55M: Keplerian rotation; for Sz 65 an azimuthally symmetric elevated emission surface z(r) = z0 * (r/1'')^ψ * exp(-(r/r_taper)^q_taper)
- 2024A&A...682A..55M: Disc midplane lies on the binary orbital plane; uniform eccentricity distribution; sin(i) orbital inclination distribution
- 2024A&A...682A..55M: Low disc viscosity (α < 0.01); gap width scales with planet Hill radius
- 2024A&A...689A..41V: Unresolved sources are point-like with first-order polynomial spectral behaviour
- 2024A&A...689A..41V: Cosmology Planck2014_XIII, H0=67.7, Om=0.307; non-relativistic SZ (relativistic corrections neglected)
- 2024A&A...689A..41V: ACT and ALMA+ACA likelihoods independent
- 2024A&A...689A..41V: Local scaling relations of Arnaud2010 used for Y to M500
- 2024A&A...689A..41V: Constant temperature along line of sight
- 2019A&A...623A.150V: gas surface density = 100 x dust
- 2019A&A...623A.150V: R_V=3.1, A_V=0.5 (Sz 71), 1.0 (Sz 98)
- 2019A&A...623A.150V: UV excess varied up to factor 10 from accretion-based estimate
- 2019Natur.570...83M: Alpha = 0.1, chi = 1 (uniform disk) or 1/4 (cloudlets), cloudlet radius r = 1e-3 Rmax
- 2021MNRAS.503.1459B: Standard geometrically thin, optically thick accretion disk; spherical clouds in thermodynamic equilibrium with disk radiation absorbed over half their surface…
- 2021MNRAS.503.1174K: Jet spectral index \alpha = -1.04 \pm 0.03 (explored range -0.7 to -1.5, and -1.2); cavity energy E_cav = 4pV; Lorentz factor 10^3 - 10^5 and photon index 2 fo…
- 2024ApJ...969...56M: pure thermal SZE; kSZE neglected
- 2020A&A...638A..70D: non-relativistic tSZ, kSZ neglected, flat ΛCDM Ωm=0.30 H0=70
- 2019A&A...628A.100D: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected
- 2025ApJ...989....7T: T proportional to R^-1/2 and aspect ratio 3.33e-2 (M*/1 Msun)^-1/2 at 1 au
- 2025ApJ...989....7T: Isolated disks, no envelope or streamer feeding; t=0 is the end of Class I
- 2025ApJ...989....7T: alpha_SS constant in time and radius; photoevaporative mass-loss rate constant in time
- 2025ApJ...989....7T: External UV irradiation neglected
- 2024A&A...682A.186L: Eight literature gNFW pressure profiles considered (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT)
- 2024A&A...682A.186L: Ideal gas law; relativistic SZ correction negligible (<~1.5%); X-ray spectral temperature not used
- 2018ApJ...865..157A: Distances from Gaia DR2 with uniform d prior
- 2020EPJWC.22800009E: Three-dimensional triaxial ellipses for gas and total mass
- 2019MNRAS.487.4037D: Overpressurized sphere radius ~90 kpc, offset ~130 kpc; adiabatic index 5/3
- 2025A&A...694A.147G: Literature inclinations and position angles (BP Tau from IMFIT)
- 2020ApJ...891...90R: spherical symmetry
- 2019A&A...629A.104G: Spherical models; M200 extrapolated from M500 assuming GNFW mass distribution
- 2020PASJ...72...33K: M500 = 8.8e14 h^-1 Msun, r500 = 0.92 h^-1 Mpc at z = 0.597


### Limitations the authors admit
- 2021A&A...650A.153D: Chandra source counts do not constrain the ICM temperature distribution.
- 2021A&A...650A.153D: Most X-ray hardness structures have low significance.
- 2021A&A...650A.153D: Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map.
- 2021A&A...650A.153D: SZ masses may be biased by nonhydrostatic gas and mass–inner-slope degeneracy.
- 2021A&A...650A.153D: Limited spectral coverage leaves thermal and kinetic SZ strongly degenerate.
- 2021A&A...650A.153D: Interferometric filtering favors compact, low-mass pressure models and limits extrapolation to large scales.
- 2021A&A...650A.153D: Weak-lensing positional precision limits confidence in the southern gas–mass offset.
- 2021A&A...650A.153D: Dust mass and temperature require better high-frequency observations.
- 2016ApJ...829L..23B: Short-spacing problem makes Mach number anti-correlated with pressure normalization
- 2016ApJ...829L..23B: Pre-shock temperature unconstrained in Chandra data
- 2024A&A...682A..55M: 12CO (2-1) was not robustly detected at native resolution, requiring a 0''.07 uv taper and spectral averaging to 1 km/s, which limits sensitivity to small-scale velocity perturbations, disc warping, …
- 2024A&A...682A..55M: Continuum oversubtraction reduces 12CO brightness near the line centre along the minor axis, limiting searches for inner-outer disc misalignments.
- 2024A&A...682A..55M: Low SNR on the longest baselines makes the tentative ~6 au feature in the Sz 65 frank fit uncertain, and the ~3-4 au beam barely reaches the expected pressure scale height H ≤ 2.7 au in the inner dis…
- 2024A&A...682A..55M: Low SNR and poorer spatial resolution of 12CO in Sz 66 (located towards the primary beam edge) prevent reliable kinematic constraints and lead to large relative uncertainties in gas disc size.
- 2024A&A...689A..41V: Lack of short baselines makes beta–P0 degeneracy and template discrimination weak; gNFW poorly suited for filaments
- 2019A&A...623A.150V: Model absolute fluxes uncertain by a factor of a few; UV excess and accretion-to-UV conversion uncertain by up to an order of magnitude
- 2019Natur.570...83M: Line could be unlucky combination of molecular lines or foreground absorption
- 2021MNRAS.503.1459B: The torus-to-SMBH mass ratio is fixed to M_torus/M_smbh = 0.02 rather than varied as a free parameter.
- 2021MNRAS.503.1459B: Simulations assume a dissipationless system and neglect cloud collisions and tidal shearing/merging.
- 2021MNRAS.503.1459B: Radiation pressure on cloud dynamics near the accretion disk is neglected.
- 2021MNRAS.503.1459B: Temperature distribution model uses a simple blackbody equilibrium approximation and neglects radiative transfer in a dusty medium within the torus.
- 2021MNRAS.503.1174K: Small sample size of 10 cluster galaxies prevents detection of subtle deviations in the q_TIR vs M_* relation
- 2021MNRAS.503.1174K: Radio luminosity and cavity power estimates depend strongly on the unknown radio spectral index, which cannot be tightly constrained without deeper low-frequency observations
- 2021MNRAS.503.1174K: Low S/N (4\sigma) of the diffuse X-ray ICM emission prevents direct detection of X-ray cavities, measurement of cluster binding energy, or precise localisation of the X-ray peak
- 2021MNRAS.503.1174K: Possible flux boosting of up to ~40% in the faint radio-jet flux measurements
- 2019MNRAS.490.5134B: Only dof=1 for short baselines; limited SNR prevents 2D fitting
- 2024ApJ...969...56M: Halo mass estimate from Lya gas dynamics is uncertain
- 2024ApJ...969...56M: tSZE cannot be separated from kSZE without deep observations at other frequencies
- 2024ApJ...969...56M: Stack insensitive to non-spherically symmetric kSZE
- 2024ApJ...969...56M: Best-fitting model chi-square similar to zero signal
- 2020A&A...638A..70D: Limited angular dynamic range, short integrations and unresolved-source contamination limit mass inference
- 2019A&A...628A.100D: Systematics from cluster geometry and complex post-shock gas distribution; model does not capture X-ray morphology
- 2025ApJ...989....7T: Order of fitting matters because no parameter set fits all constraints
- 2025ApJ...989....7T: Disk mass is the most uncertain constraint; Ophiuchus and Lupus/Upper Sco masses come from slightly different approaches
- 2025ApJ...989....7T: Upper Sco median accretion rate is an upper limit because half the sample has upper limits
- 2025ApJ...989....7T: External photoevaporation and multiplicity are neglected; Upper Sco is the only old-region reference
- 2024A&A...682A.186L: Diffuse emission within 2 arcsec of the AGN is not observationally constrained
- 2024A&A...682A.186L: SZ normalisation may be underestimated because of interferometric filtering of large scales
- 2024A&A...682A.186L: Low significance of SZ and X-ray signals limits detailed morphological comparison
- 2024A&A...682A.186L: ICM metallicity practically unconstrained
- 2018ApJ...865..157A: Resolution insufficient to constrain depression in HK Lup; tentative values
- 2018ApJ...865..157A: Lupus multiplicity not thoroughly vetted
- 2020EPJWC.22800009E: ALMA and NIKA2 images are very preliminary.
- 2020EPJWC.22800009E: Missing high-resolution SZ data at radial scales from 30 to 100 arcsec.
- 2020EPJWC.22800009E: More sensitive observations and a larger cluster sample are needed.
- 2019MNRAS.487.4037D: Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations
- 2025A&A...694A.147G: Small sample limits statistical conclusions
- 2025A&A...694A.147G: Resolution differences between targets may change apparent gap depth
- 2025A&A...694A.147G: Ages are highly uncertain
- 2025A&A...694A.147G: Lowest-resolution ALMA data give larger residuals; higher resolution would improve fits
- 2020ApJ...891...90R: Outermost pressure bin likely biased low; unquantified additional systematic
- 2019A&A...629A.104G: Residual positive signal from undetected sources means significance is conservative; S/N too low to strongly constrain pressure models
- 2020PASJ...72...33K: Equation-of-state limit is weak
- 2020PASJ...72...33K: Absolute values of the X-ray pseudo pressure are arbitrary
- 2020PASJ...72...33K: Temperature at r > 250 kpc cannot be constrained by the ALMA data
- 2020PASJ...72...33K: X-ray-only deprojection includes statistical errors only

### Settings cards flag as needed but not stated
- casa version: 2
- alma/aca calibrated measurement-set release identifiers, calibration casa/pipeline versions, and an…: 1
- exact visibility likelihood, visibility-weight treatment, and implementation of the 5% flux-calibra…: 1
- forward-model map grid, line-of-sight integration limits, primary-beam model, and frequency integra…: 1
- numerical fixed gnfw parameters and the complete pressure-to-mass normalization inherited from arna…: 1
- sampling configuration, stopping criteria, convergence diagnostics, and reproducible model-evidence…: 1
- exact modified power-law equation and the dust-model parameter priors.: 1
- numerical herschel upper limits, aperture sizes, backgrounds, and likelihood treatment of nondetect…: 1
- functional form and uncertainty treatment of the advact integrated-flux prior.: 1
- x-ray spectral model, abundance and absorption choices, fitting statistic, extraction regions, and …: 1
- exact compact-source subtraction models and diffuse-emission apertures used in the radio analysis.: 1
- additional flagging details for the alma data: 1
- specifics of the mcmc-in-casa uv-fitting code, sampler and priors: 1
- casa and ciao versions (only caldb 4.7.1 given): 1
- clean parameters (cell, size, masking, threshold): 1
- gnfw parameter values and priors on amplitude, shock radius, mach number: 1
- binning of chandra profile and x-ray temperature fitting details: 1
- priors for the radio/b-field calculation and cooling assumptions: 1
- exact upstream-temperature scaling chain: 1
- exact cell (pixel) size and image dimensions (imsize) used in clean for both continuum and 12co cub…: 1
- exact solution intervals (solint) and number of rounds for phase self-calibration of projects 2018.…: 1
- exact channel ranges flagged as line-containing when averaging line-free channels for continuum: 1
- parameters used to generate the keplerian mask during 12co cleaning: 1
- continuum subtraction task and polynomial order (e.g. uvcontsub) used before imaging 12co: 1
- exact value of the wsmooth hyperparameter used in the final frank fits: 1
- priors, number of walkers, and number of steps used in the eddy mcmc fitting: 1
- exact alma/aca uv-selection, channel binning and weights used in the visibility fits: 1
- dynesty settings (live points, bounding, sampling): 1
- exact act dr6 map products, beams, transfer functions and cutout size: 1
- tapering and tclean parameters for display images: 1
- how evidence-weighted mass average across models is computed: 1
- y-to-m500 conversion implementation details: 1
- band 4 point-source model details and line-channel ranges removed: 1
- line-free channels / continuum subtraction method for cn cubes: 1
- detection criterion (s/n threshold) for the 36 detections: 1
- casa version used for imaging and self-calibration (only imfit 4.3.1 given): 1
- image size and cell size: 1
- exact aperture sizes and per-source fluxes in the full table: 1
- dali input files, full chemistry settings and grid spacing: 1
- mcmc priors, walkers and chain length for the uv fits: 1

## Paper excerpts (21 of 21, chosen for detail and spread over fields/years)

### 2021A&A...650A.153D: Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger at z ≃ 1.13 (2021; galaxy_clusters_and_sz, agn_and_quasars; archival_reuse)
- question: Reconstruct the intracluster pressure distribution and investigate the merger and diffuse radio emission in SPT-CL J2106-5844.
- step 5: Search for SZ pressure peaks and compact contamination
  - method: Jointly forward-model Band 3/4 ALMA+ACA visibilities; project a gNFW pressure model and sample its Fourier transform at measured uv coordinates; search for point sources. [SZ modeling: "the reconstruction method is devised to sample the Fourier transform of a map of the SZ effect from a model galaxy cluster to the $u\varv$-plane coordinates of the sampled visibilities."] [Free modeling run: "is obtained by numerical integration of a generalized Navarro-Frenk-White (cite: Nagai2007) pressure profile along the line-of-sight direction"]
  - parameter: Free SZ centroid, mass parameter, and inner slope [Free modeling run: "We perform a first modeling run assuming the universal parametrization by (cite: Arnaud2010) but allow the model centroid, mass parameter, and slope at small radii to vary."]
  - parameter: Unresolved sources: point models with power-law spectra [Free modeling run: "we use point source models to describe the contamination from unresolved compact sources with flux characterized by a simple power-law spectral dependence."]
  - assumption: Isothermal ICM; thermal SZ relativistic correction from Itoh2004 [SZ modeling: "We compute the average relativistic corrections to the thermal SZ spectrum by means of the approximation by (cite: Itoh2004)."] [SZ modeling: "Given the large uncertainties on the temperature distribution, we assume this to be described by an isothermal model"]
  - assumption: Flat Λ Cold Dark Matter: ΩM=0.30, ΩΛ=0.70, H0=70.0 km s−1 Mpc−1 [Introduction: "Throughout this work, we assume a spatially flat $\Lambda$ Cold Dark Matter cosmological model, with $\Omega_{\mathrm{M}}=0.30$, $\Omega_{\Lambda}=0.70$, and $H_0=70.0~\mathrm{km\,s^{-1}\,Mpc^{-1}}$."]
  - assumption: Do not model the extended radio source; extrapolate it with α=−1 to check contamination [Free modeling run: "We do not consider any model component to describe the extended radio source, which should not significantly contaminate the measured SZ signal."] [Free modeling run: "by assuming a power law spectrum with average spectral index $\alpha=-1$"]
  - fitting: Bayesian; uniform centroid prior across ACA field; wide uninformative mass/slope and point-source priors; split-normal temperature prior from the X-ray estimate. [Free modeling run: "The centroid coordinates are assumed to have a uniform prior extending over the field of view of ACA, while we consider wide uninformative priors for both the mass and slope parameters."] [Free modeling run: "Uninformative priors are assumed for the position, amplitude, and spectral index."]
  - validation: Test alternate gNFW/point-source priors and observation subsets; both SZ components remain identified. [Free modeling run: "checked that the two SZ components are identified independent of any prior assumptions on the gNFW parameters or point-like component, or of the specific subsets of observations employed in the modeling."]
- step 6: Fit two SZ components and compare model evidence
  - method: Fit two universal-profile SZ components plus a central point source with modified power-law spectrum; compare against zero- and one-SZ-component models. [Multicomponent model: "we repeat the analysis this time including two separate SZ components along with the point-like feature with a modified power-law spectrum describing the central radio source."] [Multicomponent model: "Again, we assume a universal profile (cite: Arnaud2010) with free mass parameter and inner slope for each of the SZ model components."]
  - parameter: Declination ordering for separate modes [Multicomponent model: "in order to enforce the identifiability of the separate modes, we introduce an ordering condition on their declinations as detailed in Appendix A2 of (cite: Handley2015)."]
  - parameter: Also fit a model with all gNFW slopes fixed to the universal pressure profile [Multicomponent model: "when fixing all the gNFW slopes to the values for the universal pressure profile in (cite: Arnaud2010)"]
  - assumption: M500 parametrization assumes a self-similar pressure profile under hydrostatic equilibrium [Multicomponent model: "the presence of $M_{500}$ in our parameter set follows from the specific parametrization adopted by (cite: Arnaud2010) to get a self-similar pressure profile under the assumption of hydrostatic equilibrium."]
  - assumption: Evidence-to-significance conversion assumes a Gaussian posterior and neglects changes in prior volume [Multicomponent model: "is performed under the assumption of a Gaussian posterior distribution and neglecting any change in the prior volume due to the difference in the parameter sets between the models with and without the thermal SZ components."]
  - fitting: Bayesian model evidence; same SZ priors as the free run, with declination ordering [Multicomponent model: "We consider the same uniform priors as in Sect. [3.2.1](#sec:res:sz:onesz) for each of the SZ components."] [Multicomponent model: "the inclusion of the two-component model for the thermal SZ effect from SPT-CL J2106-5844 is found to improve the Bayesian log-evidence by $\Delta\log\mathcal{Z}=120.72\pm0.16$"]
  - validation: Compare Bayesian evidence and inspect raw, model, and residual ACA images; images are display-only. [Multicomponent model: "Also, two components are found to be preferred over one SZ model at the $\sim9.9\sigma$ level."] [Multicomponent model: "the reconstructed images of the raw, best-fit model, and corresponding residual interferometric data"]
- step 8: Test for kinetic SZ contributions
  - method: Add kinetic SZ terms to both subclusters and fit mass and line-of-sight velocity with an integrated-SZ-flux prior. [Constraining the kinetic SZ signal: "a multicomponent model analogous to the one introduced in the previous section but including a kinetic SZ term for both the subclusters."] [Constraining the kinetic SZ signal: "Further, we introduced a prior on the integrated SZ flux in order to break (or, at least, reduce) the degeneracy between the thermal and kinetic spectral components of the SZ signal."]
  - parameter: Fixed universal gNFW slopes; AdvACT cylindrically integrated SZ flux within r500 [Constraining the kinetic SZ signal: "we restricted the analysis to the case with all the slopes of the gNFW pressure distributions fixed to the values for the universal pressure model (cite: Arnaud2010)."] [Constraining the kinetic SZ signal: "we considered the estimate of the cylindrically integrated SZ flux within $r_{500}$"]
  - assumption: Isothermal ICM; Nozawa2006 relativistic corrections; neglect primary CMB anisotropies [Constraining the kinetic SZ signal: "Under the same assumption adopted in the previous section of an isothermal model"] [Constraining the kinetic SZ signal: "and is computed according to the approximation provided by (cite: Nozawa2006)."]
  - fitting: Marginalized posterior for M500 and βz; integrated-flux prior reduces spectral degeneracy [Constraining the kinetic SZ signal: "the marginalized posterior for the main parameters — the mass $M_{500}$ and the line-of-sight component of the peculiar velocity in units of the speed of light $\beta_{\mathrm{z}}$"]
  - validation: Inspect velocity posterior tails and uncertainties; compare masses with the thermal-only fixed-slope estimates. [Constraining the kinetic SZ signal: "the determination of the best-fit value of the parameter is driven by the high $\beta_{\mathrm{z}}$ tail of the posterior distribution."] [Constraining the kinetic SZ signal: "systematically lower but consistent with the estimates reported in the previous section considering the same universal profile slopes."]
- step 10: Compare gas, mass, galaxies, and merger scenarios
  - method: Compare SZ peaks with weak lensing, X-ray brightness/hardness, BCG and galaxy redshifts; predict X-ray luminosity from SZ masses. [Discussion: "provides a comparative view of the SZ signature of SPT-CL J2106-5844 (both model and dirty image) with the weak lensing and X-ray surface brightness distribution in the cluster."] [Discussion: "one can predict the X-ray luminosities of the two substructures using the scaling relation from (cite: Mantz2016)."]
  - parameter: Cylindrical SZ integration aperture: 1.69′, equivalent to AdvACT r500 [The dynamics of the ICM substructures: "The reported SZ flux density is computed as the cylindrically integrated SZ signal within an aperture of $1.69\ensuremath{'}$, equivalent to the AdvACT estimate for SPT-CL J2106-5844’s $r_{500}$."]
  - assumption: Use universal-profile masses for the predicted X-ray luminosity [Discussion: "When considering the masses estimated under the assumption of a universal pressure model"]
  - validation: Compare predicted and observed core-excised X-ray luminosity and compare ALMA+ACA integrated SZ flux with AdvACT. [Discussion: "lower than the corresponding value of $20.5\substack{+1.0\\-1.0}\cdot10^{44}~\mathrm{erg~s^{-1}}$ measured from the core-excised X-ray observations"] [The dynamics of the ICM substructures: "lower than the measurement $4.7\substack{+1.1\\-1.3}\cdot 10^{-4}~\mathrm{arcmin^2}$ inferred from the AdvACT catalog (cite: Hilton2020)."]
- result: Two-SZ-component log-evidence improvement over no SZ = 120.72 ± ±0.16 dimensionless [Multicomponent model: "improve the Bayesian log-evidence by $\Delta\log\mathcal{Z}=120.72\pm0.16$ with respect to the model without any SZ components"]
- result: SZ detection significance relative to null model = 15.6 ± not stated σ [Multicomponent model: "roughly corresponding to a $15.6\sigma$ detection in comparison to the null model."]
- result: Preference for two SZ components over one = ∼9.9 ± not stated σ [Multicomponent model: "Also, two components are found to be preferred over one SZ model at the $\sim9.9\sigma$ level."]
- result: Northern SZ component M500, free inner slope = 2.60 × 10^14 ± +0.57/-0.54 × 10^14 M⊙ [Multicomponent model: "$2.60\substack{+0.57\\-0.54}\cdot 10^{14}~\mathrm{M_{\odot}}$"]
- result: Southern SZ component M500, free inner slope = 1.34 × 10^14 ± +0.52/-0.52 × 10^14 M⊙ [Multicomponent model: "$1.34 \substack{+0.52\\-0.52}\cdot 10^{14}~\mathrm{M_{\odot}}$"]
- result: Northern SZ component inner slope = 0.47 ± +0.11/-0.12 dimensionless [Multicomponent model: "$0.47\substack{+0.11\\-0.12}$"]
- result: Southern SZ component inner slope = 0.86 ± +0.25/-0.24 dimensionless [Multicomponent model: "$0.86\substack{+0.25\\-0.24}$"]
- result: Northern SZ component mass, fixed universal slopes = 3.10 × 10^14 ± +0.10/-0.10 × 10^14 M⊙ [Multicomponent model: "we obtain masses of $3.10\substack{+0.10\\-0.10} \cdot 10^{14}~\mathrm{M_{\odot}}$ and $3.26\substack{+0.25\\-0.25} \cdot 10^{14}~\mathrm{M_{\odot}}$ for the northern and southern SZ components, respectively."]
- result: Southern SZ component mass, fixed universal slopes = 3.26 × 10^14 ± +0.25/-0.25 × 10^14 M⊙ [Multicomponent model: "we obtain masses of $3.10\substack{+0.10\\-0.10} \cdot 10^{14}~\mathrm{M_{\odot}}$ and $3.26\substack{+0.25\\-0.25} \cdot 10^{14}~\mathrm{M_{\odot}}$ for the northern and southern SZ components, respectively."]
- result: Central source flux at 5 GHz, multicomponent fit = 0.690 ± +0.037/-0.037 mJy [Multicomponent model: "$0.690\substack{+0.037\\-0.037}~\mathrm{mJy}$"]
- result: Central source spectral index, modified power law = -1.10 ± +0.05/-0.05 dimensionless [Multicomponent model: "$-1.10\substack{+0.05\\-0.05}$"]
- result: Central source spectral curvature = 0.123 ± +0.022/-0.022 dimensionless [Multicomponent model: "$0.123\substack{+0.022\\-0.022}$"]
- result: Northern component βz = 1.7 × 10^-2 ± +2.0/-1.5 × 10^-2 dimensionless [Constraining the kinetic SZ signal: "We measure values for $\beta_{\mathrm{z}}$ of $1.7\substack{+2.0\\-1.5}\cdot10^{-2}$ and $0.2\substack{+2.0\\-0.8}\cdot10^{-2}$ for the northern and southern SZ features, respectively"]
- result: Southern component βz = 0.2 × 10^-2 ± +2.0/-0.8 × 10^-2 dimensionless [Constraining the kinetic SZ signal: "We measure values for $\beta_{\mathrm{z}}$ of $1.7\substack{+2.0\\-1.5}\cdot10^{-2}$ and $0.2\substack{+2.0\\-0.8}\cdot10^{-2}$ for the northern and southern SZ features, respectively"]
- result: Northern component line-of-sight velocity = 5088 ± +6092/-4435 km s−1 [Constraining the kinetic SZ signal: "equivalent to line-of-sight velocities of $5088\substack{+6092\\-4435}~\mathrm{km~s^{-1}}$ and $463\substack{+6027\\-2538}~\mathrm{km~s^{-1}}$."]
- result: Southern component line-of-sight velocity = 463 ± +6027/-2538 km s−1 [Constraining the kinetic SZ signal: "equivalent to line-of-sight velocities of $5088\substack{+6092\\-4435}~\mathrm{km~s^{-1}}$ and $463\substack{+6027\\-2538}~\mathrm{km~s^{-1}}$."]
- result: Northern component mass with kinetic SZ = 2.26 × 10^14 ± +0.83/-0.72 × 10^14 M⊙ [Constraining the kinetic SZ signal: "the inclusion of the kinetic SZ term causes a variation in the masses to $2.26\substack{+0.83\\-0.72}\cdot10^{14}~\mathrm{M_{\odot}}$"]
- result: Predicted total X-ray luminosity, universal-profile SZ masses = 11.4 × 10^44 ± +2.1/-1.8 × 10^44 erg s−1 [Discussion: "this leads to the total X-ray luminosity in the $0.1-2.4~\mathrm{keV}$ band of $11.4\substack{+2.1\\-1.8}\cdot10^{44}~\mathrm{erg~s^{-1}}$"]
- result: Measured core-excised X-ray luminosity, 0.1-2.4 keV comparison = 20.5 × 10^44 ± +1.0/-1.0 × 10^44 erg s−1 [Discussion: "the corresponding value of $20.5\substack{+1.0\\-1.0}\cdot10^{44}~\mathrm{erg~s^{-1}}$ measured from the core-excised X-ray observations"]
- result: Northern SZ centroid offset from BCG = around 24 ± not stated kpc [The dynamics of the ICM substructures: "We measure an offset of around $24~\mathrm{kpc}$ and $69~\mathrm{kpc}$ between the reconstructed SZ centroid and, respectively, the BCG and X-ray peak."]
- result: Northern SZ centroid offset from X-ray peak = 69 ± not stated kpc [The dynamics of the ICM substructures: "We measure an offset of around $24~\mathrm{kpc}$ and $69~\mathrm{kpc}$ between the reconstructed SZ centroid and, respectively, the BCG and X-ray peak."]
- result: Southern SZ peak offset from weak-lensing component = >50 ± not stated kpc [Discussion: "We observe a moderate offset ($>50~\mathrm{kpc}$) between the southern SZ peak and the corresponding weak-lensing component"]
- result: Cylindrically integrated model SZ signal within 1.69′, free inner slopes = 2.17 × 10^-4 ± +0.26/-0.18 × 10^-4 arcmin² [The dynamics of the ICM substructures: "for our SZ model of $2.17\substack{+0.26\\-0.18}\cdot10^{-4}~\mathrm{arcmin^2}$"]
- result: Cylindrically integrated model SZ signal within 1.69′, universal pressure model = 3.01 × 10^-4 ± +0.74/-0.77 × 10^-4 arcmin² [The dynamics of the ICM substructures: "($3.01\substack{+0.74\\-0.77}\cdot10^{-4}~\mathrm{arcmin^2}$ in the case of universal pressure model)"]
- limitation (authors): Chandra source counts do not constrain the ICM temperature distribution. [Chandra: "The low number of source counts in the available *Chandra* data did not allow for deriving significant constraints on the temperature distribution of the ICM within SPT-CL J2106-5844."]
- limitation (authors): Most X-ray hardness structures have low significance. [Chandra: "aside from the bright core region, it is not possible to identify any structure with a significance higher than $2\sigma$."]
- limitation (authors): Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map. [Diffuse emission: "the different angular resolutions of the available radio data, combined with the severe sparsity and low significance of the observations at high frequencies, do not allow for building a detailed map of the spectral index distribution"]
- not stated (card): ALMA/ACA calibrated measurement-set release identifiers, calibration CASA/pipeline versions, and any additional flagging or averaging.; Exact visibility likelihood, visibility-weight treatment, and implementation of the 5% flux-calibration uncertainty.; Forward-model map grid, line-of-sight integration limits, primary-beam model, and frequency integration across spectral windows.; Numerical fixed…

### 2016ApJ...829L..23B: ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe (2016; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can ALMA SZ measurements detect the pressure discontinuity of a merger shock at the NW radio relic of El Gordo, and what Mach number and relic magnetic field result when combined with Chandra and ATCA data?
- step 3: Fit SZ shock model to ALMA uv-data
  - method: GNFW pressure plus R-H pressure boost at shock radius, fit directly to visibilities by MCMC within CASA [2.3 ALMA-SZ data: "This is done using an MCMC method within CASA and is computationally expensive, due to the large data volume."]
  - software: CASA
  - parameter: Free: pressure amplitude, shock radius, Mach number; slopes consistent with X-ray; outer slope marginalized within 30% [2.3 ALMA-SZ data: "leaving the pressure amplitude, shock radius and the Mach number as free parameters"]
  - assumption: p_down/p_up = (5M^2-1)/4 [2.3 ALMA-SZ data: "$p_{\mathrm{down}}/p_{\mathrm{up (GNFW)}} = (5{\cal M}^2 -1)/4$"]
  - fitting: MCMC [2.3 ALMA-SZ data: "This is done using an MCMC method within CASA"]
  - validation: Mock ALMA observations with M=1, 2, 4 shocks [2.3 ALMA-SZ data: "We make extensive simulations for mock ALMA observations"]
- step 4: Joint SZ/X-ray Mach number
  - method: Derive pre-shock pressure prior from X-ray density and temperature (upstream T scaled from downstream T via R-H) and apply to SZ fit [3.3 Joint SZ/X-Ray modeling: "we scale from the downstream $T_\mathrm{X}$ value using the Mach number in a chain, from the R-H condition for temperature jump."]
  - parameter: Post-shock T_X from 1' region = 16.8 keV [3.3 Joint SZ/X-Ray modeling: "The post-shock temperature is measured from a wider $1{^{\prime}}$ region ($T_\mathrm{X} = 16.8^{+2.4}_{-1.8}$ keV)"]
  - assumption: Upstream X-ray density and temperature measurements independent [3.3 Joint SZ/X-Ray modeling: "we use a pressure prior assuming the upstream X-ray density and temperature measurements are independent"]
- result: SZ shock radius = 870 ± +14/-13 kpc [3.1 SZ shock modeling: "$r_{\mathrm{sh}}=870^{+14}_{-13}$ kpc"]
- result: Mach number from SZ alone = 1.4 ± +1.2/-0.2 dimensionless [3.1 SZ shock modeling: "${\cal M}= 1.4^{+1.2}_{-0.2}$, supporting ${\cal M}> 1$ at more than $98\%$ confidence"]
- result: Mach number SZ with weak-lensing mass prior = 1.5 ± +0.5/-0.2 dimensionless [3.1 SZ shock modeling: "reduces the errors to ${\cal M}= 1.5^{+0.5}_{-0.2}$"]
- result: Joint SZ/X-ray Mach number = 2.4 ± +1.3/-0.6 dimensionless [3.3 Joint SZ/X-Ray modeling: "${\cal M}= 2.4^{+1.3}_{-0.6}$"]
- result: Post-shock temperature = 16.8 ± +2.4/-1.8 keV [3.3 Joint SZ/X-Ray modeling: "$T_\mathrm{X} = 16.8^{+2.4}_{-1.8}$ keV"]
- limitation (authors): Short-spacing problem makes Mach number anti-correlated with pressure normalization [2.3 ALMA-SZ data: "its amplitude is anti-correlated with the pressure normalization. This is an inherent limitation of the current ALMA observation"]
- limitation (authors): Pre-shock temperature unconstrained in Chandra data [3 Results and Discussion: "the pre-shock temperature in this high-$z$ object remains unconstrained due to the high background-to-cluster photon ratio"]
- not stated (card): Additional flagging details for the ALMA data; Specifics of the MCMC-in-CASA uv-fitting code, sampler and priors; CASA and CIAO versions (only CALDB 4.7.1 given); CLEAN parameters (cell, size, masking, threshold); GNFW parameter values and priors on amplitude, shock radius, Mach number; Binning of Chandra profile and X-ray temperature fitting details; Priors for the radio/B-field calculation and …

### 2024A&A...682A..55M: High-resolution ALMA observations of compact discs in the wide-binary system Sz 65 and Sz 66 (2024; protoplanetary_disks; observational_alma_primary)
- question: Whether compact protoplanetary discs around the wide-binary stars Sz 65 and Sz 66 exhibit substructures on spatial scales of ~4 au
- step 2: Measure image-plane continuum and CO fluxes, disc geometry, radial profiles, R90 sizes, spectral indices, and dust masses
  - method: 2D Gaussian fitting in the image plane for PA and inclination, deprojecting and azimuthally averaging surface brightness for 1D profiles and cumulative 90% flux radii (R90), integrating moment 0 maps above 3σ, combining with Band 7 fluxes … [5.1. Continuum emission: "When we integrate over this profile out to the point at which the emission drops to the rms of the image, 90% of the flux from the disc (R 90 ) is contained within 0''.17 (27 au)."] [5.1. Continuum emission: "The dust mass can be estimated from the measured continuum flux by assuming optically thin thermal emission and using Equation 1"]
  - software: CASA, Astropy
  - parameter: 3σ contour threshold for integrated continuum flux and moment map creation [5.1. Continuum emission: "The integrated flux density measured within a 3σ contour is 28.0 mJy."] [5.2. 12CO (2-1) emission: "Moment maps are created by combining channels containing line emission above 3σ."]
  - assumption: Optically thin thermal dust emission, distance d = 153 pc (Sz 65) and 154.4 pc (Sz 66), midplane temperature T = 20 K, dust opacity κ_ν = 0.1 (ν/10^12 Hz)^β cm^2 g^-1 with β = 1.0, 10% flux calibration uncertainty [5.1. Continuum emission: "where d is the Gaia distance to Sz 65 of 153 pc, Bν is the Planck function using frequency of the observation 230.255 GHz and a midplane temperature of 20 K."] [5.1. Continuum emission: "We adopted the commonly used prescription κν = 0.1 (ν/1012 Hz)β cm2 g−1 following Beckwith et al. (1990), where β is the opacity power index, which we assumed to be 1.0."]
  - fitting: Gaussian fit to continuum emission in the image plane [5.1. Continuum emission: "A Gaussian fit to the emission in the image plane gives a position angle on the sky of 110 ± 0.5 o, a major axis FWHM of 229 ± 3 milliarcsecond and a minor axis FWHM 103 ± 1 milliarcsecond"]
  - validation: Compared derived inclination, PA, R90, and dust masses with literature values from Ansdell et al. (2016, 2018), Andrews et al. (2018c), and Hendler et al. (2020) [5.1. Continuum emission: "Our results are very similar to those found by modelling of the visibilities by Andrews et al. (2018c) using Band 7 observations of Sz 65."] [5.3.1. Measurements from the image plane: "Ansdell et al. (2018) found a larger size of 64 ± 2 au for previous continuum observations with a coarser angular resolution, but our value is consistent with measurements made in analyses in the uv plane by Andrews et al. (2018c) and Hendler et al. (2020)."]
- step 4: Kinematic modelling of 12CO (2-1) rotation velocity maps
  - method: Create peak velocity maps from the 1.0 km/s cube above 3σ using bettermoments, and fit Keplerian rotation models (with an elevated flared emission surface for Sz 65, flat for Sz 66) using eddy MCMC [5.3.3. Analysis of the molecular gas di…: "We used the tool eddy (Teague 2019) to fit a rotation model to each of Sz 65 and Sz 66 using a model of a gas disc that rotated in a Keplerian manner. We subtracted this model from the map of peak velocities of the cube created with bettermoments (Teague & Foreman-Mackey 2018)"]
  - software: bettermoments, eddy
  - parameter: robust = 0.0 cube, 1.0 km/s spectral resolution, 3σ threshold; for Sz 65 final fit: fixed inclination = 63.76◦, M_* = 0.76 M_sun, d = 153.1 pc; for Sz 66 fit: fixed M_* = 0.31 M_sun, d = 156.0 pc [5.3.3. Analysis of the molecular gas di…: "using an image created with Briggs weighting and robust=0.0, a spectral resolution averaged to 1.0 km/s, and a 3σ threshold."] [Figure A3 caption: "Corner plot showing the MCMC results for the rotational model fit to the 12CO observations, achieved by fixing the inclination to the continuum value of 63.76◦, using a stellar mass of 0.76 M⊙ (Alcalá et al. 2017) and a distance derived from Gaia EDR3 153.1 pc."]
  - assumption: Keplerian rotation; for Sz 65 an azimuthally symmetric elevated emission surface z(r) = z0 * (r/1'')^ψ * exp(-(r/r_taper)^q_taper) [5.3.3. Analysis of the molecular gas di…: "model to each of Sz 65 and Sz 66 using a model of a gas disc that rotated in a Keplerian manner."]
  - fitting: MCMC fitting in eddy [5.3.3. Analysis of the molecular gas di…: "For the final fit to the disc, we fixed the robust mass and inclination values of the disc to avoid issues that can arise due to the degeneracy between the parameters (see Figure A3 for the results of the MCMC fitting)."]
  - validation: Subtracted rotation models from peak velocity maps to inspect velocity residuals; ran a grid of models varying PA and inclination; compared kinematic stellar mass of Sz 65 with spectroscopic mass from Alcalá et al. (2017) [5.3.3. Analysis of the molecular gas di…: "Through this modelling, we also obtained a kinematic constraint on the stellar mass of Sz 65 of M∗ = 0.77 ± 0.01 M⊙. This agrees very well with the results of spectroscopic modelling by Alcalá et al. (2017), who derived a mass of 0.76 M⊙."] [5.3.3. Analysis of the molecular gas di…: "A grid of models in which PA and inclination were varied in the fitting process did not reduce this effect, suggesting that it is not a issue that arises due to a poor fit to the disc geometry."]
- step 5: Probabilistic modelling of binary tidal truncation radii
  - method: Compute probability distributions P(R_t) of equilibrium tidal truncation radii using the Pichardo et al. (2005) semi-analytical formula and Torres (1999) deprojection via Monte Carlo sampling of orbital parameters [5.3.4. Tidal truncation: "Pichardo et al. (2005) gave a semi-analytical approximation for a truncated disc size that we can write as"] [5.3.4. Tidal truncation: "Following the approach of Harris et al. (2012), we used a Monte Carlo approach to sample ω, i, e, and v, assuming the eccentricity distribution to be uniform, and that orbital inclinations have a sin(i) dependence."]
  - parameter: 10^6 Monte Carlo realizations per case; uniform eccentricity priors [0.0, 0.7] and [0.0, 0.9]; mass ratio q = M_Sz65 / M_Sz66 (and inverted for Sz 66) [5.3.4. Tidal truncation: "Figure 12 shows the results of the calculations for a truncation radius of both Sz 65 and Sz 66 after running 10^6 models for each case. These samplings were repeated for two different uniform eccentricity priors [0.0, 0.7] as adopted in Harris et al. (2012) and [0.0, 0.9] in order to consider high-eccentricity cases."]
  - assumption: Disc midplane lies on the binary orbital plane; uniform eccentricity distribution; sin(i) orbital inclination distribution [5.3.4. Tidal truncation: "Following the approach of Harris et al. (2012), we used a Monte Carlo approach to sample ω, i, e, and v, assuming the eccentricity distribution to be uniform, and that orbital inclinations have a sin(i) dependence. This analysis also assumes that the disc midplane lies on the orbital plane of the binary system."]
  - fitting: Monte Carlo sampling [5.3.4. Tidal truncation: "Following the approach of Harris et al. (2012), we used a Monte Carlo approach to sample ω, i, e, and v"]
  - validation: Tested sensitivity to eccentricity prior by comparing e_max = 0.7 and e_max = 0.9 [5.3.4. Tidal truncation: "These samplings were repeated for two different uniform eccentricity priors [0.0, 0.7] as adopted in Harris et al. (2012) and [0.0, 0.9] in order to consider high-eccentricity cases."]
- step 6: Estimate upper limit on gap-opening planet mass in Sz 65 and compare brightness temperature profiles with DSHARP
  - method: Apply the Lodato et al. (2019) Hill-radius gap-width scaling relation to the frank gap/ring locations in Sz 65, and compute radial brightness temperature T_B(R) profiles to compare against DSHARP and CX Tau [6.1. Evidence of substructure in the hi…: "For example, following Lodato et al. (2019), we can assume low viscosity"] [6.2. DSHARP sample comparison: "The brightness temperature, T B, of the continuum radial profile was calculated and plotted alongside those"]
  - parameter: Gap minimum at r = 20 au, ring peak at 24 au, gap width ∆ = 4 au, scaling constant k = 4.5 - 8, stellar mass M_* = 0.76 M_sun [6.1. Evidence of substructure in the hi…: "k is a constant arising from the modelling, and it varies between 4.5-8 (Lodato et al. 2019; Rosotti et al. 2016), M∗ is the stellar mass, and r is the radial position of the planet. For Sz 65, M∗=0.76 (Alcalá et al. 2017), and we can measure the gap width as described by using the frank fit to the radial profile, whi…"]
  - assumption: Low disc viscosity (α < 0.01); gap width scales with planet Hill radius [6.1. Evidence of substructure in the hi…: "For example, following Lodato et al. (2019), we can assume low viscosity (α < 0.01) and that the width of the gap opened by a planet, ∆, scales with the Hill radius of the planet"]
- result: Sz 65 1.3 mm continuum integrated flux density = 28.0 (or 28) ± 3 mJy [5.1. Continuum emission: "The integrated flux density measured within a 3σ contour is 28.0 mJy."]
- result: Sz 65 continuum peak intensity = 1.34 ± not stated mJy/beam [5.1. Continuum emission: "The peak in emission is 1.34 mJy/beam, which for the image rms of 13 μJy/beam gives a signal-to-noise ratio of 95 for this observation."]
- result: Sz 65 dust disc radius R90 = 27 ± 4 au [5.3.1. Measurements from the image plane: "R 90 for the continuum is 27 ± 4 au, and for the CO gas, it is 142 ± 15 au around Sz 65."]
- result: Sz 65 12CO gas disc radius R90 = 142 ± 15 au [5.3.1. Measurements from the image plane: "R 90 for the continuum is 27 ± 4 au, and for the CO gas, it is 142 ± 15 au around Sz 65."]
- result: Sz 65 R_gas / R_dust ratio = 5.3 ± 0.9 dimensionless [5.3.1. Measurements from the image plane: "The ratio of R gas / R dust for Sz 65 is 5.3 ± 0.9."]
- result: Sz 65 disc inclination (image plane Gaussian fit) = 63 ± 1 degrees [5.1. Continuum emission: "A Gaussian fit to the emission in the image plane gives a position angle on the sky of 110 ± 0.5 o, a major axis FWHM of 229 ± 3 milliarcsecond and a minor axis FWHM 103 ± 1 milliarcsecond, corresponding to an inclination on the sky of 63 ± 1 o ."]
- result: Sz 65 disc position angle (image plane Gaussian fit) = 110.0 ± 0.5 (or 1) degrees [5.1. Continuum emission: "A Gaussian fit to the emission in the image plane gives a position angle on the sky of 110 ± 0.5 o, a major axis FWHM of 229 ± 3 milliarcsecond and a minor axis FWHM 103 ± 1 milliarcsecond"]
- result: Sz 65 spectral index α (Band 6 to Band 7) = 2.3 ± 0.3 dimensionless [5.1. Continuum emission: "For Sz 65, the flux measured in Band 7 (890 μm) by Ansdell et al. (2016) was 64.5 mJy, which gives a spectral index α = 2.3 ± 0.3"]
- result: Sz 65 dust mass estimate = 16.1 ± not stated M_earth [5.1. Continuum emission: "With these inputs, we calculate a dust mass estimate of 16.1 M⊕"]
- result: Sz 66 1.3 mm continuum integrated flux density = 14.4 (in text) / 6 (in Table 2) ± 1 (in Table 2) mJy [5.1. Continuum emission: "The integrated flux density is 14.4 mJy, with a peak value of 0.55 mJy/beam, giving a peak signal-to-noise ratio of 39."]
- result: Sz 66 continuum peak intensity = 0.55 ± not stated mJy/beam [5.1. Continuum emission: "The integrated flux density is 14.4 mJy, with a peak value of 0.55 mJy/beam, giving a peak signal-to-noise ratio of 39."]
- result: Sz 66 dust disc radius R90 = 16 ± 4 au [5.3.1. Measurements from the image plane: "We find 16 ± 4 au and 47 ± 15 au in Sz 66."]
- result: Sz 66 12CO gas disc radius R90 = 48 (or 47) ± 15 au [abstract: "The observations show that Sz 66 is very compact: 90% of the flux is contained within 16 au, and 90% of the molecular gas flux lies within 48 au."]
- result: Sz 66 R_gas / R_dust ratio = 2.9 ± 1.0 dimensionless [5.3.1. Measurements from the image plane: "For Sz 66, the ratio is lower at 2.9"]
- result: Sz 66 disc inclination (image plane Gaussian fit) = 67.8 (or 68) ± 1 degrees [5.1. Continuum emission: "A Gaussian fit to the image plane returns a best fit with a position angle 80.0 o and a shape of 116 mas x 43.8 mas FWHM, corresponding to an inclination of 67.8 o ."]
- result: Sz 66 disc position angle (image plane Gaussian fit) = 80.0 ± 1 degrees [5.1. Continuum emission: "A Gaussian fit to the image plane returns a best fit with a position angle 80.0 o and a shape of 116 mas x 43.8 mas FWHM, corresponding to an inclination of 67.8 o ."]
- result: Sz 66 spectral index α (Band 6 to Band 7) = 2.2 ± 0.3 dimensionless [5.1. Continuum emission: "Ansdell et al. (2016) measured a flux at 890 μm of 14.78 mJy, which led us to calculate α = 2.2 ± 0.3."]
- result: Sz 66 dust mass estimate = 3.4 ± not stated M_earth [5.1. Continuum emission: "With Equation 1, this gives a dust mass estimate for Sz 66 of 3.4 M⊕ ."]
- result: Sz 65 12CO moment 0 integrated flux = 629 ± not stated mJy/beam.km/s [5.2. 12CO (2-1) emission: "In the moment 0 map, the integrated flux measured from pixels above 3σ around Sz 65 is 629 mJy/beam.km/s, with a peak brightness of 61 mJy/beam.km/s."]
- result: Sz 66 12CO moment 0 integrated flux = 382 ± not stated mJy/beam.km/s [5.2. 12CO (2-1) emission: "Around Sz 66, an integrated flux of 382 mJy/beam.km/s is measured and the peak lies at 74.3 mJy/beam.km/s."]
- result: Sz 65 kinematic stellar mass = 0.77 ± 0.01 M_sun [5.3.3. Analysis of the molecular gas di…: "Through this modelling, we also obtained a kinematic constraint on the stellar mass of Sz 65 of M∗ = 0.77 ± 0.01 M⊙."]
- result: Sz 65 12CO emission surface aspect ratio z0 = 0.0342 (or 0.03) ± +0.0003/-0.0003 dimensionless [5.3.3. Analysis of the molecular gas di…: "This modelling achieves a best-fit value of the aspect ratio constant z0=0.03 (see Figure A3 for the MCMC results)."]
- result: Sz 66 12CO kinematic inclination = 38.4599 (or 38) ± +0.2284/-0.2387 degrees [5.3.3. Analysis of the molecular gas di…: "This fitting procedure finds an inclination value for the 12CO gas disc of 38◦, which is significantly different from that derived from images of the dust disc, which was found to be 68◦."]
- result: Most likely predicted tidal truncation radius R_t for Sz 65 = 276 ± not stated au [5.3.4. Tidal truncation: "Sz 65 has a most likely predicted truncation radius of 276 au, which is also much larger than the measured R 90, which is 161 au."]
- result: Most likely predicted tidal truncation radius R_t for Sz 66 = 195 ± not stated au [5.3.4. Tidal truncation: "In Figure 12, Sz 66 is expected to be the more compact disc, with its most likely truncation radius found at 195 au."]
- result: Upper limit on planet mass in Sz 65 gap = 0.04-0.2 ± not stated M_Jup [6.1. Evidence of substructure in the hi…: "When we account for variation in k, this means that an upper limit on the mass of a planet found is 0.04-0.2 M Jup, for the brightness variation we observe."]
- limitation (authors): 12CO (2-1) was not robustly detected at native resolution, requiring a 0''.07 uv taper and spectral averaging to 1 km/s, which limits sensitivity to small-scale velocity perturbations, disc warping, and elevated emission surfaces (making z… [4. Calibration and data reduction: "12 CO (2-1) emission was not robustly detected by our new observations at the native angular and spectral resolution."]
- limitation (authors): Continuum oversubtraction reduces 12CO brightness near the line centre along the minor axis, limiting searches for inner-outer disc misalignments. [5.3.3. Analysis of the molecular gas di…: "We note that the CO brightness line decreases around the line centre, primarily along the minor axis of the discs, possibly due to an oversubtraction of continuum. This limits our ability to search for misalignments between the inner and outer disc."]
- limitation (authors): Low SNR on the longest baselines makes the tentative ~6 au feature in the Sz 65 frank fit uncertain, and the ~3-4 au beam barely reaches the expected pressure scale height H ≤ 2.7 au in the inner disc. [5.3.2. Non-parametric visibility fitting: "The visibility fitting suggests a smaller feature at about 6 au in Sz 65, for which there is no counterpart in either of the profiles extracted from the image plane. We therefore remain cautious about this potential gap."]
- not stated (card): Exact cell (pixel) size and image dimensions (imsize) used in clean for both continuum and 12CO cubes; Exact solution intervals (solint) and number of rounds for phase self-calibration of projects 2018.1.00271 and 2018.1.01458; Exact channel ranges flagged as line-containing when averaging line-free channels for continuum; Parameters used to generate the Keplerian mask during 12CO cleaning; Conti…

### 2024A&A...689A..41V: XLSSC 122 caught in the act of growing up: Spatially resolved SZ observations of a z = 1.98 galaxy cluster (2024; galaxy_clusters_and_sz; observational_alma_primary)
- question: What are the dynamical state and morphology of the ICM of the z=1.98 cluster XLSSC 122, as traced by resolved SZ observations?
- step 1: Model compact-source contamination
  - method: Fit point-source models (RA, Dec, amplitude, spectral slope, calibration scales) jointly to Band 3 and Band 4 in the uv-plane with lower uv-cut of 11 kλ; subtract bright source before SZ modeling [4 Interloper and cluster member removal: "with a lower *uv*-cut of 11 k$\lambda$ to exclude extended emission."]
  - software: dynesty
  - assumption: Unresolved sources are point-like with first-order polynomial spectral behaviour [4 Interloper and cluster member removal: "Unresolved, compact sources are modeled using point-like (Dirac delta) emission models with a first-order polynomial to describe their spectral behavior."]
- step 2: Single-component ICM forward modeling
  - method: gNFW (theoretical) and A10/M14 template (empirical) pressure models integrated to Compton y, converted to SZ brightness per band, Fourier transformed, sampled at data uv-points with primary beam; Gaussian likelihood on unbinned visibilitie… [3 Methodology: "We then apply the ALMA and ACA transfer function to the model to account for the missing baselines and compute the likelihood of the resulting model on the unbinned visibilities"]
  - software: dynesty
  - parameter: Mostly flat priors; Gaussian priors on calibration and redshift [3.3 Joint likelihood modeling: "we mainly use flat priors except for the calibration and redshift uncertainty parameters which we marginalize over."]
  - parameter: Evidence convergence threshold Δln B = 0.01 [3.3 Joint likelihood modeling: "set to $\Delta\ln\mathcal{B}=0.01$"]
  - assumption: Cosmology Planck2014_XIII, H0=67.7, Om=0.307; non-relativistic SZ (relativistic corrections neglected) [1 Introduction: "$H_0=67.7$ kms$^{-1}$Mpc$^{-1}$ and $\Omega_{\rm m} = 0.307$"]
  - assumption: ACT and ALMA+ACA likelihoods independent [3.3 Joint likelihood modeling: "Hence, we assume no covariance between the ACA+ALMA observations and the ACT maps."]
  - fitting: Static nested sampling with dynesty; significance from Bayes factor against null model [3.2 Visibility-based modeling of the ICM: "The implementation uses the static nested sampling method implemented in the `dynesty` package"]
  - validation: Residual maps in uv plane; Bayes factor comparisons [5.1.1 The theoretical formalism: "The residuals in Figure [1] are obtained by subtracting the model in the visibility plane from the data."]
- step 5: Derive SZ and dynamical masses
  - method: Evidence-weighted average of empirical-formalism masses (ALMA+ACA+ACT); velocity dispersion biweight of 32 members with Munari scaling, converted to M500 with colossus [7 Mass estimates: "Our SZ mass is calculated by taking the evidence-weighted average of the mass estimates from the empirical formalism runs"]
  - software: colossus
  - parameter: A = 1177.0 km/s, alpha = 0.364 [7 Mass estimates: "with $A = 1177.0$ km s$^{-1}$ and $\alpha = 0.364$"]
  - assumption: Local scaling relations of Arnaud2010 used for Y to M500 [7 Mass estimates: "we make use of local scaling relations from (cite: Arnaud2010) to convert $Y_{\rm 500,c}$ to an SZ-derived halo mass"]
  - validation: Compared with X-ray, CARMA, ACT catalog masses [Mass estimates: "We also quote the derived cluster mass of XLSSC 122 as reported in the ACT cluster catalog (cite: Hilton2021)."]
- step 6: Pseudo-temperature map
  - method: Ratio of SZ flux over sqrt of X-ray surface brightness at ~5'' resolution [8.2 Thermodynamical implications: "taking the ratio of the SZ flux over the square root of the X-ray surface brightness"]
  - assumption: Constant temperature along line of sight [8.2 Thermodynamical implications: "under the assumption of constant temperature along the line of sight"]
- result: SZ detection significance, ALMA+ACA = ~10.9–11.2 ± not stated sigma [5.1 ALMA+ACA modeling: "we detect the SZ effect at $\sim10.9-11.2\sigma$ in the ACA+ALMA data"]
- result: SZ detection significance, ALMA+ACA+ACT = 15 ± not stated sigma [9 Conclusions: "which increases to $15\sigma$ when ACT observations are included"]
- result: M500,c (SZ) = 1.66e14 ± +0.23/-0.20 e14 Msun [7 Mass estimates: "$M_{500,\mathrm{c}} = 1.66^{+0.23}_{-0.20} \times 10^{14}~\rm M_\odot$"]
- result: Eccentricity (ALMA+ACA+ACT) = 0.46 ± +0.12/-0.16 dimensionless [5.2 ALMA+ACA+ACT joint likelihood model…: "likelihood-weighted average of $e=0.46^{+0.12}_{-0.16}$"]
- result: Velocity dispersion sigma200,c = 1014 ± 169 km/s [7 Mass estimates: "We found a $\sigma_{200,\mathrm{c}} = 1014~\pm169$ km s$^{-1}$"]
- result: log10 M500,c dynamical = 14.69 ± +0.13/-0.18 log Msun [7 Mass estimates: "$\log_{10} M_{500,\mathrm{c}}^{\mathrm{dyn}} = 14.69^{+0.13}_{-0.18}~\rm M_\odot$"]
- result: Y(<r500,c) A10-MD = 2.0e-5 ± +0.6/-0.4 e-5 Mpc^2 [8.3 Time scales: "we find $Y(<r_{500,\mathrm{c}}) = 2.0^{+0.6}_{-0.4} \times 10^{-5}~\textnormal{Mpc}^2$"]
- result: SZ peak offset from BCG/X-ray peak = 10'' (80 kpc) ± 1'' (7 kpc) arcsec [8.1 Morphological implications: "offset from the BCG and the peak of the X-ray emission by $10\ensuremath{''}\pm 1\ensuremath{''}$ ($80\pm7$ kpc)"]
- limitation (authors): Lack of short baselines makes beta–P0 degeneracy and template discrimination weak; gNFW poorly suited for filaments [5.1.2 The empirical formalism: "the lack of short baselines in the ALMA+ACA observations explains why the mass estimates vary between models"]
- not stated (card): Exact ALMA/ACA uv-selection, channel binning and weights used in the visibility fits; dynesty settings (live points, bounding, sampling); Exact ACT DR6 map products, beams, transfer functions and cutout size; Tapering and tclean parameters for display images; How evidence-weighted mass average across models is computed; Y-to-M500 conversion implementation details; Band 4 point-source model detail…

### 2019A&A...623A.150V: The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN (2019; protoplanetary_disks, astrochemistry; large_program_or_survey)
- question: What is the CN N=3-2 emission morphology and flux distribution of Lupus Class II disks, and what do they imply for gas disk sizes and UV irradiation, compared with DALI models?
- step 5: Resolved CN rings in Sz 71 and Sz 98
  - method: Keplerian-masked moment-zero maps, azimuthally averaged deprojected radial profiles [4.1: "these profiles have been made by azimuthally averaging over the (deprojected) moment-zero maps"]
  - software: CASA
- step 6: Search for continuum substructure in uv-plane
  - method: Fit deprojected visibilities binned at 15 klambda with Gaussian core (Model 1) vs Gaussian core plus cosine-modulated Gaussian (Model 2) [uv-plane analysis: "subsequently the data were binned to $15$ k$\lambda$ bins in u,v-space"]
  - software: PyMC, CASA
  - parameter: baselines up to 800 klambda (Sz 71) and 500 klambda (Sz 98) [uv-plane analysis: "Baselines up to 800 k$\lambda$ are used for our fit to Sz 71, and up to 500 k$\lambda$ for Sz 98"]
  - fitting: MCMC with PyMC; priors and likelihood not stated [uv-plane analysis: "were obtained from MCMC-fits to the observations with the *PyMC* Python module."]
  - validation: BIC comparison of Model 1 and 2 [uv-plane analysis: "the two-component Gaussian model fits the continuum significantly better than the single-component one, when comparing the Bayesian Information Criterion"]
- step 7: SED fitting to set disk structure
  - method: RADMC3D grid for flaring, scale height, mass, inner radius, then DALI with small and settled large grains [SED fitting procedure: "we used the `RADMC3D`-code to globally constrain the flaring angle of the disk $\psi$, its scale height $h_r$, the disk mass $M_d$"]
  - software: RADMC-3D, DALI
  - parameter: gamma=1, Rout ~200 AU, f in [0.85,0.99], chi in [0.2,1.0] [SED fitting procedure: "We explore only $f = [0.85, 0.99]$ and $\chi = [0.2, 1.0]$."]
  - assumption: gas surface density = 100 x dust [4.2.1: "The gas surface density is $100 \times$ the dust surface density and is not decoupled."]
  - assumption: R_V=3.1, A_V=0.5 (Sz 71), 1.0 (Sz 98) [SED fitting procedure: "We corrected the data for extinction using $R_V = 3.1$, and $A_V = 0.5$ mag and $1.0$ mag for Sz 71 and Sz 98 respectively"]
- step 8: Model CN rings with DALI
  - method: Thermo-chemical DALI models with varied UV excess, ray-traced and convolved with 0.3'' Gaussian beam, compared to radial profiles and fluxes [4.2.1: "After ray-tracing each model, the images were convolved with an $0.3''$ circular Gaussian beam"]
  - software: DALI
  - parameter: Sz 71: logL(912-1100A)=-5.2 (M1), -4.1 (M2); Sz 98: -3.4 [Table 2: "| Sz 71 | M1 | -5.2 | 0.8 |"]
  - assumption: UV excess varied up to factor 10 from accretion-based estimate [4.2.1: "we have allowed for variations in the UV excess at these wavelengths of up to a factor 10"]
  - validation: Compare model and observed radial profiles and integrated fluxes [Model results: "the most remarkable feature of the CN emission, its concentration in a ring, is indeed reproduced in the model radial profiles, and occurs at radii within 20 AU of those seen in the data"]
- result: CN ring peak radius Sz 71 / Sz 98 = 40 / 60 ± not stated AU [4.1.1: "The peak emission is found at 40 and 60 AU for Sz 71 and Sz 98 respectively"]
- result: Unresolved continuum ring radius Sz 98 = 117 ± not stated AU [uv-plane analysis: "located at 117 AU"]
- result: Delta BIC Sz 71 / Sz 98 = 1296.9 / 1382.7 ± not stated dimensionless [uv-plane analysis: "$\Delta_{\rm{BIC}} = 1296.9$ for Sz 71, and for Sz98, $\Delta_{\rm{BIC}} = 1382.7$"]
- result: DALI model CN flux Sz 71 M2 / Sz 98 M1 = 3.9 / 3.7 ± not stated Jy km/s [Table 2: "| Sz 98 | **M1** | -3.4 | 3.7 |"]
- limitation (authors): Model absolute fluxes uncertain by a factor of a few; UV excess and accretion-to-UV conversion uncertain by up to an order of magnitude [4.2: "lead to an uncertainty of a factor of a few in flux (cite: woitke18)"]
- not stated (card): Line-free channels / continuum subtraction method for CN cubes; Detection criterion (S/N threshold) for the 36 detections; CASA version used for imaging and self-calibration (only imfit 4.3.1 given); Image size and cell size; Exact aperture sizes and per-source fluxes in the full table; DALI input files, full chemistry settings and grid spacing; MCMC priors, walkers and chain length for the uv fi…

### 2019Natur.570...83M: A cool accretion disk around the Galactic Centre black hole (2019; milky_way_ism, agn_and_quasars; observational_alma_primary)
- question: Is there a cool (10^4 K) ionized gas disk in the accretion flow of Sgr A* at 10-10^5 Schwarzschild radii, detectable in the H30alpha recombination line?
- step 3: Derive emission measure, amplification factor, disk density, mass, accretion rate
  - method: Recombination-line emissivity relation with Storey & Hummer emissivity; amplification from Br gamma limit; Shakura-Sunyaev uniform disk and BLR-like cloudlet models [main text: "we obtain the effective volume emission measure of the ionized hydrogen in the disk"]
  - software: Mathematica
  - parameter: T=1e4 K, emissivity 1.25e-31 erg/s cm^3, D=8 kpc, Rmax=0.23 arcsec, Rmin=0.07 arcsec [Disk of a uniform density: "an isothermal disk at $T=10^4~\mathrm{K}$ with an outer radius $R_\mathrm{max} = 0.23$ arcsec and an inner radius $R_\mathrm{min} = 0.07$ arcsec"]
  - assumption: Alpha = 0.1, chi = 1 (uniform disk) or 1/4 (cloudlets), cloudlet radius r = 1e-3 Rmax [BLR-like Ensemble of Clouds.: "Here we used $r=10^{-3} R_\mathrm{max} = 9 \mu \mathrm{pc}$ as a characteristic size of cloudlets"]
  - validation: Ionization equilibrium check against Sgr A* plus Wolf-Rayet star ionizing flux [Ionization Equilibrium: "Thus we conclude that the ionizing photon flux required to keep the disk ionized is a collective effect of Sgr A\* and nearby orbiting stars."]
- result: Effective volume emission measure = 1.8e60 ± not stated cm^-3 [main text: "\mathscr{M}{\mathrm{EM}} = 1.8 \times 10^{60} \, \textrm{cm}^{-3}."]
- result: Amplification factor M = >=80 ± not stated dimensionless [main text: "The relation above implies that H30$\alpha$ has to be amplified by a factor $\mathscr{M}\gtrsim 80.$"]
- result: Uniform-disk accretion rate = 2.7e-10 ± not stated Msun/yr [main text: "\dot{M} (R_\mathrm{mean} )= 2.7 \times 10^{-10}"]
- result: Uniform-disk mass = 1.0e-4 ± not stated Msun [main text: "M= 1.0 \times 10^{-4}"]
- result: Ionizing photon rate Q0 = 4.6e45 ± not stated s^-1 [Ionization Equilibrium: "Q_0 =4.6 \times 10^{45} \left( \frac{\mathscr{M}}{100}\right)^{-1} \,\mathrm{s^{-1}}"]
- limitation (authors): Line could be unlucky combination of molecular lines or foreground absorption [main text: "the possibility remains that the double-peaked line profile we see is an unlucky combination of molecular lines or is partially due to a foreground absorption"]
- not stated (card): Exact line-free channel lists per spectral window; CASA version; Pipeline/calibration details and flux calibrator choice per execution; Aperture center and shape used for the spectrum; Cell size, image size, deconvolver, masks, and clean threshold; Line/continuum image weighting beyond robust 0.5; CARAMEL model priors, sampler and fit settings (code proprietary); Details of Br gamma limit derivat…

### 2021MNRAS.503.1459B: Dynamical model of an obscuring clumpy torus in AGNs - I. Velocity and velocity dispersion maps for interpretation of ALMA observations (2021; agn_and_quasars, nearby_galaxies; theory_or_simulation_compared_to_alma)
- question: Develop a dynamical N-body model of a self-gravitating obscuring clumpy torus in an AGN to construct velocity, velocity dispersion, and temperature maps and interpret ALMA and VLTI/MIDI observations.
- step 4: Derive cloud temperatures and construct temperature distribution maps for NGC 1068
  - method: Calculate equilibrium blackbody cloud temperatures heated by an anisotropically emitting Shakura-Sunyaev accretion disk using ray tracing from the center, then project onto a 100x100 cell observer grid via line-of-sight ray tracing. [Temperature of clouds in the torus: "We send the rays from the accretion disk over the whole range of steradians with a step that is equal to the angular size of a cloud at 3 pc distance."] [Temperature of clouds in the torus: "For this reason, the next step is to divide the image into $100\times100$ cells and each cell gets the value of the mean temperature within it."]
  - parameter: Accretion rate M_dot = 0.2 M_sun/year (from L_bol = 5.65 x 10^44 erg/s); image grid = 100 x 100 cells; epsilon_cl = 0.01 and 0.025; theta = 45 deg [Temperature of clouds in the torus: "Taking into account ([\[eq10.9\]](#eq10.9)), we obtain the accretion rate in NGC 1068 to be $\dot{M} \approx 0.2 M_\odot$/year."] [Temperature of clouds in the torus: "Fig.[18](#fig:temp_maps_01) and [19](#fig:temp_maps_025) show the temperature distribution maps for a single cloud radius $\varepsilon_{\rm cl} = 0.01$ and $\varepsilon_{\rm cl} = 0.025$ respectively, for the initial half-opening angle of the wind $\theta=45^\circ$."]
  - assumption: Standard geometrically thin, optically thick accretion disk; spherical clouds in thermodynamic equilibrium with disk radiation absorbed over half their surface; anisotropic disk flux F(theta) = (1/3) cos(theta)(1 + 2 cos(theta)); optically… [Temperature of clouds in the torus: "Assume that the clouds are in thermodynamic equilibrium with the accretion disk. Within the framework of a standard geometrically thin and optically thick accretion disk, the energy flux emitted by the disk surface has the form (cite: Shakura1973):"] [Temperature of clouds in the torus: "To take it into account in our model, we use an angular dependence for the flux (cite: Phillips1986; Netzer1987) for the semi-infinite scattering atmosphere:"]
  - validation: Compared derived cloud temperatures and hot-region morphology with VLTI/MIDI mid-infrared observations of NGC 1068. [Temperature of clouds in the torus: "So, for the given accretion rate and torus scales, the temperature satisfies the observational values (cite: Jaffe2004; Raban2009)."]
- result: Accretion rate in NGC 1068 (M_dot) = 0.2 ± not stated M_odot/year [Temperature of clouds in the torus: "Taking into account ([\[eq10.9\]](#eq10.9)), we obtain the accretion rate in NGC 1068 to be $\dot{M} \approx 0.2 M_\odot$/year."]
- result: Maximum equilibrium cloud temperature at torus throat in NGC 1068 (T_cl^max) = 820 ± not stated K [Temperature of clouds in the torus: "For the accretion rate $\dot{M}=0.2 M_\odot/$ year, the equilibrium temperature has a maximum value $T_{\rm cl}^{\rm max} \simeq 820$ K at the inner edge (throat) of the torus with $r_{\rm min} \simeq 0.4$ pc; and a minimal value $T_{\rm cl}^{\rm min} \simeq 300$ K in the torus body region with $r_{\rm max} \simeq 3$ …"]
- result: Minimum equilibrium cloud temperature in torus body in NGC 1068 (T_cl^min) = 300 ± not stated K [Temperature of clouds in the torus: "For the accretion rate $\dot{M}=0.2 M_\odot/$ year, the equilibrium temperature has a maximum value $T_{\rm cl}^{\rm max} \simeq 820$ K at the inner edge (throat) of the torus with $r_{\rm min} \simeq 0.4$ pc; and a minimal value $T_{\rm cl}^{\rm min} \simeq 300$ K in the torus body region with $r_{\rm max} \simeq 3$ …"]
- limitation (authors): The torus-to-SMBH mass ratio is fixed to M_torus/M_smbh = 0.02 rather than varied as a free parameter. [Initial conditions: "Actually, the ratio $M_{\text{torus}}/M_{\text{smbh}}$ should be a free parameter."]
- limitation (authors): Simulations assume a dissipationless system and neglect cloud collisions and tidal shearing/merging. [Results of N-body simulations: "These oscillations have been derived under the assumption that the system is dissipationless. Were collisions included in the simulation, the result might be different."]
- limitation (authors): Radiation pressure on cloud dynamics near the accretion disk is neglected. [Box-orbits as an explanation for the os…: "Obviously, the dynamics of clouds located near the accretion disk can be also influenced by the radiation pressure (cite: Plewa2013; Venanzi2020). However we neglect here this effect, leaving its investigation to a future paper."]
- not stated (card): Order of the Hermite integration scheme (4th, 6th, or 8th) actually used in the production phi-GPU runs; Random number seed or realization details for initial orbital element distributions; Exact snapshot time (in orbital periods) from the N=128k simulation used to construct the ray-traced velocity, dispersion, and temperature maps; Quantitative goodness-of-fit metric (if any) used to select the …

### 2021MNRAS.503.1174K: Feedback factory: multiple faint radio jets detected in a cluster at z = 2 (2021; high_z_galaxies, agn_and_quasars, galaxy_clusters_and_sz; multi_facility_alma_minor)
- question: What is the role of AGN radio-jet based kinetic feedback and the compliance of cluster galaxies to the TIR-radio correlation within the z=2 galaxy cluster CL J1449+0856?
- step 5: Calculate integrated radio-jet luminosity, mechanical cavity power, SZ residual correlation, and Inverse-Compton X-ray contribution
  - method: Integrate rest-frame 10 MHz - 10 GHz radio luminosity from the 6 jets, convert to cavity power P_cav via the O'Sullivan et al. (2011) scaling relation, compare jet locations with the ALMA+ACA 92 GHz SZ residual map, and estimate IC X-ray f… [Radio emission: How much do we really h…: "To make a comparison, we add up the contributions of all the detected jets in place of the jets from a central AGN, which gives us a flux of 30.6\pm3.3 \, \mu Jy and a corresponding integrated radio luminosity (10 MHz–10 GHz rest-frame) of 2.1 ~(\pm 0.2)~ \times 10^{41} ~ergs~ s^{-1}."] [Quantifying the feedback: "We can hence use the integrated radio luminosity from all these jets"]
  - assumption: Jet spectral index \alpha = -1.04 \pm 0.03 (explored range -0.7 to -1.5, and -1.2); cavity energy E_cav = 4pV; Lorentz factor 10^3 - 10^5 and photon index 2 for IC calculation [Radio emission: How much do we really h…: "With a robust sample of 190 extragalactic radio-jets, they find a mean spectral index of -1.04 \pm 0.03 that we use in our calculation."] [Quantifying the feedback: "This comes out to be 4pV under the assumption that the cavity is dominated by relativistic plasma."]
  - validation: Assessed flux boosting upper limit (~40% assuming 1.5\sigma noise contribution per source) and tested single central jet R1 alone [Radio emission: How much do we really h…: "We can also have flux boosting contributions and we estimate a generous upper limit of the resulting overestimation of the jet flux to be \sim40\%, by assuming an additional noise contribution of 1.5\sigma for each source."] [Radio emission: How much do we really h…: "But repeating the same analysis with the central jet (R1) only brings down the luminosity by a factor of 4, keeping it well within the scatter and still slightly above the average."]
- result: Integrated radio luminosity (10 MHz - 10 GHz rest-frame) of the 6 jets (for \alpha = -1.04) = 2.1e41 ± 0.2e41 ergs s^{-1} [Radio emission: How much do we really h…: "To make a comparison, we add up the contributions of all the detected jets in place of the jets from a central AGN, which gives us a flux of 30.6\pm3.3 \, \mu Jy and a corresponding integrated radio luminosity (10 MHz–10 GHz rest-frame) of 2.1 ~(\pm 0.2)~ \times 10^{41} ~ergs~ s^{-1}."]
- result: AGN-jet cavity power P_cav (for \alpha = -1.04) = 1.14e44 ± 0.55e44 ergs s^{-1} [Quantifying the feedback: "to get a $\rm P_{\rm cav}=1.14 ~(\pm 0.55)~ \times 10^{44} ~\rm ergs~ s^{-1}$"]
- result: AGN-jet cavity power P_cav upper limit (for \alpha = -1.5) = 4.7e44 ± not stated ergs s^{-1} [Quantifying the feedback: "The details of this distribution, although indeterminable with the current data, have large implications especially since the –1.5 limit results in a P_{cav} \sim 4.7 ~ \times 10^{44} ~ergs~ s^{-1}."]
- result: AGN-jet cavity power P_cav (for \alpha = -1.2) = 1.8e44 ± not stated ergs s^{-1} [Quantifying the feedback: "This gives a P_{cav} \sim 1.8 ~ \times 10^{44} ~ergs~ s^{-1}."]
- result: Inverse-Compton X-ray luminosity upper limit from Chandra stacking = 2.2e42 ± not stated ergs s^{-1} [Inverse-Compton contribution: "The generous upper limit hence derived from the total counts detected is 2.2~ \times 10^{42}~ ergs~s^{-1} or 3\% of the ICM X-ray luminosity."]
- limitation (authors): Small sample size of 10 cluster galaxies prevents detection of subtle deviations in the q_TIR vs M_* relation [TIR-radio correlation: "As shown in Fig. 4, we see an agreement within 1\sigma (0.2 dex), although acknowledging the inability of our limited dataset to detect a more subtle digression in the behaviour of q_{TIR}, if it exists."]
- limitation (authors): Radio luminosity and cavity power estimates depend strongly on the unknown radio spectral index, which cannot be tightly constrained without deeper low-frequency observations [Radio emission: How much do we really h…: "It is worth noting however that this luminosity calculation is strongly dependent on the radio spectral index which can be anywhere between –0.7 (cite: delhaize17) to –1.5 (the upper limit we calculate based on our GMRT 325 MHz measurements)."]
- limitation (authors): Low S/N (4\sigma) of the diffuse X-ray ICM emission prevents direct detection of X-ray cavities, measurement of cluster binding energy, or precise localisation of the X-ray peak [Radio emission: How much do we really h…: "However, we can only estimate a rough peak of the X-ray emission with the limited S/N, which still seems to be within this region."]
- not stated (card): CASA version used for JVLA and GMRT data reduction; Exact flagging commands and channel ranges for JVLA spectral windows 13, 14, and 15; Pre-reduced ALMA 870 um continuum image from Coogan et al. (2018) and 92 GHz SZ residual map from Gobat et al. (2019), as ALMA reduction parameters are not restated in this paper

### 2019MNRAS.490.5134B: Detecting the halo heating from AGN feedback with ALMA (2019; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Can the SZ decrement from AGN-heated halo gas around quasar HE0515-4414 be detected in the ALMA visibility plane after subtracting compact positive sources?
- step 4: inspect residuals for SZ
  - method: Subtract model from visibilities; bin residuals in 1 klambda bins; tclean residual images [3 Results: "The residuals were found by subtracting the model presented in Fig. 4 from the observed visibilities."]
  - software: CASA, tclean
  - validation: Checked >50 uv tracks and >20 antenna pairs in shortest bin [3.2 Visibility Plane: "We plotted the uv coordinates of the visibilities inside that bin and observed over 50 uv-tracks."]
- step 6: compare with FABLE simulation
  - method: simobserve of FABLE SZ map, same pipeline; derive correction factor 2.5 [4.2 Comparison with Simulations: "This suggests a total SZ flux of 0.5 mJy from HE0515-4414 after correcting for the primary beam attenuation and the flux resolved out by the array (i.e. a correction factor of 2.5)."]
  - software: CASA, simobserve
- result: SZ flux (uncorrected) = ~0.2 ± not stated mJy [Conclusion: "We report a SZ flux of $\sim$ 0.2 mJy"]
- result: Corrected SZ flux = ~0.5 ± not stated mJy [Conclusion: "$\sim$ 0.5 mJy after applying a correction factor"]
- result: SW bowl significance = 3.2 ± not stated sigma [3.1 Image Plane: "In our analysis this feature has a slightly lower significance, 3.2$\sigma$."]
- limitation (authors): Only dof=1 for short baselines; limited SNR prevents 2D fitting [3.3 Significance: "Our positive emission model, however, has 17 parameters, leaving dof=1."]
- not stated (card): Cell size and image size for tclean; Mask and clean threshold/iterations; MCMC sampler type, priors, number of walkers/steps for GALARIO fits; Exact visibility binning/weighting and which data columns were used; Procedure for inferring the 3.35 sigma with dof=1 details and per-bin values; Model for correction factor beyond FABLE comparison; noise realisation details of simulations

### 2024ApJ...969...56M: Observational Constraints on Sunyaev─Zeldovich Effect Halos around High-z Quasars (2024; agn_and_quasars, galaxy_clusters_and_sz; observational_alma_primary)
- question: Is there hot, ionized circumgalactic gas (thermal SZE) around high-z ultraluminous quasars, and what halo mass and AGN feedback wind power does a stacked ALMA continuum limit imply?
- step 5: Convert stacked flux to Compton y
  - method: Interpret stacked continuum decrement as thermal SZE and convert to Compton parameter using the Sazonov & Sunyaev formulation [2.2 Stacked SZE Signal: "We interpret the stacked continuum flux observations as SZE signal by converting to Compton parameter"]
  - assumption: pure thermal SZE; kSZE neglected [2.2 Stacked SZE Signal: "For stacked QSO environments we use a pure thermal SZE model to determine the Compton parameters."] [2.2 Stacked SZE Signal: "Our stacking analysis will not be sensitive to the non-spherically symmetric kSZE."]
- result: Peak y in 6 arcsec stacked image (east side, r ~5 arcsec) = 2.4e-5 (~2.6 sigma) ± not stated dimensionless [2.2 Stacked SZE Signal: "peaking at $y= 2.4e-5$ or $\sim2.6\sigma$."]
- limitation (authors): Halo mass estimate from Lya gas dynamics is uncertain [Introduction: "uncertain due to radiative transfer effects and possible non-gravitational motions in the Ly"]
- limitation (authors): tSZE cannot be separated from kSZE without deep observations at other frequencies [Introduction: "It is also not possible to separate the tSZE from any kSZE contribution without further very deep observations at other frequencies."]
- limitation (authors): Stack insensitive to non-spherically symmetric kSZE [2.2 Stacked SZE Signal: "Our stacking analysis will not be sensitive to the non-spherically symmetric kSZE."]
- not stated (card): Manual mask definitions (regions) for QSO and serendipitous sources in each of the ten fields; Which channels were flagged as line-contaminated per SPW and the continuum reference frequency used; tclean deconvolver, niter, cleaning threshold value, weighting scheme details, and uv-taper values/units used for the 6 and 3 arcsec images; Self-calibration solution parameters beyond 'scan length' (ref…

### 2020A&A...638A..70D: The Massive and Distant Clusters of WISE Survey. SZ effect of Verification with the Atacama Compact Array - Localization and Cluster Analysis (2020; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can ACA Band 3 observations robustly validate MaDCoWS cluster candidates through the thermal SZ effect, and what cluster masses do they give?
- step 2: fit SZ + point-source model to visibilities
  - method: Bayesian forward modeling of raw visibilities with gNFW pressure model (fixed shape parameters) plus Dirac-delta point sources with flat spectrum [3 Analysis technique: "we perform a Bayesian forward-modeling analysis directly on the visibilities of the ACA MaDCoWS sample"]
  - parameter: free: M500, z, centroid, point source positions and fluxes, flux normalization [3.3 Parameter priors: "The position $\bm{x}_{\textsc{ps}}$ and the source flux $i_{\textsc{ps}}$ are left free to vary."]
  - assumption: non-relativistic tSZ, kSZ neglected, flat ΛCDM Ωm=0.30 H0=70 [3.1 Estimating cluster masses: "we neglect any temperature-dependent corrections arising from the fully relativistic treatment of the thermal SZ effect"]
  - fitting: Normal priors on centroid (sigma 14.3, 15 arcsec); split-normal priors on z; normal prior on flux scaling; wide uninformative priors on point source flux [3.3 Parameter priors: "we adopt split-normal priors (cite: Wallis2014) on the redshifts $z$"]
  - validation: data-free runs show no prior-induced biases [3.3 Parameter priors: "have shown no biases in the parameter inference related to choice in the prior distributions"]
- step 3: assess detection significance
  - method: Bayes factor between SZ+point-source and point-source-only models, converted to sigma_eff [4 Results and discussion: "$\sigma_{\mathrm{eff}}\simeq\sqrt{2\Delta\log{\mathcal{Z}}}$"]
  - parameter: sigma_eff >~ 3 indicates robust detection [4 Results and discussion: "a value of $\sigma_{\mathrm{eff}}\gtrsim3$ is indicative of a robust detection"]
  - validation: Compared with dirty-image significance for most significant cluster [4 Results and discussion: "corresponding to a statistical significance of $4.06\sigma$"]
- result: clusters with significant SZ detection = 7 of 10 ± not stated clusters [abstract: "we obtain a significant detection of the SZ effect for seven out of the ten VACA LoCA clusters"]
- result: highest sigma_eff (universal profile) = 7.77 ± not stated dimensionless [4 Results and discussion: "$\sigma_{\mathrm{eff}}=7.77$"]
- result: M500 of most significant cluster (universal) = 2.57 ± +0.30/-0.30 1e14 Msun [Table 3: "$2.57\substack{+0.30\\-0.30}$"]
- result: point source flux in radio-lobe cluster field = 0.20 ± +0.06/-0.04 mJy [4.3 Unresolved sources: "$i_{\textsc{ps}}=0.20\substack{+0.06\\-0.04}~\mathrm{mJy}$"]
- limitation (authors): Limited angular dynamic range, short integrations and unresolved-source contamination limit mass inference [abstract: "the limited angular dynamic range of the ACA in Band 3 alone, short observational integration times, and possible contamination from unresolved sources"]
- not stated (card): Sampler name and settings (the evidence is computed, but the nested-sampling code is not named); Cluster IDs are missing from the converted tables, so rows cannot be matched to clusters; Spectral-window averaging and uv-data weighting or flagging applied before fitting; Redshift split-normal prior widths per cluster beyond the table values; Exact mass-richness fit procedure and likelihood; Code u…

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

### 2025ApJ...989....7T: The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). VII. Testing Accretion Mechanisms from Disk Population Synthesis (2025; protoplanetary_disks; theory_or_simulation_compared_to_alma)
- question: Which disk evolution scenario (turbulence-driven accretion with photoevaporative winds, or MHD disk-wind-driven accretion) reproduces the AGE-PRO disk gas masses and CO sizes together with disk fractions and accretion rates?
- step 1: Define individual disk evolution models
  - method: 1D vertically integrated disk evolution for two scenarios: turbulence-driven (Shakura-Sunyaev alpha) with photoevaporative wind, and MHD disk-wind with analytical solutions [2.1 Individual disks: "The evolution of an individual disk is computed using a 1D formalism, where the MHD equations are integrated in the vertical direction."]
  - parameter: 4 parameters per disk (M0, R0, generalized alpha, wind mass-loss parameter); MHD model adds omega [2.1 Individual disks: "In both scenarios, the evolution of an individual disk is set by 4 parameters"] [2.1 Individual disks: "For the MHD disk-wind model, an additional parameter, $\omega$, controls the secular evolution of the magnetic field."]
  - parameter: Inner disk radius 0.1 au [2.2.1 Turbulence-driven evolution: "we adopt an inner disk radius of 0.1 au"]
  - parameter: Disk dispersed when stellar accretion rate falls below 1e-12 Msun/yr [2.2.1 Turbulence-driven evolution: "a disk is considered to be dispersed when the stellar accretion rate drops below a threshold of $10^{-12}~M_{\odot}/yr$"]
  - parameter: Total photoevaporative mass-loss rate is a free parameter scaling the Picogna et al. 2021 profile [2.2.1 Turbulence-driven evolution: "we take the total mass-loss rate as a free parameter to scale the mass-loss rate profile"]
  - parameter: MHD analytical solution with alpha_SS = 0, constant lambda and constant alpha_DW across the disk [2.2.2 MHD wind-driven evolution: "in the absence of radial transport of angular momentum ($\alpha_{SS} = 0$)"] [2.2.2 MHD wind-driven evolution: "The analytical solutions further assume a constant $\lambda$ value in space and time and a constant $\alpha_{DW}$ across the disk."]
  - assumption: T proportional to R^-1/2 and aspect ratio 3.33e-2 (M*/1 Msun)^-1/2 at 1 au [2.2.1 Turbulence-driven evolution: "we assume that $T \propto R^{-1/2}$ and $\epsilon(R=1~\text{au}) = 3.33 \times 10^{-2}~(M_*/1M_{\odot})^{-1/2}$"]
  - assumption: Isolated disks, no envelope or streamer feeding; t=0 is the end of Class I [2.1 Individual disks: "We only consider isolated disks that are not fed by any envelope or streamer."] [2.1 Individual disks: "The time $t=0$ can therefore be considered as the end of the Class I phase"]
  - assumption: alpha_SS constant in time and radius; photoevaporative mass-loss rate constant in time [2.2.1 Turbulence-driven evolution: "For simplicity, we assume $\alpha_{SS}$ to be constant in time."] [2.2.1 Turbulence-driven evolution: "We further assume that the mass-loss rate is constant over time."]
  - assumption: External UV irradiation neglected [2.1 Individual disks: "We further neglect the impact of mild external UV irradiation"]
- limitation (authors): Order of fitting matters because no parameter set fits all constraints [4.2 Origin of the discrepancy with turb…: "in the absence of a set of parameters that fits all the constraints, the order in which the observations are fitted matters."]
- limitation (authors): Disk mass is the most uncertain constraint; Ophiuchus and Lupus/Upper Sco masses come from slightly different approaches [4.3.2 Disk gas mass: "Overall, we find that disk mass is a crucial parameter along with accretion rates but indubitably the most uncertain."]
- limitation (authors): Upper Sco median accretion rate is an upper limit because half the sample has upper limits [2.3.1 Observational data: "Therefore, the median value of the accretion rate should be considered as an upper limit."]
- not stated (card): Numerical median values and spreads of disk mass and CO size for Oph, Lupus and Upper Sco (given only graphically in Figure 3, with the per-source AGE-PRO tables in companion papers); Diskpop and Popcorn version, radial grid, time grid, random seed and outer-radius settings; Exact grids of median R0, M0, t_nu,0, omega and f_M explored in each stage, and how the best-fit models were selected from …

### 2024A&A...682A.186L: Feeding and feedback processes in the Spiderweb proto-intracluster medium (2024; galaxy_clusters_and_sz, high_z_galaxies; observational_alma_primary)
- question: Derive the thermodynamic profiles of the Spiderweb proto-ICM (z=2.16), test for a cool core, constrain the classical mass deposition rate and estimate the feedback energy budget, by combining Chandra X-ray density with ALMA SZ pressure
- step 5: Reconstruct SZ pressure profile from ALMA+ACA visibilities
  - method: Bayesian forward modelling of uv-plane visibilities with a line-of-sight integrated gNFW pressure model fitted jointly with a radio-galaxy point-component model; centroid fixed to the X-ray centroid; models combined with Bayesian Model Ave… [5 SZ and X-ray combined analysis: "the SZ distribution is obtained as the line-of-sight integral of a generalized Navarro-Frenk-White (NFW, (cite: 2007Nagai)) pressure distribution, with scaling parameters and radial slopes fixed to match specific formulations from the literature"] [5 SZ and X-ray combined analysis: "we inferred the SZ component jointly with the radio galaxy model, defined by the optimal, ordered set of point-like components, as in (cite: 2023DiMascolo)"]
  - software: dynesty
  - parameter: uv upper threshold 65 klambda [5 SZ and X-ray combined analysis: "We also consistently imposed an upper threshold of $65~\mathrm{k\lambda}$ to the analysed visibilities to make the extended radio galaxy unresolved in the direction orthogonal to the jet axis."]
  - parameter: SZ centroid fixed to X-ray centroid so that only the mass term (M500) is free per pressure model [5 SZ and X-ray combined analysis: "we did, however, fix the centroid position of the SZ model component to match the one derived by modeling the soft-band X-ray surface brightness distribution"] [Pressure models: "In such a way, the parameter set for each parameter reduces to the mass term only."]
  - assumption: Eight literature gNFW pressure profiles considered (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT) [Pressure models: "the self-similar extended pressure model by (cite: 2017Gupta)"]
  - fitting: Nested sampling with dynesty; priors and likelihood details not stated [5 SZ and X-ray combined analysis: "The posterior exploration was performed using the nested sampling algorithm (cite: 2004Skilling; 2022Ashton), as implemented in the `dynesty` package (cite: dynesty; 2022Koposov)."]
  - validation: Model parameters statistically consistent with Di Mascolo et al. 2023; BMA profile used as reference with model variance propagated [5 SZ and X-ray combined analysis: "the parameters for each of the reconstructed models are found to be statistically consistent with the ones reported in (cite: 2023DiMascolo)"] [5 SZ and X-ray combined analysis: "we propagate the variance between the various pressure models in the marginalized posterior distribution"]
- step 7: Derive the temperature profile from SZ pressure and X-ray density
  - method: Marginalize the pressure model realizations within each X-ray annulus, then divide by the binned electron density: kT_e = P_e/n_e [5.2 Pressure and temperature profiles: "we post-processed the pressure profiles to estimate the $P_e(r)$ by marginalizing the values of the analytic realizations within each annulus"] [5.2 Pressure and temperature profiles: "the average electron temperature within a given annulus is finally computed as the ratio $k_{B}T_{e}(r)=P_{e}(r)/n_e(r)$"]
  - assumption: Ideal gas law; relativistic SZ correction negligible (<~1.5%); X-ray spectral temperature not used [5.2 Pressure and temperature profiles: "When simply assuming the ideal gas law"] [5.2 Pressure and temperature profiles: "we do not make use of the information provided by the X-ray spectral analysis"]
  - validation: Compared with the X-ray spectral kT=2.0 keV of Tozzi et al. 2022b; SZ-derived value lower by a factor of ~3, discussed as metallicity, non-thermal contamination or SZ filtering systematics [5.2 Pressure and temperature profiles: "this value is lower by a factor of $\sim 3$ with respect to that obtained in (cite: 2022bTozzi) with the X-ray spectral analysis"]
- result: M500 for A10 UP pressure model = 2.47 ± +0.44/-0.54 1e13 Msun [Table 1: "$2.47\substack{+0.44\\-0.54}$"]
- result: M500 for A10 MD pressure model = 2.01 ± +0.39/-0.49 1e13 Msun [Table 1: "$2.01\substack{+0.39\\-0.49}$"]
- result: M500 for M14 UP pressure model = 2.82 ± +0.53/-0.65 1e13 Msun [Table 1: "$2.82\substack{+0.53\\-0.65}$"]
- result: M500 for M14 NCC pressure model = 2.84 ± +0.53/-0.66 1e13 Msun [Table 1: "$2.84\substack{+0.53\\-0.66}$"]
- result: M500 for L15 REF pressure model = 2.59 ± +0.42/-0.48 1e13 Msun [Table 1: "$2.59\substack{+0.42\\-0.48}$"]
- result: M500 for L15 8.0 pressure model = 4.30 ± +0.55/-0.68 1e13 Msun [Table 1: "$4.30\substack{+0.55\\-0.68}$"]
- result: M500 for L15 8.5 pressure model = 6.54 ± +0.78/-0.95 1e13 Msun [Table 1: "$6.54\substack{+0.78\\-0.95}$"]
- result: M500 for G17 EXT pressure model = 2.20 ± +0.39/-0.55 1e13 Msun [Table 1: "$2.20\substack{+0.39\\-0.55}$"]
- result: Pressure profile average slope = ~1 ± not stated dimensionless [5.2 Pressure and temperature profiles: "with an average slope of $\sim 1,$ which is significantly flatter than the density profile"]
- result: Temperature at ~15 kpc and beyond 100 kpc = ~0.6 keV at ~15 kpc; ~1.8 keV beyond 100 kpc ± not stated keV [5.2 Pressure and temperature profiles: "a clear temperature gradient with value increasing from $\sim 0.6$ keV at $\sim 15$ kpc up to $\sim 1.8$ keV beyond 100 kpc"]
- result: Density-weighted SZ temperature at r>2 arcsec = 0.7 ± 0.3 keV [5.2 Pressure and temperature profiles: "$kT_{SZ,EW}= (0.7 \pm 0.3)$ keV"]
- limitation (authors): Diffuse emission within 2 arcsec of the AGN is not observationally constrained [2.1 Chandra X-ray data: "the surface brightness of the diffuse component within a radius of 2 arcsec is not observationally constrained and was treated as a free parameter"]
- limitation (authors): SZ normalisation may be underestimated because of interferometric filtering of large scales [5.2 Pressure and temperature profiles: "the normalization of the SZ signal may be underestimated compared to the actual pressure distribution due to the impact of the large-scale interferometric filtering"]
- limitation (authors): Low significance of SZ and X-ray signals limits detailed morphological comparison [4 SZ and X-ray combined analysis: "The low significance of both the SZ signal and the X-ray emission from the proto-ICM inevitably limits the possibility of performing a detailed morphological comparison."]
- not stated (card): CASA version and pipeline version for the Band 3 and Band 4 calibration; Flux, bandpass and phase calibrators and the flux-scale uncertainty; Exact Band 4 frequency setup and number of ALMA/ACA execution blocks used; dynesty settings (live points, stopping criterion) and the priors on M500 and radio-galaxy components; Radio-galaxy point-component model and how the 'optimal ordered set' was chosen…

### 2018ApJ...865..157A: Scaling Relations Associated with Millimeter Continuum Sizes in Protoplanetary Disks (2018; protoplanetary_disks; archival_reuse)
- question: How do mm continuum sizes and luminosities of protoplanetary disks scale with each other and with stellar host mass, luminosity and accretion rate, and what do these relations imply?
- step 2: Fit visibility models to derive F_nu, R_eff, L_mm
  - method: Gaussian likelihood comparing observed visibilities with Hankel transforms of Nuker profiles with 9 parameters; effective radius encloses 68% of flux [4.1 Modeling Surface Brightness Profiles: "We adopt a Gaussian likelihood that compares the observed complex visibilities and Hankel transforms of “Nuker" surface brightness profiles (cite: lauer95)"]
  - software: emcee
  - parameter: x = 0.68 encircled luminosity fraction [4.1 Modeling Surface Brightness Profiles: "such that $f_\nu(\varrho_{\rm eff}) = x F_\nu$; we adopt $x = 0.68$"]
  - parameter: L_mm = F_nu (d/140)^2 s [4.1 Modeling Surface Brightness Profiles: "$L_{\rm mm} = F_\nu \times (d/140)^2 \times s$"]
  - assumption: Distances from Gaia DR2 with uniform d prior [4.1 Modeling Surface Brightness Profiles: "Posterior draws for the distance were made following (cite: astraatmadja16), conditioned on parallax measurements and assuming an uniform $d$ prior."]
  - fitting: Affine-invariant ensemble MCMC (emcee) with Tripathi et al. priors; special-case modified priors for 10 faint targets, Sz 91, and a depression model for HK Lup [4.2 Modifications for Special Cases: "we modified the $\varrho_t$ prior for these systems, employing a Gaussian prior with a mean of zero and a width ($\sigma = 0.13\ensuremath{''}$)"]
  - validation: Observed visibility profiles compared with synthetic data from posterior draws [5.1 Surface Brightness Modeling Results: "Figure [\[fig:visgallery\]](#fig:visgallery) compares the observed visibilities with synthetic data generated from random draws from the parameter posterior distributions."]
- result: Median Tb at 40 au = ~5 ± factor of two sd K [5.1 Surface Brightness Modeling Results: "The median $T_b$ at 40 au is $\sim$5 K, with a standard deviation of only a factor of two"]
- limitation (authors): Resolution insufficient to constrain depression in HK Lup; tentative values [4.2 Modifications for Special Cases: "These should be considered tentative values, since the data resolution is not really sufficient to do a proper evaluation of the depression properties"]
- limitation (authors): Lupus multiplicity not thoroughly vetted [Sample: "The Lupus population has not been thoroughly vetted for multiplicity, particularly at sub-arcsecond separations."]
- not stated (card): Exact prior ranges for the Nuker parameters (deferred to Tripathi et al. 2017); Visibility weighting/binning and any uv-range cuts used in the MCMC; emcee walkers, steps, burn-in and convergence criteria; Line-free channels used for continuum visibilities; Exact CASA version; Treatment of ALMA flux scale beyond the 10% factor; Details of the manual tuning of the thick/thin population models; Visi…

### 2020EPJWC.22800009E: SZ contribution to characterize the shape of galaxy cluster haloes (2020; galaxy_clusters_and_sz, cosmology; multi_facility_alma_minor)
- question: Determine cluster baryonic and dark mass distributions, 3D shapes and hydrostatic mass bias using joint X-ray, SZ and lensing analysis.
- step 1: Deproject lensing constraints in the CLUMP-3D framework
  - method: Use X-ray and SZ shape and orientation information to deproject lensing mass and concentration. [Introduction: "In a nutshell, lensing constrains the 2D mass and concentration which are deprojected thanks to the information on shape and orientation from X-ray (surface brightness and temperature) and SZ."]
  - fitting: Bayesian inference for mass, concentration, intrinsic shape and equilibrium status [Introduction: "The mass and concentration can be then determined together with the intrinsic shape and equilibrium status of the cluster as required by precision astronomy through a Bayesian inference method."]
- step 2: Constrain the temperature profile in the proposed joint analysis
  - method: Combine SZ thermal pressure with X-ray gas density. [The case of MACS1206: "to constrain the temperature profile by combining the thermal pressure from SZ and the gas density from X-ray observations"]
- step 3: Fit gas and total-mass shapes in the proposed Heritage analysis
  - method: Fit three-dimensional triaxial ellipses to combined X-ray, SZ and lensing data. [3D analysis in the context of the Herit…: "Multi-probes three-dimensional Bayesian analysis will be applied to combined X-ray, SZ and lensing data to fit three-dimensional triaxial ellipses to the gas and total mass distribution,"]
  - assumption: Three-dimensional triaxial ellipses for gas and total mass [3D analysis in the context of the Herit…: "to fit three-dimensional triaxial ellipses to the gas and total mass distribution"]
  - fitting: Multi-probes three-dimensional Bayesian analysis [3D analysis in the context of the Herit…: "Multi-probes three-dimensional Bayesian analysis will be applied to combined X-ray, SZ and lensing data"]
  - validation: Proposed comparison with ΛCDM predictions after correcting geometrical biases [3D analysis in the context of the Herit…: "assessing their consistency with $\Lambda$CDM predictions and their equilibrium once geometrical biases (like projection) are corrected for."]
- limitation (authors): ALMA and NIKA2 images are very preliminary. [The case of MACS1206: "In Figure [3](#fig:prel), we present very preliminary images from our proprietary ALMA and NIKA2 exposures."]
- limitation (authors): Missing high-resolution SZ data at radial scales from 30 to 100 arcsec. [The case of MACS1206: "We are therefore missing high resolution SZ data at radial scales from 30 to 100 arcsec."]
- limitation (authors): More sensitive observations and a larger cluster sample are needed. [3D analysis in the context of the Herit…: "We need a combination of more sensitive observational data and a larger cluster sample, as available in the Heritage project"]
- not stated (card): ALMA observing band, frequencies, spectral windows and usable continuum bandwidth.; Execution identifiers, observed integration times, configurations and baseline coverage.; Calibration software, calibrators, flagging and flux-scale uncertainty.; SZ imaging or visibility-fitting procedure, weighting, beam, noise and compact-source treatment.; Relative calibration and spatial-filtering treatment w…

### 2019MNRAS.487.4037D: A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145 (2019; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can joint forward-modelling of ALMA/ACA visibilities with Bolocam and Planck images constrain the pressure distribution of RX J1347.5-1145, and does the south-eastern SZ excess indicate a strong overpressure or reflect model geometry?
- step 3: Compare SZ pressure profile to Chandra X-ray pressure
  - method: X-ray pressure from deprojected density times temperature compared with SZ model [5.1.2: "by multiplying the radial profiles of deprojected electron density and temperature distributions"]
  - software: CIAO
  - validation: Good overall agreement within uncertainties [5.1.2: "shows good overall agreement with the X-ray profile within the uncertainties of the two independent determinations"]
- step 5: Classify X-ray perturbations and estimate SZ excess
  - method: X-ray arithmetic in two Chandra bands; crude sphere estimate of dy/y [5.2.1: "The ‘X-ray arithmetic’ method reported in (cite: Churazov2016)"]
  - assumption: Overpressurized sphere radius ~90 kpc, offset ~130 kpc; adiabatic index 5/3 [5.2.1: "sphere of overpressurized gas with radius $\sim 90~\mathrm{kpc}$"]
  - validation: Order-of-magnitude only [X-ray imaging constraints on the nature…: "These are of course only an order-of-magnitude estimates, given the complexity of the cluster and the assumptions made."]
- result: Observed SE excess dy/y = 0.24 ± not stated dimensionless [5.2.1: "$\delta \vary/\vary\sim 0.24$"]
- limitation (authors): Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations [5.2: "a direct comparison based on statistical considerations would provide misleading results"]
- not stated (card): Exact binning parameters and number of averaged visibilities; Planck MILCA implementation details and Y_cyl Gaussian prior; MCMC walkers, steps, burn-in and convergence; Fitting code is not public/versioned; Chandra reduction details and X-ray arithmetic smooth models; Source of 12.5 keV vs 7 keV temperature choices beyond brief description

### 2025A&A...694A.147G: MINDS: The influence of outer dust disc structure on the volatile delivery to the inner disc (2025; protoplanetary_disks, astrochemistry; archival_reuse)
- question: Does the outer dust disc structure seen with ALMA (gaps, cavities, outer radius) influence the molecular emission (H2O, C2H2, HCN, CO2) of the inner disc seen with JWST/MIRI-MRS?
- step 5: Fit the visibilities with a set of Gaussians (radial brightness profile)
  - method: Deprojected visibilities fitted with a sum of Gaussians modulated by cosines via Hankel transform, binned visibilities, MCMC [Visibility fitting: "The model brightness distribution consists of a set of Gaussian functions"] [Visibility fitting: "We bin the visibilities to speed up the fitting process, using the implementation of the FRANKENSTEIN-code (cite: JenningsEA20)"]
  - software: emcee, frankenstein
  - parameter: uv range limits: 2000 klambda (BP Tau, DL Tau, DR Tau, Sz 98, V1094 Sco), 3000 klambda (CI Tau, GW Lup), 1500 klambda (IQ Tau) [Visibility fitting: "For BP Tau, DL Tau, DR Tau, Sz 98, and V1094 Sco we limit the visibilities to $\leq$2000 k$\lambda$, whereas we limit the visibilities of CI Tau and GW Lup to $\leq$3000 k$\lambda$."] [Visibility fitting: "Finally, the visibilities of IQ Tau are limited to $\leq$1500 k$\lambda$."]
  - parameter: Binned visibility widths of 10-20 klambda [Visibility fitting: "the binned visibilities have widths of 1-2$\times$10$^{4}$ $\lambda$ or 10-20 k$\lambda$."]
  - parameter: Only continuum spectral windows for DR Tau, GW Lup, Sz 98 (lower uncertainties) and DL Tau; all spectral windows (lines masked) for the others [Visibility fitting: "In the cases of DR Tau, GW Lup, and Sz 98, we found that the uncertainties of the visibilities of the continuum spectral windows were significantly lower than those when including all spectral windows."]
  - parameter: Minimum number of additional Gaussians giving a good fit to visible features [Visibility fitting: "For our sample, we report the minimum of additional Gaussian functions that results in a good fit to all the visible features in the visibilities."]
  - parameter: MCMC iterations: 2500 (round 1), 10,000 (round 2), final 5000 used for posterior medians [Visibility fitting: "in the first round, we used 2500 iterations to explore the prior space, identifying the best-fit parameters."] [Visibility fitting: "In the second round, we used 10,000 iterations to explore a confined parameter space around these best-fit parameters."]
  - assumption: Literature inclinations and position angles (BP Tau from IMFIT) [ALMA observations: "we use the literature values while fitting the visibilities"]
  - fitting: emcee MCMC; medians with 16th and 84th percentile uncertainties; priors and likelihood not stated [Visibility fitting: "We fit the visibilities using the Markov Chain Monte Carlo (MCMC) implementation of the EMCEE-package (cite: emcee)."] [Visibility fitting: "The lower and upper uncertainties are, respectively, taken to be the 16$^\textnormal{th}$ and 84$^\textnormal{th}$ percentiles."]
  - validation: Convolving the visibility-fit profile with a beam-like Gaussian reproduces the image-plane profile [Radial profiles and snowlines: "Inferring a model profile by convolving the visibility fit with a Gaussian beam, tailored after the ALMA beam, results in a similar profile as that of the ALMA image plane."]
- limitation (authors): Small sample limits statistical conclusions [Correlation coefficient and p value: "However, we note that these quantities must be used with some caution, as the sample size is too small to give conclusive results."]
- limitation (authors): Resolution differences between targets may change apparent gap depth [Gap depth and resolution: "Some substructures that appear to be much deeper in one disc compared to the other, may simply be a result of a resolution difference."]
- limitation (authors): Ages are highly uncertain [Sample: "Ages are generally very uncertain and may be based on different estimation methods."]
- not stated (card): CASA version and whether the archival (pipeline or manual) calibrated measurement sets were used as delivered; Which spectral windows were treated as continuum for each source, and the line masks used on the line windows; Cell size, image size, clean mask, primary beam handling and any uv taper used for the continuum images; Inclination and position angle values per source (table columns lost in …

### 2020ApJ...891...90R: Pressure Profiles and Mass Estimates Using High-resolution Sunyaev-Zel'dovich Effect Observations of Zwicky 3146 with MUSTANG-2 (2020; galaxy_clusters_and_sz; multi_facility_alma_minor)
- question: Can MUSTANG-2 90 GHz SZ data constrain the pressure profile and mass (M500, M2500) of the relaxed cluster Zwicky 3146, and how consistent are different mass estimators?
- step 2: Fit pressure profiles (NP and gNFW) with point sources
  - method: Compton y profile to T_B, matched to Minkasi bins with full covariance; 12 NP bins 5'' to 5'; A10 gNFW [4.2 Pressure profile fitting: "We define twelve bins with twelve logarithmically spaced radii between 5$''$ and 5$'$."]
  - software: emcee
  - parameter: relativistic correction with kT_e = 7 keV; line of sight integration to ±5 R500 [4.2 Pressure profile fitting: "we assume $k_B T_e = 7$ keV"]
  - assumption: spherical symmetry [4.2 Pressure profile fitting: "The choice of adopting spherical symmetry is motivated by (1) the ease of interpretation of results and comparison to the literature"]
  - fitting: emcee MCMC with full covariance likelihood [4.2 Pressure profile fitting: "In both cases, the fitting is done with the MCMC package `emcee` (cite: foreman2013)."]
  - validation: Agreement with XMM pressure profile [7 Conclusions: "The pressure profile recovered is in excellent agreement with the pressure profile derived from *XMM*."]
- limitation (authors): Outermost pressure bin likely biased low; unquantified additional systematic [7 Conclusions: "there is an additional systematic error due the issues discussed in the previous two paragraphs, but which we are currently unable to quantify."]
- not stated (card): Minkasi code/version and availability; MCMC settings and priors for pressure profile fits; Y-M relation parameters (tabulated A,B but sources unnamed in text); Flux calibration uncertainty derivation; Point source fit details

### 2019A&A...629A.104G: Sunyaev-Zel'dovich detection of the galaxy cluster Cl J1449+0856 at z = 1.99: The pressure profile in uv space (2019; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can the thermal SZ decrement of the z=1.99 cluster Cl1449 be detected with ALMA+ACA at 92 GHz after subtracting FIR point sources in uv space, and what do the pressure profile and total mass imply?
- step 3: Fit pressure models and derive mass
  - method: Project GNFW profiles (LeB15, A10, S16, McD14) with fixed shapes, simulate with simalma, compare to uv profile with free mass; chi2 ranking [Modelling: "While we keep the GNFW parameters fixed to the various models’ values, we let the mass vary freely."]
  - software: CASA simalma
  - parameter: Compton-y background 1.6e-6 [Modelling: "including an average Compton-*y* background of $1.6\times10^{-6}$"]
  - assumption: Spherical models; M200 extrapolated from M500 assuming GNFW mass distribution [Modelling: "We here therefore extrapolate $M_{200}$ from $M_{500}$, assuming that the mass distribution follows the GNFW profile."]
  - validation: FFT approximation vs simalma differs at most ~4% [uv plane modelling: "We find a relative difference between both of at most $\sim$4% (Fig. [10](#fig:fft))"]
- step 5: Test SZ-X-ray peak offset significance
  - method: Monte Carlo of simulated A10 decrement with noise from visibility weights, point-source fit with free position [Peak offset significance: "We then perform a point-source extraction with free position, as described in Section [\[cooking\]](#cooking), which we compare to the observed offsets."]
- result: AGN 8.5 model mass = ~1.8e14 ± not stated Msun [Results and discussion: "only AGN 8.5 yields a higher mass of $\sim$$1.8\times10^{14}$ M$_{\odot}$"]
- limitation (authors): Residual positive signal from undetected sources means significance is conservative; S/N too low to strongly constrain pressure models [Conclusions: "The final S/N of the data, conservatively estimated, is not quite high enough to strongly constrain ICM pressure models."]
- not stated (card): CASA version; Fit method/statistic and uncertainty treatment for model amplitude and mass (chi2 minimisation details); How M200 was extrapolated from M500 numerically; simalma setup details (configurations, antenna lists); Point-source subtraction details for source grouping; Details of how ALMA and ACA were weighted when merged; Whether 2012.1.00885.S and 2015.1.01355.S data were used directly (…

### 2020PASJ...72...33K: Deeply cooled core of the Phoenix galaxy cluster imaged by ALMA with the Sunyaev-Zel'dovich effect (2020; galaxy_clusters_and_sz; observational_alma_primary)
- question: How much thermal gas is cooling to low temperatures in the Phoenix cluster core, probed with an ALMA SZE image combined with Chandra X-ray data independent of the X-ray spectrum
- step 5: Derive the Compton y map and compare the inner pressure profile
  - method: Divide ALMA image by c1 = 0.94, subtract mean signal at theta = 42 arcsec, apply relativistic correction with projected X-ray temperature, azimuthally average and compare with generalized NFW pressure profiles of cluster samples [4.3 Compton y-parameter map and the inn…: "the ALMA image was divided by the correction factor for the missing flux of 0.94"] [4.3 Compton y-parameter map and the inn…: "the mean signal (consistent with zero) at $\theta = 42''$ is subtracted"]
  - parameter: Geometrically spaced bins, innermost 0-4 arcsec, size increasing by a factor 1.1 [4.3 Compton y-parameter map and the inn…: "the bins are geometrically spaced with the inner-most bin at $0 < \theta < 4''$ and the size increasing by a factor of 1.1"]
  - assumption: M500 = 8.8e14 h^-1 Msun, r500 = 0.92 h^-1 Mpc at z = 0.597 [4.3 Compton y-parameter map and the inn…: "assuming $M_{500} = 8.8 \times 10^{14} h^{-1} M_{\odot}$ and $r_{500} = 0.92 h^{-1}$Mpc at $z=0.597$ for the Phoenix cluster"]
  - validation: y map morphology consistent with X-rays; inner profile agrees with local cool core expectation [4.3 Compton y-parameter map and the inn…: "overall morphology of the Compton $y$-parameter map does not exhibit deviation from that of X-rays."]
- result: Peak incremental Compton y = 5.3e-4 ± 0.4 (stat) and 0.3 (sys), in units of 1e-4 dimensionless [4.3 Compton y-parameter map and the inn…: "The peak value is $\Delta y = (5.3 \pm 0.4 \mbox{ [statistical]} \pm 0.3 \mbox{ [systematic]})\times 10^{-4}$"]
- limitation (authors): Equation-of-state limit is weak [4.1 Comparison to X-ray data: "While the limit is still weak, the observed perturbations in the Phoenix cluster core is consistent with being isobaric"]
- limitation (authors): Absolute values of the X-ray pseudo pressure are arbitrary [4.1 Comparison to X-ray data: "Note that absolute values of the pseudo pressure are arbitrary"]
- limitation (authors): Temperature at r > 250 kpc cannot be constrained by the ALMA data [4.4 Deprojected electron temperature an…: "As the temperature at $r > 250$ kpc ($\theta > 37''$) cannot be constrained by the ALMA data"]
- not stated (card): Phase centre (target field centre) coordinates are blank in the text; tclean image size, cell size, niter / number of minor cycles, gridder and phasecenter for the 7-pointing mosaic; Calibration CASA/pipeline version and whether QA2 products were used unmodified or re-calibrated; any self-calibration; Starting parameters, weighting and error treatment used in uvmodelfit; source positions are blan…

## All papers in this technique

- 2016ApJ...829L..23B (2016): ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe
- 2018ApJ...865..157A (2018): Scaling Relations Associated with Millimeter Continuum Sizes in Protoplanetary Disks
- 2019A&A...623A.150V (2019): The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN
- 2019A&A...628A.100D (2019): An ALMA+ACA measurement of the shock in the Bullet Cluster
- 2019A&A...629A.104G (2019): Sunyaev-Zel'dovich detection of the galaxy cluster Cl J1449+0856 at z = 1.99: The pressure profile in uv space
- 2019MNRAS.487.4037D (2019): A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145
- 2019MNRAS.490.5134B (2019): Detecting the halo heating from AGN feedback with ALMA
- 2019Natur.570...83M (2019): A cool accretion disk around the Galactic Centre black hole
- 2020A&A...638A..70D (2020): The Massive and Distant Clusters of WISE Survey. SZ effect of Verification with the Atacama Compact Array - Localization and Cluster Analys…
- 2020ApJ...891...90R (2020): Pressure Profiles and Mass Estimates Using High-resolution Sunyaev-Zel'dovich Effect Observations of Zwicky 3146 with MUSTANG-2
- 2020EPJWC.22800009E (2020): SZ contribution to characterize the shape of galaxy cluster haloes
- 2020PASJ...72...33K (2020): Deeply cooled core of the Phoenix galaxy cluster imaged by ALMA with the Sunyaev-Zel'dovich effect
- 2021A&A...650A.153D (2021): Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger a…
- 2021MNRAS.503.1174K (2021): Feedback factory: multiple faint radio jets detected in a cluster at z = 2
- 2021MNRAS.503.1459B (2021): Dynamical model of an obscuring clumpy torus in AGNs - I. Velocity and velocity dispersion maps for interpretation of ALMA observations
- 2024A&A...682A..55M (2024): High-resolution ALMA observations of compact discs in the wide-binary system Sz 65 and Sz 66
- 2024A&A...682A.186L (2024): Feeding and feedback processes in the Spiderweb proto-intracluster medium
- 2024A&A...689A..41V (2024): XLSSC 122 caught in the act of growing up: Spatially resolved SZ observations of a z = 1.98 galaxy cluster
- 2024ApJ...969...56M (2024): Observational Constraints on Sunyaev─Zeldovich Effect Halos around High-z Quasars
- 2025A&A...694A.147G (2025): MINDS: The influence of outer dust disc structure on the volatile delivery to the inner disc
- 2025ApJ...989....7T (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). VII. Testing Accretion Mechanisms from Disk Population Synthesis
